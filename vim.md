#### Vim 编辑器

`vim` 是 `vi` 的升级版，被誉为编辑器之神。

`vim` 分四种模式： __普通模式__ ，__插入模式__ ，__命令模式__ __可视化模式__，。

普通模式：默认打开文件就是普通模式。
插入模式：按下 `i` 、 `I` 、 `a` 、 `A` 、 `o` 、 `O` 键进入插入模式。
命令行模式：按下 `:` 键会进入命令行模式。
可视化模式：按下 `v` 、`V` 、`Ctrl + v` 进入可视化模式。

__一般模式常用操作：__
```
x（小写）删除光标所在位置的下一个字符
X（大写）删除光标所在位置的前一个字符
i 光标所在位置后插入
I 行首添加
a 光标所在位置添加
A 行尾添加
o （小写）下一行添加
O (大写)上一行添加
dd 删除光标所在行
5dd 删除光标所在下5行
dG 删除全部
u 撤销
ctrl r 反撤销
yy 复制行
5yy 复制5行
ggyG 复制全部
p （小写）光标下一行粘贴
P (大写)光标上一行粘贴
gg 光标跳转到第一行
G 光标跳转到最后
0 光标跳转当前行第 1 列，下标从 0 开始
12 l 光标跳转到第 11 列
v #操作方向键，移动光标选中字符
V #操作方向键，移动光标选中行
```

__命令模式常用操作：__
```
q 退出
！ 强制
q！ 强制退出
w 保存
wq 保存退出
wq！ 强制保存退出
set nu 显示行号
set nonu 隐藏行号
8 跳转到指定行
$ 跳转文件尾
open path/filename 打开其他文件编辑
？关键字 向下搜索
/关键字 向上搜索
set hlsearch #设置搜索高亮
set nohlsearch #取消搜索高亮
set cul #光标高亮当前行
set nocul #光标取消高亮当前行
set cuc #光标高亮当前列
set nocuc #光标取消高亮当前列
```

__个人 Vim 配置__

配置文件位于 `~/.vimrc`

```
filetype on #识别文件类型
syntax on #高亮语法
set tabstop=4 #tab缩进转为 4 个空格
set expandtab #tab转空格
set softtabstop=4 #tab 转为 4 个空格。
set incsearch #搜索跳转到第一个匹配的值
set ignorecase #搜索不区分大小写
set autoread #当有其他人修改文件自动读取
set autoindent #自动缩进
set showmode #底部显示当前模式
set showcmd #在底部显示命令
set paste #粘贴时保持缩进格式
```

修改完退出终端重新打开或者执行 `source ~/.vimrc` , 如有报错无需理会，报错原因是 `shel` 无法识别 `vim` 的配置。

