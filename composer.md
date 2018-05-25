#### Composer php 软件包依赖管理器

```
composer list #显示所有命令

composer show #显示所有包信息

composer install #在 composer.json 配置中添加依赖库之后运行此命令安装

composer create-project laravel/laravel Laravel --prefer-dist 5.1.* #创建项目

composer search packagename #搜索包

composer update #更新所有包

composer update monolog/monolog #更新指定包

composer remove monolog/monolog #移除指定的包

composer require monolog/monolog #添加指定包

composer require monolog/monolog:1.19 #添加指定包和版本

composer require monolog/monolog=1.19 #添加指定包和版本

composer require monolog/monolog 1.19 #添加指定包和版本

composer dump-autoload #如果更新了composer.json需要更新autoload
```