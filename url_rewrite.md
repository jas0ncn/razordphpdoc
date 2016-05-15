# Url 重写

Razord PHP 使用了 Url 重写，这意味着你的服务器必须支持 Url 重写，以下介绍在 Apache 和 Nginx 下如何设置Url重写。

### Apache

在 `[Apache安装目录]/conf/httpd.conf` 中找到

```ini
#LoadModule rewrite_module modules/mod_rewrite.so
```
去掉前面的井号：

```ini
LoadModule rewrite_module modules/mod_rewrite.so
```

在 `[Apache安装目录]/conf/extra/httpd-vhost.conf` 中找到

```ini
Options FollowSymLinks
AllowOverride None
Order deny,allow
Deny from all
```
修改为：

```ini
Options FollowSymLinks
AllowOverride All
Order deny,allow
Deny from all
```

重启 Apache 即可

### Nginx

在 `Linux` 下执行：
```bash
vim /etc/nginx/conf.d/[YOURCONFIG].conf
```
然后修改 `.conf` 文件中对 PHP 代理的设置：

```bash
location ~ .php$ {

    [...Some Code]

    if (!-f $request_filename){
    	set $rule_0 1$rule_0;
    }
    if (!-d $request_filename){
    	set $rule_0 2$rule_0;
    }
    if ($1 !~ "^(index\.php|robots\.txt|static)"){
    	set $rule_0 3$rule_0;
    }
    if ($rule_0 = "321"){
    	rewrite ^/(.*)$ /index.php/$1 last;
    }

    [...Some Code]

}
```

### 部署在二级目录

如果你将 RazordPHP 部署在二级目录，请注意修改 `.htaccess` （Apache 环境下）

```
...
RewriteRule ^FOLDER_NAME/(.*)$ /index.php/$1 [L]
RewriteRule ^FOLDER_NAME /index.php/index [L]
...
```

同理，Nginx 环境下修改为：

```bash
...
rewrite ^/FOLDER_NAME/(.*)$ /index.php/$1 last;
rewrite ^/FOLDER_NAME /index.php/index last;
...
```

当设置了二级目录的Url重写时，请将 `.htaccess` 放在二级目录而不是放在顶层目录中。同时，您需要访问

重启 Nginx 即可。