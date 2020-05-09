# 获取监控数据 - GetMetric

## 简介

获取监控数据





## 使用方法

您可以选择以下方式中的任意一种，发起 API 请求：
- 多语言 OpenSDK（[Python](https://github.com/ucloud/ucloud-sdk-python3) / [Go](https://github.com/ucloud/ucloud-sdk-go) / [Java](https://github.com/ucloud/ucloud-sdk-java)）
- [UAPI 浏览器](https://console.ucloud.cn/uapi/detail?id=GetMetric)
- [工作流引擎 StepFlow](https://console.ucloud.cn/stepflow/manage/)

## 定义

### 公共参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Action**     | string  | 对应的 API 指令名称，当前 API 为 `GetMetric`                        | **Yes** |
| **PublicKey**  | string  | 用户公钥，可从 [控制台](https://console.ucloud.cn/uapi/apikey) 获取                                             | **Yes** |
| **Signature**  | string  | 根据公钥及 API 指令生成的用户签名，参见 [签名算法](api/summary/signature.md)  | **Yes** |

### 请求参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Region** | string | 地域。 参见 [地域和可用区列表](api/summary/regionlist) |No|
| **Zone** | string | 可用区。参见 [可用区列表](api/summary/regionlist) |No|
| **ProjectId** | string | 项目ID，不填为默认项目。子账户必须填写项目ID |No|
| **ResourceType** | string | 资源类型 |**Yes**|
| **ResourceId** | string | 资源Id（目前除sharebandwidth可以不传入ResourceId外，其他资源必须传入，sharebandwidth不传入会默认使用获取到的第一个资源Id） |No|
| **TimeRange** | integer | 拉取最近多少秒的监控数据，默认1小时，即3600；最大1个月 |No|
| **BeginTime** | integer | 起始时间unixtimestamp，若传入TimeRange，此项忽略 |No|
| **EndTime** | integer | 结束时间unixtimestamp，若传入TimeRange，此项忽略；若只传入BeginTime，此项默认为当前时间 |No|
| **MetricName.N** | string | 指标名称（不同ResourceType对应不同的MetricName） |**Yes**|

### 响应字段

| 字段名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **RetCode** | integer | 返回状态码，为 0 则为成功返回，非 0 为失败 |**Yes**|
| **Action** | string | 操作指令名称 |**Yes**|
| **Message** | string | 返回错误消息，当 RetCode 非 0 时提供详细的描述信息 |No|




## 示例

### 请求示例
    
```
https://api.ucloud.cn/?Action=GetMetric
&Region=cn-bj2
&Zone=cn-bj2-04
&ResourceType=uhost
&ResourceId=uhost-xxx
&MetricName.1=NetPacketIn
&MetricName.0=NetPacketOut
&BeginTime=1431505992
&EndTime=1431506592
```

### 响应示例
    
```json
{
  "Action": "GetMetricResponse",
  "DataSets": {
    "NetPacketIn": [
      {
        "Timestamp": 1431506100,
        "Value": 0
      },
      {
        "Timestamp": 1431506400,
        "Value": 0
      }
    ],
    "NetPacketOut": [
      {
        "Timestamp": 1431506100,
        "Value": 0
      },
      {
        "Timestamp": 1431506400,
        "Value": 0
      }
    ]
  },
  "RetCode": 0
}
```




