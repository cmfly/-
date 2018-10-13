一、**实验概述** 

在传统运维场景中，有很多常规操作，需要我们登录到服务器手动执行命令或者脚本来实现，本次腾讯云TechWork，我们将带大家快速实战一个运维操作工具箱，展示通过蓝鲸平台提供的能力，在页面上点点鼠标，轻松实现这些常规的运维操作，提升运维效率，解放运维同学们的双手。

**二、准备工作**

1. 蓝鲸社区版环境及账号（培训方提供，不需要自己搭建）
2. 蓝鲸应用开发环境（安装指南见蓝鲸开发者中心）
3. 自己用起来顺手的IDE，推荐PyCharm或Sublime
4. Git仓库管理工具，命令行即可

**三、实验架构**

![](https://lh3.googleusercontent.com/rXhBqBLmOVrzFLv2erPVmOplKjDiizcT3LBA2S2GwwT_KAjaF32DdRxw2cOaPMOm9UtRSZ2vH5xadWoptD5ix-Z8XT7pD9VKV-i3SxI-jEwMPcvKvPhm6dqXegCUnsbNBu5g89vh9-1YA7N39g)

**四、任务一：创建一个蓝鲸应用**

**任务目标: 在蓝鲸PaaS开发者中心中，创建一个蓝鲸应用，然后迁出项目初始化代码。**

**1.创建蓝鲸应用**

- 创建一个代码仓库

![](https://lh4.googleusercontent.com/KZRSCeu1G1aCyr9ejUm3OA4xRxJMW-K45Yq1iEaDF7qg8uyTXuSy0BhcsJuWg5JYKFIV7v_mgXQazan8OgwXaO9RBkKIOXm8VDMjDcXlNi3jnqGzVOdHttXDWTQskn6Y5IexyoQVEj7BUzL9VA)

- 打开蓝鲸开发者中心，创建一个蓝鲸应用

![](https://lh3.googleusercontent.com/GU1Bt5NXcXVm6nU7kD0J0HlVWb6ZJsJXYRwiTOCwc4oua0SVw6j-mOR6lWbB2EFUbo7F596_FtoZI_11ZcJ8D-Mz4mpcKTT65J6kxLf_--iyUlChGvAX5BDR9-ECreK1fUullXhkM1AYib0iPA)

- 根据要求填写应用信息

![](https://lh4.googleusercontent.com/4VwMOHm2-E4MWComLkkJDDH1sTWUEAW08bTsKICIA_3J02KWz7uwiFYHP8msohneGeh8x4pcxf2NNHKelyD_ZNjW3rR3SySLFJw1vT2Cu3brZ7Yzr-qNnB6M_LlO4c-iKvKO5jzKvIsLjn90gg)

- 确认创建

![](https://lh4.googleusercontent.com/wsjuzP2yKzsTP0RG_aU9WymXJiTRQi3HZ4emqSbu2jHtIWm0BhEfA7wS4OXrK4i9DVUg_SJQzQgnM3CSgqc21nb3FBck9rHpT061vbpVFvwf2nW6lRyK4y8As_vw1DhR437J-wMOuMj3NVXtcw)

**2.下载蓝鲸应用开发框架**

- 下载开发框架

![](https://lh5.googleusercontent.com/gg8lP6cvCHK5i6BEqHaafarvEtDmVSeztcPgCTBsfVXhdech4FfEGLRqfxXSdc6uXUdaDw3tKOc0WHZ5oizZdYM4V1H1zYADNT3cov5Wn7Us2pDx3TuXPKHwyGBrH6m1eF74r_ixr_Nx7aGMxA)

- 更新开发框架APP\_ID, APP\_TOKEN, BK\_PAAS\_HOST

![](https://lh3.googleusercontent.com/7A-fq_J9yawT7wOegjDZXdF39n7-F0ivgQ1jJ7CFcrPm6bYwgZx53z1vCZefl3FgbHjb37x1oS_46TaJTy0VMi3Ibm1W79B68Dl4mveo_UvLWSQt2tgvKaEpIoLczUD_WQ7kyHuLSisFn_3cFA)

- 解压framework并执行如下命令：

```
cd framework
git init
git remote add origin http://can.o.qcloud.com/hongsonggao/public-demo.git
git add .
git commit -m "Initial commit"
git push -u origin master
```

**3.安装Python依赖包**

```
pip install -r requirements.txt
```

**4.本地配置host并访问demo页面**

在 C:\Windows\System32\drivers\etc文件中添加如下一行：

127.0.0.1 dev.paasce-poc.o.qcloud.com

- 更改本地开发数据库

![](https://lh6.googleusercontent.com/nhM2O8tMhlgtDKX3cvwXyLSjNB3-5MqOYYnQia1RfCOQZLs8q1Oui02_Pj1B0ySR5B79wdQTdHnWaY3RqdyqrbSE6lyZ3R4jlM2tlICciVZYCjk1vdnOngjHVCYQmv79dB_g4b9xoAm-Rbzltw)

- 生成初始化数据表：

```
python manage.py migrate
```

- 启动工程：

```
python manage.py runserver 8080
```

- 用浏览器打开：[http://dev.paasce-a.o.qcloud.com:8080](http://dev.paasce-a.o.qcloud.com:8080/) 

![](https://lh4.googleusercontent.com/MSKPWbjU0zdtIaCl3JD3-TewIH6BFS-SxSkFggaSqtyYvJGhzND6odVS7KDJfEc1dn1ocX6CwRFV8maOYfM_x6sfQE0WGmuvv_7FLNQgdSmt96kjRkAZ9GF1jgEA2hA1IBfI3WKesFnmlVtv1A)

**五、任务二：前端页面开发**

**任务目标: 学习使用蓝鲸MagicBox的拖拽工程，快速拖拽出应用的前端页面，并加入到前面的开发框架中，并渲染出第一个页面。**

**1.利用蓝鲸MagicBox拖拽前端页面模板**

![](https://lh3.googleusercontent.com/uSi-3vYuGbVTsJO768egc6CxQ8ko4bL1ps5S84Ef31p8kL_bUiqonVfFL5T9XK5XbVHfc2HQsgludVHwiAl0EkyALAEx9RE4eSqMGoxcwje8bcdKb2zbaNiXQfVt-6DJYzJbcJaJQezSagghaA)

![](https://lh3.googleusercontent.com/-mOrfOYQzqxCsBpsZBvtbn-Fk8MKFsifTOuohw9tC9JhLkTS89hTkpSRGoNDJ9fubnl79ptEXbqkm1IjePN_WA750gDdRgZUpjc8y-v2T9QUTib-zNRG3HOfp1SF3Jv_CbzxZI4mGF3Vd16VoQ)

![](https://lh4.googleusercontent.com/sh19nQSYYKnql2IIbcA3M-YGHwjD_ZtUzNraPC2deg-vnxwC8UiohNWrUwdboSZplfr53j42FGiyoJtLYPsqZzdAvcJm7CDng4oNQrkeyp3e9VJKbFnOXM0RNVlYVLbLw61VynxRbZPDSSfIdQ)

![](https://lh3.googleusercontent.com/VJFqkAh-GfqGqiOhHNflkh4i9t3yb2d4cim1boW4KLnw1EC-OWZwKCdvXS3NNcOSh9d_hS9qZbz4st3pQLt7fvbZUAILvk5nRad8WpcIbu9bo_FXKnlG78eIrgCDJYcuIYHncVHZtKJyrAQH5Q)

**2.后端渲染前端页面**

- 修改home\_application/views.py: 

![](https://lh5.googleusercontent.com/sPbfxxInqNhABghNsCLT7_GHoLekfRnKUMV8PR-NiXwQsqpRhlbFnaMJg0NwzUFFPxQDDbvpV7gnEGw8YcZ8JIkOnP6ef5yZXSobDv8sygS7FFXfuMI5dWaAqgZWDT2Cjil2xgivqaQSUwCXWQ)

- 修改home\_application/urls.py 

![](https://lh3.googleusercontent.com/BL28xyljXEYJ-0uN0d5QrFUVgwxBGmgo2V1lXNYqZ3ZJ6-7wX-BZ2OwTpbjCt1mziaieH-W_GwbTLEYxr6CorZGk6RBaqy9kISt4-XH-UDum-2hZnQy3DTTC5wk1twlI50Kyj51tLOt5o_-oxQ)

- 修改页面导航：
- execute.html:

![](https://lh4.googleusercontent.com/_tIuJ1HtSNe39afp5wCktAaz3CvopQWnO_eL1rUP-rt6oLe_8CGzgPjGAcNXt_7YzkZJP0dVwpf20bJGTz6rnv2mz01UncQ6tig4g_fx706dcMFYYUi4APCR2r4EWua2-xLNPizxMvb7lUxKAg)

- history.html: 

![](https://lh5.googleusercontent.com/HArjrCVbtHi36NCtBGTXG8_ByCQaTrhBjfOSo8HmHsssf45p8Kdqtja9MRcQPFOTh2zRXG3gr3408utfBYB4JpjL1gormuvaTToM_Q-ptt8Dt43-FxvV1VJOmPjMAOYiv3yjlNuAPntMcrqJtQ)

**4.更换 执行任务 > 选择机器 表格为可操作表格：**

- 在magicBox中找到可操作表格：

![](https://lh6.googleusercontent.com/gLrnonNB3M5ZXWXZdoX0ojQ-WMy_8wpkkWKLWhji9qqe4g-FUN2gYkSQhqM1XTauvHbJIQSkC6ijRnirMQQKx6WjuzpRs4C0vTb10ePAfzDbmNg3N9D_QUfh5YzKkKBDtgYGFC0qrCXR3VQMRg)

![](https://lh6.googleusercontent.com/u7GgRwFeKqZtvwqspiU9AdA_OvNbJXoPc0-_uFiwtF6Z_H7FRiuGsxUQylTb2P766gJYouDEiqihs2VB3PcVWthx5xeaoo_vBX80ppKl7n9QbpelPMCXmBvpB5Ygxb29e2yhEILluxleDNRgkA)

- 删除多余tr并复制代码：

![](https://lh4.googleusercontent.com/ph2TqXA7AW8ALeSnSov3QkXBqQPRpL9Yd9dTZuLAVxViinfmH9Yh_NBuYkvonjq0SWMQZtRoVbhkv9En0zUocX6UyaG8njeuQ_LHl2UReHC4XtI7wuoLTLU6be5w4iP06Jc-Ha7s7JUkRPMCkg)

![](https://lh4.googleusercontent.com/KwFv_xM6YeR4n3w275UBDbVeZI2DSYE-_FXqFLVXlijXJdTHHk92jUZWv-fUo8lK04v5wZF3_9kTBrDfYuuRrTdg3xXmfXvYcAjzQPj_99Z9AX2PxvOlbaTQl1tvJh55ftgG4lQaE0vutELiiA)

- 删掉execute.html中的表格并将magicBox代码粘贴到此位置：

![](https://lh4.googleusercontent.com/gq7NmLD22kBbVNx9Iq5IDO2PMgR6FqcA3V8xvQf59g92tdcmOC3-886Mdgp8Uc_ZzKLbCoOl8eqgRhO7Y8otzWnpQ__M5UxwmlY0mKZ9rB7DlhR3Jbhfs-LXhQKOwwzTCJ_GC6CoLhC4UPezpQ)

![](https://lh6.googleusercontent.com/7-wrMuGTo1DrSr2598xUPfX6L4LET43rNhldE8Es7cVY_608YkhLopAsptIk6jBmdDPQywqfVUl9qp3StXEQBRjkYmoxpdMIBKK72jem2oRJtN80hG1lT-8FtDUUlhkZmtQoKOPQkIHMQAofxw)

- 删掉多余代码：

![](https://lh6.googleusercontent.com/mjWvwcdtIN_9ajiH1qrcIlsAWE8a0yEM4By6xo9JJrVy84bbXUQLqLqzkCnG7WC_7p0vR7HQwXDMildhWoXqu73kkoPi9LUCeS81lTJH4W-yf1vTHHFU42xaClpHLPwGAb25Ov-4yWsQKAiMaw)

**六、任务三：实现首页功能**

**任务目标: 练习蓝鲸ESB组件调用，从配置平台查询业务列表和主机信息。**

**1.调用cmdb的业务查询接口，获取并展示业务列表**

- 将functions/1\_views\_get\_biz\_list.py 拷到 home\_application/views.py 并：

![](https://lh4.googleusercontent.com/1Zk9WQj_8TMKNKb4pYeZ9uVL7PSv5ThDtF1Q_g8jpFlCFbjWyXbgHn8M8irGP38LqdDK1w2VhGlvxv0Y3ZmZb7v1Aq7463dahBjpwzm-q0cOQr_bX-1o1i9P0kjA6LBW5s9W77k5qQPQkw7KAw)

- 在home\_application.views.home中：

![](https://lh3.googleusercontent.com/eMhX9oOf8noUL0BmUd7c0UciZhYOhAeUYFy3vxKst1P2lKpaqsKAq7pZFreh-0rj0cJY0i_1WNXCKKjKcPx3b2MPh9eMT-O66fykvl88UeSsfJ5doZvk2tsGQXbxSzhgPWbKc6hqkAjAB6WsZQ)

- 在home\_application/execute.html中渲染：

![](https://lh3.googleusercontent.com/H1vJFF5zLZPv3519mmUs59kR-cOkhSixfgV9SBbBKowWyUNTW_BcuHnWqZZWHQpoaC6hoUL96JhbOYvWXfnmyO9pFbDpRpsYCbe8YQc3LlqZcusb42av4D6AaqPuZszTcBIbgVwQJgi_8cgY1w)

- 刷新页面，可以看到业务数据：

![](https://lh5.googleusercontent.com/FB7V_FdqfBMNZxZOoZwdCCDjBd0fiIAaQcxJP4w8WGfM-NyP7CxrA_BsrDMnHP8TVvox00yxiIvkxgy1tGUUrSvp6_YANwO7UBDuKtvXXcBlXR7-nSAofciGSZa6AapIA9o08Ker0q9soZMYtA)

**2.建立script表，查询并展示脚本列表**

- 将functions/2\_models\_script.py拷到home\_application/models.py

并：

![](https://lh4.googleusercontent.com/HlBU0-ssiR-Bftd1G_Rw7trdmjbPDgXxjzSHmuOTrTfiJ1bcOyqbKt4gjFzbNtHOt2ABuNUOjI1KLzPOGF72UiJgoLOHb46eLgSztGeCR6ZG-1tWY17HvLQE_6DlxAZuIQ87LiuC4xe36Qls6A)

- 在home\_application/admin.py中：

![](https://lh3.googleusercontent.com/-wla6UjjcioIr8kNd0cYL_YmqQ66qFaFPxSJwBVWMGoMiN2UN50ml4oiZEE-fKj7vWLZZmlCsNjKtXyWXHfFSLO1-mKodJ5kI8ujaTn1ncaGk0OqearI99IPR7Z93qMetbrdWanhSVtcruP8JA)

- 执行命令：

```
python manage.py makemigrations
python manage.py makemigrations home_application
python manage.py migrate
```

- 访问admin界面：[http://dev.paasce-poc.o.qcloud.com:8080/admin/](http://dev.paasce-poc.o.qcloud.com:8080/admin/) 可以看到Script表：

![](https://lh6.googleusercontent.com/_mCOV9K33k0DSXGkFacdX7CyLl3WvP7kD8i7o2cunhvKC-P8OAekUFKIX5_wkh-oQuxmhQWUaARez84-oOskhaC5aXxSDU1dL1l4U1Mn6-HBuXydcsmXG3zT3FmMwMacRy5rn2G8jTBvgtDSnw)

点击进去，添加几条脚本记录:

![](https://lh4.googleusercontent.com/OIfx2X1Uy30Nnjp5DT5EzzZ1Ubry0XQCBO53fxIz8I2sKkaF_aXXEUUK6sBkOR6UQZWzbqKrIPpn1vRsdGzxQjUispL9FWkFD8V2nOLPXpCAa1q8zVrhn0LA8V8c0QxGvR3ayeIwfc6oJzLFxg)

此处有一个需要注意的地方：

为了不让空格等符号被转义，需要将conf/default.py的MIDDLEWARE\_CLASSES中的CheckXssMiddleware注释掉：

![](https://lh6.googleusercontent.com/xMkrrskUGNl1WSpzOa3Du0HXiaOXe9uEKfdk6KqbKltsfrS2yUKOr34txsp6z5Dh0qcYsQWPcrPnNMSMqsagm1jDBd2tdtqAcBA5n9EMZH8m6JjDO3fSpQAmFm8FC8sczGRlNxsMzEYrqE7JKw)

1. 在home\_application.views.home中：

![](https://lh3.googleusercontent.com/90A0YIetPr3Gq23YL7LbGmNiKnln2rN5MnkzxVqS0XEEqbqYZcMspvur9lQDmLNmv2iZ3xH2Bs6B2erpavUePF1gcS3q1KNN_EE1PNkQWyV6mS5Ub1_dDr2mTySaIvAI91wlKwobBYQzkr5N1Q)

- 在home\_application/execute.html中渲染：

![](https://lh3.googleusercontent.com/8bDCrMdlASpApC4ZK-6bSSRL484CRujhqb0b4UHLKcMVRjAReAiUrSAIm8JXm-6v4IlTOv-o-ldocnonEjBrQVc9S9qGcuRvmjw50rx2udzvMTQRWh-y60Q-bmIgZAhuKWbbVbk600kPYW_aKQ)

- 刷新页面，可以看到script数据：

![](https://lh4.googleusercontent.com/NYSHzpD5o3hbjfhuWeedcBCTq4O-Qvl7tSNoPusjTRkfwQ6ydIRLkmsrzGEQK18106In_nOE5oN0pfALNsbAZoiT2pfQZNg2sHINHCndYlPhX_GjdJXfsqJyXA0D4CVI9RYHyDeDcoRpnGI8ag)

**3.添加脚本参数输入框id:**

![](https://lh5.googleusercontent.com/lK_tZvo-9VoJYpFqqPzjh3k-JiaJdxAJ8rA6WkO0nNx1-RxODNHSshuRhSPp4HhSSn7Mcm0PkdxIw9nPxZUuyRlE3XbBMtiKMgftsZEyASbF4QmdOSO9RPCxzq_MvuyLKnQj1s824ZTJkr1Zmw)

**4.查询主机：**

- 在execute.html中修改table

![](https://lh6.googleusercontent.com/3Nq46foYgym2pZOcGuTmBaJ8UyfyBUL4iKgZfg7mTcuqOwMCyGkLNad0FG89pqJAFGIUH3dqcOOoattUhK5oASVwoXTaV75CC_LmLmLLCYS4LpXuVTMC9D77OHjeIWJOfjP9g2y-zWoaHEO0QA)

- 添加3\_execute\_tbody.html到templates/home\_application/下，命令为：execute\_tbody.html
- 将functions/4\_views\_get\_hosts.py 拷到home\_application.views中

**并：**

![](https://lh6.googleusercontent.com/akobKW_i0VE_28t_woTfY1TW8aPaamzXgr_Qz7-Lzkh4uz74zbhY2xZ4klhILGJp7xFA4KwnpEj5qYuaEqOxMmLhnSa1SH9AC0y_1z89teITONySfrx_gcJOTwech4TxI-MdG_bqHsVVt0glqA)

- 在home\_application/urls.py中添加路由：

![](https://lh5.googleusercontent.com/a0DwxJhxgdNXqTX_PN8r3bWaqVyQabx3PSUtnDhCdlXN9JlLxKLaPZkiZtmlCsJf2uFcW4Z24z68NS0LsEfuSgwIpylya3Afgs2GMUMjuWpi_5qpYYofVISVLeG3JzClXGhnoiYaQJAlPdhc1A)

- 在浏览器中查看接口返回：

![](https://lh6.googleusercontent.com/Jm-x8TnP-pwq5bwYsT8EiRA_AcJBvO7shZx4idAMiirSZIXHWM-Ea09vBG9_IB5XpPpkKUTdQVElDEnfMi2uP6BFEv32IpreS4-kmjktkMzHidDi-txGCNqwr5yaeOtmMgh6LHXrJAFLxwjNwQ)

- 在execute.html中：

在最底的<script>标签中，删掉不用的两个js函数：

![](https://lh6.googleusercontent.com/yKNPRBu6XvTbSPdMYbuypACaXv1Ur0lYkawLoL-VdjzBWHtLRjhpBivJi65PGVXI5xu0HFg-tTZBjHmr3Su-xO1BEsFJC2gTNkZg3xzSvmCqqjLU1bCEUA14ArEip1PWwbsNra4ku0y9xab7AA)

并将functions/4\_execute\_html\_get\_hosts.js拷入：

![](https://lh4.googleusercontent.com/c__wLc1u1ui48dwb63w2VemOyIAAmerzj46xkac3I4rc2z-WuIPX_c7XaYLNyuvdWgiwQNMh3PHvRAyPoG1oWVdkk3Y5UlzRVu5J2_n4REiTi_si95PjXM9p4qBKf6a6uCRAopYtmovpVtO60g)

- 在浏览器控制台调用get\_host()看效果：

![](https://lh4.googleusercontent.com/ulw1scPrLxKZhXyVqjrmpxBBYjoBWc3YbLE3uqrBrutbB0effjSjP3UMC17Fk0X8aFO7lVQzb6l16WEczeY4Qguq8ORQaaNXxhh7rsQkbd05XSBRXjRBsc3PZE2JTT-uTyA5WGu05dd-y4jsgQ)

- 在execute.html的<script>中添加如下代码：

![](https://lh4.googleusercontent.com/mfNV8uw_V5jn0qZqzyBXTf9dtyiz-0G9QKZBd2FRnyqL263GZBXsRxouVjhT5PN3uWcPenhMwstMQL0iJF8IrJf7P4XgtGHcExqeRjvUDWqNxfZgO2RM4_Esvvdb5CjaLGtFtz3hGOMZZ-32ug)

- 于是页面会在初始化和业务发生变化时进行主机查询，并渲染表格。

**5.执行脚本：**

- 建立脚本执行表：

将6\_models\_operaton.py拷到home\_application.models下。

- 添加admin, 并migrate生成表

![](https://lh3.googleusercontent.com/xl9-wxkJXHW5ZVImBKahZ9zZA6Qwdq7pRdYacNF_CO0QwEa927mUInLxZrMxaIsVgGb8KDidJpKUdd1bCfbGJVM1zLnLxrtQOgUfuAgZpkneHPEQvEDo2625nHQi_7b10SIgUTakcdKkvE-BzQ)

- 将7\_models\_execute\_n\_run\_script\_n\_poll\_job\_task.py中的三个函数拷到home\_application.views中。

并：

![](https://lh4.googleusercontent.com/ejRvcRiDLJbbuUKPEcYBTkRhyxBs1j2SwJn__WZR6fS34YNSQ24Dp5hYqacKmQgE_K-OBeYiHKeJVMD3fndxXN03SC_mGqZRtjz3w3r7zC19UcyLGafgU68FnxURmJovfz8Mu3N9Gt3M-D1ySQ)

- 在home\_application.urls中添加路由：

![](https://lh5.googleusercontent.com/6dtJWHIxyIKMHnm6z40OT1IDtljkCa4d0H06-dWNsvoDWxT3RviLUBQINd--8g-i_RMkpTa__Kp2lfuV8fu1TpuB6Tiil_AOOTzdqwjo-wDqYAwQm50grD3B9j_VEvf4JbvT3jQTwLA5o9thAQ)

- 在execute.html中删除掉<table>中的<tfoot>:

![](https://lh6.googleusercontent.com/hX7MAhQnsqhKO75eBvFUmnJAUsLJge8J5PZY-9AAnhnt78ENXsH-kl_iwEN6z7-kw_AgIsUBE22IGpae3DcmMFP04sRJck6E21gGfwCYK6iN0BKBY5BJO9OWLjFFISkk-sMtwKqPeXr2MJowdA)

- 在execute.html中：

![](https://lh3.googleusercontent.com/LrStXVWEJX1rAad-wmsc313OuvZ3CbQJDeaXJxmGuAK9lu3Hep2VVbH9XS3FxUUG7h7z3pa2f0B0qmVdB0WdgEj-JBfCmGBoltkX5Gcw4NONOElP7AnKKUKsHlrignT7QsHfUGLME9AJ47RTqg)

并删掉此<script>标签

- 在execute.html中，为执行按钮加上id：

![](https://lh5.googleusercontent.com/7B6zmhfzob6ajtnhSvqSOq1PcSmFmB5liHy4vvzsHeNw5AAtEO0gZT7TcI48wASlXmTlCTOnVZ0xjwgzwKQegXJNN0kgC0G4uswmN_Ob5Nuwm0DfsN2-rtIGnKGwiGTDNBrnoOUUcljsrhCuwA)

- 将8.js中的submitSuccess()函数拷到execute.html底部的<script>标签中。

并将8.js中的<link>标签和<script>标签拷到execute.html的head中。

- 可以在浏览器的控制台中调用submitSuccess()函数看效果：

![](https://lh4.googleusercontent.com/VdwsKJbk6c_wYxwNDEAsfwd7Zeuhd82Ysmu157qQd1bhLa9fppucEZQLrzttMFM0QNDLUIUroctYo6EGlKODEefGYNGp8BVh-q1dd2yRNfazaQdg9LfTCBO7uaQURugTNFbMwCC7WiSbnbY1Hg)

![](https://lh5.googleusercontent.com/aXXhQrt4xZB-lKRgAUvWc1uzWCwG7Ls3NrSWfiQdhqtp_QVKD2G0Ou1SYM9tDwRUtBxb5P-FnjOwpUBG_eR8K2NtRInsT-bZ8HCdPT8gfYf6IsXA9c8bAdu3t8mYSX4VO_I8kR8-6BwrAScE4w)

- 将9.js拷到execute.html底部<script>标签的$(function()){ … }中
- 此时在页面上点击执行会报403错误：

![](https://lh5.googleusercontent.com/PH25oUXM4QnyT6hVN6lU4-VvWm3UBKx-0bT2SskddkgBUz8lXpvCrthNmMyQa9z1G9Utf1Ly7U8QvcR3CSi3_Lq7FgaCQTF_usW0kwnDOtRd1ri2cI0guf3RcbKOrYxelrh-7vg3OfzJsWc0tQ)

需要从templates/home\_application/base.html中拷两个标签到execute.html中：

![](https://lh3.googleusercontent.com/A2RVSR6WyMpa4v6Yqt2CfJXk1tat9EvxZEaelDI86pFasHa73joRMyygWdFakKFquNhbONgPsXKTA7HNhWQCNR6TFU_DQxR6wlT7hiCg7XYtirtRiNMEEbeSrjgW54QVxojzifhP1yM3frk_0g)

![](https://lh3.googleusercontent.com/gSOCpvoCUwUwgzBTdlDpm2Y989ABNwSJQV1RXLuE71jNBxj0AWvsrFl3PKNo6jU5eSmwaig98hdkgKMWVVoB9T-s33ISKTx3KSPAQqZ-jE9XpjzizG29G2NmOVNq_LznY7WfQPmjM-C8snb98g)

- 此时再点击执行即可跳出任务提交成功的操作提示。并且可以在数据库中看到提交任务的记录：

![](https://lh5.googleusercontent.com/h8kZDg0V-x6WCnQreq6p0cy1IOYHL1IjbUtUt2MF1w4nq2hXW5P4qDnHO1f2ycQNhJosHlJ5phogHRJkc6VXtFeQAUjIBesPfEaGXjxth_ltCib9QSFdJ85DdsvrIDMuc5LvUSLlYN95paqoCA)

![](https://lh5.googleusercontent.com/sDgk3Zh7ba9lzIXThyABgDPAKB-ih0G9tY5gmjMzTeQeQ9Hz9YtZUFFc5RBeX7U_WIUbODf3FhTIyjdTDwjlhcjhfSZBTw-8rsQ4tifp_YaFDQ1EE-WH_L4n05XZS2zXSNYCSqrn02PcqrTFKw)

- 在conf.default.py中添加celery\_imports。(并注释掉示例任务)：

![](https://lh3.googleusercontent.com/cgKVoJwFtg7_Zsp3TbuEZOQqCKjeJPST6GBZg9oGHQld_A2URNBtQ9ahWKVPjRChoxXkP2qzj_LwEwsuWpwgC5x1Fbj-kxz4nxt9yC7Srn5wzWzAuHrrlGHAvVlRJIGewMRzwWYDIVpjgO0oLg)

- 执行如下命令启动celery worker进程：

```
python manage.py celery worker –settings=settings -l info
```

- 再次提交任务，即可看到任务可以正常执行：

![](https://lh6.googleusercontent.com/XCmUDwEWnzd5Ort_CGaS_63ldroy5DzTteA1QqtAujTxAjEbIXVDyBbBt-XWHCpJIpFmczuvbzAA6T-1yDTFaiSSZtiHoe7U4k3mgNxY52db_Gh2HmjrH6YPPGgrCaSSK2OD-i1uNQ_pvyfBcQ)

**七、任务四：实现历史操作查询功能**

**任务目标: 实现操作历史记录查询功能，可以查询作业的日志详情。**

**1.查询条件选项显示：**

- 在home\_application.views.show\_history添加数据获取函数：

![](https://lh5.googleusercontent.com/ghNvU4e3yVi4gfCqa7LRsg_GWPacf-AVhrR_IrWcl7YViFuRXFlm-v11lapvTdC_D96oMcTmEX6kit7_2Q91natvbBsdKJ8i_rkmPjm4kqY-IHMsnxDMGwPLJW23JJzKEfgIKn7l_5_J6Nc-AA)

- 在history.html中渲染业务数据：

![](https://lh5.googleusercontent.com/MDFm2sTlI_knJbk8pZOY3SgnrxE8851nlH6Ua_ATrfyQxFYP-mIBXq7zIzWnndOE9rRdmiB0GO6m6Rurxrsn_1uWyuYQH3X5ePTC34nRXGHgzK4NsUx1QO7G7-mZTgogfi_kaCPGpGYMWabXhg)

- 刷新页面可以看到业务数据：

![](https://lh5.googleusercontent.com/o-4_rNBQjZrg_lq7-vuDQVBylaf1tEHZzHZ0Wn_JRYAdJrWlLouW24DgGWEY2MZRKi4YFbuvEe5C-Wy2eXJEH9vlkUwiYAQV44Hzzr5OVNse3lkkl3m0lVxefkBcA8Np3nqFpoy0Rm2RjVvOzg)

- 在history.html中渲染用户数据：

![](https://lh3.googleusercontent.com/t0lr5Xx67JMeMXXV4AaTHBZstKcCy96Lu_htuVreEVlgRpFiXXHSzPLihxfcfWhbuxK2f10DySr-Pt7iGHzXqBHGDwHfEh-tW0fLQxcqCYV3DD3ZvcoehjR4tky26PBo6Zq8z8tfILxPb8e-6w)

- 刷新页面可以看到用户数据：

![](https://lh4.googleusercontent.com/pCvjOJyoThkqecMf1XKL7u0_XpKl95QOmNCykMkN03t9O52bpuzVadQJx93_5caA9GaOyC-UwB00bAWtQSNLW7WYsx-N_80G5sft86Otd6583X8n_TbaCO-Nbmdw7okqOpdXISMNsT7_QyZEUA)

- 在history中渲染任务数据：

![](https://lh6.googleusercontent.com/5aA34hIAeQYPi537aqP2vYSyzP8QmHJFUimgc0EPxYHmw63GEslPp6nq3QO5uubIvZ_R0ANz5JRbSvIWYi7FkimsFhwda-aBeSehMUnGgDgmPr17Sxtr8vJFLbclWyYyz1gX0GDxcg0j5SEpfw)

- 刷新页面可以看到任务数据：

![](https://lh3.googleusercontent.com/8t8_no7UIslhCQKM9vNXmXW319BoKLNy2otxNrY_6_PeucmElhOZ3I93MEeWmX8mCBZa3jlE3MpBNaD46HZE9ynPRiopH7ngU8goPvwETymdMfvkPEGRR2YdMKvVsh5qiurRPD_cN7qw6BFZ1A)

**2.添加日期选择插件：**

- 在magicBox中选择日期插件：

![](https://lh4.googleusercontent.com/NuLrymJVLN0tJFO6jtzo617bFFQ2HsX-wDx-2sgqtWKDv899SoPPezhHQBCDO57YAD6jpJe77OTBnpQF6LNvSRKF4wAPCF3iuuL5JS8OhGj6dF4s9VGWMQl2q07wD2vwWf76r122inJTDOZqsQ)

- 拷代码到history.html相应位置：

![](https://lh3.googleusercontent.com/mggYkckLA8gtH-zI0tULAcT5W7hxVSVcagxkq9ZcHsLCwUaIgf09JwHbzd0gpESob4HWHrsfLzLHrCpOE9TcMqxToFakO1maA_kKhg4czZwgL7fGWmMlkbcl0W2xduco1dmvBu3kVT7QX-j7-g)

![](https://lh3.googleusercontent.com/iZcZsTfWABanAE4Us14uXXO781Y9ojJyPQ0zumxMAKZOUwFqcIFVYdF2Vn-RGUXh2JxjTyleoj-BxgbXqGH2ER1X8gD_VdY5VDovsxGbEDR_LBnsyQhptXmZw0wW7vHvFGOAa392yh3QG-H7MQ)

![](https://lh3.googleusercontent.com/JkfeBurOopktnVeVSPxpbRnR-rpWZobmMrA1I-2jwqUQni1IOfj0PGmpUWrFGe95_0x8uAy5ABExoTF6NhULyfnU4CvJ8SVoJ70Bz2dZb_lMMhV3s5G_R0KNJsk6kKzCOI9iEkVnndb8AtHA5A)

![](https://lh3.googleusercontent.com/ivQrqTmEFGz14TtR0vj4ZMcKUpRQFTMY22VbEEzQHEcHeNvGi01Is2RWZVDXbrkFuIGGavW6dSOXPhCk3nqFFzuqlhk22v36UEV_70on9T2w05SVbmRgup6gYkw23dPZMZQA06VtYl70-gn8Hg)

- 修改：

![](https://lh3.googleusercontent.com/jL_NVhTkebdZOzRO_92gLyNm9efF5s2gvXgmJB-ThxdmrGHLa_apZnJoumsMe-_0SWwZzMoQeFhP-28H0Fj9yZneM4e2fjJxiIA0lsZBaNkm-gH6KAW4VqqMZfrdW7HCOSRyWwtTafzKdoQCKg)

![](https://lh3.googleusercontent.com/adyHYHC_LzbP_jCobwD2uzJBLisd-IiK0aN8y7wekOOma03CZJDzXelFYBLhidb4196GZRaCzITB178nnjUWc_aaVPcNDeV-7VGn4vmyKcD81U0hm4aZ5onrwFu1_6f2zEZUwWHPYI7TD__VJA)

**3.更换显示table:**

- 删掉原<table>和相关标签：

![](https://lh5.googleusercontent.com/-590pbywek-phVCHXnzXLt5zo50LoOYXnbHt29UcofzPc1oGMn6AF-hMtf-NvL1o0PiNIJ-OKVFDOgsFph9lE71j_PL9GZpJ9ALjIxV6V8UgBkzfbE7-Ktif9ZCaEpeyNmzRTF90GC3g6mJQKg)

- 将10.html中的<table>标签拷到刚才删掉的位置
- 将10.html中的<link>标签和<script>标签拷到头部

**4.查询操作记录功能：**

- 将11\_views\_get\_operations.py中的函数拷到home\_application.views
- 在home\_application.urls中添加路由：

![](https://lh5.googleusercontent.com/Q8SXH1LfpxBs8leoC9lUutOpPY7drCUzz4bI4j912FiGqYC0MNb5ivlOoZOUemDkjY9Qh7Sj9OXw-Qo3-8eUyvzOnB6GZZR2bQFscnrr-Qzz-pejvlFc4jSiqOUmbewrarSqTliTD2kiX5sn0Q)

- 在页面访问该路由：

![](https://lh6.googleusercontent.com/IUaMtyux74frboOl_zBMvw6IU87HymF8O2BMrJbB1xSkvExhjijH7Qy08DYWMsFBjTudpKLGMllxxeU0WSevIvhYtWgRjvZGpG7m1i8L3hMivw7GlQRfDbf0CqsFfIXz6tUjxCTLmiAHEap5wg)

- 将12\_history\_html\_table.js 拷到history.html底部<script>标签之中：

![](https://lh3.googleusercontent.com/U0hRNC-QhLWhcLSIgyFGj-8qNhemTAZdZ4snQZXbxcEdqcPGWX1hpO8TjKZwrR_LkR4IUxWzV07ZJSLD9olfHlnjyHZqaWPdzISgH4YxwN58iiWF8ZTDR-lAQeA-LHQQ0I_ZLeEiqYr4nJmBmw)

- 刷新任务记录页面：

![](https://lh4.googleusercontent.com/KZRalBerR0k0zkRj8iWPZY-pL3jGZO7bWpDDSzIwSYXBxlMxbVQMpipqHlLDZPF6WvEuzCpzSrKxVBzsIqRgLhhK3Nchdcas3d6qYKHZ9QQDwgKfDhNSrfPkNKXIUa0zQ8HZB2AqizVdOplMBA)

- 更改查询条件，在控制台执行如下函数：

![](https://lh5.googleusercontent.com/BUy6tS7Ln7Rd2ekMllw5fYC_INnfVFlU1HYwvedgbjGUbQ234VVgpaOXQkY_xvAQQtVNrPnKrzZUu6y3PIkMdSGVTozxizsesIFBo61waU7q3KakIxdc3vy0e77SrQh4vUHY7R_cBsOPARHwdA)

- 给查询按钮添加id:

![](https://lh5.googleusercontent.com/DtmpTz7TJzmi_uNGt29iqKn-dScn_Z_IiUugEUTIvQ9139EW0jt6yzuhZ7FJv4EG2eLkUp0zb0iUoyHWmMcUiOf8QQuXQNg7LltCsOYubwkStslIT548LzhnezTdn6YVawYp8h5bLHBsGIMcLQ)

- 在页面上体验查询条件
- 在将13.py中的函数拷到home\_application.views中
- 在home\_application.urls中添加路由：

![](https://lh4.googleusercontent.com/M7siSicZhFPOnwLLkjfKObekplGABiLZHJ5JZrs48wKcfEBsmQv78itbaPfJc4ROGFbDRRsCdkYqp3le5SNrMU11UWxMKbP4Rw8JYX3y3uGk3Zn_VuMbuuA8kO5aHfn3Mgy-5N4VLIt2j_HbYQ)

- 在浏览器测试路由：

![](https://lh5.googleusercontent.com/UOvs8_C_D5Elv_MNm41JpCx2kYWIg7R9nSdhs3Qm7rnlww2hrbVSxmJS0fvVByK9gR0v_4mjuVVQDctJ5NNoFE2GmQC24CSifJ1fRbL0jRfrS-IaDYL-tsoWiIIT0Keklmn-o7kFHLahpcn7qQ)

- 将14.js中的两个函数拷到history.html底部的<script>标签之内，

并：

将其中的两个标签拷到顶部

- 在页面上点击“详情”查看弹出效果
- 将15.html中的<style>标签拷到history.html的顶部
- 在页面上点击“详情”查看样式效果

**八、扩展练习**

1.如何将任务记录中的业务显示由id变为业务名称？

![](https://lh6.googleusercontent.com/6tjtRqgmVz508GAuzbVnvlABOjqKy_rKxINC1Hq6ojhFpTCbkP4BXBau33cvpwtE1qvO1-R71cE1J1ZAzKT1OpMkzk7Mfp-vjgvb4iR6wDdzjcpKzT0Yst5hLUUKeL4nBsZfrcyTw5AkwOx6WQ)

2.如何用报表显示脚本使用情况信息？

**九、实验总结**

本次实验主要带大家体验了在蓝鲸PaaS中快速开发一个运维类应用，希望通过本次课程，可以加深大家对蓝鲸平台及蓝鲸应用开发的理解，更多内容请查询蓝鲸官网。
