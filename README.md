# DNMP(Docker+Nginx+Mysql+Php) + V2ray

>安装docker及docker-compose的详细说明参考： [在docker-compose环境下以ws+tls方式一键搭建v2ray(So easy)](https://www.4spaces.org/docker-compose-install-v2ray-ws-tls/)；

示例域名：`4spaces.org`用于网站，`v2.coding996.com`用于v2ray服务。

**1.修改配置**

将`sample.env`文件，重命名为`.env`，里面配置的数据库密码等信息。

**2.为`4spaces.org`申请证书**

1）修改`init-letsencrypt.sh`

**将`your_domain`修改为`4spaces.org www.4spaces.org`**，将`your_email_address`修改为自己的邮箱地址。

2）修改Nginx配置

* 网站主目录

将`www/4spaces`目录改为你自己的目录名，比如`www/your_domain`，命令为：

```
mv ./www/4spaces ./www/your_domain
```

* `nginx配置`

其中，`services/nginx/conf.d/4spaces.conf`文件为网站域名对应配置；`services/nginx/conf.d/v2ray.conf`为v2ray对应配置。

将`services/nginx/conf.d/v2ray.conf`重命名为`services/nginx/conf.d/v2ray.conf.bak`，命令为：

```
mv services/nginx/conf.d/v2ray.conf  services/nginx/conf.d/v2ray.conf.bak
```

并将`services/nginx/conf.d/4spaces.conf`配置文件中的`server_name`、`root`分别改成自己的域名和网站目录位置。 


3）启动相关容器

```
docker-compose up -d
```

4）开始申请证书

```
docker container stop nginx

bash ./init-letsencrypt.sh
```

**3.为`v2.coding996.com`申请证书**

1）修改`init-letsencrypt.sh`

将`your_domain`修改为`v2.coding996.com`，将`your_email_address`修改为自己的邮箱地址。


2）开始申请证书

```
bash ./init-letsencrypt.sh
```

完成。