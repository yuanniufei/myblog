#myblog基本介绍

这是我的第一个Python web入门项目,使用flask框架,代码简单容易理解,基本功能简单,
flush信息提示完善,可以给刚入门的同学做一个参考,下面简单介绍下目前实现的功能:

#用户方面
用户登录/注册/密码加密/邮箱验证(验证后才能发表文章和评论)
首页统计文章浏览量和评论数量
用户可以自定义上传图像
> 还需完善用户个人资料页,展示相关信息和修改个人资料,
管理员和普通用户分别用不同页面显示,优化前端布局 已完成

#文章/评论
支持markdown格式发表文章,控制文章字数,修改文章

#后台管理
管理员对可以对所有用户进行管理,包括限制登录,给予和收回管理权限
删除用户,对文章进行修改好删除,评论删除

>后期还会在后台加上统计图表 已完成

使用celery 异步处理,已经redis缓存

已部署在亚马逊EC2上,网址www.51datas.com,欢迎大家光临并提出宝贵意见或建议

#主要部分截图
##首页
![image](https://github.com/qyzxg/myblog/blob/master/screenshot/主页.png)
##文章详情页
![image](https://github.com/qyzxg/myblog/blob/master/screenshot/文章详情页1.png)
##用户资料页
![image](https://github.com/qyzxg/myblog/blob/master/screenshot/用户资料页.png)
##用户后台首页
![image](https://github.com/qyzxg/myblog/blob/master/screenshot/用户后台首页.png)
##用户消息管理,管理员可以群发消息
![image](https://github.com/qyzxg/myblog/blob/master/screenshot/站内信.png)
##管理员后台首页
![image](https://github.com/qyzxg/myblog/blob/master/screenshot/管理员后台首页.png)
