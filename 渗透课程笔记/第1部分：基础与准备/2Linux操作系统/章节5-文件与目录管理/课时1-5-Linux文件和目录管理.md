---
title: 课时1-5-Linux文件和目录管理
url: https://www.yuque.com/u29002979/ep2zrx/pq7p6grty9e85fou_st4z6a
---

<a name="bVqdZ"></a>

# 课程大纲

1. 列出目录
2. 打印工作路径
3. 切换工作路径
4. 查看文件类型
5. 复制文件或目录
6. 查找文件或者目录
7. 创建目录
8. 移动或者重命名
9. 删除文件或目录
10. 创建空文件
11. 软链接和硬链接
12. 挂载

<a name="zDUTW"></a>

# 常规命令格式

Command   Options   Arguments
命令               选项           参数

> rm -rf /*
> \-r递归
> \-f强制

Options选项:命令的行为方式
Arguments参数:命令的对象 <a name="ndgS6"></a>

## Linux怎么删库跑路?

打开系统Terminal(终端)输入:

|      sudo        |   rm  |  -rf   |  /* |
| --- | --- | --- | --- |
| 以系统管理员的身份执行       | ReMove   移除    | 递归，强制  | 目最下所有文件 |

以系统管理者的身份移除Rubbish Flies目录下的所有文件\ <a name="ggfpV"></a>

## 规范

- 命令
- 空格
- 大小写
- 顺序 <a name="I1oJq"></a>

## 命令选项详细参考资料

<https://wangchujiang.com/linux-command>
[https://www.linuxcool.com](https://www.linuxcool.com.com)

<a name="FX22Q"></a>

# 文件和目录管理

<a name="er8g0"></a>

## 列出目录内容和属性

命令: Is
全拼: list
格式: Is 选项 文件名
例:
ls -a
lI --block-size=M

<a name="jam3z"></a>

## 打印工作路径

命令. pwd
全拼: print working directory
格式: pwd

<a name="x8JMT"></a>

## 切换工作目录

命令: cd
全拼: change directory
格式: cd相对路径或者绝对路径

|  符号 |  指代 |
| --- | --- |
| 绝对路径 | 由根目录 / 开始写起 |
| 相对路径 | 从当前所在的工作目录开始写起 |
| `/` | 根目录 |
| `.` | 代表当前目录 |
| `~` | 代表用户工作目录，vim ~/.bashrc |
| `../` | 代表上一-级目录 |
| `../../` | 上上一级目录，以此类推，超出范围的时候代表根目录 |

<a name="Mw8R1"></a>

## 查看文件类型

命令: file
格式: file 选项 文件或目录
file -i 文件名 <a name="yfnq6"></a>

## 复制文件或目录

命令: cp
全拼: copy
格式: cp 选项源文件 目标文件

\-R/r:递归处理，将指定目录下的所有文件与子目录一并处理;
\-f: 强行复制文件或目录，不论目标文件或目录是否已存在;

<a name="UunOw"></a>

## 查找文件或者目录

find
格式: find 目录 选项 名字或模式

\-name 名字
find /etc -name a*
find / -name "aaa" 2> /dev/null

\-type类型参数
f 普通文件, d目录
find /root -type f

\-size大小
find /root -type f -size 10M

\-exec command
把find找到的内容作为命令的参数去执行
{}就是找到的内容
find . -name "*.txt" -exec rm -rf{} ; (包括子目录)
find . -name aaa -exec mv {} bbb ;

<a name="tGqdL"></a>

### 其他查找命令

whereis :查找二进制程序、代码等相关文件路径
which:查找并显示给定命令的绝对路径
locate: updatedb程序每天会跑一次，建立文件索引 <a name="OUltD"></a>

## 创建目录

命令:mkdir
全拼: make direcotry
格式: mkdir选项目录名
mkdir test
mkdir -p /usr/local/soft/redis

\-p 创建多级目录

<a name="Ys95f"></a>

## 移动或者重命名

命令: mv
全拼: move
格式: mv选项 原文件 新文件
mv 1.txt 2.txt
mv /a/1.txt /b/1.txt <a name="kS2an"></a>

## 删除文件

命令: rm
全拼: remove
格式: rm 选项(多个)文件名
删除空目录: rmdir
\-r 递归(连同子文件夹一起删除)
\-f 强制删除
find . -name "a.json" -exec rm -rf {}

<a name="QTFeJ"></a>

## 创建空文件

命令: touch
格式: touch 选项 文件名
touch a.txt <a name="kbti7"></a>

## 挂载mount

问题: -个目录树怎么使用多个磁盘?
原路径: /dev/sdb1 挂载到: /sdb-u
mkdir /sdb-u
mount /dev/sdb1 /sdb-u

<a name="UKbhI"></a>

## 链接

命令: In
全拼: link
格式: In 源文件 链接文件 <a name="bAeQW"></a>

### 创建硬链接:

In 1.php hard.php
vim hard.php
cat 1.php
注意:
1、用户不能给目录创建硬链接
2、只有相同的文件系统才可以创建硬链接(tmpfs NTFS FAT32) <a name="WS95b"></a>

### 软链接

查看软链接:
II /usr/bin/nc
创建软链接:&#x20;
In -s /usr/local/phpstudy/system/phpstudyctl /usr/bin/study
使用:
study

源文件删除，软连接失效
