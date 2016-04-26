# 路由

Razord PHP没有一个硬性的函数命名规定，Razord对注释进行解析，将规定的路由和相应的路径进行绑定，达到路由绑定的效果。

#### 语法

Url路由绑定接受两个参数，一个规定匹配的 `method` ，一个规定匹配的路径。 

```
@url([METHOD], [PATH])
```

##### 例子

我们来看个例子：

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

再来看另一个例子：
    
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

在实际的开发过程中，我们可能会遇到需要查询参数（`query`）的路径，Razord允许开发者在路由上绑定查询参数，具体语法如下：

```
@url([METHOD], [PATH/:KEY])
```

注意，记得在相应的函数上加入第二个参数（例中的`$query`），`$query`是一个数组，结构为 `array('KEY' => 'VALUE')` ，`KEY` 为路由绑定的键名：

```php
    ...
    /**
     * @url(GET, '/index/:keyword')
     */
    public function funciontName ($modules, $query) {
        print_r($query); // array('keyword' => 'value')
    }
    ...
```

同样的，你可以绑定多个参数，看例子：

```php
    ...
    /**
     * @url(GET, '/index/:keyword1/:keyword2')
     */
    public function funciontName ($modules, $query) {
        print_rt($query); // array('keyword1' => 'value1', 'keyword2' => 'value2')
    }
    ...
```

以上代码你都可以在 `./controller/index.class.php` 中找到。

#### 注意

你仍可以通过 `$_GET` 和 `$_POST` 等全局变量获取查询参数值，但我们不建议这么做。