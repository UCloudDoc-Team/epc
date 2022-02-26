# CentOS安装GUI桌面 #

### CentOS7安装XRDP远程桌面

#### 1、安装Xfce桌面
```
# yum -y groupinstall Xfce "X Window system"
```


#### 2、配置xfce为默认桌面 
```
# vim ~/.Xclients

#!/bin/bash
XFCE="$(which xfce4-session 2>/dev/null)"
exec "$XFCE"

# chmod +x ~/.Xclients
```


#### 3、安装xrdp
```
# yum -y install epel-release

# yum -y install xrdp tigervnc tigervnc-server
```
?> Xrdp最终会自动启用VNC，所以需要安装tigervnc-server。



#### 4、启动XRDP
```
# systemctl start xrdp

# systemctl enable xrdp

# netstat -ntlp |grep xrdp

tcp        0      0 127.0.0.1:3350          0.0.0.0:*               LISTEN      13607/xrdp-sesman

tcp        0      0 0.0.0.0:3389            0.0.0.0:*               LISTEN      13608/xrdp 
```


#### 5、远程连接测试体验

windows自带的远程桌面连接：附件 -> 远程桌面连接，或者打开运行，输入mstsc命令即可。


?> vnc是大部分Linux发行版默认的基于RFB协议的远程桌面程序，但对于普通用户来说，vnc的用户体验并不好，需要安装客户端。

