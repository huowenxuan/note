# 集成jpush-react-native，运行iOS release时报link错误，重复引用。
设置工程中 **Build Active Architecture Only** 下 release 为 yes，只能调试用，最终打包还是要设置为NO--真机运行没问题 
# addListener的回调方法中不能执行removeListener，回调方法会失效
# iOS友盟分享从其他应用返回时没有回调，需要在appdelegate中加上openURL一系列方法。安卓需要在MainApplication中复写onResult。。。方法
# Picker控件的items必须是一个数组，不能是一个个组件，需要把他们加到数组中放在piker标签里

