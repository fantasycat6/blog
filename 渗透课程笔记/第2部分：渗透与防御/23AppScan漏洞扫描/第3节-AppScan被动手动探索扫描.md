# 第三节-AppScan被动手动探索扫描

被动式扫描：浏览器代理到AppScan，然后进行手工操作，探索产生出的流量给AppScan进行扫描。

他的优点是：扫描足够精准，覆盖率更加高，减少不必要的干扰包等等

## 1.扫描基础准备

### 1.火狐安装FoxyProxy

1.打开扩展和主题

```
about:addons
```

2.输入FoxyProxy 点击【回车】搜索

![image-20211220101102542](https://image.201068.xyz/assets/image-20211220101102542.png)

3.点击 【FoxyProxy Standard】

![image-20211220101117058](https://image.201068.xyz/assets/image-20211220101117058.png)

4.点击【添加到 Firefox】

![image-20211220101133106](https://image.201068.xyz/assets/image-20211220101133106.png)

### 2.马士兵靶场

1.进入靶场

```
https://www.bafangwy.com/battle
```

2.启动dvwa靶场

![image-20211220101210330](https://image.201068.xyz/assets/image-20211220101210330.png)

![image-20211220101218208](https://image.201068.xyz/assets/image-20211220101218208.png)

3.访问靶场

```
http://39.101.162.123:64936/login.php
admin
password
```

4.设置安全等级为low

![image-20211220101245688](https://image.201068.xyz/assets/image-20211220101245688.png)

![image-20211220101251950](https://image.201068.xyz/assets/image-20211220101251950.png)

## 2.扫描步骤

### 1选择【扫描】--【手动探索】--【外部设备】

![image-20211220101317215](https://image.201068.xyz/assets/image-20211220101317215.png)

![image-20211220101326318](https://image.201068.xyz/assets/image-20211220101326318.png)

### 2.火狐浏览器点击【代理】--选择【选项】

![image-20211220101344037](https://image.201068.xyz/assets/image-20211220101344037.png)

### 3.点击【添加】

![image-20211220101355972](https://image.201068.xyz/assets/image-20211220101355972.png)

### 4.输入标题【appsacn】，添加ip【127.0.0.1】，添加端口【49729】，点击保存

![image-20211220101409923](https://image.201068.xyz/assets/image-20211220101409923.png)

![image-20211220101417072](https://image.201068.xyz/assets/image-20211220101417072.png)

### 5.开启代理

![image-20211220101432626](https://image.201068.xyz/assets/image-20211220101432626.png)

### 6.操作被测网站

![image-20211220101444737](https://image.201068.xyz/assets/image-20211220101444737.png)

### 7.切换到appScan 点击【停止记录】

![image-20211220101456598](https://image.201068.xyz/assets/image-20211220101456598.png)

### 8.选择网站，点击【确定】

![image-20211220101508810](https://image.201068.xyz/assets/image-20211220101508810.png)

![image-20211220101515856](https://image.201068.xyz/assets/image-20211220101515856.png)

### 9.点击【扫描】，选择【仅测试】

![image-20211220101534029](https://image.201068.xyz/assets/image-20211220101534029.png)

### 10.点击【是】

![image-20211220101544955](https://image.201068.xyz/assets/image-20211220101544955.png)

### 11.选则储存位置，点击保存

![image-20211220101556686](https://image.201068.xyz/assets/image-20211220101556686.png)

### 12.等待测试结果

![image-20211220101609909](https://image.201068.xyz/assets/image-20211220101609909.png)

![image-20211220101617427](https://image.201068.xyz/assets/image-20211220101617427.png)

## 3.appscan内置浏览器扫描

### 1.点击【手动探索】，选则【AppScan Chromium 浏览器】

![image-20211220101630427](https://image.201068.xyz/assets/image-20211220101630427.png)

### 2.点击【是】

![image-20211220101650772](https://image.201068.xyz/assets/image-20211220101650772.png)

### 3.输入URL 点击【确定】

![image-20211220101703074](https://image.201068.xyz/assets/image-20211220101703074.png)

### 4.点击取消

![image-20211220101715529](https://image.201068.xyz/assets/image-20211220101715529.png)

### 5.点击【配置】--【参数和cookie】--【定制头】

![image-20211220101727775](https://image.201068.xyz/assets/image-20211220101727775.png)

### 6.在火狐浏览器复制cookie

![image-20211220101740026](https://image.201068.xyz/assets/image-20211220101740026.png)

### 7.切换到AppScan，点击【+】，添加cookie，点击【确定】

![image-20211220101752959](https://image.201068.xyz/assets/image-20211220101752959.png)

### 8.点击确定

![image-20211220101803601](https://image.201068.xyz/assets/image-20211220101803601.png)

### 9.点击【手动探索】，选则【AppScan Chromium 浏览器】

![image-20211220101815512](https://image.201068.xyz/assets/image-20211220101815512.png)

### 10.进行手工探索，完成后，点击【确定】

![image-20211220101829329](https://image.201068.xyz/assets/image-20211220101829329.png)

![image-20211220101836928](https://image.201068.xyz/assets/image-20211220101836928.png)

### 11.点击【确定】

![image-20211220101848039](https://image.201068.xyz/assets/image-20211220101848039.png)

![image-20211220101854695](https://image.201068.xyz/assets/image-20211220101854695.png)

### 12.点击【扫描】--【仅测试】

![image-20211220101906463](https://image.201068.xyz/assets/image-20211220101906463.png)

13.点击【是】

![image-20211220101916451](https://image.201068.xyz/assets/image-20211220101916451.png)

### 14.选择保存位置，点击【保存】

![image-20211220101929768](https://image.201068.xyz/assets/image-20211220101929768.png)

### 15.等待扫描结果

![image-20211220101941766](https://image.201068.xyz/assets/image-20211220101941766.png)

![image-20211220101948472](https://image.201068.xyz/assets/image-20211220101948472.png)

