# 添加新守卫

你可以在config/auth.php随时添加新守卫，在auth.guards设置中：

```php
'guards' => [
    'trainees' => [
        'driver' => 'session',
        'provider' => 'trainees',
    ],
],
```

这里我们创建了一个名为trainees的新守卫，让我们想象一下，我们在本节的剩余部分我们正在构建一个应用程序，我们的用户是物理培训师，他们有自己的学员，它们可以登录到自己的子域名，所以我们需要一个单独的守卫。

驱动的两个选项是token和session。提供者唯一选项是用户，它针对默认用户表提供认证，但是你也可以轻松的创建自己的提供者。


