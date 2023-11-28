# 利用python进行微信防撤回的监听

## 项目介绍

> 基于python+wxpy进行微信防撤回的监听

利用python进行微信防撤回，实际上的原理是这个微信和你聊天的对象同处再一个群里，它会实时监控聊天记录，
检测到消息状态为撤回，就会从撤回之前的保存的记录里，拿出这条数据，转发给出去，从而达到一个防撤回的效果。
通俗的讲就是实时备份你的聊天记录，然后提取出来撤回的那条消息，然后通过你的微信发出去。

* 如果对您对此项目有兴趣，可以点 "Star" 支持一下！

* 或者您可以 "follow" 一下，如有问题请直接在 Issues 中提


----------


## 产品依赖于:
 - [Python][1]
 - [Wxpy][2]

## 项目运行
	# 安装Python环境
	可百度一下相关教程，在这不做说明

    # 克隆到本地
    git clone https://github.com/liu-ziting/python-wx-fch.git
    
    # 进入文件夹
    cd python-wx-fch
    
    # 安装依赖
    pip install 
	可通过 pip install 直接安装相关模块，
	如运行时还有因模块报错，也可以直接pip install 【模块名】直接安装即可。
	本项目以及后续相关都依赖于以下模块
	
	import requests
	from requests import exceptions
	from urllib.request import urlopen
	from bs4 import BeautifulSoup
	from urllib.parse import urlencode
	from threading import Timer
	import re
	from wxpy import *
	import  schedule
	import  time
	import http
	import  json 
	import datetime
	import random
	import os
	import ctypes
	
	重要：其中 wxpy 模块是本项目以及后续项目中很重要的模块，就是因为这个开源项目，我们才能使其与微信产生交互。
    
    # 运行
	 
	直接点击文件PreventWithdrawal或者在目录中打开cmd:PreventWithdrawal.py，运行即可。

## 代码说明

获取你要检测的群对象，如果你想监听所有对象，则不需要；
将撤回的消息 转发到特定的群里，以供再其他微信查看，可以是单个好友或者文件传输助手

```python
Test = bot.groups().search(u'C.B.M电子竞技俱乐部') 

recallNotice = ensure_one(bot.groups().search('C.B.M电子竞技俱乐部')) 
```

注册事件，所有群的消息

```python
@bot.register(Group)
```

撤回类型

```python
# 文本 TEXT = 'Text'
# 位置 MAP = 'Map' 1
# 名片 CARD = 'Card' 2
# 分享 SHARING = 'Sharing' 3
# 图片 PICTURE = 'Picture'  4
# 语音 RECORDING = 'Recording' 5
# 文件 ATTACHMENT = 'Attachment' 6
# 视频 VIDEO = 'Video' 7
```

  [1]:https://www.python.org/
  [2]:https://wxpy.readthedocs.io/zh/latest/
  [3]:https://www.runoob.com/python/python-install.html
