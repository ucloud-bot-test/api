# 服务单上传附件鉴权 - AuthenticateTicketUpload

## 简介

服务单上传附件鉴权





## 使用方法

您可以选择以下方式中的任意一种，发起 API 请求：
- 多语言 OpenSDK（[Python](https://github.com/ucloud/ucloud-sdk-python3) / [Go](https://github.com/ucloud/ucloud-sdk-go) / [Java](https://github.com/ucloud/ucloud-sdk-java)）
- [UAPI 浏览器](https://console.ucloud.cn/uapi/detail?id=AuthenticateTicketUpload)
- [工作流引擎 StepFlow](https://console.ucloud.cn/stepflow/manage/)

## 定义

### 公共参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Action**     | string  | 对应的 API 指令名称，当前 API 为 `AuthenticateTicketUpload`                        | **Yes** |
| **PublicKey**  | string  | 用户公钥，可从 [控制台](https://console.ucloud.cn/uapi/apikey) 获取                                             | **Yes** |
| **Signature**  | string  | 根据公钥及 API 指令生成的用户签名，参见 [签名算法](api/summary/signature.md)  | **Yes** |

### 请求参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **FileName** | string | 文件名 |**Yes**|

### 响应字段

| 字段名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Message** | string | 返回错误消息，当 RetCode 非 0 时提供详细的描述信息 |No|
| **TotalCount** | integer | 0：返回成功；1：返回失败 |No|
| **DataSet** | string | 返回对象-授权码 |No|
| **RetCode** | integer | 返回状态码，为 0 则为成功返回，非 0 为失败 |**Yes**|
| **Action** | string | 操作指令名称 |**Yes**|




## 示例

### 请求示例
    
```
https://api.ucloud.cn/?Action=AuthenticateTicketUpload
&FileName=MuiHOFWJ
```

### 响应示例
    
```json
{
  "Action": "AuthenticateTicketUploadResponse",
  "RetCode": 0
}
```




