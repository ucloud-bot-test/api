# 获取节点监控数据 - GetUvodnNodeData

## 简介

获取节点监控数据





## 使用方法

您可以选择以下方式中的任意一种，发起 API 请求：
- 多语言 OpenSDK（[Python](https://github.com/ucloud/ucloud-sdk-python3) / [Go](https://github.com/ucloud/ucloud-sdk-go) / [Java](https://github.com/ucloud/ucloud-sdk-java)）
- [UAPI 浏览器](https://console.ucloud.cn/uapi/detail?id=GetUvodnNodeData)
- [工作流引擎 StepFlow](https://console.ucloud.cn/stepflow/manage/)

## 定义

### 公共参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Action**     | string  | 对应的 API 指令名称，当前 API 为 `GetUvodnNodeData`                        | **Yes** |
| **PublicKey**  | string  | 用户公钥，可从 [控制台](https://console.ucloud.cn/uapi/apikey) 获取                                             | **Yes** |
| **Signature**  | string  | 根据公钥及 API 指令生成的用户签名，参见 [签名算法](api/summary/signature.md)  | **Yes** |

### 请求参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **ProjectId** | string | 项目ID。不填写为默认项目，子帐号必须填写。 请参考[GetProjectList接口](api/summary/get_project_list) |No|
| **NodeId** | string | 节点id |**Yes**|
| **BeginTime** | integer | 查询起始时间 |No|
| **EndTime** | integer | 查询结束时间 |No|
| **Type.N** | integer | 0CPU使用率, 1内存使用率, 2 网卡出流量, 3网卡入流量, 4网卡出包量, 5网卡入包量, 6磁盘读流量, 7磁盘写流量, 8磁盘读次数, 9磁盘写次数 |**Yes**|

### 响应字段

| 字段名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **RetCode** | integer | 返回状态码，为 0 则为成功返回，非 0 为失败 |**Yes**|
| **Action** | string | 操作指令名称 |**Yes**|
| **DataSets** | [*DataSet*](#DataSet) | 带宽数据实例集合 |No|
| **Message** | string | 返回错误消息，当 RetCode 非 0 时提供详细的描述信息 |No|

#### 数据模型


#### DataSet

| 字段名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **CPUUtilization** | array[[*MonitorInfo*](#MonitorInfo)] | cpu使用率 |No|
| **MemUtilization** | array[[*MonitorInfo*](#MonitorInfo)] | 内存使用率 |No|
| **NICOut** | array[[*MonitorInfo*](#MonitorInfo)] | 网卡出带宽 |No|
| **NICIn** | array[[*MonitorInfo*](#MonitorInfo)] | 网卡入带宽 |No|
| **NetPacketOut** | array[[*MonitorInfo*](#MonitorInfo)] | 网卡出包量 |No|
| **NetPacketIn** | array[[*MonitorInfo*](#MonitorInfo)] | 网卡入包量 |No|
| **IORead** | array[[*MonitorInfo*](#MonitorInfo)] | 磁盘读取量 |No|
| **IOWrite** | array[[*MonitorInfo*](#MonitorInfo)] | 磁盘写入量 |No|
| **DiskReadOps** | array[[*MonitorInfo*](#MonitorInfo)] | 磁盘读取次数 |No|
| **DiskWriteOps** | array[[*MonitorInfo*](#MonitorInfo)] | 磁盘写入次数 |No|

#### MonitorInfo

| 字段名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **TimeStamp** | integer | 时间戳 |**Yes**|
| **Value** | integer | 值 |**Yes**|

## 示例

### 请求示例
    
```
https://api.ucloud.cn/?Action=GetUvodnNodeData
&ProjectId=org-xxx
&NodeId=uedn-node-xxx
&Type.0=6
&Type.1=7
&BeginTime=1568793055
&EndTime=1569397855
```

### 响应示例
    
```json
{
  "Action": "GetUvodnNodeDataResponse",
  "DataSets": {
    "IORead": [
      {
        "TimeStamp": 1568793300,
        "Value": 9063642624
      },
      {
        "TimeStamp": 1568793600,
        "Value": 9064899584
      },
      {
        "TimeStamp": 1568793900,
        "Value": 9066116608
      },
      {
        "TimeStamp": 1568794200,
        "Value": 9067363840
      },
      {
        "TimeStamp": 1568794500,
        "Value": 9069628416
      }
    ],
    "IOWrite": [
      {
        "TimeStamp": 1568793300,
        "Value": 9063642624
      },
      {
        "TimeStamp": 1568793600,
        "Value": 9064899584
      },
      {
        "TimeStamp": 1568793900,
        "Value": 9066116608
      },
      {
        "TimeStamp": 1568794200,
        "Value": 9067363840
      },
      {
        "TimeStamp": 1568794500,
        "Value": 9069628416
      }
    ]
  },
  "RetCode": 0
}
```




