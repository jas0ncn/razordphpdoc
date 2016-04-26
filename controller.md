# 控制器

Razord PHP的应用中，每一个二级目录对应一个控制器，控制器应放在和 `index.php` 同级的 `controller` 目录下，命名规则为：
```
[CONTROLLER_NAME].class.php
```
对应的 `http` 路径为：
```
xxx.com/[CONTROLLER_NAME]
```
特别的，若访问域名的根目录 `xxx.com/` 时，Razord将直接调用 `index.class.php` ，所以无论如何，控制器目录都必须有 `index.class.php` 这个文件。