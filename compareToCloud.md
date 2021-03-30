# 对比云计算服务商

## 阿里云 ##
* [官网地址](https://www.aliyun.com/product/ehpc?spm=5176.19720258.J_8058803260.82.e9392c4aEd4RuR)

### 申请方式 ### 
* 创建集群，需创建计算节点，管控节点，登录节点。各项配置总计32项
* [源站链接](https://ehpc.console.aliyun.com/?spm=5176.159202.850386.btn1.6ff56a56oFQpKk&accounttraceid=bfa3cf1311644cbf8303d97574b9f925eeli#/clustercreation?clusterType=cluster&referrer=%2Fcluster&regionId=cn-hangzhou) （需登录控制台）

### 支持规格 ### 
* 支持所有阿里云ECS的虚拟机/物理机机型，但各机型性能无统一文档，需逐一测试
* 最大实例规格：104 vCPU
* 支持CPU类型：
  * [Intel Skylake](https://ark.intel.com/content/www/us/en/ark/products/codename/37572/skylake.html): 2017年
  * [Intel Cascadelake (2nd Xeon)](https://ark.intel.com/content/www/us/en/ark/products/series/192283/2nd-generation-intel-xeon-scalable-processors.html): 2019年
* 支持GPU类型：
  * [Nvidia Tesla V100](https://www.nvidia.com/en-us/data-center/v100/)
  * [Nvdia Tesla T4](https://www.nvidia.com/en-us/data-center/tesla-t4/)
* [源站链接](https://help.aliyun.com/document_detail/57680.html?spm=a2c4g.11186623.6.544.6f7c57barEwsyj)

### 计费方式 ### 
* 除了资源费用，收取额外管理费用（中国大陆地域：0.02元/核/小时，海外地域：0.03元/核/小时）
* 收取额外NAS存储费用和登录节点外网流量费用
* [源站链接](https://help.aliyun.com/document_detail/57844.html?spm=5176.spm-b.0.0.23f3e91aA9UjGD)

## 腾讯云 ##
* 无HPC产品

### 支持规格 ###
* 最大实例规格：标准型SA2 180vCPU, 464G内存 
* 支持CPU类型：
  * [AMD EPYC2 ROME 2.6GHz处理器, 睿频3.3GHz](https://www.amd.com/en/processors/epyc-7002-series?gclid=CjwKCAjw9MuCBhBUEiwAbDZ-7j5x30uRMgboWjhVzleib9K9fHoIRbPw9deClC85595oQJMQEf3ZLBoCIFUQAvD_BwE)：2019年发布
    * 规格详情：基础主频：2.6GHz，全核睿频：3.3GHz
  * [Intel Cascade Lake 8255C](https://ark.intel.com/content/www/us/en/ark/products/series/192283/2nd-generation-intel-xeon-scalable-processors.html)：2019年发布
    * 规格详情：基础主频：2.5GHz
  * [Intel Cooper Lake ](https://ark.intel.com/content/www/us/en/ark/products/codename/189143/cooper-lake.html): 2020年发布
    * 规格详情：基础主频：2.5GHz
* 支持GPU类型：
  * [Nvidia Tesla V100](https://www.nvidia.com/en-us/data-center/v100/)
  * [Nvdia Tesla T4](https://www.nvidia.com/en-us/data-center/tesla-t4/)
* [源站链接](https://cloud.tencent.com/document/product/213/11518)

### 计费方式 ###
* 资源费用
  * S5.8XLARGE64（32核，64GB，Intel Xeon Cascade Lake 8255C/Intel Xeon Cooper Lake 2.5G）：4.78元/节点/时（0.15元/核时）
  * S5.16XLARGE256（64核，256GB，Intel Xeon Cascade Lake 8255C/Intel Xeon Cooper Lake 2.5G）：14.35元/节点/时（0.22元/核时）
  * S5.16XLARGE256（64核，256GB，Intel Xeon Cascade Lake 8255C/Intel Xeon Cooper Lake 2.5G）：14.35元/节点/时（0.22元/核时）
  * SA2.32XLARGE256（128核，256GB，AMD EPYC2 Rome 2.6G）：14.34元/节点/时（0.11元/核时）
  * SA2.45XLARGE464（180核，464GB，AMD EPYC2 Rome 2.6G）：23.07元/节点/时（0.13元/核时）
* 收取额外NAS存储费用和登录节点外网流量费用
* [源站链接](https://buy.cloud.tencent.com/price/cvm/calculator?devPayMode=hourly&regionId=33&zoneId=330001&instanceType=S5.8XLARGE64&imageType=linux&systemDiskType=CLOUD_PREMIUM&systemDiskSize=440&bandwidthType=TRAFFIC_POSTPAID_BY_HOUR&bandwidth=1)

## 华为云 ##
* 无HPC产品

### 支持规格 ###
* 最大实例规格：超大内存型E3 208vCPU, 2932GB
* 最大裸金属实例规格：physical.c6sd.3xlarge 104CPU, 304GB
* 支持CPU类型：
  * [裸金属服务器Intel Cascade Lake 6266 V6 (3.0 GHz)](https://ark.intel.com/content/www/us/en/ark/products/series/192283/2nd-generation-intel-xeon-scalable-processors.html)：2019年发布 
  * [裸金属服务器Intel Cascade Lake 6278 V6 (2.6 GHz)](https://ark.intel.com/content/www/us/en/ark/products/series/192283/2nd-generation-intel-xeon-scalable-processors.html)：2019年发布 
  * [裸金属服务器Intel Skylake-SP Xeon Gold 6161](https://ark.intel.com/content/www/us/en/ark/products/codename/37572/skylake.html)：2017年发布
* 支持GPU类型：
  * [Nvidia Tesla V100](https://www.nvidia.com/en-us/data-center/v100/)
  * [Nvdia Tesla T4](https://www.nvidia.com/en-us/data-center/tesla-t4/)
* [源站链接](https://support.huaweicloud.com/intl/zh-cn/productdesc-bms/bms_pd_0015.html)

### 计费方式 ###
* 资源费用
  * 通用计算增强型C3（32核，64GB）：6.68元/节点/时（0.21元/核时）
  * 通用计算增强型C3（60核，128GB）： 13.37元/节点/时（0.22元/核时）
  * 超大内存型E3（208核，2932GB）：132.28元/节点/时（0.63元/核时）
  * 裸金属服务器BMS physical.s4.3xlarge（44核，384GB）：9560元/节点/月（0.3元/核时） 

* 收取额外NAS存储费用和登录节点外网流量费用
* [源站链接](https://www.huaweicloud.com/pricing.html?tab=detail#/ecs)

## AWS ##
* [官网地址](https://aws.amazon.com/cn/hpc/?nc2=h_ql_sol_use_hpc)

### 支持规格 ### 
* 最大实例规格：96 vCPU (Intel Cascadelake 或 AMD EPYC2）
* 支持CPU类型：
  * Intel Skylake 8175M ：
     * [Skylake CPU](https://ark.intel.com/content/www/us/en/ark/products/codename/37572/skylake.html): 2017年发布
     * M5实例，基础主频：2.5GHz，全核睿频：3.1GHz
  * Intel Cascadelake：
     * [Cascadelake CPU (2nd Xeon)](https://ark.intel.com/content/www/us/en/ark/products/series/192283/2nd-generation-intel-xeon-scalable-processors.html): 2019年发布
     * M5n实例，全核睿频3.1 GHz
     * C5n实例：全核睿频3.4 GHz
     * C5实例: 全核睿频3.6GHz
     * M5zn实例：全核睿频4.5GHz
  * [AMD EPYC2](https://www.amd.com/zh-hans/processors/epyc-7002-series): 2019年发布
     * M5a实例：全核最大主频2.5GHz
     * C5a实例：全核最大主频3.3GHz
* 支持GPU类型：
  * [Nvidia Tesla A100](https://www.nvidia.com/en-us/data-center/a100/)
  * [Nvidia Tesla V100](https://www.nvidia.com/en-us/data-center/v100/)
  * [Nvdia Tesla T4](https://www.nvidia.com/en-us/data-center/tesla-t4/)
* [源站链接](https://aws.amazon.com/cn/ec2/instance-types/)

### 计费方式 ### 
* 资源费用：
  * c5a.8xlarge 1.552USD（0.0485USD核时）
  * c5.18xlarge（72核144G） 3.888USD（0.054USD核时）
  * c5.metal（96核192G） 5.184USD（0.054USD核时）
* 收取额外NAS存储费用和登录节点外网流量费用
* [源站链接](https://aws.amazon.com/cn/ec2/pricing/on-demand/)
