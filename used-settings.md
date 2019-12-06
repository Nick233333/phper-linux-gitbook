#### ssh 公私钥登录配置

第一步，在客户端生成公钥
```
ssh-keygen -t rsa #生成的公钥匙在 ~/.ssh/ 目录下
```
第二步，把公钥上传到服务器端，登录服务器追加公钥到 authorized_keys 文件

__简单版__

```
ssh-copy-id -i ~/.ssh/id_rsa.pub username@ip
```

__复杂版__

```
scp id_rsa.pub root@ip地址:文件保存路径
ssh root@ip #登录服务器
cd id_rsa.pub 文件保存路径
cat id_rsa.pub >> /root/.ssh/authorized_keys 追加到文件中

```
> 如果 .shh 目录或 authorized_keys 文件不存在需要自己新建



第三步，修改服务器端 ssh 配置文件 /etc/ssh/sshd_config

```
RSAAuthentication yes #开启RSA验证
PubkeyAuthentication yes #是否使用公钥验证
PasswordAuthentication no #禁止使用密码验证登录
chmod 700 /root/.ssh/     #为了安全把文件修改权限，可选，部分系统新建即为 700
chmod 600 /root/.ssh/authorized_keys  #为了安全把文件修改权限，可选，部分系统新建即为 600
```

第四步，服务器端重启 ssh 服务
```
service sshd restart #重启 sshd 服务
```

---

#### ssh 连接超时配置

把 `/etc/ssh/sshd_config` 文件中 `ClientAliveInterval` 、`ClientAliveCountMax` 两个配置修改为

```
ClientAliveInterval 60 #服务端向客户端发送信息的间隔时间，单位为秒
ClientAliveCountMax 3  #服务端发送信息的总次数
```

`CentOs` 直接修改即可，`Ubuntu` 默认没有需要新增。

重启服务

```
systemctl restart sshd
```

---

#### 禁止 ping 服务器配置

第一种方法：临时生效配置
```
sudo sysctl -w net.ipv4.icmp_echo_ignore_all=1 #临时生效禁止 ping 作用，重启服务器后恢复

sudo sysctl -w net.ipv4.icmp_echo_ignore_all=0 #解除禁止 ping 作用
```

第二种方法：永久生效配置

编辑 /etc/sysctl.conf 文件
```
sudo vim /etc/sysctl.conf 
```
在配置文件中添加 
```
net.ipv4.icmp_echo_ignore_all=1 
``` 
如果已经有 `net.ipv4.icmp_echo_ignore_all` 这一行了，直接修改=号后面的值即可的。（0表示允许，1表示禁止）
修改完成后执行 `sysctl -p` 使新配置生效

第三种方法：通过 iptables 配置
```
sudo iptables -A INPUT -p icmp --icmp-type 8 -s 0/0 -j DROP #往防火墙添加规则

删除已添加的iptables规则
sudoi ptables -L -n --line-numbers #将所有iptables以序号标记显示

sudo iptables -D INPUT 8 #删除INPUT里序号为8的规则
```

---

#### 自定义 ssh 登录

在 `.ssh` 目录下新建 `config` 文件，内容如下

```
Host test1           #自定义名称
HostName ip          #服务器 ip 地址
User nick            #用户名
Port 22              # ssh 端口号，默认 22 可以不设置

Host test2           #自定义名称
HostName ip          #服务器 ip 地址
User nick            #用户名
Port 22228           # ssh 端口，自定义端口，修改为指定端口号
IdentityFile /your/path/ # 密钥文件地址，要绝对路径
```

连接方式

```
ssh test1 #如果配置了公私钥就直接登录，没有的话输入密码登录
```

---

#### 修改主机名

临时生效，重启服务器会还原

```
hostname ubuntu-1604
```

永久生效

1. 修改 `/etc/hostname` 文件中的名称
2. 修改 `/etc/hosts` 文件中的旧名称，或者新添加一条 `127.0.0.1 ubuntu-1604`

> 适用于 `Ubuntu 16.04` 和 `CentOS 7` 以上版本




