---
layout: post
title: "rails with thin and nginx deploy"
date: 2014-08-04 15:08
comments: true
categories: 
---

### 1.环境说明
* [nginx](http://nginx.org/) 静态资源处理（图片，css，js等资源）与反向代理(转发rails请求)

* [thin](https://github.com/macournoyer/thin/) 处理rails请求，Why Thin？比较简单，性能还可以，中小型站问题不大；

* 默认项目目录/data/htdocs/xxx.dev.com

* Git 版本控制工具

* [capistrano](http://www.capistranorb.com/) 自动化部署工具

---

### 2.Nginx安装及配置

#### 2.1 Nginx安装
* wget http://nginx.org/download/nginx-1.7.3.tar.gz #下载nginx 例/home/software目录

* tar zxvf nginx-1.7.3.tar.gz #解压nginx

* cd nginx-1.7.3

* ./configure  --prefix=/usr/local/webserver/nginx --with-http_stub_status_module --with-http_ssl_module #配置nginx参数

* make && make install #编译并安装

####2.2 Nginx站点配置

{% highlight c%}
#demo_app 与下面proxy_pass 名称保持一致
upstream demo_app {
  server 127.0.0.1:8000;
  server 127.0.0.1:8001;
  server 127.0.0.1:8002;
}

server {
  listen       80;
  server_name  xxx.dev.com ;

  root /data/htdocs/xxx.dev.com;
  
  #处理assets静态资源，nginx直接处理
  location ~* /.*\.(png|jpg|ico|jpeg|css|js|eot|ttf|woff|svg|otf) {
   root /data/htdocs/xxx.dev.com/public;
  }

  location / {
    proxy_set_header  X-Real-IP  $remote_addr;
    proxy_set_header  X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header Host $http_host;
    proxy_redirect off;
    if (-f $request_filename/index.html) {
      rewrite (.*) $1/index.html break;
    }
    if (-f $request_filename.html) {
      rewrite (.*) $1.html break;
    }
    #转发rails请求
    if (!-f $request_filename) {
      proxy_pass http://demo_app; 
      break;
    }
  }
  
  location ~ .*\.(gif|jpg|jpeg|png|bmp|swf)$
  {
    expires      30d;
  }

  location ~ .*\.(js|css)?$
  {
    expires      1h;
  }
  
  #站点日志
  access_log  logs/xxx.dev.com.log  access;
}

{% endhighlight %}

#### 2.3 Nginx 相关命令
* nginx -t #测试nginx配置文件正确性；
* nginx -s reload #重新加载配置文件；

---


### 3.Rails 部署
* git clone https://xxx.git  xxx.dev.com
* 如果使用rvm 设置.rvmrc文件；
* cd到项目目录 bundle install;
* rake db:create RAILS_ENV=production #创建数据库；
* rake db:migrate RAILS_ENV=production #迁移数据库文件；
* rake db:precompile RAILS_ENV=production #编译assets下静态资源文件到public目录下；
* thin start -p 8000 -C config/thin.yml #启动thin服务
* thin stop -p 8000 -C config/thin.yml #停止thin服务

#### 3.1 Thin配置文件参考
* 将thin的配置文件放到项目config/thin.yml即可；

{% highlight c%}
#thin config
#user: www #指定项目运行用户
#group: www #指定项目运行用户组
pid: tmp/pids/thin.pid
timeout: 30
wait: 30
log: log/thin.log
max_conns: 1024
require: []
environment: production
#environment: development 指定运行环境
max_persistent_conns: 512
servers: 3 #指定服务数，比如指定8000端口，那么会起8000-8002端口服务
threaded: false
daemonize: true #是否后台运行
#socket: tmp/sockets/thin.sock
chdir: /data/htdocs/xxx.dev.com
tag: thin-server #ps命令搜索标签名称

{% endhighlight %}