# 领券中心 API
Java API
标签: 【coupon-center】【栾锋】

version 1.0.0

---

<!-- ## 一、【券列表】 -->

## 1、多渠道和会员编号查询可领取的券列表（分页）

- **接口描述**  
> 通过渠道列表和会员编号查询可领取的券列表（分页）  
  

- **接口信息**  
> **接口地址：** http://192.168.7.33:8080/coupon/CouponService/queryAvailableCouponListPage   
> **提交方式：** POST,GET  
> **方法名称：** queryAvailableCouponListPage  
  

- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----:|
|channelCodes| array | 是 | 渠道列表 |
|customerCode|string|是|会员编号|
|sortOrder|string|是|排序字段，固定为0|
|pageNo|number|是|当前页码|
|pageSize|number|是|每页大小|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
|beginDate|number|1496246401000|开始日期|
|desc|string|满20减19，立即生效，每人限领一张，仅O2O适用|券描述|
|endDate|number|1501516799000|结束日期|
|ruleDesc|string||券规则描述|
|status|string|ENABLE-可领，RECEIVED-已领，NONE-已领完|状态|
|templateId|string|592fd38a47422366c6f8c7b5|模版id 用于领券|
|title|string|满20减19|券标题|
|type|string|ALL ALL-整单券，GOODS-商品组合，ITEM-单品|券类型 |
|value|number|19|券金额|


 异常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 |  |
| message | String | | |




- **示例**

入参示例: 
```json
{
	"channelCodes":[
		"WXM_6369","DZG_6369"
    ],
	"customerCode":"15dd20b21b3742889456d378932b7647",
	"sortOrder":"0",
	"pageNo":1,
	"pageSize":10
}
```

返回结果
```json
[
    {
        "beginDate": 1496246401000,
        "desc": "满20减19，立即生效，每人限领一张，仅O2O适用",
        "endDate": 1501516799000,
        "ruleDesc": "",
        "status": "ENABLE",
        "templateId": "592fd38a47422366c6f8c7b5",
        "title": "满20减19",
        "type": "ALL",
        "value": 19
    }
]
```

!> **NOTICE**  
无

 
---

## 2、领券

- **接口描述**  
> 领券  
  

- **接口信息**  
> **接口地址：** http://192.168.7.33:8080/coupon/CouponService/assignCoupon   
> **提交方式：** POST,GET  
> **方法名称：** assignCoupon  
  

- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----:|
|channelCode| string | 是 | 渠道列表,公众号中为GZH |
|customerCode|string|是|会员编号|
|templateId|string|是|券模版id|


- **响应结果**


 正常

无



 异常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 |  |
| message | String | | |



- **示例**

入参示例: 
```json
{
	"channelCode":"GZH",
	"customerCode":"15dd20b21b3742889456d378932b7647",
	"templateId":"592fd38a47422366c6f8c7b5"
}
```

返回结果
```json
```

!> **NOTICE**  
无
