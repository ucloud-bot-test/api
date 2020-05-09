# 获取正在执行的分片上传id - GetMultiUploadId

## 简介

获取正在执行的分片上传id

?> Syntax:<br />	GET /?muploadid&prefix=<prefix>&marker=<marker>&limit=<limit><br />	Host: <bucket_name>.ufile.ucloud.cn<br />	Authorization: <token> <br /><br />Request Headers<br />	Authorization 下载请求的授权签名



## 使用方法

您可以选择以下方式中的任意一种，发起 API 请求：
- 多语言 OpenSDK（[Python](https://github.com/ucloud/ucloud-sdk-python3) / [Go](https://github.com/ucloud/ucloud-sdk-go) / [Java](https://github.com/ucloud/ucloud-sdk-java)）
- [UAPI 浏览器](https://console.ucloud.cn/uapi/detail?id=GetMultiUploadId)
- [工作流引擎 StepFlow](https://console.ucloud.cn/stepflow/manage/)

## 定义

### 公共参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Action**     | string  | 对应的 API 指令名称，当前 API 为 `GetMultiUploadId`                        | **Yes** |
| **PublicKey**  | string  | 用户公钥，可从 [控制台](https://console.ucloud.cn/uapi/apikey) 获取                                             | **Yes** |
| **Signature**  | string  | 根据公钥及 API 指令生成的用户签名，参见 [签名算法](api/summary/signature.md)  | **Yes** |

### 请求参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Prefix** | string | 前缀，utf-8编码，默认为空字符串 |No|
| **Marker** | string | 标志字符串，utf-8编码，默认为空字符串 |No|
| **Limit** | integer | id列表数目，默认为20 |No|

### 响应字段

| 字段名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **ErrMsg** | string | 错误提示 |No|
| **NextMarker** | string | 下一个标志字符串，utf-8编码 |No|
| **DataSet** | array[[*DataSet*](#DataSet)] | 上传id列表 |No|
| **RetCode** | integer | 返回状态码，为 0 则为成功返回，非 0 为失败 |**Yes**|
| **Action** | string | 操作指令名称 |**Yes**|
| **Message** | string | 返回错误消息，当 RetCode 非 0 时提供详细的描述信息 |No|

#### 数据模型


#### DataSet

| 字段名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **UploadId** | string | 文件上传ID |No|
| **FileName** | string | 文件名称 |No|
| **StartTime** | integer | 上传开始时间，UNIX时间戳 |No|

## 示例

### 请求示例
    
```
GET /?muploadid&prefix=lar&marker=a&limit=20 HTTP/1.1
Host: example.cn-bj.ufileos.ucloud.cn
Authorization:UCloud pRAtiCbYdYI9wqHMqcQe0D9m16YpTsKBVL3GeBZ6wn6N+00uMrI7NQ==:VdDRXKoBjX6FnxjOz+HbLtswW50=
```

### 响应示例
    
```json
{
  "DataSet": [
    {
      "FileName": "large_file_version_2",
      "StartTime": 1484116878,
      "UploadId": "3be8bd2b-4188-41d5-ac80-9ddf644a090c"
    },
    {
      "FileName": "large_file_version_4",
      "StartTime": 1484117647,
      "UploadId": "e5af977e-329c-4a25-b907-d8bc39ff95e3"
    }
  ],
  "ErrMsg": "",
  "NextMarker": "",
  "RetCode": 0
}
```




