#Navigator
##参数
* sceneStyle 将会应用在每个场景的容器上的样式。
* configureScene(route, routeStack) 两个参数为路由和当前的路由栈，返回景切换的动画
  * Navigator.SceneConfigs.PushFromRight (默认)
  * Navigator.SceneConfigs.FloatFromRight
  * Navigator.SceneConfigs.FloatFromLeft
  * Navigator.SceneConfigs.FloatFromBottom
  * Navigator.SceneConfigs.FloatFromBottomAndroid
  * Navigator.SceneConfigs.FadeAndroid
  * Navigator.SceneConfigs.HorizontalSwipeJump
  * Navigator.SceneConfigs.HorizontalSwipeJumpFromRight
  * Navigator.SceneConfigs.VerticalUpSwipeJump
  * Navigator.SceneConfigs.VerticalDownSwipeJump
* initialRoute 定义启动时加载的路由。路由是导航栏用来识别渲染场景的一个对象。initialRoute必须是initialRouteStack中的一个路由。initialRoute默认为initialRouteStack中最后一项。
* initialRouteStack 提供一个路由集合用来初始化。如果没有设置初始路由的话则必须设置该属性。如果没有提供该属性，它将被默认设置成一个只含有initialRoute的数组。
* navigationBar 可选参数，提供一个在场景切换的时候保持的导航栏。
* navigator 可选参数，提供从父导航器获得的导航器对象。
* onDidFocus 每当导航切换完成或初始化之后，调用此回调，参数为新场景的路由。
* onWillFocus 会在导航切换之前调用，参数为目标路由。
* renderScene(route, navigator) 必要参数。用来渲染指定路由的场景。调用的参数是路由和导航器。

##函数
* getCurrentRoutes() - 获取当前栈里的路由，也就是push进来，没有pop掉的那些。
* jumpBack() - 跳回之前的路由，当然前提是保留现在的，还可以再跳回来，会给你保留原样。
* jumpForward() - 上一个方法不是调到之前的路由了么，用这个跳回来就好了。
* jumpTo(route) - 跳转到已有的场景并且不卸载。
* push(route) - 跳转到新的场景，并且将场景入栈，你可以稍后跳转过去
* pop() - 跳转回去并且卸载掉当前场景
* replace(route) - 用一个新的路由替换掉当前场景
* replaceAtIndex(route, index) - 替换掉指定序列的路由场景
* replacePrevious(route) - 替换掉之前的场景
* resetTo(route) - 跳转到新的场景，并且重置整个路由栈
* immediatelyResetRouteStack(routeStack) - 用新的路由数组来重置路由栈
* popToRoute(route) - pop到路由指定的场景，在整个路由栈中，处于指定场景之后的场景将会被卸载。
* popToTop() - pop到栈中的第一个场景，卸载掉所有的其他场景。

#Navigator.NavigationBar
```javascript
const NavigationBarRouteMapper = {
      // 可选
      LeftButton (route, navigator, index, navState) {
        return <BackNavButton/>
      },

      // 必须
      Title (route, navigator, index, navState) {
        return  <Text>{route.title}</Text>
      },

      // 可选
      RightButton (route, navigator, index, navState) {
        return <TouchableOpacity/>
      }
    }

  <Navigator
    navigationBar=<Navigator.NavigationBar routeMapper={NavigationBarRouteMapper}
  />
```
