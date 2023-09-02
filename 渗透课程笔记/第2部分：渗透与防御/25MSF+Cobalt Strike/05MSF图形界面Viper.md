**MSF图形化界面Viper(炫彩蛇)下载与使用**

Viper是一款图形化内网渗透工具,将内网渗透过程中常用的战术及技术进行模块化及武器化.

集成杀软绕过,内网隧道,文件管理,命令行等基础功能.

当前已集成70+个模块,覆盖初始访问/持久化/权限提升/防御绕过/凭证访问/信息收集/横向移动等大类.

**在Kali Linux上安装Docker**

```
apt-get update

#使用apt安装docker 
apt-get install -y docker.io 

#设置开机启动 
systemctl start docker

#检查启动状态 
docker version
```

​              

![1640043246556](https://img.gyxnb.top/img/1640043246556.png)

 **安装docker-compose**

```
curl -L https://get.daocloud.io/docker/compose/releases/download/1.25.5/docker-compose-`uname -s`-`uname -m` > /usr/bin/docker-compose

#给赋可执行状态 
chmod +x /usr/bin/docker-compose
```

![1640043297604](https://img.gyxnb.top/img/1640043297604.png)

 

```
#设置安装目录
export VIPER_DIR=/root/VIPER

#执行如下命名生成安装目录,并进入安装目录 
mkdir -p $VIPER_DIR && cd $VIPER_DIR
```

​              

![1640043341743](https://img.gyxnb.top/img/1640043341743.png)

**执行如下命令生成docker-compose.yml**

如果你看到的命令是乱的  https://note.youdao.com/s/GdzSJnWD  看这个文档

 

```
tee docker-compose.yml <<-'EOF'
version: "3"
services:
  viper:
  	image: registry.cn-shenzhen.aliyuncs.com/toys/viper:latest
    container_name: viper-c
    network_mode: "host"
    restart: always
    volumes:
      - ${PWD}/loot:/root/.msf4/loot
      - ${PWD}/db:/root/viper/Docker/db
      - ${PWD}/module:/root/viper/Docker/module
      - ${PWD}/log:/root/viper/Docker/log
      - ${PWD}/nginxconfig:/root/viper/Docker/nginxconfig
    command: ["VIPER_PASSWORD"]
EOF
```

​              

![1640043385926](https://img.gyxnb.top/img/1640043385926.png)

**设置登录密码**

Viper不允许使用默认密码,diypassword替换为自定义密码密码

```
export VIPER_PASSWORD=root
```

​              

![1640043439186](https://img.gyxnb.top/img/1640043439186.png)

**写入密码到docker-compose.yml**

```
sed -i "s/VIPER_PASSWORD/$VIPER_PASSWORD/g" docker-compose.yml

#使用命令查看一下配置 
cat docker-compose.yml
```

​                

![1640043478861](https://img.gyxnb.top/img/1640043478861.png)



**创建启动Viper**

```
cd $VIPER_DIR
docker-compose up -d 

#或者
#启动viper
docker-compose start    
```

> 启动Viper 时，执行
>
> docker-compose up -d
>
> 会遇到“ERROR: Get "https://registry.cn-shenzhen.aliyuncs.com/v2/": net/http: request canceled while waiting for connection (Client.Timeout exceeded while awaiting headers)”的报错，这里的解决方案是**修改DNS服务**。具体操作如下：
>
> `vim /etc/resolv.conf`
>
> **将dns修改为8.8.8.8**，
>
> 即将 nameserver 后面的DNS地址改为`8.8.8.8`
>
> 
>
>
> 重启docker 服务
>
> `systemctl restart docker`
>
> 
>
> 然后进入到安装目录，$VIPER_DIR表示你的安装viper的目录
>
> `cd $VIPER_DIR`
>
> 然后执行
>
> `docker-compose up -d`
> 顺利启动

![1640043509764](https://img.gyxnb.top/img/1640043509764.png)

**等待15s系统启动,访问炫彩蛇 **

- `https://192.168.70.3:60000`
-  登录. 用户名:root 
-  密码: root

![1640043540568](https://img.gyxnb.top/img/1640043540568.png)



**注意：**

**所有的docker-compose命令必须在安装目录执行才会有效果**

