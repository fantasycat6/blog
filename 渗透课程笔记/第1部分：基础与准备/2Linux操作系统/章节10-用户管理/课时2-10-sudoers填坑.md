---
title: 课时2-10-sudoers填坑
url: https://www.yuque.com/u29002979/ep2zrx/eanqok869l6q1ctn_nqngxk
---

<a name="vOgWo"></a>

# /etc/sudoers

格式:
wuya ALL=(ALL) ALL
kali ALL=(ALL) NOPASSWD: /bin/useradd

全拼: super user do
`sudo -l`
`sudo` command (要执行的命令) <a name="LPyxE"></a>

### 解决没有编辑sudoers权限

使用`visudo`编辑权限
