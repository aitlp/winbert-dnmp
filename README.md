# DNMP(Docker+Nginx+Mysql+Php) + V2ray


示例域名：`4spaces.net`用于网站，`v2.coding996.com`用于v2ray服务。



1.修改配置

将`sample.env`文件，重命名为`.env`，里面配置的数据库密码等信息。

2.修改`init-letsencrypt.sh`

将`your_domain`修改为自己的域名，将`your_email_address`修改为自己的邮箱地址。

3.修改Nginx配置

其中，`services/nginx/conf.d/4spaces.conf`文件为网站域名对应配置；`v2ray.conf`为v2ray对应配置。
