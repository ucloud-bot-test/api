# 批量复制WAF规则 - CopyWafDomainRules

## 简介

批量复制WAF规则，目前支持防护规则、CC规则、恶意IP惩罚规则、黑白名单、返回码防护规则的复制





## 使用方法

您可以选择以下方式中的任意一种，发起 API 请求：
- 多语言 OpenSDK（[Python](https://github.com/ucloud/ucloud-sdk-python3) / [Go](https://github.com/ucloud/ucloud-sdk-go) / [Java](https://github.com/ucloud/ucloud-sdk-java)）
- [UAPI 浏览器](https://console.ucloud.cn/uapi/detail?id=CopyWafDomainRules)
- [工作流引擎 StepFlow](https://console.ucloud.cn/stepflow/manage/)

## 定义

### 公共参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Action**     | string  | 对应的 API 指令名称，当前 API 为 `CopyWafDomainRules`                        | **Yes** |
| **PublicKey**  | string  | 用户公钥，可从 [控制台](https://console.ucloud.cn/uapi/apikey) 获取                                             | **Yes** |
| **Signature**  | string  | 根据公钥及 API 指令生成的用户签名，参见 [签名算法](api/summary/signature.md)  | **Yes** |

### 请求参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **ProjectId** | string | 项目ID。不填写为默认项目，子帐号必须填写。 请参考[GetProjectList接口](api/summary/get_project_list) |No|
| **FullDomain** | string | 源域名 |**Yes**|
| **DestDomain.N** | string | 目的域名 |**Yes**|
| **RuleType** | string | 规则类型,CCRule:CC规则； ProtectionRule：防护规则； AutoBlacklistRule：自动拦截规则； HTTPDisguiseRule：信息防护规则； RegionBlockRule：区域封堵规则；WhiteList：白名单规则；BlackList：黑名单规则 |**Yes**|
| **Append** | boolean | 赋值方式是否追加；true：追加，false：覆盖；默认未覆盖 |No|

### 响应字段

| 字段名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **RetCode** | int | 返回状态码，为 0 则为成功返回，非 0 为失败 |**Yes**|
| **Action** | string | 操作指令名称 |**Yes**|
| **Message** | string | 返回错误消息，当 `RetCode` 非 0 时提供详细的描述信息 |No|




## 示例

### 请求示例
    
```
https://api.ucloud.cn/?Action=CopyWafDomainRules
&ProjectId=org-xxx
&FullDomain=www.test.com
&DestDomain.0=www.test1.com
&DestDomain.1=www.test2.com
&RuleType=CCRule
&Append=false
```

### 响应示例
    
```json
{
  "Action": "CopyWafDomainRulesResponse",
  "RetCode": 0
}
```





