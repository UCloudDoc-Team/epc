# EPC节点组操作指南

## 创建节点组
登录EPC产品控制台，点击【创建】，选择节点组的tab，如下图所示：
![image](/images/EPC3.0/createnode1.png)
![image](/images/EPC3.0/createnode2.png)

支持选择时付、月付、年付以及后付费等多种付费方式，您可按需选择CPU节点或者GPU节点以及对应规格。</br>
节点组可选择一次性创建一台或者多台高性能计算节点，每个节点可自定义系统盘、网络带宽，满足各类场景需要。
如果是新用户登录，在创建计算节点时，可同步创建一块20G的共享存储，新创建的计算节点自动挂载在共享存储上。

## 登录节点
资源创建成功之后，资源将跳转到资源列表页，如下图所示：
![image](/images/EPC3.0/list01.png)

点击【计算直连0】或者【计算直连1】等其他计算直连，可正常登录计算节点。
![image](/images/EPC3.0/login_12.png)


## 共享存储文件上传和下载

计算节点创建成功之后，共享存储同步创建成功，展示资源列表页上方。
共享存储可通过计算节点内部登录：

![image](/images/EPC3.0/FSx02.png)

### 通过 FTP/SFTP 上传下载
**适用于Windows、macOS、Linux 操作系统**

在“超算存储”点击【详情】

![image](/images/EPC3.0/upload_01.png)

按照如图提供的用户名、密码、地址和端口号信息，使用 FTP/SFTP 客户端(Filezilla)登陆。

![image](/images/EPC3.0/upload_02.png)
![image](/images/EPC3.0/upload_03.png)

### SCP上传下载
**适用于Windows、macOS、Linux 操作系统**

从登录节点资源详情复制外网登录IP

![image](/images/EPC3.0/upload_11.png)

复制本地目录到集群，在命令行界面输入

```
$ scp -r local_folder root@113.31.xx.xx:remote_folder
```
### WinSCP上传下载(Windows)

**适用于Windows操作系统**

打开WinSCP，输入主机名、SSH用户、密码，点击登录。

![image](/images/EPC3.0/upload_12.png)

复制本地目录到集群，把左边的目录拖移到右边即可。

![image](/images/EPC3.0/upload_13.png)




