[TOC]

# Word2vec

计算文本向量，查找相似词

https://www.biaodianfu.com/word2vec-wikipedia.html

https://github.com/lzhenboy/word2vec-Chinese

## 获取维基百科中文语料

### 下载维基百科中文语料库用来训练

https://dumps.wikimedia.org/zhwiki/latest/zhwiki-latest-pages-articles.xml.bz2 如果下载慢可以搜索百度网盘找别人分享的下载

## 处理语料库

### 对XML进行提取和组织

两种方式，使用第二种

#### Python写的维基百科抽取器Wikipedia Extractor

```shell
git clone https://github.com/attardi/wikiextractor.git
python ./wikiextractor/WikiExtractor.py -b 2048M -o extracted zhwiki-latest-pages-articles.xml.bz2
```

共执行74分钟，total of page: 2345527, total of articl page: 1033838; total of used articl page: 1033838，导出到当前目录下的 extracted/AA/wiki_00

二次处理，去掉括号、书名号等

```
import re
import sys
import codecs
 
 
def filte(input_file):
    p1 = re.compile('[（\(][，；。？！\s]*[）\)]')
    p2 = re.compile('《》')
    p3 = re.compile('「')
    p4 = re.compile('」')
    p5 = re.compile('<doc (.*)>')
    p6 = re.compile('</doc>')
    p7 = re.compile('『』')
    p8 = re.compile('『')
    p9 = re.compile('』')
    p10 = re.compile('-\{.*?(zh-hans|zh-cn):([^;]*?)(;.*?)?\}-')
    outfile = codecs.open('std_' + input_file, 'w', 'utf-8')
    with codecs.open(input_file, 'r', 'utf-8') as myfile:
        for line in myfile:
            line = p1.sub('', line)
            line = p2.sub('', line)
            line = p3.sub('“', line)
            line = p4.sub('”', line)
            line = p5.sub('', line)
            line = p6.sub('', line)
            line = p7.sub('', line)
            line = p8.sub('“', line)
            line = p9.sub('”', line)
            line = p10.sub('', line)
            outfile.write(line)
    outfile.close()
 
 
if __name__ == '__main__':
    input_file = sys.argv[1]
    filte(input_file)
```

保存为`file.py`，执行 `python3 file.py wiki_00`，几分钟后，在相同目录下会生成一个`std_wiki_00`（重命名为 zhwiki_raw.txt 即可）

### gensim的wikicorpus库

执行转换

```python
from gensim.corpora import WikiCorpus
import os
 
 
class Config:
    data_path = '/'
    zhwiki_bz2 = 'zhwiki-latest-pages-articles.xml.bz2'
    zhwiki_raw = 'zhwiki_raw.txt'
 
 
def data_process(_config):
    i = 0
    output = open(os.path.join(_config.data_path, _config.zhwiki_raw), 'w')
    wiki = WikiCorpus(os.path.join(_config.data_path, _config.zhwiki_bz2), lemmatize=False, dictionary={})
    for text in wiki.get_texts():
        output.write(' '.join(text) + '\n')
        i += 1
        if i % 10000 == 0:
            print('Saved ' + str(i) + ' articles')
    output.close()
    print('Finished Saved ' + str(i) + ' articles')
 
 
config = Config()
data_process(config)
```

直接执行，几分钟即可，生成一个zhwiki_raw.txt

### 化繁为简

```sh
# 安装opencc
export HOMEBREW_NO_AUTO_UPDATE=true
brew install opencc

# 使用opencc
opencc -i zhwiki_raw.txt -o zhswiki_raw.txt -c t2s.json
```

最终生成  zhswiki_raw.txt

### 分词

```sh
# 直接使用jieba分词，得到zhswiki_cut.txt，1秒完成
python3 -m jieba -d " " ./zhswiki_raw.txt >./zhswiki_cut.txt
```

## word2vec训练模型

```python
import os, sys
import logging
import multiprocessing
from optparse import OptionParser
from gensim.corpora import WikiCorpus
from gensim.models import Word2Vec
from gensim.models.word2vec import LineSentence

def word2vec_train(infile,outmodel,outvector,size,window,min_count):
    '''train the word vectors by word2vec'''

    # train model
    model = Word2Vec(LineSentence(infile),size=size,window=window,min_count=min_count,workers=multiprocessing.cpu_count())

    # save model
    model.save(outmodel)
    model.wv.save_word2vec_format(outvector,binary=False)


if __name__ == '__main__':
    program = os.path.basename(sys.argv[0])
    logging.basicConfig(level=logging.INFO,format='%(asctime)s - %(levelname)s - %(message)s')
    logger = logging.getLogger(program)

    logger.info('running ' + program)

    # parse the parameters
    parser = OptionParser()
    parser.add_option('-i','--input',dest='infile',default='corpus.zhwiki.segwithb.txt',help='zhwiki corpus')
    parser.add_option('-m','--outmodel',dest='wv_model',default='zhwiki.word2vec.model',help='word2vec model')
    parser.add_option('-v','--outvec',dest='wv_vectors',default='zhwiki.word2vec.vectors',help='word2vec vectors')
    parser.add_option('-s',type='int',dest='size',default=400,help='word vector size')
    parser.add_option('-w',type='int',dest='window',default=5,help='window size')
    parser.add_option('-n',type='int',dest='min_count',default=5,help='min word frequency')

    (options,argv) = parser.parse_args()
    infile = options.infile
    outmodel = options.wv_model
    outvec = options.wv_vectors
    vec_size = options.size
    window = options.window
    min_count = options.min_count

    try:
        word2vec_train(infile, outmodel, outvec, vec_size, window, min_count)
        logger.info('word2vec model training finished')
    except Exception as err:
        logger.info(err)
```

保存为 word2vec_train.py

```sh
python3 word2vec_train.py -i zhswiki_cut.txt -m zhwiki.word2vec.model -v zhwiki.word2vec.vectors -s 400 -w 5 -n 5
```

得到基于Wiki中文语料库训练好的word2vec模型和词向量：
word2vec模型文件：
(1) `zhwiki.word2vec.model`
(2) `zhwiki.word2vec.model.trainables.syn1neg.npy`
(3) `zhwiki.word2vec.model.wv.vectors.npy`
word2vec词向量文件：
`zhwiki.word2vec.vectors`

## 模型测试（查看相似词）

```python
from gensim.models import Word2Vec
if __name__ == '__main__':
    WORD2VEC_MODEL_DIR = './zhwiki.word2vec.model'
    model = Word2Vec.load(WORD2VEC_MODEL_DIR)

    # 查看词向量，向量包含词义和上下文关系
    # vec = model['北京']
    # print('北京：', vec)

    # 查看相似词
    sim_words = model.most_similar('德甲')
    print('The most similar words: ')
    for w in sim_words:
        print(w)
```

## 如何应用到推荐系统

[如何使用 word2vec 来做推荐系统](https://blog.csdn.net/Xw_Classmate/article/details/99028680)