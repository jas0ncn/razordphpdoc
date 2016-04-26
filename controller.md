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

每个控制器都是一个PHP类，类中的每一个方法相应的处理一个唯一规则的请求，而这个唯一规则就是路由规则，应写在注释中，这个在之前的 [路由章节](router.md) 中已经讲过了