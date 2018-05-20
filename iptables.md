#### iptables 命令

- 防火墙分为__硬件防火墙__和__软件防火墙__

- 防火墙策略一般分为两种：__开放__和__屏蔽__

- iptables 是 `Linux` 上常用的__防火墙软件__

- iptables 一共有__四张表__和__五条链__

```
iptables （选项）[表名] （选项）[链名规则] （选项）[动作]
```

__表：__ 

- Raw 负责连接跟踪
- Mangle 负责包处理
- Nat 负责地址转换
- Filter 负责包过滤

__链名规则：__ 

- PREROUTING 数据包作路由选择之前
- INPUT 接收数据包
- FORWARD 在内核空间中，从一个网络接口进入，到另一个网络接口去。转发过滤
- OUTPUT 输出数据包
- POSTROUTING 数据包作路由选择之后

__动作：__

- accept：接收数据包。
- DROP：丢弃数据包。
- REDIRECT：重定向、映射、透明代理。
- SNAT：源地址转换。
- DNAT：目标地址转换。
- MASQUERADE：IP伪装（NAT），用于ADSL。
- LOG：日志记录。

__例子__

```
iptables -I INPUT -s ip -j DROP   #屏蔽指定 ip 访问

iptables -A INPUT -p tcp --dport 2222 -j ACCEPT    #允许 2222 端口访问

iptables -A INPUT -p icmp --icmp-type 8 -s 0/0 -j DROP #屏蔽 icmp 协议，即关闭 ping 服务

iptables -L -n --line-numbers #查看已添加的规则并以序号显示

iptables -D INPUT 8 #删除序号为 8 的规则
```

补充：`-A` 代表追加，`-I` 代表插入，`-D` 代表删掉，`-R` 代表替换，`-L` 代表列表，`-p` 代表协议，` -s` 代表源地址，必须是 IP ，`-j` 代表动作，`-d` 代表目标地址，`-i` 网卡进入是数据，`-o` 代表网卡输出的数据。