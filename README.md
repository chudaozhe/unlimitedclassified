# 树形菜单
外部使用
```
composer require chudaozhe/unlimitedclassified
```

在任一 laravel 项目中新建 `[目录]/[用户名]/[包名]` 目录，形如 `packages/chudaozhe/unlimitedclassified`
进入`packages/chudaozhe/unlimitedclassified` 目录，执行 `composer init` 初始化，该怎么填就怎么填。

## 本地调试
### 修改 config/app.php
```
    'providers' => ServiceProvider::defaultProviders()->merge([
        \Chudaozhe\UnlimitedClassified\UnlimitedClassifiedServiceProvider::class,
    ])->toArray(),
```

### 修改 composer.json
composer.json
```
    "autoload": {
        "psr-4": {
            ...
            "Chudaozhe\\UnlimitedClassified\\": "packages/chudaozhe/unlimitedclassified/src/"
        }
    },
```
修改完之后执行
```
composer dump-autoload
```
### 任一控制器中调用
```
$data = [
    ['id'=>1,'pid'=>0,'name'=>1],
    ['id'=>2,'pid'=>0,'name'=>2],
    ['id'=>3,'pid'=>1,'name'=>3],
    ['id'=>4,'pid'=>2,'name'=>4],
    ['id'=>5,'pid'=>3,'name'=>5],
    ['id'=>6,'pid'=>4,'name'=>6],
    ['id'=>7,'pid'=>5,'name'=>7],
    ['id'=>8,'pid'=>6,'name'=>8],
];

return (new \Chudaozhe\UnlimitedClassified\UnlimitedClassified)->getUnlimitedClassified($data, 'pid','child');

//门面
return UnlimitedClassified::getUnlimitedClassified($data, 'pid','child');
//服务容器
return app('unlimited_classified')->getUnlimitedClassified($data, 'pid','child');
```
