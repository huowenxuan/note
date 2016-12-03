## 属性
* automaticallyAdjustContentInsets: bool 自动调整网页内容
* contentInset:{top, left, bottom, right} 定义内容距离WebView四边的距离
* html 指定用于显示的html字符串
* injectedJavaScript 允许运行JavaScript
* startInLoadingState: bool 刚开始加载时显示Loading状态
* source   
		{
	* uri: string,  // 指定webView加载的网址  
	* method: string,  // 指定加载方式，除非服务器配合，否则不要设置  
	* headers: object,  // 加载HTTP消息头，除非服务器配合，否则不要  设置
	* body: string  // HTTP消息体， 除非服务器配合，否则不要设置  
	} 或者  
	{  
	* html: string, // 用来指定直接加载的HTML  
	* baseUrl: string // 用来将需要加载的文件路路写成相对于项目的相对路径  
	}
	
## 属性
* onError
* onLoad
* onLoadEnd
* onLoadStart
* onNavigationStateChange 导航状态改变回调
* renderError
* renderLoading

####iOS-only
* allowsInlineMediaPlayback 页面中的视频是在网页中播放还是原生的视频播放器播放，默认false，表示使用原生播放。如果希望在网页中播放，需要设置为true，而且html网页中相应的视频元素必须包含webkit-playsinline属性
* bounces
* onShouldStartLoadWithRequest 网页中任何js发起的请求都会交个这个回调函数，返回true或false来确定是否执行js发起的请求
* scalesPageToFit: bool 是否适配当前WebView大小，以及能否缩放网页
* scrollEnabled

####android-only
* domStorageEnabled: bool 是否允许DOM在本机存储
* javaScriptEnabled: 是否允许运行网页中的js脚本，在iOS上永远都执行

##函数
* reload


