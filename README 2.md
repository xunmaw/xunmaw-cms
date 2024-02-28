# 欢迎━(*｀∀´*)ノ亻!

# 瀑布内容管理系统

### 瀑布内容管理系统，采用SpringBoot + Apache Shiro + Mybatis Plus + Thymeleaf 实现的内容管理系统(附带权限管理)，是搭建博客、网站的不二之选。

## 文档目录

- [项目介绍](#项目介绍)
- [安装](#安装)
- [使用](#使用)
- [代码结构](#代码结构)
- [主要项目负责人](#主要项目负责人)
- [参与贡献方式](#参与贡献方式)
- [互动交流](#互动交流)
- [开源协议](#开源协议)


## 项目介绍

### **XUNMAW-CMS**，致力于开发最精简、实用的CMS管理系统，适合搭建博客、企业网站等，完美自适应。
###### 满足您的强迫症(包括我自己的强迫症[手动狗头])

后台测试账号 账号：admin 密码：123456

## 技术栈
Spring Boot、Apache Shiro、MyBatis-Plus、Alibaba Druid、Redis、MySQL、Thymeleaf、Google Guava<br/>

![JDK](https://img.shields.io/badge/JDK-1.8-green.svg)
![Maven](https://img.shields.io/badge/Maven-3.3.9-green.svg)
![MySQL](https://img.shields.io/badge/MySQL-5.7-green.svg)
![Redis](https://img.shields.io/badge/Redis-3.0.503-green.svg)
![license](https://img.shields.io/badge/license-MIT-yellow.svg)

## 安装

1. 将本项目源码导入本地开发工具(如 IntelliJ IDEA )，本地开发工具需要安装 [lombok](https://projectlombok.org/) 插件
2. 安装`Mysql`数据库：`Mysql`版本最低支持5.7，新建 database `CREATE DATABASE pb_cms_base;`
3. 初始化数据库：找到项目数据库文件:`docs/db/pb_cms_base.sql`，执行 `pb_cms_base.sql`
4. 安装`Redis`：`Redis`最低版本支持 3.2
5. 修改(`resources/application.yml`)配置文件
    1. 修改数据库链接相关连接串、用户名和密码(可搜索`datasource`)
    2. redis配置(可搜索`redis`)
6. 运行项目(三种方式)
    1. 项目根目录下执行`mvn -X clean package -Dmaven.test.skip=true`编译打包，然后执行`java -jar pb-cms/target/pb-cms.jar`
    2. 项目根目录下执行`mvn springboot:run`
    3. 直接运行`SpringbootApplication.java`
7. 前台首页，浏览器访问`http://localhost:8080`
8. 后台首页，浏览器访问`http://localhost:8080/admin`使用账号密码admin,123456登录系统后台。


## 使用

### 文件上传

文件上传目前支持三种方式：七牛云、腾讯云和本地存储。

可以在`后台管理 -> 上传管理 -> 云存储配置`页面进行文件上传相关配置

小提示：如果使用本地存储，则需要在项目的配置文件中，配置文件上传目录`file.upload-folder` 和 文件访问前缀地址`file.access-prefix-url`。

### 静态化

网站启用静态化步骤：

1. 在yml配置文件中，配置好静态页面文件生成的文件夹路径
2. 启动项目，进入后台->网站管理->基础信息，切换到开启“静态化”，点击保存

## 代码结构

```
├── main
│   ├── java
│   │   └── com
│   │       └── puboot
│   │           ├── SpringbootApplication.java 项目启动类
│   │           ├── common    公共资源，如注解、切面、shiro集成、通用工具类等
│   │           ├── component 项目公共组件
│   │           ├── enums     枚举类
│   │           ├── exception 全局异常处理
│   │           └── module
│   │               └── admin 后台模块
│   │               └── blog  前端模块
│   └── resources
│       ├── application-dev.yml 开发环境配置文件
│       ├── application-prd.yml 生产环境配置文件
│       ├── application.yml     通用配置文件
│       ├── logback-spring.xml  日志配置文件
│       ├── mapper              Mybatis XML文件
│       ├── static
│       │   ├── admin           后台css、js、插件、图片
│       │   ├── css             项目前后台通用css文件
│       │   ├── favicon.ico     项目前后台通用css文件
│       │   ├── img             项目前后台通用图片文件
│       │   ├── js              项目前后台通用js文件
│       │   ├── libs            项目前后台通用类库
│       │   └── theme           主题相关资源
│       │       └── pb
│       └── templates           项目页面目录
│           ├── admin           后台页面目录
│           │   ├── article     文章管理
│           │   ├── category    分类管理
│           │   ├── comment     评论管理
│           │   ├── database    数据库监控
│           │   ├── fragments   通用页面
│           │   ├── index       后台首页
│           │   ├── link        友链管理
│           │   ├── onlineUsers 在线用户
│           │   ├── permission  权限管理
│           │   ├── role        角色管理
│           │   ├── site        站点管理
│           │   ├── tag         标签管理
│           │   ├── theme       主题管理
│           │   ├── upload      上传管理
│           │   └── user        用户管理
│           ├── error
│           │   ├── 403.html
│           │   ├── 404.html
│           │   ├── 4xx.html
│           │   ├── 500.html
│           │   └── 5xx.html
│           ├── home
│           │   └── fragments  前端通用页面
│           ├── system
│           │   ├── kickout.html  踢出页面
│           │   ├── login.html    登录页面
│           │   └── register.html 注册页面
│           └── theme             主题目录
│               └── pblog         默认主题
└── test
    └── java
        └── com
            └── puboot
                ├── SpringbootApplicationTests.java 单元测试

## 主要项目负责人

## 参与贡献方式

1. Fork 本项目
2. 新建 feature_xxx 分支
3. 提交代码
4. 提交 Pull Request

## 开源协议

MIT © 2023 xunmaw
