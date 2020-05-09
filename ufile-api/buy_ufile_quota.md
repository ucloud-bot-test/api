# 购买配额 - BuyUFileQuota

## 简介

购买配额

?> QuotaType和Quota参数限制说明如下：<br />1) storage-volome的单位为GB*天，Quota取值范围为 [100, 30 000 000]，且Quota是100的倍数；<br />2）download-traffic的单位为GB，Quota取值范围为 [1, 102 400]；<br />3）request-count的单位为万次，Quota取值范围为 [1, 1 000 000]



## 使用方法

您可以选择以下方式中的任意一种，发起 API 请求：
- 多语言 OpenSDK（[Python](https://github.com/ucloud/ucloud-sdk-python3) / [Go](https://github.com/ucloud/ucloud-sdk-go) / [Java](https://github.com/ucloud/ucloud-sdk-java)）
- [UAPI 浏览器](https://console.ucloud.cn/uapi/detail?id=BuyUFileQuota)
- [工作流引擎 StepFlow](https://console.ucloud.cn/stepflow/manage/)

## 定义

### 公共参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Action**     | string  | 对应的 API 指令名称，当前 API 为 `BuyUFileQuota`                        | **Yes** |
| **PublicKey**  | string  | 用户公钥，可从 [控制台](https://console.ucloud.cn/uapi/apikey) 获取                                             | **Yes** |
| **Signature**  | string  | 根据公钥及 API 指令生成的用户签名，参见 [签名算法](api/summary/signature.md)  | **Yes** |

### 请求参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Region** | string | 地域。 参见 [地域和可用区列表](api/summary/regionlist) |**Yes**|
| **ProjectId** | string | 项目ID。不填写为默认项目，子帐号必须填写。 请参考[GetProjectList接口](api/summary/get_project_list) |No|
| **QuotaType** | string | 配额类型，取值为storage-volume, download-traffic或request-count |**Yes**|
| **Quota** | integer | 配额数值 |**Yes**|
| **CouponId** | string | 代金券编号 |No|

### 响应字段

| 字段名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **OrderNumber** | string | 订单号 |No|
| **RetCode** | integer | 返回状态码，为 0 则为成功返回，非 0 为失败 |**Yes**|
| **Action** | string | 操作指令名称 |**Yes**|
| **Message** | string | 返回错误消息，当 RetCode 非 0 时提供详细的描述信息 |No|




## 示例

### 请求示例
    
```
https://api.ucloud.cn/?Action=BuyUFileQuota
&Region=cn-bj2
&QuotaType=storage-volume
&Quota=100
```

### 响应示例
    
```json
{
  "Action": "BuyUFileQuotaResponse",
  "OrderNumber": "2015033100171121010",
  "Retcode": 0
}
```




