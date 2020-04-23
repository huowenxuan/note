[TOC]

## 6 模型融合

推荐系统三个阶段

1. 挖掘：离线进行

2. 召回：物品太多，从全量物品中筛选部分可靠物品，舍弃大部分物品的同时保证好的效果

   通过各种推荐算法生成推荐结果

3. 排序：对上一步的推荐结果进行排序，是否推荐给用户，由融合模型说了算

融合模型的作用可以统一各个模型，还可以提升效果

###逻辑回归和梯度提升决策树组合 

常见，开源成熟，落地快

逻辑回归**LR**用来执行**CTR**预估。逻辑回归是广义线性模型，对非线性关系无能为力。需要两个东西：

1. 特征

   把用户-物品的组合表示为向量或数字、布尔类型，值可是是用户年龄、该品类的开销、白天晚上、省份代表的数字等

   数据库字段转为特征：

   1. 独热编码。枚举值，例如三个类别可变为 001 010  100
   2. 特征分段。“是否是”可变为布尔值；连续值可分段，例如热度可分为0,50 51,100...
   3. 特征变换。把连续值变到有限的值域内，例如0-1，或做离散化

2. 权重

   每个特征都有权重，需要模型从大量历史数据中学习。希望越多权重为0越好，降低计算复杂度；并且可在线学习，不断更新

   经典的方法有梯度下降，树模型可天然肩负起特征组合的任务，梯度提升决策树（GBDT），对原始的特征进行有效的组合，一棵树的一个叶子节点就是一种特征组合

缺点：

1. 两两组合导致特征维度灾难
2. 组合后的特征大部分无效
3. 组合后的样本稀疏，有空组合，但并不能找到符合组合特征的样本，没办法为这个组合训练有效参数（无法学习到参数权重）

### 因子分解机 FM

可代替逻辑回归，用隐因子向量的点积代替单个权重参数，可用来做模型融合

FFM为因子分解机的扩展模型，认为特征和特征之间有某种关系

开源实现有libfm、libffm、xlearn(c++、命令行、Python、R)，xlearn输入格式为libsvm(最普遍的稀疏样本采用的格式)，包含LR、FM、FFM（模型文件依次显著增大）

```python
import xlearn as xl

param = {'task':'binary', 'lr':0.2,
         'epoch': 20, 'k':2,
         'lambda':0.002, 'metric':'auc'}

train_data = "../../data/criteo_conversion_logs/small_train.txt"
test_data = "../../data/criteo_conversion_logs/small_test.txt"

lr_model = xl.create_linear()
lr_model.setTrain(train_data)
lr_model.setValidate(test_data)
lr_model.setTest(test_data)
lr_model.setSigmoid()
lr_model.fit(param, './lr_model.out')

fm_model = xl.create_fm()
fm_model.setTrain(train_data)
fm_model.setValidate(test_data)
fm_model.setTest(test_data)
fm_model.setSigmoid()
fm_model.fit(param, './fm_model.out')

ffm_model = xl.create_ffm()
ffm_model.setTrain(train_data)
ffm_model.setValidate(test_data)
ffm_model.setTest(test_data)
ffm_model.setSigmoid()
ffm_model.fit(param, './ffm_model.out')
```

### Wide & Deep 模型

特征工程+线性模型为宽(wide)模型，深度神经网络是深(deep)模型。深度学习，可以更精准表达用户和物品的关系，但是可解释性不好。Wide&Deep为两者结合。  

模型训练完成后，每次请求都输入用户特征和内容列表，对每个内容进行评分，评分用W&D模型计算，再按计算的CTR从高到低排序；为了达到10ms响应，多线程并行批量计算内容

```python
from __future__ import absolute_import
from __future__ import division
from __future__ import print_function

import argparse
import shutil
import sys
import tempfile

import pandas as pd
from six.moves import urllib
import tensorflow as tf

"""
构建特征
深模型使用数值模型和编码后的类别特征（indicator编码用于可枚举值、embedding用于无法枚举的值，例如文本关键字）
"""
CSV_COLUMNS = [
    "age", "workclass", "fnlwgt", "education", "education_num",
    "marital_status", "occupation", "relationship", "race", "gender",
    "capital_gain", "capital_loss", "hours_per_week", "native_country",
    "income_bracket"
]

gender = tf.feature_column.categorical_column_with_vocabulary_list(
    "gender", ["Female", "Male"])
education = tf.feature_column.categorical_column_with_vocabulary_list(
    "education", [
        "Bachelors", "HS-grad", "11th", "Masters", "9th",
        "Some-college", "Assoc-acdm", "Assoc-voc", "7th-8th",
        "Doctorate", "Prof-school", "5th-6th", "10th", "1st-4th",
        "Preschool", "12th"
    ])
marital_status = tf.feature_column.categorical_column_with_vocabulary_list(
    "marital_status", [
        "Married-civ-spouse", "Divorced", "Married-spouse-absent",
        "Never-married", "Separated", "Married-AF-spouse", "Widowed"
    ])
relationship = tf.feature_column.categorical_column_with_vocabulary_list(
    "relationship", [
        "Husband", "Not-in-family", "Wife", "Own-child", "Unmarried",
        "Other-relative"
    ])
workclass = tf.feature_column.categorical_column_with_vocabulary_list(
    "workclass", [
        "Self-emp-not-inc", "Private", "State-gov", "Federal-gov",
        "Local-gov", "?", "Self-emp-inc", "Without-pay", "Never-worked"
    ])

# 针对“取值不能提前枚举”的类别特征，使用hash
occupation = tf.feature_column.categorical_column_with_hash_bucket(
    "occupation", hash_bucket_size=1000)
native_country = tf.feature_column.categorical_column_with_hash_bucket(
    "native_country", hash_bucket_size=1000)

# Continuous base columns.
age = tf.feature_column.numeric_column("age")
education_num = tf.feature_column.numeric_column("education_num")
capital_gain = tf.feature_column.numeric_column("capital_gain")
capital_loss = tf.feature_column.numeric_column("capital_loss")
hours_per_week = tf.feature_column.numeric_column("hours_per_week")

# 离散化
age_buckets = tf.feature_column.bucketized_column(
    age, boundaries=[18, 25, 30, 35, 40, 45, 50, 55, 60, 65])

# Wide columns and deep columns.
base_columns = [
    gender, education, marital_status, relationship, workclass, occupation,
    native_country, age_buckets,
]

crossed_columns = [
    tf.feature_column.crossed_column(
        ["education", "occupation"], hash_bucket_size=1000),
    tf.feature_column.crossed_column(
        [age_buckets, "education", "occupation"], hash_bucket_size=1000),
    tf.feature_column.crossed_column(
        ["native_country", "occupation"], hash_bucket_size=1000)
]

deep_columns = [
    # indicator编码用于可枚举值
    tf.feature_column.indicator_column(workclass),
    tf.feature_column.indicator_column(education),
    tf.feature_column.indicator_column(gender),
    tf.feature_column.indicator_column(relationship),
    # embedding用于无法枚举的类别特征
    tf.feature_column.embedding_column(native_country, dimension=8),
    tf.feature_column.embedding_column(occupation, dimension=8),
    age,
    education_num,
    capital_gain,
    capital_loss,
    hours_per_week,
]


def maybe_download(train_data, test_data):
  """Maybe downloads training data and returns train and test file names."""
  if train_data:
    train_file_name = train_data
  else:
    train_file = tempfile.NamedTemporaryFile(delete=False)
    urllib.request.urlretrieve(
        "https://archive.ics.uci.edu/ml/machine-learning-databases/adult/adult.data",
        train_file.name)  # pylint: disable=line-too-long
    train_file_name = train_file.name
    train_file.close()
    print("Training data is downloaded to %s" % train_file_name)

  if test_data:
    test_file_name = test_data
  else:
    test_file = tempfile.NamedTemporaryFile(delete=False)
    urllib.request.urlretrieve(
        "https://archive.ics.uci.edu/ml/machine-learning-databases/adult/adult.test",
        test_file.name)  # pylint: disable=line-too-long
    test_file_name = test_file.name
    test_file.close()
    print("Test data is downloaded to %s"% test_file_name)

  return train_file_name, test_file_name


def build_estimator(model_dir, model_type):
  """
  训练模型
  """
  if model_type == "wide":
    # LinearClassifier线性分类器: 以为0/1特征为代表的wide_columns及交叉特征
    m = tf.estimator.LinearClassifier(
        model_dir=model_dir, feature_columns=base_columns + crossed_columns)
  elif model_type == "deep":
    # DNNClassifier DNN分类器: 以数值型特征、Embedding特征为代表的deep_columns
    m = tf.estimator.DNNClassifier(
        model_dir=model_dir,
        feature_columns=deep_columns,
        hidden_units=[100, 50])
  else:
    # DNNLinearCombinedClassifier 复合分类器
    m = tf.estimator.DNNLinearCombinedClassifier(
        model_dir=model_dir,
        linear_feature_columns=crossed_columns,
        dnn_feature_columns=deep_columns,
        dnn_hidden_units=[100, 50])
  return m


def input_fn(data_file, num_epochs, shuffle):
  """训练样本，对原始样本做处理"""
  df_data = pd.read_csv(
      tf.gfile.Open(data_file),
      names=CSV_COLUMNS,
      skipinitialspace=True,
      engine="python",
      skiprows=1)
  # remove NaN elements
  df_data = df_data.dropna(how="any", axis=0)
  # 收入大于50k
  labels = df_data["income_bracket"].apply(lambda x: ">50K" in x).astype(int)
  return tf.estimator.inputs.pandas_input_fn(
      x=df_data,
      y=labels,
      batch_size=100,
      num_epochs=num_epochs,
      shuffle=shuffle,
      num_threads=5)


def train_and_eval(model_dir, model_type, train_steps, train_data, test_data):
  """Train and evaluate the model."""
  train_file_name, test_file_name = maybe_download(train_data, test_data)
  # Specify file path below if want to find the output easily
  model_dir = tempfile.mkdtemp() if not model_dir else model_dir

  m = build_estimator(model_dir, model_type)
  # set num_epochs to None to get infinite stream of data.
  m.train(
      input_fn=input_fn(train_file_name, num_epochs=None, shuffle=True),
      steps=train_steps)
  # set steps to None to run evaluation until all data consumed.
  results = m.evaluate(
      input_fn=input_fn(test_file_name, num_epochs=1, shuffle=False),
      steps=None)
  print("model directory = %s" % model_dir)
  for key in sorted(results):
    print("%s: %s" % (key, results[key]))
  # Manual cleanup
  shutil.rmtree(model_dir)


FLAGS = None


def main(_):
  train_and_eval(FLAGS.model_dir, FLAGS.model_type, FLAGS.train_steps,
                 FLAGS.train_data, FLAGS.test_data)


if __name__ == "__main__":
  parser = argparse.ArgumentParser()
  parser.register("type", "bool", lambda v: v.lower() == "true")
  parser.add_argument(
      "--model_dir",
      type=str,
      default="",
      help="Base directory for output models."
  )
  parser.add_argument(
      "--model_type",
      type=str,
      default="wide_n_deep",
      help="Valid model types: {'wide', 'deep', 'wide_n_deep'}."
  )
  parser.add_argument(
      "--train_steps",
      type=int,
      default=2000,
      help="Number of training steps."
  )
  parser.add_argument(
      "--train_data",
      type=str,
      default="",
      help="Path to the training data."
  )
  parser.add_argument(
      "--test_data",
      type=str,
      default="",
      help="Path to the test data."
  )
  FLAGS, unparsed = parser.parse_known_args()
  tf.app.run(main=main, argv=[sys.argv[0]] + unparsed)
```

## 7 探索和利用

解决冷启动和探索新兴趣

### MAB问题和Bandit算法

MAB多臂老虎机问题，关于选择的问题，都可简化为MAB问题，冷启动、探索与利用（EE）问题（不断探索用户新兴趣）都是MAB问题，在不确定中试错找到一定程度的确定性

解决MAB的一类Bandit算法，关键元素：

* 臂：每次推荐要选择候选池，推荐策略或物品类别
* 回报：用户是否喜欢推荐结果
* 环境：无法控制的因素——用户

核心思想是：看选择会带来多少遗憾，好坏的指标就是累计遗憾，越少越好。套路是小心的试，确定某个选项好就多选择，不好就少选择，不确定就多选择

对比不同的Bandit算法效果：那个算法累计遗憾增长的慢，就是效果好

* 汤普森采样算法

  每次选择时候，每个臂的概率分布（贝塔分布）独自产生一个随机数（收益越好，分布越窄，越在中心，越接近1），按照这个随机数排序，输出最大的臂对应的物品

  有效，一行代码可实现，简单的数学基础。要为每个用户保存一套参数，臂有m个，用户有n个，就要保存2mn个参数（每个臂有两个参数α和β）

  效果最好，最简单

* UCB算法

  置信区间上界，为每个臂评分，选择评分最高的，输出后观察反馈，更新参数

* Epsilon贪婪算法

  朴素，简单有效

Bindit是动态的推荐过程；所有的Bindit算法同时处理的臂数不能太多，通常几百个，太多计算代价太大

```python
import numpy as np
from numpy.random import beta
import matplotlib.pyplot as plt

class Bandit(object):

    def __init__(self, arm_priority):
        self._cumulative_regret_list = []
        self._cumulative_regret = 0
        self._priority = arm_priority
        self._best= np.max(self._priority)
        self._win_of_arms = np.zeros(len(arm_priority))
        self._loss_of_arms = np.zeros(len(arm_priority))

    def pull(self, arm):
        return int(np.random.rand() < self._priority[arm])

    def select(self):
        raise Exception('not implement')

    def update(self, arm, reward):
        self._win_of_arms[arm] += reward
        self._loss_of_arms[arm] += 1 - reward
        regret = self._best - self._priority[arm]
        self._cumulative_regret += regret
        self._cumulative_regret_list.append(
            self._cumulative_regret)

    def simulate(self):
        arm = self.select()
        reward = self.pull(arm)
        self.update(arm, reward)
    
    @property
    def cumulative_regret(self):
        return self._cumulative_regret

    @property
    def cumulative_regret_list(self):
        return self._cumulative_regret_list

class ThompsonSamplingBandit(Bandit):

    def __init__(self, arm_priority):
        Bandit.__init__(self, arm_priority)

    def select(self):
        randoms = beta(1+self._win_of_arms, 1+self._loss_of_arms)
        return np.argmax(randoms)

class UCBBandit(Bandit):

    def __init__(self, arm_priority):
        Bandit.__init__(self, arm_priority)
        self._trials = 0
        self._avg_reward = np.zeros(len(arm_priority))

    def select(self):
        trial_of_arms = self._win_of_arms + self._loss_of_arms
        avg = self._avg_reward
        avg += np.sqrt(2*np.log(1+self._trials)/(1+trial_of_arms)) 
        return np.argmax(avg)

    def update(self, arm, reward):
        Bandit.update(self, arm, reward)
        self._trials += 1
        trials_of_arm = self._win_of_arms[arm] + self._loss_of_arms[arm]
        self._avg_reward[arm] = ((trials_of_arm - 1)*self._avg_reward[arm]
                            + self._win_of_arms[arm])/trials_of_arm


class EpsilonGreedyBandit(Bandit):

    def __init__(self, arm_priority, epsilon, min_trials = 0):
        Bandit.__init__(self, arm_priority)
        self._epsilon = epsilon
        self._avg_reward = np.zeros(len(arm_priority))
        self._trials = 0
        self._min_trials =  min_trials

    def select(self):
        if (np.random.rand() < self._epsilon
            or self._trials <  self._min_trials):
            return np.random.choice(range(len(self._win_of_arms)))
        arm = np.argmax(self._avg_reward)
        return arm

    def update(self, arm, reward):
        Bandit.update(self, arm, reward)
        self._trials += 1
        trials_of_arm = self._win_of_arms[arm] + self._loss_of_arms[arm]
        self._avg_reward[arm] = self._win_of_arms[arm]/trials_of_arm
#        self._avg_reward[arm] = ((trials_of_arm - 1)*self._avg_reward[arm]
#                            + self._win_of_arms[arm])/trials_of_arm
    

if __name__ == '__main__':
    priority = [0.15, 0.20, 0.42]
    name1, bandit_1 = "ThompsonSampling", ThompsonSamplingBandit(priority)
    name2, bandit_2 = "UCB", UCBBandit(priority)
    name3, bandit_3 = "greedy", EpsilonGreedyBandit(priority, 0)
    name5, bandit_5 = "epsilon0.05", EpsilonGreedyBandit(priority, 0.05)
    name8, bandit_8 = "random", EpsilonGreedyBandit(priority, 1)
    name9, bandit_9 = "greedy-naive", EpsilonGreedyBandit(priority, 3)
    t = 1000
    for i in range(t):
        bandit_1.simulate()
        bandit_2.simulate()
        bandit_3.simulate()
        bandit_5.simulate()
        bandit_8.simulate()
        bandit_9.simulate()
   
    c1, = plt.plot(range(t), bandit_1.cumulative_regret_list)
    c2, = plt.plot(range(t), bandit_2.cumulative_regret_list)
    c3, = plt.plot(range(t), bandit_3.cumulative_regret_list)
    c5, = plt.plot(range(t), bandit_5.cumulative_regret_list)
    c8, = plt.plot(range(t), bandit_8.cumulative_regret_list)
    c9, = plt.plot(range(t), bandit_9.cumulative_regret_list)

    plt.ylabel('cumulative regret')
    plt.xlabel('t')
    plt.legend(handles= [c1, c2, c3, c5,  c8, c9],
               labels = [name1, name2, name3, name5, name8, name9],
               loc = 'best')
    plt.show()
```

解决冷启动：

* 用分类或Topic表示每个用户的兴趣，通过几次试验，刻画出新用户心中对每个Topic的感兴趣程度
* 如果用户对某Topic感兴趣，就表示我们得到了收益，如果给用户推荐了不感兴趣的Topic，推荐系统就表示很遗憾了（效果一般？）
* 针对每个新用户，用汤普森采样为每个Topic采样一个随机数，排序后，输出采样值Top K的推荐物品。这里一次性选择了Top K个臂
* 等待获取用户反馈，没有反馈则直接更新对应Topic的β值，用户点击则更新α值

### 加入特征的UCB算法

前面的算法都没有使用臂的特征信息（特征是机器学习的核心要素），对于新加入的臂，只能从零开始积累

雅虎提出了LinUCB算法，加入特征信息，每次估算臂的置信区间时，不仅会根据实验，也会根据特征信息来进行估算

构建用户特征：

* 人口统计学：性别（2类）、年龄（离散成10个区间）
* 地域信息
* 行为类别：代表用户历史行为的1000个类别取值

内容特征：

* 几十个类别
* 内容标签

用户矩阵和内容矩阵都归一化变成单位向量，再用逻辑回归拟合用户对文章的点击行为矩阵，预测点击与否的概率，训练后得到矩阵：把用户的特征空间映射到物品的特征空间，相当于用户特征降维。最后对投影后的特征对用户聚类，得到5个类，文章也聚类成5个类，加上常数1，用户和文章各自被表示成6维向量，就可以应用LinUCB了

```python
import numpy as np
import scipy as sp
from scipy import linalg

"""
推荐、更新模型参数
"""
class LinUCB(object):

    def __init__(self, alpha = 0.25,
                 r1 = 0.8, r0 = 0,
                 d = 2, arms = []):
        self._alpha = alpha
        self._r1 = r1
        self._r0 = r0
        self._d = d
        self._arms = arms
        self._Aa = []
        self._AaI = []
        self._ba = []
        self._theta = []
        for arm in range(len(self._arms)):
            self._Aa.append(np.identity(d))
            self._ba.append(np.zeros((d, 1)))
            self._AaI.append(np.identity(d))
            self._theta.append(np.zeros((d, 1)))
        self._x = None
        self._xT = None

    def pull(self, arm):
        return int(np.random.rand() < self._arms[arm])

    def select(self, user_feature = None):
        if not user_feature:
            user_feature = np.identity(self._d)
        # context feature d x 1
        xaT = np.array([user_feature])
        xa = np.transpose(xaT)
        arm_count = len(self._arms)
        AaI_tmp = np.array([self._AaI[arm] for arm in range(arm_count)])
        theta_tmp = np.array([self._theta[arm] for arm in range(arm_count)])
        expected_reward = np.array([np.dot(xaT, self._theta[arm])
                                    for arm in range(arm_count)])
        bound = np.array([self._alpha * np.sqrt(np.dot(np.dot(xaT,
                                                              self._AaI[arm]),
                                                       xa))
                          for arm in range(arm_count)])
        confidence_bound = expected_reward + bound
        selected_arm = np.argmax(confidence_bound)

        self._x = xa
        self._xT = xaT
        return selected_arm

    def update(self, arm, reward):
        r = self._r1 if reward == 1 else self._r0
        self._Aa[arm] += np.dot(self._x, self._xT)
        self._ba[arm] += r * self._x
        self._AaI[arm] = linalg.solve(self._Aa[arm], np.identity(self._d))
        self._theta[arm] = np.dot(self._AaI[arm], self._ba[arm])

    def simulate(self, user):
        arm = self.select(user)
        reward = self.pull(arm)
        self.update(arm, reward)
        return arm


if __name__ == '__main__':
    arms = [0.8, 0.3]
    linucb = LinUCB(arms = arms)
    users = [[1,0], [0, 1]]
    t = 10
    for i in range(t):
        for user in users:
            arm = linucb.simulate(user)
```

### Bandit与协同过滤

COFIBA算法：根据用户对物品偏好不同，将用户分为不同的群体，在下一次由用户所在的群体集体预估物品可能的收益，这个集体就有了协同效果，再实时根据用户的真实反馈，更新用户的个人参数用于下次调整收益和置信区间。和LinUCB的区别是针对所在集体而不是个人

（原理和过程没写，太复杂，需要时候根据步骤自行总结）

```python
import numpy as np
import networkx as nx
import math
from scipy.sparse import csr_matrix
from scipy.sparse.csgraph import connected_components as cc

class Item(object):
    """
    Item 类，两个元素：
    _id -- Item ID
    _feature -- 特征向量
    """

    def __init__(self, item_id, feature, priority):
        self._id = item_id
        self._feature = feature
        self._priority = priority

    def pull(self):
        return int(np.random.rand() < self._priority)

    @property
    def id(self):
        return self._id

    @property
    def x(self):
        return self._feature

    @property
    def feature(self):
        return self._feature

class User(object):
    """
    User 类， 单个用户的诸多参数，同LinUCB中的参数
    """
    def __init__(self, d, lambda_, uid):
        '''
        personal parameters:
        '''
        self._d = d
        self._reward = 0
        self._A = lambda_*np.identity(n = self._d)
        self._b = np.zeros(self._d)
        self._AI = np.linalg.inv(self._A)
        self._theta = np.zeros(self._d)
        self._I = lambda_ * np.identity(n = d)
        '''
        cluster parameters:
        '''
        self._avg_A = self._A
        self._avg_b = self._b
        self._avg_AI = np.linalg.inv(self._avg_A)
        self._avg_theta = np.dot(self._avg_AI, self._avg_b)

    def update(self, x, reward, alpha_2):
        self._A += np.outer(x,x)
        self._b += x * reward
        self._AI = np.linalg.inv(self._A)
        self._theta = np.dot(self._AI, self._b)

    def update_cluster_avg_parameters(self, clusters, uid, graph, users):
        self._avg_A = self._I
        self._avg_b = np.zeros(self._d)
        for i in range(len(clusters)):
            if clusters[i] == clusters[uid]:
                self._avg_A += (users[i]._A - self._I)
                self._avg_b += users[i]._b
        self._avg_AI = np.linalg.inv(self._avg_A)
        self._avg_theta = np.dot(self._avg_AI, self._avg_b)

    def predict(self, alpha, x, trials):
        expected_reward = np.dot(self._avg_theta, x)
        bound = np.sqrt(np.dot(np.dot(x, self._avg_AI),  x))
        ucb = expected_reward + alpha * bound * np.sqrt(math.log10(trials + 1))
        return ucb

class Cofiba(object):
    def __init__(self, d, alpha, alpha_2, lambda_, user_count, item_count):
        self._trials = 0
        self._d = d
        self._alpha = alpha
        self._alpha_2 = alpha_2
        self._item_count = item_count
        self._user_count = user_count
        self._users = [User(d, lambda_, i) for i in range(user_count)]
        self._item_graph = np.ones([self._item_count, self._item_count])
        cluster_count, item_clusters = cc(csr_matrix(self._item_graph))
        self._cluster_count_of_item = cluster_count
        self._item_clusters = item_clusters
        self._user_graph = []
        self._user_clusters = []
        for i in range(self._cluster_count_of_item):
            self._user_graph.append(np.ones([user_count, user_count]))
            _, user_clusters = cc(csr_matrix(self._user_graph[i]))
            self._user_clusters.append(user_clusters)
  
    @property
    def alpha(self):
        return self._alpha

    @property
    def trials(self):
        return self._trials

    @property
    def alpha_2(self):
        return self._alpha_2

    @property
    def users(self):
        return self._users

    def get_item_cluster(self, item):
        return self._item_clusters[item]

    def select(self, items, uid):
        max_exptected_reward = -1
        item_selected = None
        for item in items:
            item_cluster_index = self._item_clusters[item._id]
            self.update_user_clusters(uid, item._feature, item_cluster_index)
            user = self._users[uid]
            user_cluster = self._user_clusters[item_cluster_index]
            user.update_cluster_avg_parameters(user_cluster,
                                               uid,
                                               self._user_graph,
                                               self._users)
            ucb_prob = self._users[uid].predict(self.alpha,
                                                item._feature,
                                                self._trials)
            if max_exptected_reward < ucb_prob:
                item_selected = item.id
                feature = item._feature
                max_exptected_reward = ucb_prob
        self._trials += 1
        return item_selected

    def update_user_clusters(self, uid, feature, item_cluster_index):
        n = len(self._users)
        user_expected_reward = np.dot(self._users[uid]._theta, feature)
        user_cb = np.sqrt(np.dot(np.dot(feature, self._users[uid]._AI),  feature)) 
        trials_alpha = np.sqrt(np.log10(self._trials + 1))
        for j in range(n):
            theta = self._users[j]._theta
            AI = self._users[j]._AI
            expected_reward = np.dot(theta, feature)
            user_cb = np.sqrt(np.dot(np.dot(feature, AI), feature))
            center_distance = math.fabs(user_expected_reward - expected_reward)
            bounds = self.alpha_2 * (user_cb + user_cb) * trials_alpha
            if center_distance > bounds:
                self._user_raph[item_cluster_index][uid][j] = 0
                self._user_graph[item_cluster_index][j][uid] = 0

        user_graph = csr_matrix(self._user_graph[item_cluster_index])
        cluster_count, user_clusters = cc(user_graph)
        self._user_clusters[item_cluster_index] = user_clusters
        return cluster_count

    def update_item_clusters(self, uid, item_selected, items):
        m = self._item_count
        n = self._user_count
        user_neighbor = {}
        item_cluster_index = self.get_item_cluster(item_selected)
        trials_alpha = np.sqrt(np.log10(self._trials + 1))
        AI1 = self._users[uid]._AI
        for item in items:
            if self._item_graph[items[item_selected].id][item._id] == 1:
                user_neighbor[item._id] = np.ones([n,n])
                for i in range(n):
                    theta1 = self._users[uid]._theta
                    feature = item._feature
                    theta2 = self._users[i]._theta
                    center_distance = math.fabs(np.dot(theta1, feature)
                                     - np.dot(theta2, feature))
                    AI2 = self._users[i]._AI
                    expected_reward1 = np.sqrt(np.dot(np.dot(feature, AI1), feature))
                    expected_reward2 = np.sqrt(np.dot(np.dot(feature, AI2), feature))
                    bounds = self.alpha_2 * (expected_reward1 + expected_reward2)
                    bounds *= trials_alpha
                    if center_distance > bounds:
                        user_neighbor[item._id][uid][i] = 0
                        user_neighbor[item._id][i][uid] = 0
                if not np.array_equal(user_neighbor[item._id],
                                      self._user_graph[item_cluster_index]):
                    self._item_graph[item_selected._id][item._id] = 0
                    self._item_graph[item._id][item_selected._id] = 0
        item_graph = csr_matrix(self._item_graph)
        self._cluster_count_of_item, self._item_clusters = cc(item_graph)

        self._user_graph = []
        self._user_clusters = []
        n = self._user_count
        for i in range(self._cluster_count_of_item):
            self._user_graph.append(np.ones([n, n]))
            cluster_count, user_clusters = cc(csr_matrix(self._user_graph[i]))
            self._user_clusters.append(user_clusters)
        return self._cluster_count_of_item

if __name__ == '__main__':
    lambda_ = 0.1
    alpha  = 0.2
    d = 5
    alpha_2 = 2.0
    item_count = 100
    user_count = 100
    items = [Item(i, np.random.rand(d), np.random.rand())
                for i in range(item_count)]
    cofiba = Cofiba(d = d,
                    alpha = alpha,
                    alpha_2 = alpha_2,
                    lambda_ = lambda_,
                    user_count = user_count,
                    item_count = item_count)
    uid = 5

    item_selected = cofiba.select(items, uid)
    reward = items[item_selected].pull()
    cofiba.users[uid].update(items[item_selected].feature,
                             reward,
                             alpha_2)
    cofiba.update_user_clusters(uid,
                                items[item_selected].feature,
                                cofiba.get_item_cluster(item_selected))
    cofiba.update_item_clusters(uid,
                                item_selected,
                                items)
```

## 9 其他算法

### 排行榜

热门榜也是非常重要的推荐算法。1）解决冷启动。2）老用户发现兴趣。3）当推荐系统出问题或者无任何推荐时，排行榜作为兜底策略

按点赞数、转发数、评论数、销量排序的缺点：1）容易刷榜。2）马太效应，热门物品永远在榜单。3）不能反映不同时间段的变化，同样马太效应

**考虑时间因素**

Hacker News计算热度分数算法。排行榜想象成梯子，物品在梯子上随着时间下降，增加热度可以抵挡重力

> $P-1/(T+2)^G$
>
> P 帖子得票数，减去作者自己的投票
>
> T 帖子发布距离现在的小时数
>
> G 帖子热度重力因子，越大热度分数衰减越快 0.5，1.2，1.5，1.8

牛顿冷却算法。关注度如温度，物体冷却速度和当前温度与环境温度之差成正比

> $T(t) = H + Ce^{-αt}$
>
> H 环境温度，可以是平均投票数，如平均销量，不影响排序，可忽略
>
> t 物品存在小时
>
> C 净剩票数，t时刻物品已经得到的票数
>
> α 冷却系数，自然冷却的速度
>
> | 过去24小时后票数翻多少倍才能保证热度不变 | Α    |
> | ---------------------------------------- | ---- |
> | 翻倍                                     | 0.03 |
> | 增加2倍                                  | 0.05 |
> | 增加3倍                                  | 0.06 |
> | 增加300倍                                | 0.24 |

**考虑好评率**（评分）

威尔逊区间，为每个物品计算出威尔逊区间后，使用bandit算法，使用类似UCB算法的方式取出物品，构建排行榜

*贝叶斯平均*

### 采样算法

问题：保留多少用户兴趣标签

加权采样，每次召回不使用全部的用户标签，按照权重采样一部分标签来使用。好处：

1. 减少召回的时间复杂度
2. 保留更多用户标签
3. 每次召回时标签还能有所变化
4. 依然受标签权重大小制约

**有限数据集**

已知样本总量。希望每次输出一部分标签，每次的标签都不一样，但又能反映权重，输出的概率和权重成正比

针对每个标签计算，前k个就是采样结果

> $S_i = R^{1/w_i}$
>
> $w_i$ 第i个标签的权重
>
> R 遍历第i个标签时产生的0-1之间随机数
>
> $S_i$ 第i个标签的采样分数，用于排序选择结果

**无限数据集（流式数据）**

不知样本总量，或者总量太大，不愿意遍历（流采样）。使用蓄水池采样，可对推荐结果采样，将采样结果用于质量监控，也可以对用户实时行为采样，实时计算推荐结果。加权蓄水池可用于对内容按热度采样输出

例如有n个样本，取出k个，蓄水池采样：

1. 先取出前k个留着，随时准备输出
2. 从第k+1个开始，每个都以k/n的概率替换k个样本中的一个

加权蓄水池采样：

1. 为每个样本生成一个分数，分时使用有限数据集算出
2. 如果推荐结果不足k，则将这个新的样本直接保存到推荐结果
3. 如果已有k个，对比分数，如果小于k个样本中最小的，就替换它（排序）

### 重复检测

消费端避免采集到重复的内容，消费端防止用户消费到重复的内容

**生成端的重复检测**

检测内容重复，主要用于抓取数据

Simhash算法：希望只要主要内容不变，不重要的词不同，就认为是重复的。为每个内容生成一个整数表示指纹，根据这个指纹做重复或相似的检查

**消费端的重复检测**

想要保留更长的已读列表，需要布隆过滤器

不是百分百准确，可以设置一个概率

## 10 架构总览

### 内容采集和分析

抓取、清洗、转码

### 离线计算

批量计算，构建在分布式计算集群，早年在Hadoop使用Map—Reduce计算任务，后来使用基于Spark基于内存计算。输出：

* 推荐结果：对于老用户可直接产生
* 用户画像：可解决冷启动，根据用户特征得到实时推荐
* 排序模型：CTR预估模型

#### 离线层

主要面对的数据源是Hadoop，HDFS分布式文件系统，所有日志都存在这里，是全量数据中心，通过Pig或Hive等工具，从全量日志中按照算法要求抽取出不同的数据，构建算法所需数据源。数据源比较多时，需要专业的管理工具：数据构建好后需要订阅发布模式及时通知、监控体系，Netflix使用Hermes

#### 近线层

使用实时数据，不保证实时任务。数据来源是行为事件队列，计算的结果保存到在线数据库，当用户发起请求再提供服务

过程：从事件队列中获取最近一个或几个用户行为，将用户已反馈过的物品从离线推荐结果中剔除（去重），然后用这些数据作为样本，用小批量梯度下降的优化方法去更新融合模型的参数

核心组件是流计算，框架有Storm、Spark Streaming、Flink等，Netflix使用Manhattan

### 推荐服务

实时刷新服务

* 离线推荐和实时召回相融合
* 个性化实时排序
* 去重
* 返回ID列表，不关心展现

重点是排序模型，一般保留“百”级别的ID，将内容特征和用户特征和其他特征拼接成稀疏特征向量，逐一预估CTR

####在线层

要处理的对象是已经预处理后的推荐结果，是少量物品的集合。在微秒秒级别完成，在线层适合的逻辑计算：

* 简单的算法逻辑，如排行榜加权采样
* 模型的预测逻辑（Interface阶段）
* 和用户互动性强的一些算法逻辑，如Bandit算法

如果计算过程中出现意外，假如ID对应的物品不存在，就需要降级，可取出热门排行榜的数据

还需要实时记录用户行为，防止推荐重复内容

### 日志收集及其他配套

日志收集、监控（数据管道、离线计算、在线服务）

### 简化

1. 去掉近线层
2. 避免使用分布式系统。几千万用户、几十万到百万的物品做协同过滤或矩阵分解，充分发挥单机的能力，效率远优于Spark，性能不足就升级单机配置

当数据量还不太大时，离线层算法不多，在线层的线上融合也不必太复杂，简单的加权融合即可

### 搜索引擎、推荐系统、广告系统

完全可以把ElasticSearch作为管理各种推荐结果的数据库来使用，按不同的方式建索引，再根据条件搜索，重新融合排序输出

## 关键模块

### 日志收集

数据来源有两种：数据库如用户信息，后端埋点

各种推荐算法所需要的数据就是矩阵，可以把要收集的数据归纳成以下四类

| 矩阵           | 算法应用                                 | 模型        | 说明                                               | 来源   |
| -------------- | ---------------------------------------- | ----------- | -------------------------------------------------- | ------ |
| 用户、属性矩阵 | 内容推荐、模型融合                       | UserProfile | 用户属性数据                                       | 数据库 |
| 物品、属性矩阵 | 内容推荐、模型融合                       | ItemProfile | 物品属性数据                                       | 数据库 |
| 用户、用户矩阵 | 协同过滤、矩阵分解                       | Relation    | 关系数据（非必须）                                 | 数据库 |
| 用户、物品矩阵 | 协同过滤、矩阵分解发、深度学习、模型融合 | Event       | 事件数据，用户行为，如曝光、浏览、点击、收藏、购买 | 日志   |

日志需要的数据

* 用户ID
* 物品ID
* 事件名称
* 事件
* 可选
  * 设备信息、位置信息
  * 从什么事件来
  * 从什么页面来
  * 事件发生时的用户属性、物品属性

通过nginx、后端服务、RESTful接口，RPC服务等数据源获取数据；可应用到Kafka、HDFS、ElasticSearch、MongoDB等。（通过kafka等分布式消息队列作为收集后落地前的队列，可作为落地的缓冲，也可作为实时计算的数据源）

日志收集工具有Logstash、Flume等，Fluened更轻量灵活，分为客户端（负责采集）和服务端（收集），采用JSON统一日志

### 实时推荐

需要达到1秒以下响应、特征实时更新、模型实时更新

**实时消息队列**使用Kafka或Redis等临时方案

实时推荐建立在**流计算**平台上，常见的有Twitter的Storm，Yahoo的S4、Spark Streaming和Flink，Storm使用者越来越多，社区越来越繁荣，也是真正的流计算

* Spout：喷嘴，接入一个数据流，把数据喷洒出去
* Bolt：螺栓，两段水管的连接处，两端可接入喷嘴，也可接入另一个螺栓，数据流进入下一个环节
* Tuple：元组，流水
* Topology：拓扑结构，由上面三个元组组成

在Storm中要运行所有计算和统计任务：清洗数据、合并用户的历史行为、重新更新物品相似度、在线更新机器学习模型、更新推荐结果

实时相似度计算，以基于物品的协同过滤为例：

增量更新物品之间的相似度：取出这个用户的历史评分物品列表，在所有物品和新物品之间要增加一个共同评分，新物品本身也要增加一个评分用户数。对于Storm，需要实现：

TODO P312底部

### AB实验

A/B测试

### 推荐服务

#### 存储

推荐系统在离线层产生的结果需要保存进数据库，供近线层实时更新

（ElasticSearch可用作推荐系统的第一版，直接承担存储和计算的任务）

**特征数据**

数据量最大，如画像，更新不频繁，有两种：稀疏（文本类、用户标签类）和稠密（Embedding、隐因子模型产出参数）

稀疏数据以两种形态存在：正排和倒排，正排是以ID为主键查询，倒排是以特征作为主键查询，稀疏特征才会有倒排，正排常用内存KV数据库存储，如Redis，倒排使用列式数据库如HBase和Cassandra（列式数据库适合批量写入和批量查询，适合推荐系统，Cassandra去中心化的分布式数据库，读写性能优于HBase，更适合推荐系统，HBase是有Master节点的分布式数据库，强一致性）

稠密数据使用文件存储，采用内存映射可以高效读取和使用，或者序列化后存入内存kv数据库

**模型**

机器学习模型使用分布式参数服务器，对于未达到超大规模的数据，可采用更灵活的PMML文件吗；或直接使用scikit-learn等提供的文件导出；还有一种是虚拟内存映射mmap，把数据以二进制形式存在磁盘中，采用虚拟内存映射的方式快读读取，解决数据过大不能读入内存，又想随机读取的需求

非机器学习模型，不统一

**召回策略计算的候选集数据**

通常是ID列表，使用Redis sorted set

#### API

**数据录入API**

| 接口      | 用途             | 输入参数                             | 备注                 |
| --------- | ---------------- | ------------------------------------ | -------------------- |
| /User     | 录入用户信息     | userid、attribute、value             | 可以接受多个属性和值 |
| /Item     | 录入物品信息     | itemid、attribute、value             | 同上                 |
| /Relation | 录入一个关系数据 | from、to、weight                     |                      |
| /Event    | 录入事件         | userid、itemid、eventname、timestamp |                      |

**猜你喜欢 /Recommend  相关推荐 /Relative  热门排行 /Hot**

请求：

* UserID
* PageID：推荐的页面ID，关系到业务策略
* FromPage：从什么页面来
* PositionID：页面中的推荐位ID
* Size：请求数量
* Offset：偏移量，翻页

响应

* items：推荐列表，完整数据
* recommend_id：标志每一次调用，曝光ID，用于推荐后追踪推荐效果，重要
* size
* page

**信息流API**

需要已读过滤，去掉页数的概念

问题：如果请求超时，这次的结果已经放入已读列表，就不会再推荐，同时没有保证API的“幂等”（两次访问得到一样的结果），信息流API只需要让API在使用相同recommend_id时得到一样的结果（需要前端构建这个唯一id），需要将这个id为键，将推荐结果缓存起来，设置过期时间

### 开源工具

内容分析，处理文本，转化为结构化的文本

* 主题模型
* 词嵌入
* 文本分析

|      |      |      |      |      |
| ---- | ---- | ---- | ---- | ---- |
|      |      |      |      |      |
|      |      |      |      |      |
|      |      |      |      |      |
|      |      |      |      |      |
|      |      |      |      |      |
|      |      |      |      |      |
|      |      |      |      |      |

将单机发挥到极致再考虑分布式。FastText和word2vec的词嵌入是一样的，但是FastText还提供分类功能，效果几乎等同CNN，效率却和线性模型一样

协同过滤和矩阵分解

