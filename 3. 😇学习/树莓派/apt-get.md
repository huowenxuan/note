# 错误
## 无法修正错误，因为您要求某些软件包保持现状，就是它们破坏了软件包间的依赖关系
下列软件包有未满足的依赖关系：
libjpeg62-turbo-dev : 依赖: libjpeg62-turbo (= 1:1.3.1-12+deb8u2) 但是 1:1.5.1-2 正要被安装
 
安装对应版本即可 `apt-get install xxx=version`
`sudo apt-get install libjpeg62-turbo=1:1.3.1-12+deb8u2`