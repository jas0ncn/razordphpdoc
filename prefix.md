# 二级目录部署

在 RazordPHP v1.1 的更新中，我们带来了一个全新的功能：`prefix`

### 什么是 `prefix` ？

当我们在平常的开发过程中，`RESTful api` 并不一定是作为整个网站的顶级目录的，更多的可能是如下的 url ：

```
http(s)://xxx.com/api
```

这就带来了一个问题，如果你将 RazordPHP 部署在二级目录里，可能会导致路由解析错误。

因此，我们带来了 `prefix` 来解决二级目录部署的问题

### 如何使用

`prefix` 的使用非常的简单，只需要在 RazordPHP 实例化的时候加上一个 `prefix` 参数，例如这样：

```php
$Razord = new Bootstrap('api');
```

这个时候，RazordPHP 将会把 `/api` 当成顶级路径，直接访问 `xxx.com/api` 将会指向 `index` 控制器而不是 `api` 控制器。

请注意，如果你将 RazordPHP 部署在二级目录，Url重写也需要相应的修改，具体请查看 [Url重写](url_rewrite.md#部署在二级目录)