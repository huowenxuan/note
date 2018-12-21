---
title: 小Demo
---

# byte转kb, mb, gb
```javascript
formatBytes(bytes, decimals=0) {
  if(bytes == 0) return '0 Byte';
  var k = 1024; // 可改为1000
  var dm = decimals + 1 || 3;
  var sizes = ['Bytes', 'KB', 'MB', 'GB', 'TB', 'PB', 'EB', 'ZB', 'YB'];
  var i = Math.floor(Math.log(bytes) / Math.log(k));
  return parseFloat((bytes / Math.pow(k, i)).toFixed(dm)) + ' ' + sizes[i];
}
```



                      