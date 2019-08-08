# 路由参数

如果你定义的路由在URL中有可变的参数,那么在路由中定义他们并传递给闭包是非常简单的\(参见示例3-5\)

{% code-tabs %}
{% code-tabs-item title="Example 3-5. Route parameters" %}
```php
Route::get('users/{id}/friends',function ($id) {
    return $id;
});
```
{% endcode-tabs-item %}
{% endcode-tabs %}

你可以在路由参数后面添加"?"使得该参数变成可选参数,如示例3-6,在这种情况下还应该为路由对应的变量提供默认值.

{% code-tabs %}
{% code-tabs-item title="Example 3-6. Optional route parameters" %}
```php
Route::get('users/{id?}',function ($id='fallbackId') {
    return $id;
});
```
{% endcode-tabs-item %}
{% endcode-tabs %}

而且，您可以使用正则表达式（regex）来定义路由只在在参数满足特定要求时匹配，如示例3-7所示。

{% code-tabs %}
{% code-tabs-item title="Example 3-7. Regular expression route constraints" %}
```php
Route::get('users/{id}',function ($id) {
    return $id;
})->where('id','[0-9]+');

Route::get('users/{username}',function ($username) {
    return $username;
})->where('username','[A-Za-z]+');

Route::get('posts/{id}/{slug}',function ($id,$slug) {
    return $id.$slug;
})->where(['id'=>'[0-9]+','slug'=>'[A-Za-z]+']);
```
{% endcode-tabs-item %}
{% endcode-tabs %}

你可能已经猜到了，如果您访问的路径与路由字符串匹配，但regex与参数不匹配，则不会匹配。由于路由是从上到下匹配的，users/abc将跳过示例3-7中的第一个闭包，但它将与第二个闭包匹配，因此它将被路由到那里。另一方面，posts/abc/123与任何闭包都不匹配，因此它将返回404（未找到）错误。
