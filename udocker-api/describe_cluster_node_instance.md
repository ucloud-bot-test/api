# 获取节点 - DescribeClusterNodeInstance

## 简介

获取节点





## 使用方法

您可以选择以下方式中的任意一种，发起 API 请求：
- 多语言 OpenSDK（[Python](https://github.com/ucloud/ucloud-sdk-python3) / [Go](https://github.com/ucloud/ucloud-sdk-go) / [Java](https://github.com/ucloud/ucloud-sdk-java)）
- [UAPI 浏览器](https://console.ucloud.cn/uapi/detail?id=DescribeClusterNodeInstance)
- [工作流引擎 StepFlow](https://console.ucloud.cn/stepflow/manage/)

## 定义

### 公共参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Action**     | string  | 对应的 API 指令名称，当前 API 为 `DescribeClusterNodeInstance`                        | **Yes** |
| **PublicKey**  | string  | 用户公钥，可从 [控制台](https://console.ucloud.cn/uapi/apikey) 获取                                             | **Yes** |
| **Signature**  | string  | 根据公钥及 API 指令生成的用户签名，参见 [签名算法](api/summary/signature.md)  | **Yes** |

### 请求参数

| 参数名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **Region** | string | 地域。 参见 [地域和可用区列表](api/summary/regionlist) |**Yes**|
| **Zone** | string | 可用区。参见 [可用区列表](api/summary/regionlist) |No|
| **ProjectId** | string | 项目ID。不填写为默认项目，子帐号必须填写。 请参考[GetProjectList接口](api/summary/get_project_list) |**Yes**|
| **ClusterId** | string | 集群实例Id  |**Yes**|
| **Offset** | integer | 数据偏移量, 默认为0 |No|
| **Limit** | integer | 返回数据长度, 默认为20，最大值10000000 |No|
| **NodeIds.N** | string | 节点实例ID, 如果为空, 则返回当前Cluster所有符合条件的节点；n=0,1,2... |No|

### 响应字段

| 字段名 | 类型 | 描述信息 | 必填 |
|:---|:---|:---|:---|
| **TotalCount** | integer | 满足条件的总数 |No|
| **NodeSet** | string | 节点实例列表, 每项参数可见NodeSet结构 |No|
| **RetCode** | integer | 返回状态码，为 0 则为成功返回，非 0 为失败 |**Yes**|
| **Action** | string | 操作指令名称 |**Yes**|
| **Message** | string | 返回错误消息，当 RetCode 非 0 时提供详细的描述信息 |No|




## 示例

### 请求示例
    
```
https://api.ucloud.cn/?Action=DescribeClusterNodeInstance
&Region=cn-bj2
&Zone=cn-bj2-02
&ProjectId=org-xxx
&ClusterId=cluster-xxx
&NodeIds.0=dnode-xxx
```

### 响应示例
    
```json
{
  "Action": "DescribeClusterNodeInstanceResponse",
  "NodeSet": [],
  "RetCode": 0,
  "TotalCount": 0
}
```




