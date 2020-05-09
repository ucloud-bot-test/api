# 获取已上传成功的分片列表 - GetMultiUploadPart

## 简介

获取已上传成功的分片列表

?> Syntax:<br />	GET /?muploadpart&uploadId=<uploadid><br />	Host: <bucket_name>.ufile.ucloud.cn<br />	Authorization: <token> <br /><br />Request Headers<br />	Authorization 下载请求的授权签名



## 使用方法

您可以选择以下方式中的任意一种，发起 API 请求：
- 多语言 OpenSDK（[Python](https://github.com/ucloud/ucloud-sdk-python3) / [Go](https://github.com/ucloud/ucloud-sdk-go) / [Java](https://github.com/ucloud/ucloud-sdk-java)）
- [UAPI 浏览器](https://console.ucloud.cn/uapi/detail?id=GetMultiUploadPart)
- [工作流引擎 StepFlow](https://console.ucloud.cn/stepflow/manage/)

## 定义

### 公共参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Action**     | string  | 对应的 API 指令名称，当前 API 为 `GetMultiUploadPart`                        | **Yes** |
| **PublicKey**  | string  | 用户公钥，可从 [控制台](https://console.ucloud.cn/uapi/apikey) 获取                                             | **Yes** |
| **Signature**  | string  | 根据公钥及 API 指令生成的用户签名，参见 [签名算法](api/summary/signature.md)  | **Yes** |

### 请求参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **UploadId** | string | 上传ID |**Yes**|

### 响应字段

| 字段名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **ErrMsg** | string | 错误提示 |No|
| **UploadId** | string | 上传ID |No|
| **Key** | string | 文件名称 |No|
| **Status** | integer | 上传状态，0：未完成，1：完成 |No|
| **Parts** | array[[*PartsItem*](#PartsItem)] | 分片列表 |No|
| **RetCode** | integer | 返回状态码，为 0 则为成功返回，非 0 为失败 |**Yes**|
| **Action** | string | 操作指令名称 |**Yes**|
| **Message** | string | 返回错误消息，当 RetCode 非 0 时提供详细的描述信息 |No|

#### 数据模型


#### PartsItem

| 字段名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **PartNum** | integer | 分片编号 |No|
| **Etag** | string | 分片etag值 |No|

## 示例

### 请求示例
    
```
GET /?muploadpart&uploadId=e5af977e-329c-4a25-b907-d8bc39ff95e3 HTTP/1.1
Host: example.cn-bj.ufileos.ucloud.cn
Authorization:UCloud pRAtiCbYdYI9wqHMqcQe0D9m16YpTsKBVL3GeBZ6wn6N+00uMrI7NQ==:VdDRXKoBjX6FnxjOz+HbLtswW50=
```

### 响应示例
    
```json
{
  "ErrMsg": "",
  "Key": "large_file_version_4",
  "Parts": [
    {
      "Etag": "K8y9LzjxXBPrfVqJ_Z2F9ZXiO8M=",
      "PartNum": 0
    },
    {
      "Etag": "K8y9LzjxXBPrfVqJ_Z2F9ZXiO8M=",
      "PartNum": 1
    },
    {
      "Etag": "8AELsK7_teqWNDghPCj9IdowvBA=",
      "PartNum": 2
    }
  ],
  "RetCode": 0,
  "Status": 0,
  "UploadId": "e5af977e-329c-4a25-b907-d8bc39ff95e3"
}
```




