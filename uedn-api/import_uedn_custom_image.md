# 导入自定义镜像 - ImportUEdnCustomImage

## 简介

导入自定义镜像





## 使用方法

您可以选择以下方式中的任意一种，发起 API 请求：
- 多语言 OpenSDK（[Python](https://github.com/ucloud/ucloud-sdk-python3) / [Go](https://github.com/ucloud/ucloud-sdk-go) / [Java](https://github.com/ucloud/ucloud-sdk-java)）
- [UAPI 浏览器](https://console.ucloud.cn/uapi/detail?id=ImportUEdnCustomImage)
- [工作流引擎 StepFlow](https://console.ucloud.cn/stepflow/manage/)

## 定义

### 公共参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Action**     | string  | 对应的 API 指令名称，当前 API 为 `ImportUEdnCustomImage`                        | **Yes** |
| **PublicKey**  | string  | 用户公钥，可从 [控制台](https://console.ucloud.cn/uapi/apikey) 获取                                             | **Yes** |
| **Signature**  | string  | 根据公钥及 API 指令生成的用户签名，参见 [签名算法](api/summary/signature.md)  | **Yes** |

### 请求参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **ProjectId** | string | 项目ID。不填写为默认项目，子帐号必须填写。 请参考[GetProjectList接口](api/summary/get_project_list) |No|
| **ImageId** | string | 镜像Id，不传参表示新导入镜像，传参表示已有镜像分发到指定机房 |No|
| **ImageName** | string | 镜像名称，不带镜像ID时必填 |No|
| **UFileUrl** | string | UFile镜像文件下载地址，不带镜像ID时必填 |No|
| **OsType** | string | 操作系统平台，linux、windows，不带镜像ID时必填 |No|
| **Format** | string | 镜像格式，可选RAW、qcow2， 不带镜像ID时必填 |No|
| **ImageDesc** | string | 镜像描述 |No|
| **IdcId.N** | string | 镜像需要导入机房 |**Yes**|

### 响应字段

| 字段名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **ImageId** | string | 镜像Id |**Yes**|
| **RetCode** | integer | 返回状态码，为 0 则为成功返回，非 0 为失败 |**Yes**|
| **Action** | string | 操作指令名称 |**Yes**|
| **Message** | string | 返回错误消息，当 RetCode 非 0 时提供详细的描述信息 |No|




## 示例

### 请求示例
    
```
https://api.ucloud.cn/?Action=ImportUEdnCustomImage
&ProjectId=NMKlpokg
&ImageName=buufJkSJ
&UFileUrl=YWwobTcX
&OsType=xWZrLvIH
&Format=SrbnKCbS
&IdcId.n=yejuAhRZ
&ImageDesc=KjFVIejJ
&ImageId=EROnlqHT
```

### 响应示例
    
```json
{
  "Action": "ImportUEdnCustomImageResponse",
  "ImageId": "DffcgmDT",
  "RetCode": 0
}
```




