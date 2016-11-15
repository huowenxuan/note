##获取当前网络状态
```javascript
NetInfo.fetch().done((status)=> {
    console.log(status)
})
```
在Android中，需要在AndroidManifest.xml中添加:
```xml
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```
####Android status值：
* NONE - 设备处于离线状态
* BLUETOOTH - 蓝牙数据连接
* DUMMY - 模拟数据连接
* ETHERNET - 以太网数据连接
* MOBILE - 移动网络数据连接
* MOBILE_DUN - 拨号移动网络数据连接
* MOBILE_HIPRI - 高优先级移动网络数据连接
* MOBILE_MMS - 彩信移动网络数据连接
* MOBILE_SUPL - 安全用户面定位（SUPL）数据连接
* VPN - 虚拟网络连接。需要Android5.0以上
* WIFI - WIFI数据连接
* WIMAX - WiMAX数据连接
* UNKNOWN - 未知数据连接
####iOS status值：
* none - 设备处于离线状态。
* wifi - 设备处于联网状态且通过wifi链接，或者是一个iOS的模拟器。
* cell - 设备是通过Edge、3G、WiMax或是LTE网络联网的。
* unknown - 发生错误，网络状况不可知

##判断是否联网
```javascript
NetInfo.isConnected.fetch().done((isConnected) => {
  console.log('First, is ' + (isConnected ? 'online' : 'offline'));
});
```

##监听网络状态
```javascript
NetInfo.addEventListener('change', (status)=> {})
```
