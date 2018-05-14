#### apt-get Ubuntu 系统软件包管理器

`apt-get` 命令是 `Debian Linux` 发行版中的 `APT` 软件包管理工具。所有基于 `Debian` 的发行都使用这个包管理系统。

```
apt-get install xxx #安装软件

apt-get remove xxx ##删除软件

apt-get purge xxx #删除软件并删除配置文件

apt-get autoremove xxx #自动删除未使用的软件

apt-get update #检查软件并升级

apt-get upgrade #升级软件

apt-get clean #清理所有软件缓存

apt-get autoclean #清理旧版本的软件缓存
```

补充：部分系统需要具有 `root` 权限的普通用户才能执行，在命令前加 `sudo` 即可。

#### yum CentOS 系统软件包管理器

`yum` 命令是在 `Fedora` 和 `Red Hat` 以及 `SUSE` 中基于 `rpm` 的软件包管理器，它可以使系统管理人员交互和自动化地更细与管理RPM软件包，能够从指定的服务器自动下载 `RPM` 包并且安装，可以自动处理依赖性关系，并且一次安装所有依赖的软体包，无须繁琐地一次次下载、安装。

```
yum install xxx #安装软件

yum erase xxx #删除软件

yum info xxx #查看软件信息

yum list #列出软件列表

yum reinstall xxx #重新安装软件

yum search xxx #搜索软件

yum update #升级所有软件
```

补充：部分系统需要具有 `root` 权限的普通用户才能执行，在命令前加 `sudo` 即可。