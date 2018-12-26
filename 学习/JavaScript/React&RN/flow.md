# 安装

1. 安装时候不能使用brew，会卡住，使用npm install flow-bin -g
2. 终端输入flow运行，但是报错版本不对。RN中默认生成了.flowconfig文件，并且指定了一个低版本的flow，修改[version]下面的版本号即可
3. 在每个需要检查的文件最上方加入`//@flow`或者`/*@flow*/`，或者给某个类、变量标注`//@flow`即可进行检查

# flow自带一个变量type，用于声明对象或者类的类型

```js
type Prop = {
    a: any,
    b: mixed,
    c: Object,
    imgs: Array<string>,
    imgs2: string[]
}
type State = {}
class App extends PureComponent<Props, State> {
  constructor(props: Props) {
    super(props)
    this.state = {
    }
  }
}
```

# 忽略node_modules
.flowconfig

```
[ignore]
.*/node_modules/.*
```

# 运行提示react-native、redux等库找不到

```
// 需要VPN
yarn global add flow-typed
flow-typed install
```

修改后没好，重启下电脑就好了？

# @connect警告，忽略decorators
flow警告这还是一个提案，在.flowconfig忽略它，等号左右不能有空格

```
[optioins]
esproposal.decorators=ignore
```

# 优化
因为container需要props包含types、dispatch、router等固定props，而在每个container中都重复写一遍是很不明智的，而每个container都有各自单独的props，找到了一种办法可以合并不同的type

```
type ContaienrProps = {
  dispatch: mixed,
  types: mixed,
  router: Router
}

type Props = {
   id: string
}

class App extends PureComponent<ContainerProps & Props> {
  constructor(props: ContainerProps & Props) {
      super(props)
  }
}
```

上面的写法在constructor中比较繁琐，而且重复了，优化：

```
type ContaienrProps = {
  dispatch: mixed,
  types: mixed,
  router: Router
}

type Props = ContaienrProps & {
   id: string
}

class App extends PureComponent<Props> {
  constructor(props: Props) {
      super(props)
  }
}
```

封装在一个文件中：

```
PropTypes.js
export type ContainerProps = {
  dispatch: any, // 官方推荐能用mixed就不用any，但是在这个文件中使用mixed会报错，any就没有问题，需要再研究
  types: any,
  router: Router
}

// 导入
import type {ContainerProps} from '../utils/PropTypes'
```

# Flow / PropType
Flow type是编码时的检查，propTypes是运行时的检查，都是必要的
                      