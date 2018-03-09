---
date: 2018-01-12 14:42:03
---

# 联系方式

- 手机：17375724973
- Email：shichuyao@hotmail.com
- QQ/微信号：154832909


# 个人信息

 - 石矗垚/男/1987 
 - 本科/怀化学院/广播电视工程 
 - 工作年限：6年
 - 技术博客：[https://chuyao.github.io](https://chuyao.github.io)

 - 期望职位：Android高级程序员，应用架构师
 - 期望薪资：面议
 - 期望城市：长沙


# 工作经历
## 湖南蚁坊软件股份有限公司 （ 2017年4月 ~ 至今 ）

### 微信逆向采集 
- 项目负责人，框架设计，代码重构及日常维护
- Xposed框架研究及应用，root权限管理
- 微信附近的人、朋友圈消息、公众号资源逆向采集，朋友圈图片(wxpc格式)逆向解码

项目中的一些问题及解决方案
1. 项目前期赶进度，静态变量、内部类、Context等引用混乱，单类多实例，导致内存泄漏及应用进程停止的问题，在重构时引入leakcanary框架进行排查解决，提高应用稳定性
2. 微信封号，前期进行附近的人采集时，逆向注入固定的地理坐标，时间长了会被微信识别账号异常，封号。解决方案是引入轨迹采集机制，模拟正常人的轨迹（家，单位，随机出行地等），昼夜频率差异，进行地理坐标注入及采集，在稳定采集任务的同时达到养号的目的
3. 心跳服务，使用AlarmManager替换Timer行使轮循任务，解决Timer因异常不能恢复工作的问题


### 青橙派(Orange Pi)Android系统定制 
- 基于全志H3/H5主板集成方案的Orange Pi Android系统定制
- Orange Pi Android4.4/5.1系统源码编译、Rom打包及烧录
- Android系统定制，root权限开放(su移植)，Xposed框架移植

整理的一些笔记
1. [OrangePi系统源码编译](https://chuyao.github.io/2018/01/07/orangepi-pch3-source-compile/)
2. [OrangePi系统基础定制](https://chuyao.github.io/2018/01/07/orangepi-pch3-system-customization/)


### 蚁讯即时通讯应用
- 网络通讯模块重构，引入Retrofit+RxJava新技术框架

  
## 小叶云(北京)信息技术有限公司 （ 2016年8月 ~ 2017年3月 ）

### 小叶收银 
- 小叶收银机系统开发，收银操作员、顾客会员、商品存销业务设计
- Android系统分屏异显功能开发
- 收银机周边辅助设备(扫码枪、钱箱、小票打印机、电子秤)驱动集成及上层软件应用

项目中的一些问题及解决方案
1. 收银机分屏显示主客屏控制逻辑业务臃肿，夹杂异步控制带来客屏反应卡顿问题，解决方案是将客屏显示控制独立出来，做成应用级服务，通过AIDL与主应用进行进程间通讯，客屏应用根据不同的指令再控制屏营显示逻辑，充分解耦，利于模块化开发
2. 收银外设驱动集成混乱，解决方案是封装API，如扫码枪，封装成ScannerTextView，团队成员只需要调用封装好的View，即可完成对扫码枪的信号控制(条码、二维码解码，解码结果显示回调)
3. Butterknife、Retrofit+RxJava、Fresco、GreenDao框架的使用，充分提高开发效率，将更多精力集中到业务开发中

## 北京公牛财富科技有限公司 （ 2014年6月 ~ 2016年8月 ）

### 公牛炒股
- 炒股软件开发，券商柜台业务抽象转化
- Android客户端开发团队管理(最多时5人)
- MPAndroidChart绘制股票K线及改进
- JsBridge应用，实现web、native相互调用及通讯

## 诺基亚中国 （ 2013年6月 ~ 2014年6月 ）
- 外派驻场，Nokia Here地图SDK维护开发，地图本地化支持

## 北京加维通讯电子技术有限公司 （ 2011年7月 ~ 2013年5月 ）
- Android机顶盒系统开发，Android2.3/3.0/4.0系统编译定制
- 海思芯片主板方案集成，体感遥控器驱动移植


# 作品
- [公牛炒股](http://app.mi.com/details?id=com.imfclub.stock)，目前已停止服务
- [小叶收银](https://www.xiaoyeyun.com/#/index)

## 技术文章
- [Kotlin基础教程第四章：Kotlin类 (Android)](https://chuyao.github.io/2017/08/18/kotlin-android-tutorial-4/)
- [OpenSSL基础教程二：RSA命令行加解密](https://chuyao.github.io/2017/09/07/openssl-2-rsa-command-operation/) 
- [解决Nexus5X手机死循环启动问题(译文)](https://chuyao.github.io/2017/07/31/nexus5x-bootloop-fix/)
     
# 技能清单
以下均为我经常使用的技能
- Android开发：Java/Kotlin/JNI/ReactNative
- Web开发：Node.js/Python3，轻量使用
- 数据库相关：SQLite/MongoDB
- 版本管理及构建工具：Git/Gradle
- 单元测试：Junit
- 云和开放平台：Aliyun/微博开放平台/微信应用开发


---      
# 致谢
感谢您花时间阅读我的简历，期待能有机会和您共事。
      