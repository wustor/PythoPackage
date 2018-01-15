编码问题

上传changelog出现中文乱码的问题，主要是由于Android Studio的.properties文件的的编码以及Python的版本的默认的编码不一致所致，解决方式很简单，下面会介绍，不给过过程却很苦逼。

Python 2.X

修改.properties编码为ASCII


![python2](http://orbm62bsw.bkt.clouddn.com/python2.X.png)


 Python 3.X

 修改.properties编码为UTF-8


![python3](http://orbm62bsw.bkt.clouddn.com/python3.X.png)


填坑之路

由于我对Python也不是很熟，所以说来惭愧，我一直自恋地认为自己的代码没有问题，因为我本地的编码是utf-8,

所以就一直觉得是fir那边的问题，所以就很自信的去找了fir的客服，最后他们的转接到他们的后台，后台说他们的

默认的中文接收的编码是utf-8,让我在postman中试一下，并且很热心地给我贴了一个网上的一篇关于[Python脚本上传apk的文章](https://www.dengxiangxing.com/post/51421)，，我打开一看，卧槽，这不是我写的那篇文章么，一时气氛有些尴尬，下面贴出当时的聊天截图。

![对话](http://orbm62bsw.bkt.clouddn.com/answer.png)

然后我用postman试了一遍，确实是不会出现问题的，然后想了很久也没想明白，因为编码当时设置的是utf-8，但是我使用的是Python2.X，后来在一位Python大佬的建议下，我换了Python3.X是可以的，不过他告诉我Python2.X的默认编码是ASCII，Python3.X的默认编码是utf-8，然后我就试着把Python2.X对应的Android Stuido的.propertiers改成了ASCII试了一下，果然成功了。
