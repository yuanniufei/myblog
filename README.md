### Author:qyzxg
### Email:qyzxg@live.com

### 项目介绍
myblog是一个基于flask的开源多用户博客系统,功能基本完整,目前主要功能如下,代码简单易懂,比较适合作为入门参考:
- [x] 用户注册登录,邮件激活 
- [x] 发表(CKeditor,开启文件上传功能),修改博客,发布评论
- [x] 全文搜索,支持中文搜索
- [x] 文章收藏,文章分类
- [x] 用户关注,用户资料页
- [x] 站内信功能
- [x] 用户后台,修改图像(本地上传),密码,查看个人信息统计(echarts图表),管理自己的文章,评论,好友,消息等
- [x] 管理员后台,查看所有统计信息图表,管理所有文章,评论,用户(权限控制),发布系统通知
- [x] 其他功能,所有celery异步处理电子邮件,获取文章图片,使用redis缓存页面(首页,文章详情页等)和函数(获取图表所需数据的函数)

### 用到的技术和工具
Python 3.5.2
flask 0.12
mysql 5.7
CKeditor 4.6
echarts 3.0
celery
redis
Nginx
gunicorn
fabric3
.........
### 基本部署方法
系统:Ubuntu16.04
主机:亚马逊EC2/阿里云ECS(推荐EC2免费使用1年,速度还可以,比较稳定)
部署步骤:克隆代码到本地后,修改配置文件(config.py)
1.远程服务器安装好Python环境/Nginx/gunicorn/redis/mysql
2.对以上进行配置如Nginx配置:
    $ sudo vim /etc/nginx/site-avalidable/default
	```Bash
			server {
			listen 80 default_server;
			listen [::]:80 default_server;
			>这是HOST机器的外部域名，用地址也行
			server_name example.org;
			location / {
				# 这里是指向 gunicorn host 的服务地址
				proxy_pass http://127.0.0.1:8080;
				proxy_set_header Host $host;
				proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
			}
		}
	```
3.初始化数据库
4.将本文件拷贝到和myblog同级目录,如:www,创建deploy目录
    目录结构:
    /www
        myblog
          app
          ...
        fabfile.py
        deploy
5.填写fabric配置信息,在www目录下运行 fab build 打包程序文件,然后运行fab deploy
6.在myblog目录下运行 gunicorn -w 4 -b 127.0.0.1:8080 run:app 
*注:这只是一个基本部署,还有进程管理等可以自己Google,
该部署流程要求本地计算机为Linux平台,window需要在cygwin环境下执行*

### 网站demo部署在EC2上
网址:www.51datas.com
管理员账号:qyzxg
密码:abc123
建议自己注册账号测试,欢迎发布文章

### 网站截图
#### 首页
![image](https://github.com/qyzxg/myblog/blob/master/screenshot/2017-02-17_080528.png)
#### 文章详情页
![image](https://github.com/qyzxg/myblog/blob/master/screenshot/2017-02-17_080622.png)
#### 个人资料页
![image](https://github.com/qyzxg/myblog/blob/master/screenshot/2017-02-17_080634.png)
#### 更换图像
![image](https://github.com/qyzxg/myblog/blob/master/screenshot/2017-02-17_080642.png)
#### 后台用户管理
![image](https://github.com/qyzxg/myblog/blob/master/screenshot/2017-02-17_080659.png)
#### 后台文章管理
![image](https://github.com/qyzxg/myblog/blob/master/screenshot/2017-02-17_080708.png)
#### 后台评论管理
![image](https://github.com/qyzxg/myblog/blob/master/screenshot/2017-02-17_080715.png)


