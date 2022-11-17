# docker-compse-nginx-php74
## 目录结构如下：
```
[root@localhost lnmp]# tree
.
├── docker-compose.yml
├── nginx
│   ├── conf
│   │   ├── conf.d
│   │   │   ├── default.conf
│   │   │   └── vagrant_duanju_admin.conf
│   │   └── nginx.conf
│   └── logs
│       ├── access.log
│       ├── default.log
│       ├── duanju_admin.access.log
│       └── error.log
├── php-extension
│   └── Dockerfile
└── README.md
```



## docker-compose.yml文件配置说明

```
#定义docker compose yml版本
version: "3"  
#定义我们的服务对象
services:   
#自定义的服务名称
  nginx:    
     #镜像名称，默认拉取本地镜像，没有的话从远程获取
     image: nginx:latest
     #自定义容器的名称
     container_name: c_nginx
     #将宿主机的80端口映射到容器的80端口
     ports:
      - "80:80"
     #将宿主机的~/lnmp/www目录和容器的/usr/share/nginx/html目录进行绑定，并设置rw权限
     #将宿主机的~/lnmp/nginx/conf/default.conf和容器的/etc/nginx/conf.d/default.conf进行绑定
     volumes:
      - /home/www:/usr/share/nginx/html/:rw
      - /home/www/lnmp/nginx/conf/nginx.conf:/etc/nginx/nginx.conf
      - /home/www/lnmp/nginx/conf/conf.d:/etc/nginx/conf.d
      - /home/www/lnmp/nginx/logs:/var/log/nginx
     #设置环境变量，当前的时区
     environment:
      TZ: "Asia/Shanghai"
     #容器是否随docker服务启动重启
     restart: always
     #容器加入名为lnmp的网络
     networks:
      - lnmp
  php:
     build: ./php-extension
     container_name: php74
     restart: always
     volumes:
      - /home/www/:/var/www/html/:rw
     restart: always
     cap_add:
          - SYS_PTRACE
     networks:
          - lnmp
networks:   
  #创建了一个自定义的网络叫做lnmp
  lnmp:
```







运行命令：

``````
docker-compose up --build -d            #启动并后台运行,不加buil参数会使用本地历史镜像创建容器
docker-compose stop				#停止
``````

注：需先安装docker和docker-compose
