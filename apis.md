# API 文档

> 特别注意，使用任何 API 请先实例化 Razord 的 Bootstrap：
> ```php
> require('./config.php');
> require('./core/init.php');
> 
> $Razord = new Bootstrap;
> ```
> 以下代码演示基于实例 `$Razord`。

### `load()`

**描述：** Razord 加载模块函数，关于模块的加载，可以参考 [模块系统](module.md)

**原型：**
```php
public function load ($moduleName) {...}
```

**参数：**

`$module` 要加载的模块名称，可以是模块名称的数组

**返回值：**

无

**例子：**

```php
$Razord->load('verify'); // 加载全局验证模块
```
或
```php
$moduleNames = array('verify'); // 要加载的模块名称的数组
$Razord->load($moduleNames);
```
***

### `start()`

**描述：** Razord 应用启动函数

**原型：**
```php
public function start () {...}
```

**参数：**

无

**返回值：**

无

**例子：**

```php
$Razord->start(); // 启动框架
```
***

### `output()`

**描述：** Razord 输出模块

**原型：**
```php
public function output ($content) {...}
```

**参数：**

`$content` 要输出的内容

**例子：**

```php
$Razord->start(); // 启动框架
```