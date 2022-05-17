---
title: nginx+nps的配置修改
date: 2022-05-17 17:12:00
tags: Tips
categories: Useful Tools
author: Lcy
---

# Nginx+Nps端口修改配置

这里因为网站时80端口，同时nps又需要80端口，所以需要使用nginx进行一个转发的设置。

## nps设置

这里将http端口从80改到了8010。

```shell
http_proxy_ip=0.0.0.0
http_proxy_port=8010
https_proxy_port=443
https_just_proxy=true
#default https certificate setting
https_default_cert_file=conf/server.pem
https_default_key_file=conf/server.key
```

## nginx设置

相应的，对应的nginx就可以修改如下：

```shell
user root;
worker_processes auto;
pid /run/nginx.pid;
include /etc/nginx/modules-enabled/*.conf;

events {
	worker_connections 768;
}

http {

	sendfile on;
	tcp_nopush on;
	tcp_nodelay on;
	keepalive_timeout 65;
	types_hash_max_size 2048;

	include /etc/nginx/mime.types;
	default_type application/octet-stream;


	ssl_protocols TLSv1 TLSv1.1 TLSv1.2 TLSv1.3; 
	ssl_prefer_server_ciphers on;


	access_log /var/log/nginx/access.log;
	error_log /var/log/nginx/error.log;

	gzip on;
	server {
    		listen 80;
    		server_name *.proxy.com;
    		location / {
        			proxy_set_header Host  $http_host;
        			proxy_pass http://127.0.0.1:8010;
    		}
	}
	server {
        		listen       80;
        		server_name  *.seujyh.cn;
        		autoindex on;	
        		root    /root/luochengyu/HomePage/dist;
        		index  index.html;
        		location /about {
        			index  about.html;
        		}   
        		location /blog{
			alias  /root/luochengyu/HomePage/dist/luochengyublog/public;
        			index  index.html;
       		 }      
   	 }
	include /etc/nginx/conf.d/*.conf;
	include /etc/nginx/sites-enabled/*;
}


```

## nps的配置文件启动方法

参考配置文件：

```shell
[common]
server_addr=ip:8024
conn_type=tcp
vkey=??
auto_reconnection=true
web_username=??
web_password=??
crypt=false
compress=false
disconnect_timeout=60
```

