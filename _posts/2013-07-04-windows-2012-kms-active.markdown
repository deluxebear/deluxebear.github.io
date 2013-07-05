---
layout: post
title:  "使用亚马逊的KMS服务器来激活自己的Windows 2008 R2 或2012"
date:   2013-07-04 19:12:19
categories: System
---

#1、需要一个EC2实例（亚马逊提供免费1年的试用，如果是要激活Windows2012，你就新建Windows2012的实例），在EC2管理控制台设置“Security Groups"中的default的安全组中"Inbound"中增加1688端口远程进入实例，打开命令行，输入：slmgr /dli   查看KMS服务器的地址，在这个例子中我获得地址是如下图
![getkms](/images/kms.png)
#2、查看windows Key的软件，例如：pkeyui.exe；使用pkeyui获得此实例的windows 2012的key

#3、TCP重定向的软件，例如：TCPForward.exe；在命令行中使用: tcpforward 1688 kms服务器的地址 1688  命令行窗口不要关闭

#4、在自己本地安装windows 2012,输入刚刚获得的key

#5、在命令行中输入：slmgr /skms  kms服务器地址:1688

#6、在命令行中输入：slmgr /ato

激活工作完成，只是半年后又得从新激活，此方法仅供做测试用，请不要用于商业用途，发生的后果自负:-)














[Apache httpclient]: http://hc.apache.org/httpcomponents-client-ga/index.html