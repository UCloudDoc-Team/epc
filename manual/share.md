# 查看共享存储

共享存储：同一地域同一项目下的所有资源共享 1000GB 配额，支持热扩容。

Linux系统使用NFS存储，购买后挂载到 /172.16.0.XX/NFSSharedFiles 目录，可在命令行输入df命令查看；

![buy6](../../epc/images/buy6.png)

Windows系统挂载SMB存储，购买后挂载为一个网络盘符，与本地盘使用无异。

![buy7](../../epc/images/buy7.png)