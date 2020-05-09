# 查询房间通话详单 - QueryURtcOrderDetail

## 简介

查询房间通话详单





## 使用方法

您可以选择以下方式中的任意一种，发起 API 请求：
- 多语言 OpenSDK（[Python](https://github.com/ucloud/ucloud-sdk-python3) / [Go](https://github.com/ucloud/ucloud-sdk-go) / [Java](https://github.com/ucloud/ucloud-sdk-java)）
- [UAPI 浏览器](https://console.ucloud.cn/uapi/detail?id=QueryURtcOrderDetail)
- [工作流引擎 StepFlow](https://console.ucloud.cn/stepflow/manage/)

## 定义

### 公共参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Action**     | string  | 对应的 API 指令名称，当前 API 为 `QueryURtcOrderDetail`                        | **Yes** |
| **PublicKey**  | string  | 用户公钥，可从 [控制台](https://console.ucloud.cn/uapi/apikey) 获取                                             | **Yes** |
| **Signature**  | string  | 根据公钥及 API 指令生成的用户签名，参见 [签名算法](api/summary/signature.md)  | **Yes** |

### 请求参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Region** | string | 地域。 参见 [地域和可用区列表](api/summary/regionlist) |No|
| **Zone** | string | 可用区。参见 [可用区列表](api/summary/regionlist) |No|
| **ProjectId** | string | 项目ID。不填写为默认项目，子帐号必须填写。 请参考[GetProjectList接口](api/summary/get_project_list) |No|
| **AppId** | string | AppId |**Yes**|
| **RoomId** | string | 房间ID |**Yes**|
| **StartTime** | string | 起始时间 |**Yes**|
| **EndTime** | string | 结束时间 |**Yes**|
| **Type** | string | 产品类型（RTC/RECORD）,默认RTC |No|
| **Offset** | integer | 列表起始位置偏移量，默认为0 |No|
| **Limit** | integer | 返回数据长度，默认为20，最大100 |No|

### 响应字段

| 字段名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Msg** | string | RetCode为0时返回succed,不为0返回具体的错误消息提示内容 |**Yes**|
| **Data** | array[[*CallDetail*](#CallDetail)] | 通话详单 |**Yes**|
| **TotalCount** | integer | 总数 |No|
| **RetCode** | integer | 返回状态码，为 0 则为成功返回，非 0 为失败 |**Yes**|
| **Action** | string | 操作指令名称 |**Yes**|
| **Message** | string | 返回错误消息，当 RetCode 非 0 时提供详细的描述信息 |No|

#### 数据模型


#### CallDetail

| 字段名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **RoomId** | string | 房间ID |No|
| **UserId** | string | 用户ID |No|
| **Device** | string | 设备信息 |No|
| **Type** | string | 房间类型 |No|
| **Role** | string | 用户角色 |No|
| **Stats** | array[[*CallStat*](#CallStat)] | 消费时长统计 |No|
| **JoinTime** | integer | 加入时间 |No|
| **LeaveTime** | integer | 离开时间 |No|

#### CallStat

| 字段名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Profile** | string | 类型 |No|
| **Count** | integer | 数值 |No|

## 示例

### 请求示例
    
```
https://api.ucloud.cn/?Action=QueryURtcOrderDetail
&Region=cn-zj
&Zone=cn-zj-01
&ProjectId=IxxspcxF
&AppId=GuhyRJFy
&RoomId=oAiTQZhj
&StartTime=RrmweoSS
&EndTime=mRqQbUCe
&Offset=3
&Limit=5
&Type=uvcxDWNN
```

### 响应示例
    
```json
{
  "Action": "QueryURtcOrderDetailResponse",
  "Data": [
    {
      "Device": "pPOqiIxB",
      "JoinTime": 1,
      "LeaveTime": 5,
      "Role": "PSAtVAyc",
      "RoomId": "AyLAByUb",
      "Stats": [
        {
          "Count": 1,
          "Profile": "tLlHOEKw"
        }
      ],
      "Type": "KgGXsehp",
      "UserId": "QtTjzZTK"
    }
  ],
  "Msg": "oxmHixxX",
  "RetCode": 0,
  "TotalCount": 6
}
```




