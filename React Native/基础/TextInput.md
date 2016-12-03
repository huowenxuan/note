##属性
* autoCapitalize 自动大写方式
  * none
  * sentences 每句话首字母大写
  * words 每个单词首字母大写
  * characters 所有大写
* autoCorrect: bool 是否自动更正错误的单词输入
* autoFocus: bool 是否自动获得焦点
* defaultValue: string
* editable: bool 是否允许编辑
* keyboardType 键盘类型
  * default iOS、android都支持
  * numeric iOS、android都支持
  * email-address iOS、android都支持
  * ...其他
* MaxLength: 最多输入多少字符
* multiline: 默认false，如果是true，允许多行
* placeholder: 占位符
* placeholderTextColor: 占位符颜色
* secureTextEntry/password 是否用于输入密码
* value: 显示的字符串
* onSelectionChange: {(event)=> {}} 当用户在输入框中选择的字符串发生变化的回调
  ```javascript
  event: {
    timeStamp: Date,
    nativeEvent: {
      selection: {
        start: Number
        end: Number
      }
    }
  }
  ```
####iOS
* blurOnSubmit: 输入完成时，文本区域是否会被模糊化。对于单行，默认为true，多行默认为false。对于多行，将blurOnSubmit设为true，会使multiline会失效
* clearButtonMode 什么时候显示右侧的清除按钮
* clearTextOnFocus 开始编辑时自动清楚原来的内容
* enablesReturnKeyAutomatically 没有文字时，returnKey失效，有文字，returnKey
* keyboardAppearance 键盘颜色
  * default light dark
* onKeyPress 当一个按键被按下的回调，在onChange之前被调用
* returnKeyType 返回键类型
* selectTextOnFocus 成为焦点后，文字都被选中
* tintColor
####Android
* numberOfLines 配合multiline={true}，设置输入多少行
* textAlign
* textAlignVertical 文字在垂直方向上的位置
  * start center end
* underlineColorAndroid 下划线颜色，设置为背景色相同的颜色会吧下划线隐藏

##函数
focus() 获得焦点

##生命周期
* onFocus 组件获得焦点回调
* onChange & onChangeText   
  同时调用,onChange返回event.nativeEvent.text获得输入的字符串;onChangeText直接返回字符串，更简单
* onSubmitEditing 按下返回键  
  如果multiline为true：在iOS上，onSubmitEditing不会被调用；在Android上，会触发，但会加上一个回车换行，同时会继续保持焦点
* 失去焦点
  * 按下返回键
  * 点击了另一个TextInput组件

  **只有这两种情况才会失去焦点，后续事件才会被触发**  
  之后会依次调用onEndEditing和onBlur  
  **如果用户点击某个提交按钮来提交输入，这时失去焦点事件不会发生，所以不能用过onEndEditing和onBlur函数得到最终的字符串，所以只能通过onChangeText或onChange来获取输入**

##键盘事件
在Android上，弹出键盘后，TextInput和其上方的组件都会上移
```javascript
 import { Keyboard } from 'react-native'
 
 constructor(props) {
    super(props);
    this.state = {
      subHeight: new Animated.Value(0),
    }
  }

  componentDidMount() {
    // 安卓不识别keyboardWillShow
    if (Platform.OS == 'ios') {
      Keyboard.addListener('keyboardWillShow', this._keyboardWillShow.bind(this));
      Keyboard.addListener('keyboardWillHide', this._keyboardWillHide.bind(this));
    } else {
      Keyboard.addListener('keyboardDidShow', this._keyboardWillShow.bind(this));
      Keyboard.addListener('keyboardDidHide', this._keyboardWillHide.bind(this));
    }
  }

  componentWillUnmount() {
    if (Platform.OS == 'ios') {
      Keyboard.removeListener('keyboardWillShow');
      Keyboard.removeListener('keyboardWillHide')
    } else {
      Keyboard.removeListener('keyboardDidShow');
      Keyboard.removeListener('keyboardDidHide')
    }
  }

  _keyboardWillShow(frames) {
    let keyboardHeight = frames.endCoordinates.height;
    Animated.timing(this.state.subHeight, {
      toValue: keyboardHeight,
      duration: 300,
    }).start();
  }

  _keyboardWillHide(frames) {
    Animated.timing(this.state.subHeight, {
      toValue: 0,
      duration: 300,
    }).start();
  }
```
