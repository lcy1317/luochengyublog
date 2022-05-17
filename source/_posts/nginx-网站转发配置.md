---
title: nginx 网站转发配置
date: 2022-05-17 14:06:54
tags: Tips
categories: Tips
author: Lcy
---

```json
#user www-data;
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

# fastcgi
#fastcgi_cache_path /usr/local/nginx/fastcgi_cache levels=1:2 keys_zone=test:10m inactive=5m;
#fastcgi_connect_timeout 300;
#fastcgi_send_timeout 300;
#fastcgi_read_timeout 300;
#fastcgi_buffer_size 64k;
#fastcgi_buffers 4 64k;
#fastcgi_busy_buffers_size 128k;
#fastcgi_temp_file_write_size 128k;
#fastcgi_cache TEST;
#fastcgi_cache_valid 200 302 1h;
#fastcgi_cache_valid 301 1d;
#fastcgi_cache_valid any 1m;

	ssl_protocols TLSv1 TLSv1.1 TLSv1.2 TLSv1.3; # Dropping SSLv3, ref: POODLE
	ssl_prefer_server_ciphers on;


	access_log /var/log/nginx/access.log;
	error_log /var/log/nginx/error.log;


	gzip on;
server
    {
        listen       8081;
        server_name  localhost;
        location /api {
                root   html;
                index  index.html index.htm;
                add_header Access-Control-Allow-Origin *;
                add_header Access-Control-Allow-Methods 'GET, POST, OPTIONS';
                add_header Access-Control-Allow-Headers 'DNT,X-Mx-ReqToken,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type,Authorization';
                if ($request_method = 'OPTIONS') {
                        return 204;
                }
		proxy_pass   http://127.0.0.1:8082;
         }
    }
server {
    listen 80;
    server_name *.proxy.com;
    location / {
        proxy_set_header Host  $http_host;
        proxy_pass http://127.0.0.1:8086;
    }
}
    server {
        listen       80;
        server_name  *.seujyh.cn;
        autoindex on;	
        root    /root/Desktop/luochengyu/HomePage/dist;
        index  index.html;
        location /about {
        	#alias  /root/Desktop/luochengyu/gametheory/;
        	index  about.html;
        }   
        location /blog{
        	#alias  /root/Desktop/luochengyu/HomePage/dist/lcyblog/public;
	alias  /root/Desktop/luochengyu/HomePage/dist/luochengyublog/public;
        	index  index.html;
        }      
    }
    server {
        listen       8099;
        server_name  localhost;
        default_type application/json;
        add_header Access-Control-Allow-Origin $http_origin always;
        add_header Access-Control-Allow-Methods 'GET, POST, OPTIONS';
        add_header Access-Control-Allow-Credentials 'true';
        add_header Access-Control-Allow-Headers 'DNT,X-Mx-ReqToken,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type,Authorization';

        autoindex on;	
        #root    /root/Desktop/luochengyu/wordpress/;
        root   /root/Desktop/luochengyu/typecho/;
        location / {
        		# 这里改动了 定义首页索引文件的名称
        		index install.php;
        }
	location ~ \.php$ {
        		# 设置监听端口
        		#fastcgi_pass   127.0.0.1:9000;
		fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
        		# 设置nginx的默认首页文件(上面已经设置过了，可以删除)
        		fastcgi_index  index.php;
        		# 设置脚本文件请求的路径
        		fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
        		# 引入fastcgi的配置文件
        		include        fastcgi_params;
   	 }
    }
    server {
        listen       8901;
        server_name  localhost;
        autoindex on;	
        root    /root/Desktop/luochengyu/gametheory/;
        index analysis.html;
    }
	include /etc/nginx/conf.d/*.conf;
	include /etc/nginx/sites-enabled/*;
}

```

