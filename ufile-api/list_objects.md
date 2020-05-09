# 获取目录文件列表 - ListObjects

## 简介

用于以目录形式列出Bucket下的文件信息





## 使用方法

您可以选择以下方式中的任意一种，发起 API 请求：
- 多语言 OpenSDK（[Python](https://github.com/ucloud/ucloud-sdk-python3) / [Go](https://github.com/ucloud/ucloud-sdk-go) / [Java](https://github.com/ucloud/ucloud-sdk-java)）
- [UAPI 浏览器](https://console.ucloud.cn/uapi/detail?id=ListObjects)
- [工作流引擎 StepFlow](https://console.ucloud.cn/stepflow/manage/)

## 定义

### 公共参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Action**     | string  | 对应的 API 指令名称，当前 API 为 `ListObjects`                        | **Yes** |
| **PublicKey**  | string  | 用户公钥，可从 [控制台](https://console.ucloud.cn/uapi/apikey) 获取                                             | **Yes** |
| **Signature**  | string  | 根据公钥及 API 指令生成的用户签名，参见 [签名算法](api/summary/signature.md)  | **Yes** |

### 请求参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Authorization** | string | 获取目录文件列表请求的授权签名 |**Yes**|
| **Prefix** | string | 返回以Prefix作为前缀的目录文件列表 |No|
| **Marker** | string | 返回以字母排序后，大于Marker的目录文件列表 |No|
| **MaxKeys** | integer | 指定返回目录文件列表的最大数量，默认值为100，不超过1000 |No|
| **Delimiter** | string | 目录分隔符，默认为'/'，当前只支持是'/' |No|

### 响应字段

| 字段名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Name** | string | Bucket名称 |No|
| **Prefix** | string | 查询结果的前缀 |No|
| **MaxKeys** | integer | 查询结果的最大数量 |No|
| **Delimiter** | string | 查询结果的目录分隔符 |No|
| **IsTruncated** | boolean | 返回结果是否被截断。若值为true，则表示仅返回列表的一部分，NextMarker可作为之后迭代的游标 |No|
| **NextMarker** | string | 可作为查询请求中的的Marker参数，实现迭代查询 |No|
| **Contents** | array[[*Contents*](#Contents)] | 文件列表 |No|
| **CommonPrefixes** | array[[*CommonPrefixes*](#CommonPrefixes)] | 以Delimiter结尾，并且有共同前缀的目录列表 |No|
| **RetCode** | integer | 返回状态码，为 0 则为成功返回，非 0 为失败 |**Yes**|
| **Action** | string | 操作指令名称 |**Yes**|
| **Message** | string | 返回错误消息，当 RetCode 非 0 时提供详细的描述信息 |No|

#### 数据模型


#### Contents

| 字段名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Key** | string | 文件名称 |**Yes**|
| **MimeType** | string | 文件mimetype |**Yes**|
| **ETag** | string | 标识文件内容 |**Yes**|
| **Size** | string | 文件大小 |**Yes**|
| **StorageClass** | string | 文件存储类型 |**Yes**|
| **LastModified** | integer | 文件最后修改时间 |**Yes**|
| **CreateTime** | integer | 文件创建时间 |**Yes**|

#### CommonPrefixes

| 字段名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Prefix** | string | 以Delimiter结尾的公共前缀目录名 |**Yes**|

## 示例

### 请求示例
    
```
https://api.ucloud.cn/?Action=ListObjects
&Authorization=otXXMMnW
&Prefix=igviJcXo
&Marker=kkGeLMFB
&MaxKeys=9
&Delimiter=nTdYKjnA
```

### 响应示例
    
```json
{
  "Action": "ListObjectsResponse",
  "CommonPrefixes": [
    {
      "Prefix": "cfnzRqeg"
    }
  ],
  "Contents": [
    {
      "CreateTime": 2,
      "ETag": "hEfUAHLV",
      "Key": "GmwMhdPm",
      "LastModified": 4,
      "MimeType": "OjCSLEPm",
      "Size": "QXERFtCZ",
      "StorageClass": "yOVtxMEh"
    }
  ],
  "Delimiter": "JMCjvzKE",
  "IsTruncated": false,
  "MaxKeys": 6,
  "Name": "pPznOxlP",
  "NextMarker": "vZpbukOU",
  "Prefix": "NlRgDPOX",
  "RetCode": 0
}
```




