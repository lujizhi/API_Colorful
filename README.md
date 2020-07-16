|文档名称|Colorful—产品需求文档|
|--|--|
|文件作者|卢继志|
|产品名称|Colorful|
|产品加值|鲜花识别-百度AI开放平台植物识别API+百度AI开放平台通用物体和场景识别API|
|产品原型链接|<a href='https://modao.cc/app/593e19aae842af04f6e0da6b94739d9d0b281fe8?simulator_type=device&sticky'>Colorful</a>|

# Colorful

**加值宣言**

由于鲜花品类众多，大多时候容易混淆，甚至观赏后都无法留下深刻的印象，回忆难度大，以及不同鲜花都代表不同的花语，在不同场景下献花/送花也要考虑花语这一因素，都会给送花者带来诸多困难。Colorful通过调用**百度AI开放平台植物识别API**，反馈识别结果为植物名称及Score值，调用**百度AI开放平台通用物体和场景识别**，反馈识别结果为keyword植物名称、score值、baike_url、description部分（花语、生长习性等），调用两种API帮助用户快速回忆鲜花品类，及快速了解鲜花生长习性、花语等信息，日常积累鲜花知识。使其快速记忆鲜花品类，以及在不同情境下正确地献花/送花。

![API加值](https://gitee.com/lujizhi/API_N/raw/master/API_final_img/img/API%E5%8A%A0%E5%80%BC.png)

**人工智能概率性考量**

> TransparencyMarketResearch分析公司预计，从2013年到2019年，全球生物识别市场将以每年20.8%的速度增长。未来生物识别技术市场规模将达到233亿美元。而在国内，据相关机构调研显示，过去几年我国生物识别市场年均增速超过了60%，2015年生物识别市场规模突破了百亿大关，业界预计到2020年，生物识别市场规模将突破300亿元。

从目前来看，OCR识别技术市场份额逐年增长，越来越多的相关产品层出不穷，也不断满足人们日益增长的需求，但在一些较为专业的、需要较高精确度的领域需要实现无差错的识别，还是有一定难度的。

## 问题表述与需求列表

API驱动之智能产品，为产品进行智能加值，以“以人为本”的思维进行产品研发，满足用户的需求，解决用户痛点

### 问题表述

**用户画像1**

![用户画像1](https://gitee.com/lujizhi/API_N/raw/master/API_final_img/img/%E7%94%A8%E6%88%B7%E7%94%BB%E5%83%8F1.png)

**用户画像2**

![用户画像2](https://gitee.com/lujizhi/API_N/raw/master/API_final_img/img/%E7%94%A8%E6%88%B7%E7%94%BB%E5%83%8F2.png)

经过对使用过相关花类APP用户研究及调查，发现大多数花类APP多以内容型为主，比如分享养花技巧、晒花、记录养花生活等，而对于花类和花语的普及较少，这一定程度上使人们容易进入花类知识盲区，从而出现以下**用户痛点（问题）**：

|序号|用户痛点（问题）|
|--|--|
|1|日常生活中，想买一些鲜花来观赏，但又不了解鲜花的习性、花语等信息，从而导致养花成本太高，想在日常中积累相关鲜花知识|
|2|在一些特殊场合中，不知道该献、送哪一类别的花|
|3|鲜花品类繁多，容易混淆，如何快速回忆且反复记忆|


**用户旅程地图---使用阶段**

![用户旅程地图--使用阶段](https://gitee.com/lujizhi/API_N/raw/master/API_final_img/img/%E7%94%A8%E6%88%B7%E6%97%85%E7%A8%8B%E5%9C%B0%E5%9B%BE-%E4%BD%BF%E7%94%A8%E9%98%B6%E6%AE%B5.png)

### 需求列表

从“问题表述”栏中，总结出以下三点问题及对应的需求表述，问题分别是鲜花品类容易混淆，回忆难度大；对鲜花习性、花语等信息缺乏了解；如何帮助记忆反馈结果。对应的需求表述是快速回忆（对相关图片快速识别，得到相应的反馈结果，且仅返回“鲜花品类”结果）；链接鲜花习性、花语等信息（对相关图片快速识别，得到相应的反馈结果，返回keyword植物名称、score值、baike_url、description部分（花语、生长习性等）结果）；反复记忆（通过打卡签到的形式，打卡内容为“收藏”识别结果内容）

|问题|需求表述|
|:--:|:--:|
|鲜花品类容易混淆，回忆难度大|快速回忆|
|对鲜花习性、花语等信息缺乏了解|日常积累反馈结果|
|如何帮助记忆反馈结果|反复记忆(签到打卡，打卡内容为收藏内容，无收藏内容则随机推送）|

* 需求优先级

|优先级|需求|智能加值？|API类型|
|:--:|:--:|:--:|:--:|
|1|快速反馈、回忆|是|百度OCR图像技术-<a href='https://ai.baidu.com/tech/imagerecognition/plant'>植物识别</a>|
|2|了解鲜花习性、花语等信息|是|百度OCR图像技术-<a href='https://ai.baidu.com/tech/imagerecognition/general'>通用物体和场景识别</a>|
|3|反复记忆|否|无|

## 解决方案原型表述

**问题1：该产品如何做界面及数据流程的设计？**

答：根据用户痛点、“以人为本”的观念进行产品的研发，根据“问题表述和需求列表”栏中描述的问题和需求，对问题进行方法分析以及智能加值的运用，数据流程该部分以创新思维、数智思维来考虑相关问题，做到解决用户需求、满足用户体验。使用界面原型制作工具—墨刀，进行原型构建；使用processon流程图缕清界面和数据思路。

**问题2：该产品智能流程中是什么关键智能交互及什么关键智能API结合，进而解决谁的问题？**

答：运用两种OCR图像识别技术关键智能API，分别是植物识API和通用物体和场景识别API。关键智能交互分别是，在调用植物识别API时，可以直接在APP中的“发现”菜单栏此块帖子内容相关的鲜花图片中，点击图片并选中“鲜花识别”直接智能植物识别，反馈相应数据；在调用通用物体和场景识别API时，可以直接在“发现”菜单栏此块帖子内容相关的鲜花图片中，保存图像进行识别，即可跳转至智能通用物体和场景识别API进行识别（同理：APP中的菜单栏中的相机图标“识别”功能）。解决问题：调用植物识别API解决用户“鲜花品类繁多，容易混淆，回忆难度大”的痛点；调用通用物体和场景识别API解决用户“对鲜花生长习性、花语等信息缺乏了解”的痛点。

### 界面及关键智能交互

**界面流程图**

![界面流程图](https://gitee.com/lujizhi/API_N/raw/master/API_final_img/img/%E7%95%8C%E9%9D%A2%E6%B5%81%E7%A8%8B%E5%9B%BE.png)

**智能加值主张一**：百度AI开放平台OCR图像技术的植物识别。调用植物识别API，点击‘鲜花识别’，即自动反馈相关识别结果。识别结果只反馈鲜花品类（大类），无其他详情信息，调用这一功能主要目的是帮助用户快速回忆，而不用跳转到其他平台搜索。

![加值主张一p1](https://gitee.com/lujizhi/API_N/raw/master/API_final_img/img/%E6%99%BA%E8%83%BD%E5%8A%A0%E5%80%BC%E4%B8%BB%E5%BC%A01.png)

![加值主张一p2](https://gitee.com/lujizhi/API_N/raw/master/API_final_img/img/%E6%99%BA%E8%83%BD%E5%8A%A0%E5%80%BC%E4%B8%BB%E5%BC%A01.1.png)


**智能加值主张二**：百度AI开放平台OCR图像技术的通用物体和场景识别API。调用通用物体和场景识别API，通过保存图片，或在“拍照识别功能”中导入图片进行识别。识别结果不仅仅反馈鲜花品类（大类），还链入‘百度百科’介绍页面，description部分则是‘百度百科’页面的摘要，摘要信息大致有鲜花的生长习性、花语等。

![加值主张二p1](https://gitee.com/lujizhi/API_N/raw/master/API_final_img/img/%E6%99%BA%E8%83%BD%E5%8A%A0%E5%80%BC%E4%B8%BB%E5%BC%A02.png)

![加值主张二p2](https://gitee.com/lujizhi/API_N/raw/master/API_final_img/img/%E6%99%BA%E8%83%BD%E5%8A%A0%E5%80%BC%E4%B8%BB%E5%BC%A02.1.png)

![加值主张p3](https://gitee.com/lujizhi/API_N/raw/master/API_final_img/img/%E6%99%BA%E8%83%BD%E5%8A%A0%E5%80%BC%E4%B8%BB%E5%BC%A02.2.png)


以上两种智能加值主张中，从IDEO三要素（商业可行性、技术可行性、用户可欲性）的角度来论证其MVP加值。

从**商业可行性**的角度分析，TransparencyMarketResearch分析公司预计，从2013年到2019年，全球生物识别市场将以每年20.8%的速度增长。未来生物识别技术市场规模将达到233亿美元。而在国内，据相关机构调研显示，过去几年我国生物识别市场年均增速超过了60%，2015年生物识别市场规模突破了百亿大关，业界预计到2020年，生物识别市场规模将突破300亿元；

从**技术可行性**的角度分析：

|百度AI开放平台中的植物识别的技术优势/用户痛点|百度AI开放平台中的通用物体和场景识别的技术优势/用户痛点|
|:--:|:--:|
|可识别种类多：支持识别超过2万种通用植物和近8千中花卉|可识别物体广泛：支持识别动物、植物、商品、建筑、风景、动漫、食材、公众人物等10万个常见物体及场景，接口返回大类及细分类的名称结果|
|反馈数据可靠|外链补充，支持获取识别结果的百科信息|
|置信度排名参考|灵活性高：接口返回百科词条URL、图片和描述，支持自定义返回词条数|


从**用户可欲性**的角度分析，从目前来看，OCR识别技术市场份额逐年增长，越来越多的相关产品层出不穷，也不断满足人们日益增长的需求，但在一些较为专业的、需要较高精确度的领域需要实现无差错的识别，还是有一定难度的。在花类APP应用领域，目前已有可对鲜花识别的应用程序，例如识花、形色等。但是数量相对其他领域来说还是比较少的，依旧处于起步阶段。


### 数据流程及关键智能API使用

**数据流程图**

* 数据流程图说明：

数据流程大致分为三大部分，分别是帖子图片“鲜花识别”、帖子图片“保存图片并识别”和“拍照识别”。帖子图片“鲜花识别”的数据流程是通过点击图片，选中“鲜花识别”，识别过程中触发百度AI开放平台植物识别API（智能加值）的调用，进行缓冲识别，识别成功后，反馈鲜花品类（大类）数据（智能加值），该部分数据解决用户“鲜花品类容易混淆，回忆难度大”的痛点；帖子图片“保存图片并识别”的数据流程是通过点击图片，选中“保存图片并识别”，识别过程中触发百度AI开放平台通用物体和场景识别API（智能加值）的调用，进行缓冲识别，识别成功后，反馈鲜花品类、使用场景、花语、description描述、baike_url等数据，该部分数据解决用户“对鲜花习性、花语等信息缺乏了解”的痛点；“拍照识别”的数据流程是通过拍照上传照片或相册上传照片，上传成功后进行识别，识别过程中触发百度AI开放平台通用物体和场景识别API（智能加值）的调用，识别成功后，反馈鲜花品类、使用场景、花语、description描述、baike_url等数据。对以上数据，用户通过“收藏”行为，对反馈数据结果进行数据储存，在用户每天触发“签到”功能时，再次反馈给用户，解决“如何帮助记忆反馈结果”的痛点（数据再加值）。

![数据流程图](https://gitee.com/lujizhi/API_N/raw/master/API_final_img/img/%E6%95%B0%E6%8D%AE%E6%B5%81%E7%A8%8B%E5%9B%BE.jpg)

|数据来源|数据方案|
|:--:|:--:|
|百度AI开放平台植物识别API|快速回忆鲜花品类（大类）|
|百度AI开放平台通用物体和场景识别API|对鲜花习性、花语等信息缺乏了解|


以上两种智能加值主张中，从IDEO三要素（商业可行性、技术可行性、用户可欲性）的角度来论证其MVP加值。

从**商业可行性**的角度来说，所反馈的数据结果的收集有一定的可持续、循环价值，即再次反馈给用户加深记忆；同时，有一定的商业价值，即储存数据，用数据变现，出售给相关鲜花产业（电商等）。

从**技术可行性**的角度来说，百度AI开放平台的植物识别API及通用物体和场景识别API后台相关数据库强大，所储存数据多类，反馈数据全面且清晰，具有借鉴意义。

从**用户可欲性**的角度来说，结合用户痛点，调用API数据（智能加值），对反馈数据结果进行数据储存和再加值，使用户充当“使用数据”和“再使用数据”的角色。

**智能加值主张一**：百度AI开放平台OCR图像技术的植物识别API。
**智能加值主张二**：百度AI开放平台OCR图像技术的通用物体和场景识别API。
**数据再加值**：通过调用植物识别API及通用物体和场景识别API反馈的数据，用户的“收藏”行为对此部分的数据进行收集和储存，用户的“签到”行为触发“收藏”行为所储存的数据，再一次反馈给用户，用户进行再次记忆和数据印象的加深。

![数据再加值p1](https://gitee.com/lujizhi/API_N/raw/master/API_final_img/img/%E6%95%B0%E6%8D%AE%E5%86%8D%E5%8A%A0%E5%80%BC.png)

![数据再加值p2](https://gitee.com/lujizhi/API_N/raw/master/API_final_img/img/%E7%AD%BE%E5%88%B0%E8%AF%B4%E6%98%8E.png)


**代码块**

* 植物识别API

```
# encoding:utf-8

import requests
import base64

'''
植物识别
'''

request_url = "https://aip.baidubce.com/rest/2.0/image-classify/v1/plant"
# 二进制方式打开图片文件
f = open('./gongzhudejiari.jpg', 'rb')
img = base64.b64encode(f.read())

params = {"image":img}
access_token = '24.b0eddcf41978c205738d76cf4147621a.2592000.1597043500.282335-19922006'
request_url = request_url + "?access_token=" + access_token
headers = {'content-type': 'application/x-www-form-urlencoded'}
response = requests.post(request_url, data=params, headers=headers)
if response:
    print (response.json())

```
* 识别结果

![植物识别结果](https://gitee.com/lujizhi/API_N/raw/master/API_final_img/img/%E6%A4%8D%E7%89%A9%E8%AF%86%E5%88%ABAPI%E7%BB%93%E6%9E%9C.png)


* 数据反馈

|score|name|
|:--:|:--:|
|0.723|洋桔梗|
|0.447|玫瑰|
|0.442|月季花|


* 通用物体和场景识别API

```
# encoding:utf-8

import requests
import base64

'''
通用物体和场景识别
'''

request_url = "https://aip.baidubce.com/rest/2.0/image-classify/v2/advanced_general"
# 二进制方式打开图片文件
f = open('./gongzhudejiari.jpg', 'rb')
img = base64.b64encode(f.read())

params = {"image":img}
access_token = '24.b0eddcf41978c205738d76cf4147621a.2592000.1597043500.282335-19922006'
request_url = request_url + "?access_token=" + access_token
headers = {'content-type': 'application/x-www-form-urlencoded'}
response = requests.post(request_url, data=params, headers=headers)
if response:
    print (response.json())

```

* 识别结果

![通用物体和场景识别结果](https://gitee.com/lujizhi/API_N/raw/master/API_final_img/img/%E9%80%9A%E7%94%A8%E5%9C%BA%E6%99%AF%E5%92%8C%E5%9C%BA%E6%99%AF%E8%AF%86%E5%88%ABAPI%E7%BB%93%E6%9E%9C.png)

* 数据反馈

|score|root|baike_url|description|keyword|
|:--:|:--:|:--:|:--:|:--:|
|0.226529|植物-花束|"http://baike.baidu.com/item/%E9%A6%99%E6%A7%9F%E7%8E%AB%E7%91%B0/7830829|香槟玫瑰，蔷薇科，蔷薇属，保加利亚的国花。又称月季(香槟金、香槟酒) 古代丝绸。德国科德斯1982年培育。亲本：Anaballseedling×seedling。\"香槟\"月季为蔷薇科蔷薇属植物，在广州一年四季均可开花，花色大红，重瓣，有香味，是很好的盆栽、园林绿化月季品种。代表花语：爱上你是我今生最大的幸福，想你是我最甜蜜的痛苦，和你在一起是我的骄傲，没有你的我就像一只迷失了航线的船。\"香槟\"月季还具有一定的食用价值。|香槟玫瑰|
|0.170238|商品-工艺品|无|无|花瓶|


**人工智能概率性考量**

![人工智能概率性考量p1](https://gitee.com/lujizhi/API_N/raw/master/API_final_img/img/%E4%BA%BA%E5%B7%A5%E6%99%BA%E8%83%BD%E6%A6%82%E7%8E%87%E6%80%A7%E8%80%83%E9%87%8F-%E7%99%BE%E5%90%88.png)

![人工智能概率性考量p2](https://gitee.com/lujizhi/API_N/raw/master/API_final_img/img/%E4%BA%BA%E5%B7%A5%E6%99%BA%E8%83%BD%E6%A6%82%E7%8E%87%E6%80%A7%E8%80%83%E9%87%8F-%E7%99%BE%E5%90%88%E3%80%81%E7%8E%AB%E7%91%B0.png)

* 概率性考量

**植物识别API**：反馈score值、name数据，且score值有一定的参考价值，同时在对一张图篇有单一鲜花品类进行识别，或者一张图片有多类鲜花进行识别，都能较为精准的反馈对应数据（图一：百合，所识别结果都与百合有关；图二：玫瑰、百合花束，所识别结果都能一一反馈，且score值相对较高）

**通用物体和场景识别API**：能够反馈较全的数据（keyword、score、root、description、baike_url等），但只有识别结果为最高score值才能反馈，其余的只反馈score、root、keyword。


## 学习/实践心得总结及感谢

本文档写作进一步对“API机器学习与人工智能”课程的深化实践，结合课上知识，并引入“产品经理”和“用户视觉设计”课程的知识进行相关问题的思考和产品原型的制作。特别感谢百度AI开放平台提供的<a href='https://ai.baidu.com/tech/imagerecognition/plant'>植物识别API</a>和<a href='https://ai.baidu.com/tech/imagerecognition/general'>通用物体和场景识别API</a>代码对产品的技术支持。调用两种API，解决用户“鲜花品类容易混淆，回忆难度大”的痛点、解决用户“对鲜花习性、花语等信息缺乏了解”的痛点、解决解决“如何帮助记忆反馈结果”的痛点。

* <a href='https://modao.cc/app/593e19aae842af04f6e0da6b94739d9d0b281fe8?simulator_type=device&sticky#screen=skc903zi3jhqymp'>产品原型</a>
