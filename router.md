# 路由

Razord PHP没有一个硬性的函数命名规定，Razord对注释进行解析，将规定的路由和相应的路径进行绑定，达到路由绑定的效果。

#### 语法

Url接受两个参数，一个规定匹配的 `method` ，一个规定匹配的路径。 

```
@url([METHOD], [PATH])
```

##### 例子

我们来看个例子（ `./controller/index.class.php` ）：

```php
class index
{
    /**
     * 根目录
     * @url(GET, '/')
     */
    public function root ($modules) {
        $msg = 'Hello World';
        Boostrap::output($msg);
    }
    
    ...
```
可以发现，在注释中，多了一行：`@url(GET, '/')`，这段代码是Razord路由绑定语法。

当一个HTTP请求的 `method` 为 `GET` 时，且访问路径为 `/` 或 `/index` ，将会执行 `root` 函数。
    
```php
    ...

    /**
     * 二级目录
     * @url(GET, '/heyjason')
     */
    public function heyJason ($modules) {
        $msg = 'Hey Jason!';
        Boostrap::output($msg);
    }
    
    ...
```
同样，当HTTP请求的 `method` 为 `GET` 时，且访问路径为 `/index/heyjason` ，将会执行 `heyJason` 函数。

#### 参数路由