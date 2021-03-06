# WAF攻击发生次数概览 - StatWafAttacksTrend

## 简介

WAF攻击发生次数概览





## 使用方法

您可以选择以下方式中的任意一种，发起 API 请求：
- 多语言 OpenSDK（[Python](https://github.com/ucloud/ucloud-sdk-python3) / [Go](https://github.com/ucloud/ucloud-sdk-go) / [Java](https://github.com/ucloud/ucloud-sdk-java)）
- [UAPI 浏览器](https://console.ucloud.cn/uapi/detail?id=StatWafAttacksTrend)
- [工作流引擎 StepFlow](https://console.ucloud.cn/stepflow/manage/)

## 定义

### 公共参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Action**     | string  | 对应的 API 指令名称，当前 API 为 `StatWafAttacksTrend`                        | **Yes** |
| **PublicKey**  | string  | 用户公钥，可从 [控制台](https://console.ucloud.cn/uapi/apikey) 获取                                             | **Yes** |
| **Signature**  | string  | 根据公钥及 API 指令生成的用户签名，参见 [签名算法](api/summary/signature.md)  | **Yes** |

### 请求参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **ProjectId** | string | 项目ID，不填表示默认项目 |No|
| **BeginTime** | int | 开始时间，时间戳表示,单位：秒 |**Yes**|
| **EndTime** | int | 结束时间，时间戳表示，单位：秒 |**Yes**|
| **Domain** | string | 要统计的域名 |No|
| **Extent** | string | 统计区间，单位：秒，取值范围0-7200 |No|

### 响应字段

| 字段名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **RetCode** | int | 返回状态码，为 0 则为成功返回，非 0 为失败 |**Yes**|
| **Action** | string | 操作指令名称 |**Yes**|
| **Message** | string | 返回错误消息，当 `RetCode` 非 0 时提供详细的描述信息 |No|
| **Result** | [*StatAttackResult*](#StatAttackResult) | 攻击详情，参考StatAttackResult |No|

#### 数据模型


#### StatAttackResult

| 字段名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Count** | int | 返回节点个数 |**Yes**|
| **Detail** | array[[*StatAttackDetail*](#StatAttackDetail)] | 攻击次数详情数组，参考StatAttackDetail |**Yes**|

#### StatAttackDetail

| 字段名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Timestamp** | int | 时间戳 |**Yes**|
| **Count** | int | 攻击次数 |**Yes**|

## 示例

### 请求示例
    
```
https://api.ucloud.cn/?Action=StatWafAttacksTrend
&Extent=org-xxx
&BeginTime=1586237414
&EndTime=1586241014
```

### 响应示例
    
```json
{
  "Action": "StatWafAttacksTrendResponse",
  "Result": {
    "Count": 3,
    "Detail": [
      {
        "Count": 106,
        "Timestamp": 1586240820
      },
      {
        "Count": 1478,
        "Timestamp": 1586240880
      },
      {
        "Count": 315,
        "Timestamp": 1586240940
      }
    ],
    "Type": "AttackTotal"
  },
  "RetCode": 0
}
```





