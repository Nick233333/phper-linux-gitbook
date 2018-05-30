#### stty 命令

```
stty -echo #禁止将输入信息显示在终端

stty echo  #允许输入信息显示在终端，默认显示
```

#### tput 命令

```
tput clear #清空终端

tput civis #光标不可见  
  
tput cnorm #光标可见
```

#### read 命令

```
read name #读取终端输入的值并赋值给 name 变量

echo $name #输出变量值

read username age #读取终端输入的 2 个值，并赋值

echo $username $age #输出值

read -s passwdord #读取输入的信息赋值给 password 变量，输入的信息不显示在终端

read -p "Enter input:" var #设置输入时显示提示语

read -sp "Enter input:" var #设置输入时显示提示语，输入信息不显示在终端

read -t 10 name #设置指定时间内输入，超时主动退出
```

#### export 命令

```

```

#### typeset 命令

```

```

#### declare 命令

```

```

#### set 命令

```

```

#### unset 命令

```
unset name #删除普通变量

unset -v test #删除环境变量

unset -f fun1 #删除函数
```

#### sh 命令

```
sh xx.sh #执行脚本

sh -n xxx.sh #检查语法

sh -i xxx.sh #交互式运行脚本

sh -x xxx.sh #显示脚本执行的顺序
```

#### xargs 命令

```
cat demo.sh | xargs #将内容转成单行显示

cat demo.sh | xargs -n 3 #将内容转成多行显示，每行 3 列

echo "splitXsplitXsplitXsplit" | xargs -d X #指定 X 符号作为分隔符

echo "splitXsplitXsplitXsplit" | xargs -d X -n 2 #指定 X 符号作为分隔符，每行 2 列

cecho.sh 文件内容
#!/bin/bash 
echo $*'#'

cat args.txt | xargs -I {} ./cecho.sh -p {} -l #使用 -I 的时候，命令以循环的方式执行。如果有 3 个参数，那么命令就会连 同 {} 一起被执行 3 次。在每一次执行中 {} 都会被替换为相应的参数 
```

#### tr 命令

```
echo "HELLO WHO IS THIS" | tr 'A-Z' 'a-z' #将大写字母转换成小写

echo "Hello " | tr -d 'H' #删除指定内容
```
