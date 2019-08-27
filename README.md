# IntelligentSite
智慧工地
## 前言
这个项目是我们公司项目之一，另外还有实名制、ERP等。公司规模较小，所以这个项目由我一人开发(包括前台和后端)。但由于法律原因和我个人害怕原因，源码不以公开。只能做做简单的介绍。
## 若依
gihub项目地址:https://gitee.com/y_project/RuoYi
使用了该开源框架。
- Springboot
- Shiro
- SpringMVC
- Druid 数据库多源
- Thymeleaf 页面模板解析
等。
使用了其中的菜单管理、用户管理、权限管理框架、定时任务、生成代码的脚手架、session管理
## 功能
智慧工地项目给政府管理使用，工地按照需求需要在工地安装摄像头和扬尘设备。  
扬尘设备用于检测空气中的小颗粒物含量指数，可以带有继电器控制喷淋设备完成自动控制净化环境。智慧工地平台作为一个管理平台需要收集项目内扬尘设备上传的参数。设备由另外的厂商提供，使用的是NB-IOT技术，窄带物联网，因为我大学是物联网工程专业的，所以对这个也有几分了解，具体是设备内有一张电话卡，可以通过基站传输数据，取代了以前的lora等物联网分级架构，但这都是题外话，这部分对于我们是透明的，我们只要根据协议对接。HJ212协议是扬尘环境保护的推荐使用协议，现在一般都用这个。  
我便选用了netty(还是很有名的异步tcp传输)架构，还可以解决半包粘包问题。保持和设备的连接，然后维护这个session表，因为上文提及了联动控制，是需要拿到tcp的session回发指令的。  

利用定时任务查时间段内的平均值产生警报记录，如果连续产生警报会给项目监管人员发短信。   

另外还写了一个统计设备在线时间的功能(设备跟平台存在tcp连接说明在线)。   

播放摄像头直播内容。   

## 平台截图
![1](https://github.com/635981179/IntelligentSite/blob/master/1.png)
地图使用百度地图SDK开发，右边是市控数据网站爬取的信息。地图中，绿色代表健康，灰色代表设备离线。
![2](https://github.com/635981179/IntelligentSite/blob/master/2.png)
这个是设备实时数据和历史数据的界面。使用echarts绘图
![3](https://github.com/635981179/IntelligentSite/blob/master/3.png)
用于统计在线时长，做必要的分析
![4](https://github.com/635981179/IntelligentSite/blob/master/4.png)
项目级别的查看24小时数据和实时数据
![5](https://github.com/635981179/IntelligentSite/blob/master/5.png)
点击标签之后弹出的小窗口
![6](https://github.com/635981179/IntelligentSite/blob/master/6.png)
视频直播界面(萤石云接口)

绝大部分CSS样式是我自己手写的，个人对布局，样式有一定的掌握
