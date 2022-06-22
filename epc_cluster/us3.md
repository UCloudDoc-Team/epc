# US3同步指南
项目数据可以在US3和EPC单机之间挂载，可以在US3和EPC集群之前同步

## EPC单机<>US3同步指南
https://docs.ucloud.cn/ufile/tools/us3fs/quickaccess

## EPC集群<>US3同步指南

### US3 >> EPC集群

#### 创建自己的US3 Bucket（如果想参与集群数据同步，请在上海二创建）
https://console.ucloud.cn/ufile/ufile

![](/images/us3/US3.png)

#### 使自己计划操作的数据存在于US3 Bucket，例如EPC单机同步，或直接在US3控制台上传

#### 进入EPC控制台
https://console.ucloud.cn/uhpc/cluster?hpc=true

#### 选择集群任务管理（EPC集群）
![](/images/us3/INIT.png)

#### 进行同步设置
![](/images/us3/ENTRY.png)

#### 关联自己的US3 Bucket
![](/images/us3/RULE.png)

#### 开始同步
![](/images/us3/ENTRY.png)

#### 同步完成
![](/images/us3/DONE.png)

#### 进入网盘(EPC集群存储)管理
![](/images/us3/ENTRY.png)

#### 发现US3的数据已经同步到指定目录中，且可以在EPC集群JOB中直接访问
![](/images/us3/CHECK.png)

### EPC集群 >> US3
是 US3 >> EPC集群的逆向

#### 变更数据的同步方向
![](/images/us3/REVERSE.png)

#### 开始同步
![](/images/us3/ENTRY.png)

#### 在US3控制台check你的数据
https://console.ucloud.cn/ufile/ufile

![](/images/us3/US3.png)

#### 对US3数据进行后续的操作，例如挂载到EPC单机，或下载
