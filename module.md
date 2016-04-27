# 模块系统

Razord 设计了一套模块系统，使得你可以轻易的引入或开发一套模块。

#### 基本语法

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

#### 调用

既然是模块，载入了 Razord 中肯定要能调用，在控制器的方法中，我们强调要添加 `$module` 参数（）