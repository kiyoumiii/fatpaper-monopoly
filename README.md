Fatpaper 联机大富翁
=====

![01](kabi_dfw/01.jpg)
![02](kabi_dfw/02.jpg)
![03](kabi_dfw/03.jpg)

大富翁总项目，使用子模块引用各个大富翁部分，支持使用docker运行项目。
>全局配置请到根目录的`global.config.ts`中修改。

#### 小白食用教程（windows下使用docker desktop部署，使用镜像源免魔法）
教程: https://note.youdao.com/s/1fUq7glx

#### 注意⚠️
1. 在非localhost网络环境下部署时需要将`global.config.ts`里的`FATPAPER_HOST`修改为对应的地址或域名。
2. 搭建非本地环境时部分资源出现（403、跨域）问题：由于下行流量费用的问题，限制了除127.0.0.1和localhost以外的ip或域名的访问作者的COS资源（monopoly.sql中的资源链接），使用其他ip或域名搭建的小伙伴需要去[下载游戏资源](https://afdian.com/a/fatpaper)，在管理端进行替换相对应的资源。

#### 拉取项目
要连着子模块一起拉取到本地，
```
git clone --recursive https://github.com/FatPaper-1874/fatpaper-monopoly.git
```

子模块更新
```
git submodule update --remote
```
#### 文件目录结构
子模块的目录结构在子模块中
```
├─📁 conf--------------------------- # docker启动时需要的配置文件
│ ├─📁 sql
│ │ └─📄 init.sql------------------- # 初始数据库的sql命令
│ ├─📄 my.cnf----------------------- # mysql配置文件
│ └─📄 nginx.conf------------------- # nginx配置文件
├─📄 .dockerignore
├─📄 .gitignore
├─📄 .gitmodules
├─📄 docker-compose-local.yml------- # docker-compose文件，用于在docker启动项目
├─📄 dockerfile-monopoly-server----- # 大富翁服务器的docker文件
├─📄 dockerfile-user-server--------- # 用户服务器的docker文件
├─📄 dockerfile-web----------------- # 前端web网页的docker文件
├─📄 global.config.ts--------------- # 全局配置文件
├─📄 LICENSE
├─📄 monopoly.sql------------------- # 演示视频中使用到的演示数据
├─📄 quick-dev-start.bat------------ # 以命令行的方式快速启动
├─📄 quick-docker-build.bat--------- # docker快速打包项目
├─📄 quick-docker-start.bat--------- # docker快速运行项目
├─📄 README.md
├─📄 tencent-cloud.ts--------------- # 腾讯云COS的配置，可以不填写
└─📄 user-server-health-check.js---- # 健康检查js，用于docker-compose顺序启动
```

#### 跑起来的方法
* ##### 使用原生方法安装（开发时）
1. 环境中要有mysql，运行根目录的`monopoly.sql`文件；
2. 在拉取全部子模块后，到各个子模块使用`yarn`安装依赖；
3. 可以在各个子模块中使用`yarn dev`分别启动项目，也可以直接启动根目录的`quick-dev-start.bat`一键启动；

* ##### 使用docker启动
1. 环境中要安装docker；
2. 使用魔法🧙‍♀️；
3. 启动`quick-docker-start.bat`一键启动；
