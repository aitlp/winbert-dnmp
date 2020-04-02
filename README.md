# DNMP(Docker+Nginx+Mysql+Php) + V2ray


示例域名：`4spaces.net`用于网站，`v2.coding996.com`用于v2ray服务。



1.修改配置

将`sample.env`文件，重命名为`.env`，里面配置的数据库密码等信息。

2.为`4spaces.net`申请证书

1）修改`init-letsencrypt.sh`

将`your_domain`修改为`4spaces.net`，将`your_email_address`修改为自己的邮箱地址。

2) 修改Nginx配置

其中，`services/nginx/conf.d/4spaces.conf`文件为网站域名对应配置；`services/nginx/conf.d/v2ray.conf`为v2ray对应配置。

将`services/nginx/conf.d/v2ray.conf`重命名为`services/nginx/conf.d/v2ray.conf.bak`，命令为：

```
mv services/nginx/conf.d/v2ray.conf  services/nginx/conf.d/v2ray.conf.bak
```

3) 开始申请证书

```
sh ./init-letsencrypt.sh
```

3.为`v2.coding996.com`申请证书

1）修改`init-letsencrypt.sh`

将`your_domain`修改为`v2.coding996.com`，将`your_email_address`修改为自己的邮箱地址。

2) 修改Nginx配置

将`services/nginx/conf.d/4spaces.conf`重命名为`services/nginx/conf.d/4spaces.conf.bak`，命令为：

```
mv services/nginx/conf.d/4spaces.conf  services/nginx/conf.d/4spaces.conf.bak
```

3）停止`nginx`

```
docker container stop nginx
```

4) 开始申请证书

```
sh ./init-letsencrypt.sh
```

4.nginx配置文件复原

将刚才命名为`services/nginx/conf.d/4spaces.conf.bak`改回`services/nginx/conf.d/4spaces.conf`。

5.重启nginx

```
docker exec nginx nginx -s reload
```

完成。