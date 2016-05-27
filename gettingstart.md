# 安装

使用 git 从 github 上 `clone` 下项目的源码到 web 开发目录

```bash
git clone git@github.com:jas0ncn/razordphp.git
```

访问 http://localhost/你的目录 即可首次运行。

看到 `"Hello World"` 即运行成功！

### index.php

```php
<?php
/**
 * Razord PHP
 * @author     Jason
 * @copyright  Copyright (c) 2015 razord.ijason.cc
 * @license    http://opensource.org/licenses/MIT	MIT License
 */

/* 加载主文件 */
require('./config.php');
require('./core/init.php');

/* 实例化应用 */
$Razord = new Boostrap;

/* 加载模块 */
$moduleNames = array('verify'); // 要加载的模块名称的数组
$Razord->load($moduleNames);

/* 启动框架 */
$Razord->start();
?>
```
之后将会详细介绍 RazordPHP 的 API。
