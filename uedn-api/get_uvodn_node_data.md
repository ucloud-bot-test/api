# 获取节点监控数据-GetUvodnNodeData

获取节点监控数据

# Request Parameters
|Parameter name|Type|Description|Required|
|---|---|---|---|
|ProjectId|string|项目ID。不填写为默认项目，子帐号必须填写。 请参考[GetProjectList接口](api/summary/get_project_list)|No|
|NodeId|string|节点id|**Yes**|
|Type.n|int|0CPU使用率, 1内存使用率, 2 网卡出流量, 3网卡入流量, 4网卡出包量, 5网卡入包量, 6磁盘读流量, 7磁盘写流量, 8磁盘读次数, 9磁盘写次数|**Yes**|
|BeginTime|int|查询起始时间|No|
|EndTime|int|查询结束时间|No|

# Response Elements
|Parameter name|Type|Description|Required|
|---|---|---|---|
|RetCode|int|返回码|**Yes**|
|Action|string|操作名称|**Yes**|
|DataSets|object|带宽数据实例集合|No|

## DataSet
|Parameter name|Type|Description|Required|
|---|---|---|---|
|CPUUtilization|array|cpu使用率|No|
|MemUtilization|array|内存使用率|No|
|NICOut|array|网卡出带宽|No|
|NICIn|array|网卡入带宽|No|
|NetPacketOut|array|网卡出包量|No|
|NetPacketIn|array|网卡入包量|No|
|IORead|array|磁盘读取量|No|
|IOWrite|array|磁盘写入量|No|
|DiskReadOps|array|磁盘读取次数|No|
|DiskWriteOps|array|磁盘写入次数|No|

## MonitorInfo
|Parameter name|Type|Description|Required|
|---|---|---|---|
|TimeStamp|int|时间戳|**Yes**|
|Value|int|值|**Yes**|

# Request Example
```
https://api.ucloud.cn/?Action=GetUvodnNodeData
&ProjectId=org-xxx
&NodeId=uedn-node-xxx
&Type.0=6
&Type.1=7
&BeginTime=1568793055
&EndTime=1569397855
```

# Response Example
```
{
    "Action": "GetUvodnNodeDataResponse", 
    "DataSets": {
        "IORead": [
            {
                "TimeStamp": 1568793300, 
                "Value": 9063642624.0
            }, 
            {
                "TimeStamp": 1568793600, 
                "Value": 9064899584.0
            }, 
            {
                "TimeStamp": 1568793900, 
                "Value": 9066116608.0
            }, 
            {
                "TimeStamp": 1568794200, 
                "Value": 9067363840.0
            }, 
            {
                "TimeStamp": 1568794500, 
                "Value": 9069628416.0
            }
        ], 
        "IOWrite": [
            {
                "TimeStamp": 1568793300, 
                "Value": 9063642624.0
            }, 
            {
                "TimeStamp": 1568793600, 
                "Value": 9064899584.0
            }, 
            {
                "TimeStamp": 1568793900, 
                "Value": 9066116608.0
            }, 
            {
                "TimeStamp": 1568794200, 
                "Value": 9067363840.0
            }, 
            {
                "TimeStamp": 1568794500, 
                "Value": 9069628416.0
            }
        ]
    }, 
    "RetCode": 0
}
```
