前端：
problem
template/src/oj/problem/ 提交代码页面

后台：

submission 处理提交代码页面
template/src/oj/submission

judge/runner.py: 判题前的主要准备工作，解压缩应在此修改

judge/compiler.py 编译

judge/language.py 语言编译命令配置

#更改说明：

1、集中OS及开发环境到IMAGE MYOJ/OS的创建，修改源为aliyun,减少代码修改后的创建时间，OJ_WEB_SERVER & Judge 基于MYOJ/OS继续创建。修改OJ_WEB_SERVER代码后，运行bdweb.sh,dc;修改Judge后，运行build.sh,dc.

2、WEB 端口改为1111

3、修改Judge创建时下载源码的地址

#工具说明：

bdos.sh:myos

bdweb.sh:oj_web_server

bdmysql.sh:mysql

build.sh:judge

dc:docker-compose up

docker image list

container_name: oj_redis oj_mysql judger oj_web_server

docker run -it image_name bash 启动镜像并进入BASH交互模式，exit退出

docker rm  container_name 删除本地容器

docker rm $(docker ps -a -q) 清理所有已经创建的包括终止状态的容器

docker rmi image_id 删除本地image，删除前需要清理使用此镜像的容器

# OnlineJudge 

django
├── oj
|       __init__.py
|       settings.py
|       urls.py
|       wsgi.py
├── manage.py
└── apps
        __init__.py
        admin.py
        models.py--db table
        tests.py
        views.py

INSTALLED_APPS = (
'account',
    'announcement',
    'utils',
    'group',
    'problem',
    'admin',
    'submission',
    'contest',
    'judge',
    'judge_dispatcher',

    'rest_framework',
)


DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': "oj",
        'CONN_MAX_AGE': 10,
        'HOST': "oj_mysql",
        'PORT': 3306,
        'USER': os.environ["MYSQL_ENV_MYSQL_USER"],
        'PASSWORD': os.environ["MYSQL_ENV_MYSQL_ROOT_PASSWORD"]
    },

python manage.py syncdb

python manage.py runserver

由于作者工作学习繁忙, 目前只能保证有时间的时候修复部分BUG。

部分相关的组件已经开源, 可以参考。

 - https://github.com/QingdaoU/Judger OnlineJudge判题核心, 目前使用的是master版本, newnew分支为重构版本(推荐)
 - https://github.com/QingdaoU/JudgeServer 使用HTTP提供Judge服务
  
------------------------------------------------------------------
  
基于 Python 和 Django 的在线评测平台。

主要特点:
 
 - 基于 Docker，急速部署
 - 超级管理员管理全局，普通管理员任意创建小组和小组内比赛，方便布置作业和考试使用
 - 提供 Virtual Judge 和单点登录使用 API，不再繁琐的进行模拟登陆
 - 后台管理判题服务器，轻松分离 web 和判题服务器

安装文档: https://github.com/QingdaoU/OnlineJudgeDeploy

OpenAPI文档: https://github.com/QingdaoU/OnlineJudgeOpenAPI

Demo: https://qduoj.com

License: The Star And Thank Author License

交流QQ群: https://github.com/QingdaoU/OnlineJudge/wiki/QQ群

TODO：

 - 完善测试

![](http://7xk96g.com1.z0.glb.clouddn.com/oj-preview/FireShot%20Capture%2028%20-%20%E9%A2%98%E7%9B%AE%E5%88%97%E8%A1%A8%20-%20https___qduoj.com_problems_.png)

![](http://7xk96g.com1.z0.glb.clouddn.com/oj-preview/FireShot%20Capture%2029%20-%20A%20%20%20B%20Problem%20-%20https___qduoj.com_problem_1_.png)

![](http://7xk96g.com1.z0.glb.clouddn.com/oj-preview/FireShot%20Capture%2030%20-%20%E6%88%91%E7%9A%84%E6%8F%90%E4%BA%A4%E8%AF%A6%E6%83%85%20-%20https___qduoj.com_submission_5b229926a4218d43d9e75158be0d1bf4_.png)

![](http://7xk96g.com1.z0.glb.clouddn.com/oj-preview/FireShot%20Capture%2031%20-%20C%E8%AF%AD%E8%A8%80%E5%AE%9E%E9%AA%8C%E7%BB%83%E4%B9%A0%EF%BC%88%E4%B8%80%EF%BC%89%20-%20https___qduoj.com_contest_23_.png)

![](http://7xk96g.com1.z0.glb.clouddn.com/oj-preview/FireShot%20Capture%2035%20-%20%E6%AF%94%E8%B5%9B%E6%8E%92%E5%90%8D%20-%20https___qduoj.com_contest_17_rank_.png)

![](http://7xk96g.com1.z0.glb.clouddn.com/oj-preview/FireShot%20Capture%2033%20-%20%E5%9C%A8%E7%BA%BF%E8%AF%84%E6%B5%8B%E7%B3%BB%E7%BB%9F%20-%20%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%20-%20https___qduoj.com_admin_%23problem_problem_list.png)

![](http://7xk96g.com1.z0.glb.clouddn.com/oj-preview/FireShot%20Capture%2034%20-%20%E5%9C%A8%E7%BA%BF%E8%AF%84%E6%B5%8B%E7%B3%BB%E7%BB%9F%20-%20%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%20-%20https___qduoj.com_admin_%23contest_contest_list.png)
