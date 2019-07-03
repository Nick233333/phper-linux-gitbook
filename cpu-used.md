## 什么是 CPU 使用率

CPU 使用率是单位时间内 CPU 使用情况的统计，以百分比的方式展示，我们通常所说的 CPU 使用率，就是除了空闲时间外的其他时间占总 CPU 时间的百分比

## 怎么查看 CPU 使用率

top 和 ps 是最常用的性能分析工具:top 显示了系统总体的 CPU 和内存使用情况，以及各个进程的资源使用情况。ps 则只显示了每个进程的资源使用情况。

top 默认每 3 秒刷新一次，输出格式为:

```
top - 21:12:50 up 21 days, 23:13,  2 users,  load average: 0.05, 0.04, 0.01
Tasks: 125 total,   2 running, 123 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.7 us,  0.3 sy,  0.0 ni, 99.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  4042140 total,  1991136 free,   140000 used,  1911004 buff/cache
KiB Swap:        0 total,        0 free,        0 used.  3576656 avail Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 1011 ubuntu    20   0   40492   3696   3152 R   0.3  0.1   0:00.02 top
    1 root      20   0  119960   6116   4020 S   0.0  0.2   2:38.76 systemd
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd
    3 root      20   0       0      0      0 S   0.0  0.0   0:25.69 ksoftirqd/0
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H
    7 root      20   0       0      0      0 S   0.0  0.0   3:57.57 rcu_sched
    8 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh
    9 root      rt   0       0      0      0 S   0.0  0.0   0:10.86 migration/0
   10 root      rt   0       0      0      0 S   0.0  0.0   0:06.89 watchdog/0
   11 root      rt   0       0      0      0 S   0.0  0.0   0:05.72 watchdog/1
   12 root      rt   0       0      0      0 S   0.0  0.0   0:12.66 migration/1
```

输出结果中，第三行 %Cpu 就是系统的 CPU 使用率，只是把 CPU 时间变换成了 CPU 使用率，不过需要注意，top 默认显示的是所有 CPU 的平均值，这个时候你只需要按下数字 1 ，就可以切换到每个 CPU 的使用率了。

空白行之后是进程的实时信息，每个进程都有一个 %CPU 列，表示进程的 CPU 使用率。它是用户态和内核态 CPU 使用率的总和，包括进程用户空间使用的 CPU、通过系统调用执行的内核空间 CPU 、以及在就绪队列等待运行的 CPU。在虚拟化环境中，它还包括了运行虚拟机占用的 CPU。

top 并没有细分进程的用户态 CPU 和内核态 CPU，需要查看每个进程的详细情况，可以用 pidstat ，它正是一个专门分析每个进程 CPU 使用情况的工具。


下面的 pidstat 命令，就间隔 1 秒展示了进程的 5 组 CPU 使用率，包括:

- 用户态 CPU 使用率 (%usr)

- 内核态 CPU 使用率(%system)

- 运行虚拟机 CPU 使用率(%guest)

- 等待 CPU 使用率(%wait)

- 以及总的 CPU 使用率(%CPU)

最后的 Average 部分，还计算了 5 组数据的平均值。

```
pidstat 1 5 #每隔 1 秒输出一组数据，共输出 5 组
```

```
Linux 4.4.0-142-generic (10-53-166-171) 	07/03/2019 	_x86_64_	(2 CPU)

09:22:18 PM   UID       PID    %usr %system  %guest    %CPU   CPU  Command

09:22:19 PM   UID       PID    %usr %system  %guest    %CPU   CPU  Command
09:22:20 PM  1000      2093    0.00    1.00    0.00    1.00     1  pidstat
09:22:20 PM   113      4606    1.00    0.00    0.00    1.00     0  beam.smp

09:22:20 PM   UID       PID    %usr %system  %guest    %CPU   CPU  Command
09:22:21 PM   113      4606    0.00    1.00    0.00    1.00     0  beam.smp

09:22:21 PM   UID       PID    %usr %system  %guest    %CPU   CPU  Command
09:22:22 PM  1000      2093    0.00    1.00    0.00    1.00     1  pidstat

09:22:22 PM   UID       PID    %usr %system  %guest    %CPU   CPU  Command

Average:      UID       PID    %usr %system  %guest    %CPU   CPU  Command
Average:     1000      2093    0.00    0.40    0.00    0.40     -  pidstat
Average:      113      4606    0.20    0.20    0.00    0.40     -  beam.smp
```

## CPU 使用率过高怎么办

通过 top、ps、pidstat 等工具，你能够轻松找到 CPU 使用率较高(比如 100% )的进程，如果需要排查占用 CPU 的到底是代码里的哪个函数，推荐使用 perf。perf 是 Linux 2.6.31 以后内置的性能分析工具。它以性能事件采样为基础，不仅可以分析系统的各种事件和内核性能，还可以用来分析指定应用程序的性能问题。

perf 分析 CPU 性能问题，两种最常见用法

__第一种__

perf top，类似于 top，它能够实时显示占用 CPU 时钟最多的函数或 者指令，因此可以用来查找热点函数，使用界面如下所示:

```
sudo perf top
```

```
Samples: 674  of event 'cpu-clock', Event count (approx.): 149937500
Overhead  Shared Object            Symbol
   9.48%  [kernel]                 [k] vsnprintf
   8.02%  [kernel]                 [k] kallsyms_expand_symbol.constprop.1
   6.27%  [kernel]                 [k] format_decode
   3.79%  [kernel]                 [k] number.isra.14
   3.50%  [kernel]                 [k] memcpy_erms
   2.33%  perf                     [.] 0x000000000008c4d6
   2.04%  [kernel]                 [k] apparmor_capable
   2.04%  [kernel]                 [k] pointer.isra.22
   1.92%  [kernel]                 [k] clear_page_c_e
   1.90%  [kernel]                 [k] string.isra.4
   1.75%  perf                     [.] 0x000000000008e314
   1.60%  libc-2.23.so             [.] getdelim
   1.60%  perf                     [.] 0x0000000000082067
   1.46%  [kernel]                 [k] strnlen
   1.46%  perf                     [.] 0x000000000008e326
```

输出结果中，第一行包含三个数据，分别是采样数(Samples)、事件类型(event)和事件总数量(Event count)。比如这个例子中，perf 总共采集了 674 个 CPU 时间事件，而总事件数则为 149937500

另外，采样数需要我们特别注意。如果采样数过少(比如只有十几个)，那下面的排序和 百分比就没什么实际参考价值了。

再往下看是一个表格式样的数据，每一行包含四列，分别是:

- 第一列 Overhead ，是该符号的性能事件在所有采样中的比例，用百分比来表示。

- 第二列 Shared     ，是该函数或指令所在的动态共享对象(Dynamic Shared Object)，如内核、进程名、动态链接库名、内核模块名等。

- 第三列 Object ，是动态共享对象的类型。比如 [.] 表示用户空间的可执行程序、或者动态链接库，而 [k] 则表示内核空间。

- 最后一列 Symbol 是符号名，也就是函数名。当函数名未知时，用十六进制的地址来表示。

__第二种__

就是 perf record 和 perf report。 perf top 虽然实时展示了系统的性能信息，但它的缺点是并不保存数据，也就无法用于离线或者后续的分析。 而 perf record 则提供了保存数据的功能，保存后的数据，需要你用 perf report 解析展示。

```
sudo perf record -a #按 Ctrl+C 终止采样

sudo perf report #展示类似于 perf top 的报告

sudo perf top -g -p 21515 # -g 开启调用关系分析，-p 指定 php-fpm 的进程号 21515
```

在实际使用中，我们还经常为 perf top 和 perf record 加上 -g 参数，开启调用关系的采样，方便我们根据调用链来分析性能问题。