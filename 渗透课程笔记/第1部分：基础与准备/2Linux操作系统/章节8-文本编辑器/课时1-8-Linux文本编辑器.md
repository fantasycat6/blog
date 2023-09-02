---
title: 课时1-8-Linux文本编辑器
url: https://www.yuque.com/u29002979/ep2zrx/fdngr26334cckpx7_xol247
---

<a name="zxQ38"></a>

## 文本编辑器

Windows: Notepad (记事本)、Sublime、 UltraEdit等
Linux: VI/VIM、 nano、Emacs、Sed、 gedit、 Kate等

<a name="mxYbZ"></a>

# 课程大纲

1. VI和VIM的区别
2. VIM配置文件
3. VIM三种模式的关系
4. 命令模式
5. 编辑模式
6. 底行模式 <a name="iXRZA"></a>

# VI和VIM的区别

- VI: Visual Interface
- 1976 Bill Joy(ex)
- 1991 Bram Moolenaar
- Vim: VI IMproved

vim语法高亮 <a name="jQX1Q"></a>

# VIM配置文件

全局配置: `/etc/vimrc`
用户配置: ~/.vimrc
详细配置参考:
<https://blog.csdn.net/xiao_yi_xiao/article/details/118491698> <a name="XKNi5"></a>

# VIM三种模式切换

![image.png](../../../../assets/fdngr26334cckpx7_xol247/1668312690746-f16ae486-e981-4adb-8222-e1fb420613bb.png) <a name="kiyGK"></a>

## 命令模式

<a name="ik7BW"></a>

### 打开文件

VIM 文件名
vim /etc/sysconfig/network-scripts/ifcfg-ens33
vim redis.conf

错误提示:
E325: ATTENTION
Found a swap file by the name ".redis.conf.swp"
原因:编辑未结束
解决办法:保存文本文件，或者删除.swp <a name="h9qjT"></a>

### 移动光标操作

|  操作 | 按键  |
| --- | --- |
| 移动光标 | 方向键↑ ↓ ← → |
| 跳到行首 | HOME |
| 跳到行尾 | END |
| 向后前进多少行 | n数字 |
| 退出前进一屏(Forward)  | Ctrl+F |
| 后退一屏(Backspace) | Ctrl+B |
| 跳到文档末尾 | Shift+G  /  G  |
| 跳到文档开头 | :1 / gg |

显示文件行号：set number

<a name="xoeKW"></a>

### 搜索替换操作

|  操作 | 按键  |
| --- | --- |
| 向后查找内容 | /关键字，回车 |
| 向前查找内容 | ?关键字，回车 |
| n | 下一个关键字 |
| N | 上一个关键字 |

<a name="QEfuB"></a>

### 删除和复制操作

|  操作 | 按键  |
| --- | --- |
| 复制光标所在行 | yy |
| 粘贴到下一行/上一行 | p / P |
| 删除光标前面一个字符 | X |
| 删除光标后面1个字符 | Del/x |
| 删除一行 | dd |
| 删除光标下面n行 | ndd |
| 重复上一次的操作 | . |
| 撤消最近一次操作 | u |
| 恢复最近一次操作 | Ctrl+ R |

<a name="gY4bR"></a>

## 编辑模式

<a name="AejkP"></a>

### 进入编辑模式

a:在光标下一个字符之前插入文本
A:在光标所在的航模插入文本
i: 在光标上一个字符之前插入文本
l:在光标的行首插入文本
o:在光标所在的行下插入- -行文本
O:在光标所在的行上插入- -行文本
r:修改当前光标所在的字符
R:替换文本

<a name="aUHiP"></a>

### 撤消

编辑模式下: Ctrl+U 撤消
退出编辑模式: Esc

<a name="I2lvO"></a>

## 进入底行模式

Shift + :
`:w`保存
`:q`退出
`:wq`保存并且保存
`:q!`放弃修改，退出
:e!放弃所有更改，重新编辑(不关闭

显示行号:   ` :set nu`
:%s/word1/word2/g 把文档中的word1替换为word2
