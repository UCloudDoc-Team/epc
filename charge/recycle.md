# 回收

## 预付费资源回收

### EPC计算节点
如您的资源计费方式为按年/按月支付，资源回收流程如下：


当您的资源过期前3天：给您设置的通知接收人发送资源即将过期预警；

当您的资源过期当天：给您设置的通知接收人发送资源已过期通知；

当您的资源过期后3天：给您设置的通知接收人发送云主机即将被关机提醒，当天对云主机执行关机操作，关机后的云主机需先完成续费方可开机继续使用；

当您的资源过期后10天：给您设置的通知接收人发送云主机即将被回收提醒，当天对云主机执行回收操作（回收后的资源不可找回，还请及时续费）。


如您的资源计费方式为按小时支付，资源回收时间节点如下：

当您的资源过期后当天：发送已过期提醒；

当您的资源过期第1天：发送资源即将被回收通知；

当您的资源过期后第2天：发送回收通知，并回收主机。


### 共享存储
回收节点流程图如下：<br>
![img](/images/recycle.png)<br>

当挂载在当前共享存储上的最后一台EPC计算节点删除时，该存储进入回收流程，系统将给您发送回收预警信息邮件。

当挂载在当前共享存储上的最后一台EPC计算节点删除7天后，该存储将被回收，系统将给您发送资源回收邮件。



## 后付资源回收

按时后付费EPC计算节点每小时生成一张后付费订单，若您的账户可用余额充足，将自动扣费，若您的账户可用余额不足支持扣费，将产生欠费订单。

累计3张后付费欠费订单：发送资源可能被回收通知；

累计3张后付费欠费订单+24H：发送资源停机通知，且当天系统强制停机；

累计3张后付费欠费订单+48H:发生资源删除通知，且当天回收资源。


?> 共享存储目前仅支持预付费方式，暂时后付费场景；
?> 如客户账户有三张以上欠费订单，您将无法新开资源，支付完欠费订单之后才可继续使用。

!> 回收或删除后的资源很难被找回，还请您及时续费及备份数据，如有特殊情况，请提交工单，我们将尽力为您找回。


