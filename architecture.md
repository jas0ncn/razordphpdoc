# 架构

#### 唯一入口

Razord PHP采用唯一入口的模式，所有的路由都会经过 `index.php` 代理到相应的 `controller` ，之后会详细介绍。

#### 路由

Razord PHP没有一个硬性的函数命名规定，Razord对注释进行解析，将规定的路由和相应的路径进行绑定，达到路由绑定的效果。

我们来看个例子（ `./controller/index.class.php` ）：

