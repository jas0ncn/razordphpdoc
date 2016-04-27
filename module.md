# 模块系统

Razord 设计了一套模块系统，使得你可以轻易的引入或开发一套模块。

### 基本语法

模块本身是一个 PHP 类，遵循 PHP 类的语法，但注意，每个模块都必须有一个 `$exec` 方法，这个方法供 Razord 在加载类的时候初始化使用，如果你有任何逻辑想在程序之前执行的，也可以写在 `$exec` 中。例如 `./module/verify.class.php` 中的权限验证：

```php
/**
* 全局验证模块
*/
class verify
{
    // 必须！
    public function exec ()
    {
        return true;
    }

    ...
}
```
### 注册模块（引入模块）

在应用的入口文件（一般是 `index.php` ）中使用 `Bootstrap` 的 API `load()` 引入：

```php
$Razord->load('MODULE_NAME');
```

关于 `load()` 的详细文档，请查看 [API文档](apis.md)

注意，要载入的模块必须放在 `./module` 文件夹中，且命名同 `controller` 命名相同：

```
[MODULE_NAME].class.php
```

若命名错误或没有找到模块，Razord 将输出错误 `103`

### 调用模块

既然是模块，载入了 Razord 中肯定要能调用，在控制器的方法中，我们强调要添加 `$modules` 参数（[控制器](controller.md)），载入的模块都会被注册到这个变量中。

在控制器的方法中可以通过以下语法来调用模块方法：

```php
...
$modules['MODULE_NAME']->FUNCTION_NAME();
...
```
例如 `./controller/index.class.php` 中 `module` 方法：
```php
...
/**
 * 调用模块
 * @url(GET, '/module')
 */
public function module ($modules) {
    $msg = $modules['verify']->getMsg();
    Boostrap::output($msg); // "Hello Verify"
}
...
```