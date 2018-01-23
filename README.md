

## 上传失败

### 文件路径

检查**iconPath**&**apkPath**是否正确

### Requests库

检查一下requests库是否安装成功，**有些老板**requests库都没有安装成功就开始上传，肯定是不会成功的，如果采用pip安装，需要科学上网，如果不能科学的上网可以下载离线包进行安装，检查request是否安装成功方式如下：

- 进入Python环境：在Android Studio的命令行中输入python

  ```python
  Python 2.7.10 (default, Jul 15 2017, 17:16:57) 
  [GCC 4.2.1 Compatible Apple LLVM 9.0.0 (clang-900.0.31)] on darwin
  Type "help", "copyright", "credits" or "license" for more information.
  >>> 
  ```

- 导入requests,输入import requests

  ```java
  >>> import requests
  >>> 
  ```

  说明安装成功，然后就能够成功上传

  ​

## 编码问题

上传changelog出现中文乱码的问题，主要是由于gradle文件的编码跟Python默认的编码不一致导致，由于gradle文件的编码是默认的是跟随系统，大部分都是UTF-8,而且不便于修改，所以我将参数中的中文字段放在gradle.properties中，所以下面的解决方式就是根据这个来的。



### Python 2.X

修改.properties编码为ASCII

![python](http://orbm62bsw.bkt.clouddn.com/python.png)


 ### Python 3.X

 修改.properties编码为UTF-8

![python3](http://orbm62bsw.bkt.clouddn.com/python3.png)

### 注意事项
修改设置中的.properties文件编码，并不一定能保证改变已经存在的gradle.properties文件编码，所以改完之后查看一下，如果没有成功的话，切换到properties文件，可以点击右下面的文件分隔符切换按钮，如下图，确保编码切换成功，然后在进行上传。

![again](http://orbm62bsw.bkt.clouddn.com/again.png)

## 填坑之路

由于我对Python也不是很熟，所以说来惭愧，我一直自恋地认为自己的代码没有问题，因为我本地的编码是utf-8,

所以就一直觉得是fir那边的问题，所以就很自信的去找了fir的客服，最后他们的转接到他们的后台，后台说他们的

默认的中文接收的编码是utf-8,让我在postman中试一下，并且很热心地给我贴了一个网上的一篇关于[Python脚本上传apk的文章](https://www.dengxiangxing.com/post/51421)，，我打开一看，卧槽，这不是我写的那篇文章么，一时气氛有些尴尬，下面贴出当时的聊天截图。

![conversation](http://orbm62bsw.bkt.clouddn.com/conversation.png)


然后我用postman试了一遍，确实是不会出现问题的，然后想了很久也没想明白，因为编码当时设置的是utf-8，但是我使用的是Python2.X，后来在一位Python大佬的建议下，我换了Python3.X是可以的，不过他告诉我Python2.X的默认编码是ASCII，Python3.X的默认编码是utf-8，然后我就试着把Python2.X对应的Android Stuido的.propertiers改成了ASCII试了一下，果然成功了。
