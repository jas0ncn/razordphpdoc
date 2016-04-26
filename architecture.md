# 架构

#### 唯一入口

Razord PHP采用唯一入口的模式，所有的路由都会经过 `index.php` 代理到相应的 `controller` ，之后会详细介绍。

