---
layout: post
title: 如何用Typora自动上传图片（typora+PicGo+阿里云oss）
category: 技术开发
---
---

提出问题：如何让typora的图片自动上传到云端

解决思路：准备图片上传软件+准备云储存空间

首先需要准备两个软件和一个环境

```
node.js 用于PicGo软件安装插件使用  https://nodejs.org/en/download/
PicGo图床上传软件   https://github.com/Molunerfinn/PicGo/releases
PicGo插件地址   https://github.com/PicGo/Awesome-PicGo
```

图床是什么：图床就是用来存放照片的空间，同时允许外连到其他网站上

PicGo下载指南 进入下载链接后进去软件版本中选择最近稳定版本2.3.0

![image-20211025201219358](https://runhoutang-src.oss-cn-beijing.aliyuncs.com/img/202110281003408.png)

安装只需要一直下一步即可

安装完成之后界面如下图所示：

![image-20211025201259540](https://runhoutang-src.oss-cn-beijing.aliyuncs.com/img/202110281003410.png)

之后再**将PicGo的数据加入环境变量中。**

此电脑->属性->高级系统设置->环境变量->双击Path->添加

![image-20200512204623143](https://raw.githubusercontent.com/Run-tang/picBed/master/202110251430876.png)

![image-20200512204728770](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9waWNnby13Lm9zcy1jbi1jaGVuZ2R1LmFsaXl1bmNzLmNvbS9pbWcvaW1hZ2UtMjAyMDA1MTIyMDQ3Mjg3NzAucG5n?x-oss-process=image/format,png)

配置好环境变量之后打开需要使用的图床

![image-20211025201417223](https://runhoutang-src.oss-cn-beijing.aliyuncs.com/img/202110281003411.png)

以下是我使用的一些图床的配置方法：

1）阿里云oss图床

在搭建之前，我们需准备阿里云对象存储服务

第一步：进入阿里云官网https://www.aliyun.com/并且登录好，支付宝扫码登录即可

![image-20211028101132499](https://runhoutang-src.oss-cn-beijing.aliyuncs.com/img/202110292129095.png)

之后进入下面这个界面

![image-20211028101314650](https://runhoutang-src.oss-cn-beijing.aliyuncs.com/img/202110292129097.png)

点击立即购买即可扫码付款

之后在右上角按如下操作

![image-20211028102957768](https://runhoutang-src.oss-cn-beijing.aliyuncs.com/img/202110292129099.png)

进入如下界面后、为了安全选择开始使用子账户，创建一个只用来管理图片的账户

![image-20211028103116315](https://runhoutang-src.oss-cn-beijing.aliyuncs.com/img/202110292129100.png)

![image-20211028103341165](https://runhoutang-src.oss-cn-beijing.aliyuncs.com/img/202110292129101.png)

![image-20211028103734943](https://runhoutang-src.oss-cn-beijing.aliyuncs.com/img/202110292129102.png)

![image-20211028104023709](https://runhoutang-src.oss-cn-beijing.aliyuncs.com/img/202110292129103.png)

后面我们需要给此账户添加我们需要使用的权限

![image-20211028104305924](https://runhoutang-src.oss-cn-beijing.aliyuncs.com/img/202110292129104.png)

会弹出如下界面、按照标注选择即可

![image-20211028104630642](https://runhoutang-src.oss-cn-beijing.aliyuncs.com/img/202110292129105.png)

再在控制台选择对象存储oss 创建储存空间（**存储空间名** 就是bucket名称，如果没有，请自行创建）

按照如下选择，创建

![image-20211028105303870](https://runhoutang-src.oss-cn-beijing.aliyuncs.com/img/202110292129106.png)

![image-20211028110622621](https://runhoutang-src.oss-cn-beijing.aliyuncs.com/img/202110292129107.png)

![image-20211028110037015](https://runhoutang-src.oss-cn-beijing.aliyuncs.com/img/202110292129108.png)

**确定存储区域** 就是地域节点前部分，例如我的就是`oss-cn-beijing` (同样复制保存到记事本待会配置上传工具PicGo的时候会用上)

![image-20211028111230211](https://runhoutang-src.oss-cn-beijing.aliyuncs.com/img/202110292129109.png)

进入文件管理界面![image-20211028111841384](https://runhoutang-src.oss-cn-beijing.aliyuncs.com/img/202110292129110.png)

再新建目录/img

![image-20211028111916751](https://runhoutang-src.oss-cn-beijing.aliyuncs.com/img/202110292129111.png)

![image-20211028111932154](https://runhoutang-src.oss-cn-beijing.aliyuncs.com/img/202110292129112.png)

![image-20211028112230168](https://runhoutang-src.oss-cn-beijing.aliyuncs.com/img/202110292129113.png)

这样我们上传工具已经配置好了，但是如果需要使用Typora自动上传图片到图床我们需要在Typora软件内做好如下配置：

打开Typora在文件中选择偏好设置：

![image-20211028112452010](https://runhoutang-src.oss-cn-beijing.aliyuncs.com/img/202110292129114.png)

按照如下配置（选择好）

![image-20211028113034106](https://runhoutang-src.oss-cn-beijing.aliyuncs.com/img/202110292129115.png)

我们可以进行测试，出现如下状况就是设置成功

![image-20211028113137770](https://runhoutang-src.oss-cn-beijing.aliyuncs.com/img/202110292129116.png)

2）github图床（待后续待后续更新）

3）gitee图床（待后续更新）

