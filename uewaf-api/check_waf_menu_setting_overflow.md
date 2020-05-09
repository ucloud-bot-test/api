# 校验域名和规则数是否超出指定套餐的限制 - CheckWafMenuSettingOverflow

## 简介

校验域名和规则数是否超出指定套餐的限制





## 使用方法

您可以选择以下方式中的任意一种，发起 API 请求：
- 多语言 OpenSDK（[Python](https://github.com/ucloud/ucloud-sdk-python3) / [Go](https://github.com/ucloud/ucloud-sdk-go) / [Java](https://github.com/ucloud/ucloud-sdk-java)）
- [UAPI 浏览器](https://console.ucloud.cn/uapi/detail?id=CheckWafMenuSettingOverflow)
- [工作流引擎 StepFlow](https://console.ucloud.cn/stepflow/manage/)

## 定义

### 公共参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Action**     | string  | 对应的 API 指令名称，当前 API 为 `CheckWafMenuSettingOverflow`                        | **Yes** |
| **PublicKey**  | string  | 用户公钥，可从 [控制台](https://console.ucloud.cn/uapi/apikey) 获取                                             | **Yes** |
| **Signature**  | string  | 根据公钥及 API 指令生成的用户签名，参见 [签名算法](api/summary/signature.md)  | **Yes** |

### 请求参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **ProjectId** | string | 不填为默认项目 |No|
| **EditionType** | string | 版本类型名，Enhanced:增强版,Deluxe:高级版,Enterprise:企业版,Professional:旗舰版（已废弃） |No|

### 响应字段

| 字段名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **RetCode** | integer | 返回状态码，为 0 则为成功返回，非 0 为失败 |**Yes**|
| **Action** | string | 操作指令名称 |**Yes**|
| **UsageInfo** | [*UsageInfo*](#UsageInfo) | 用量描述，参考UsageInfo |No|
| **Message** | string | 返回错误消息，当 RetCode 非 0 时提供详细的描述信息 |No|

#### 数据模型


#### UsageInfo

| 字段名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **IPUsage** | [*UsageInfoDetail*](#UsageInfoDetail) | 独享ip用量，参考UsageInfoDetail |No|
| **DomainUsage** | string | 已添加域名数量，参考UsageInfoDetail |No|
| **BoardWidthUsageInner** | string | 内部带宽占用，参考UsageInfoDetail |No|
| **BoardWidthUsageOuter** | string | 外部带宽占用，参考UsageInfoDetail |No|
| **DomainLimit** | string | 域名数量限额，参考UsageInfoDetail |No|
| **ExclusiveIPLimit** | string | 独享ip限额，参考UsageInfoDetail |No|
| **BandwidthInner** | string | 内部带宽限额，参考UsageInfoDetail |No|
| **BandwidthOuter** | string | 外部带宽限额，参考UsageInfoDetail |No|

#### UsageInfoDetail

| 字段名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Quota** | integer | 配额数量 |No|
| **Used** | integer | 已使用数量 |No|

## 示例

### 请求示例
    
```
https://api.ucloud.cn/?Action=CheckWafMenuSettingOverflow
&ProjectId=org-xxx
```

### 响应示例
    
```json
{
  "Action": "CheckWafMenuSettingOverflowResponse",
  "RetCode": 0,
  "UsageInfo": {
    "BandwidthInner": {
      "Quota": 120,
      "Used": 0
    },
    "BandwidthOuter": {
      "Quota": 40,
      "Used": 0
    },
    "DomainLimit": {
      "Quota": 20,
      "Used": 3
    },
    "ExclusiveIPLimit": {
      "Quota": 8,
      "Used": 0
    },
    "customize_rule_set": {
      "Quota": 30,
      "Used": 0
    },
    "user_domain_cc_rules": {
      "Quota": 10,
      "Used": 0
    }
  }
}
```




