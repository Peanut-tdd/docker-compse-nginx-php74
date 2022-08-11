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