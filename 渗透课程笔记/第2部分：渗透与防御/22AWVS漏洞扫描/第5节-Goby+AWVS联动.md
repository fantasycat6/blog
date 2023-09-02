# 第五节-Goby+AWVS 联动

## 1.Goby简介

Goby是针对目标企业梳理最全面的工具，同构goby可以清晰的扫描出ip地址开放的端口，以及端口对应的服务，于此同事会根据开放的端口及应用进行实战化的测试，并不在乎他的中低危害漏洞，而更在乎的是它能直接getshell的漏洞。

AWVS这款工具大家应该都比较熟悉了，他是针对web的轻量级的漏洞扫描工具。也就是根据我们提供的被扫描地址，快速的扫描出其所有的漏洞，包含高中低及信息泄露等漏洞。

结合我们前面的介绍，大家想想，Goby探测出ip地址开放的所有服务及应用，然后直接丢给AWVS，那么AWVS是不是就可以直接进行扫描了，然后存在的网站存在的漏扫是不是一幕了然了，还需要我们去手动挖么，很显然了啊，这俩工具一联动，躺着收洞洞呗。

Goby 错误异常汇总

https://cn.gobies.org/faq.html

## 2.Goby安装

1.在附件中下载 goby-win-x64-1.9.320.zip

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/cae347217f2e4edb8f49885f9c31a6f2.png)

2.解压到喜欢的位置

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/b25b706b644b4b54a1c5444d7773c6ff.png)

3.解压目录找到Goby.exe 右键--管理员运行

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/7c563477fdff4c5a92a428fa38faba5f.png)

4.点击【是】

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/1c17dae4b2724ad9a4609c8209c568b0.png)

5.点击【More】如图所示，点击【EN】，点击【CN】

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/d1622b88bc2e43fd94bd7d394c2e6ba9.png)

6.点击【扩展程序】，搜索【AWVS】，点击【下载】

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/94e1952d4b714acd8b24bdc3b4c50976.png)

7.点击【已下载】

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/39fed8e90aeb463b8e99cbb721c626b0.png)

8.点击【设置】

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/6faa54cf76814488b5cc2e8c83b41efb.png)

9.切换到【AWVS】，点击【用户】，点击【Profile】

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/fa740fd2d32c46b5ad8cdd850deefa46.png)

10.找到【API Key】，点击【Generate New Api Key】

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/23a868079ed34c498768f5d1bfa4a755.png)

11.点击【Show】

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/3873ed2d97d04a4a8e8b8f85150c9e5d.png)

12.点击【copy】

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/f8ea9c32faf2473b90555bca447f6a83.png)

13.切换【Goby】，粘贴【API Key】和输入【AVWS WEB ADDress】，点击【Confirm】

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/8545ca84026847929bd53a6285f97edf.png)

14.点击【设置】，点击【扩展设置】，点击【确认】

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/701dd8ccce124f31979a9b6600a5e74a.png)

## 3.安装npcap-0.9995.exe

1.右键点击附件里的【npcap-0.9995.exe】，选则【以管理员身份运行】

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/f96ab014dfcd46d4a650b11b35f8f336.png)

2.点击【是】

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/d41404e228f64985a88963772328a880.png)

3.点击【I Agree】

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/3f7a7549f8cf4dab8d7bdd02685d2388.png)

4.点击【Install】

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/27389ce180dc455c9664b7ba65497d98.png)

5.点击【确定】

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/36733835588743a9a6f48f1c8995d86f.png)

6.点击【Next】

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/fa9e44c0f7ea43f580eaa960ffd22238.png)

7.点击【Finish】

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/7fd9171e27a24a3db7b5f7ae0dd12f1b.png)

## 4.Goby+AWVS联动扫描

1.点击【扫描】

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/e745ef82f410486a8c29fb843f2461df.png)

2.输入ip进行扫描,点击【开始】

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/3fbba4b002b34c17b9cef3f28df2199c.png)

3.等待扫描结果

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/d82b2aa35ea04f55bd3657510b9b4ee9.png)

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/a1555b1037414aa89d64974f5de7aa2d.png)

4.点击【Web检测】

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/0d6585029108492b92257c9fa108cba2.png)

5.点击【awvs】扫描

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/cf99391ca82e4b0db9569ca2ff4e6585.png)

6.切换到【AWVS】，点击【Scans】，点击【Goby传过来的任务】

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/8ce4d62b7ce141fdbf18e01a3150afe2.png)

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/1f1055af4d6848338edfd6a5dd4b7de1.png)

7.切回到【Goby】，点击【扩展程序】,点击【awvs】

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/f3d160eed543449cafc8a417c8d6f85d.png)

8.选择报告模板，点击【Generate】,生成报告

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/05d00d10c2bc4de8b8d857f993d32588.png)

9.点击【Export】可以导出报告

![image.png](https://fynotefile.oss-cn-zhangjiakou.aliyuncs.com/fynote/1762/1642730130000/a93fcf070fa84692ae562e68e156cdb4.png)
