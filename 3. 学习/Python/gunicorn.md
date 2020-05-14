## 浏览器多个tab访问卡死的问题

现象：workers=1时，浏览器多个tab访问gunicorn运行的API，tab1访问后，tab2、tab3再访问就会卡死，workders为2和3情况会好些但是依然不行，在tab1刷新后，tab2请求成功，tab2再刷新，tab3请求成功。通过flask直接运行、或者通过api工具和get请求都没有问题

原因：是因为通过浏览器访问时，即使请求成功，浏览器也没有把连接关掉，导致一直占用worker，刷新会把前面的连接关掉

解决：修改gunicorn工作模式，worker_class改为gevent，使用协程，可获得极高并发

