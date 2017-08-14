# 积分商城 API
Java API
标签: 【integral-mall】【栾锋】

version 1.0.0



- **服务地址：** serviceUrl  
> **开发环境：** http://192.168.7.51:8082/  
> **测试环境：**  
> **生产环境：**

---

## 商品

### 1. 商品列表  

- **接口描述**  
> 通过渠道编码分页查询商品列表

- **接口信息**  
> **接口地址：** {{serviceUrl}}/goods/integralGoodsService/queryGoods
> **提交方式：** POST,GET  
> **方法名称：** queryGoods 

- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----:|
|channelCode|string|是|渠道编码 JFM_6369|
|pageInfo|object|是|分页对象|
|pageInfo.page|int|否|分页页码|
|pageInfo.limit|int|是|每页大小|
|pageInfo.lastId|string|是|最后一个值id 第一页不填|
|goods|object|是|过滤参数|
|goods.price|number(9,2)|是|商品价格大于|
|goods.points|number(9,2)|是|积分大于*的商品|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|



 异常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 |  |
| message | String | | |




- **示例**

入参示例: 
```json
{
	"pageInfo":{
		"limit":5,
		"lastId":"5988078970b99e2d409b181b"
	},	
	"goods":{},
	"channelCode":"JFM_6369"
}
```

返回结果
```json
{
    "lastId": "5988075470b99e1b50c14f16",
    "limit": 5,
    "rows": [
        {
            "channelPrice": 13.4,
            "goodsCode": "1000973",
            "goodsImgUrl": "https://img.yifengx.com/product/1000973/1000973a1.jpg!f120",
            "goodsName": "熊胆痔灵膏 (葵花) 10克 黑龙江葵花药业股份有限公司",
            "points": 600,
            "price": 5,
            "ruleId": "5988075470b99e1b50c14f16",
            "stock": 0
        }
    ]
}
```

 **NOTICE**  
无

 
---


### 2. 商品详情  

- **接口描述**  
> 通过渠道编码分页查询商品列表

- **接口信息**  
> **接口地址：** {{serviceUrl}}/goods/integralGoodsService/queryGoodsDetail
> **提交方式：** POST,GET  
> **方法名称：** queryGoodsDetail 

- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----:|
|channelCode|string|是|渠道编码 JFM_5857|
|ruleId|string|是|规则id|




- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|



 异常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 |  |
| message | String | | |




- **示例**

入参示例: 
```json
{
	"channelCode":"JFM_5857",
	"ruleId":"598806f570b99e2c84e6e60a"
}
```

返回结果
```json
{
    "channelPrice": 11.5,
    "channels": [
        {
            "channelCode": "JFM_5857",
            "channelServiceMode": "O2O",
            "customerPickUp": false
        },
        {
            "channelCode": "JFM_6369",
            "channelServiceMode": "O2O",
            "customerPickUp": false
        }
    ],
    "goodsCode": "1000971",
    "goodsName": "罗红霉素分散片 (严迪) 75毫克*12片 哈药集团制药六厂",
    "points": 125,
    "price": 8.5,
    "ruleId": "598806f570b99e2c84e6e60a",
    "stock": 1
}
```

 **NOTICE**  
无

 
---


## 交易

### 1. 判断积分和库存是否足够

- **接口描述**  
> 根据商品编码数量，渠道和会员检查积分和库存

- **接口信息**  
> **接口地址：** {{serviceUrl}}/order/integralOrderService/calcPointsAndStock
> **提交方式：** POST,GET  
> **方法名称：** calcPointsAndStock 

- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----:|
|goods|object|是|商品对象|
|goods.ruleId|string|是|规则编码|
|goods.quantity|string|是|商品数量|
|channelCode|string|是|渠道编码|
|customerCode|string|是|会员编号|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
||string|true|正常的返回结果|


 异常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 |  |
| message | String | | |




- **示例**

入参示例: 
```json
{
	"goods":{
		"ruleId":"598806f570b99e2c84e6e60a",
		"quantity":200
	},
	"channelCode":"JFM_5857",
	"customerCode":"00000738-0E78-4A5E-B9DA-F0617CAB5748"
}
```

返回结果
```json
{
    "code": "80000005",
    "message": "【积分兑换商品】 您有积分1871,当前操作需要积分2000 ",
    "class": "com.yifeng.zt.integral.service.order.IntegralOrderServiceImpl"
}
```

 **NOTICE**  
无

 
---



### 2. 创建订单

- **接口描述**  
> 创建订单

- **接口信息**  
> **接口地址：** {{serviceUrl}}/order/integralOrderService/createGoodsOrder
> **提交方式：** POST,GET  
> **方法名称：** createGoodsOrder 

- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----:|
|order|object|是|订单对象|
|order.channelCode|string|是|渠道编码|
|order.channelServiceMode|string|是|服务模式 B2C O2O|
|order.customerCode|string|是|会员编号|
|order.deliveryArea|string|否|服务模式B2C 必填 配送区域 country|
|order.deliveryType|string|否|服务模式B2C 必填 配送方式公司 ytoexpress|
|order.freightAmount|string|否|服务模式B2C 必填 运费|
|order.orderNote|string|否|订单备注|
|order.goodsList|[]|是|订单商品列表|
|order.goodsList[i].ruleId|string|是|订单商品规则id|
|order.goodsList[i].quantity|number|是|商品数量|
|order.contact|object|否|服务模式B2C 收货人信息|
|order.contact.name|string|是|收货人姓名|
|order.contact.phone|string|是|收货人手机号码|
|order.contact.address|object|是|收货人地址|
|order.contact.address.address|string|是|收货人详细地址|
|order.contact.address.provinceCode|string|是|收货人地址省编码|
|order.contact.address.provinceName|string|是|收货人地址省名称|
|order.contact.address.cityCode|string|是|收货人地址市编码|
|order.contact.address.cityName|string|是|收货人地址市名称|
|order.contact.address.districtCode|string|是|收货人地址区编码|
|order.contact.address.districtName|string|是|收货人地址区名称|
- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
||string|true|正常的返回结果|


 异常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 |  |
| message | String | | |




- **示例**

入参示例: 
```json
{
	"order":{
		"channelCode":"JFM_6369",
		"channelServiceMode":"B2C",
		"customerCode":"00000738-0E78-4A5E-B9DA-F0617CAB5748",
		"deliveryArea":"country",
		"deliveryType":"ytoexpress",
		"freightAmount":0.00,
		"contact": {
            "name": "蒋玲娥",
            "phone": "18673107936",
            "address": {
                "address": "中房F联邦",
                "provinceCode": "430000",
                "provinceName": "湖南省",
                "cityCode": "430100",
                "cityName": "长沙市",
                "districtName": "岳麓区",
                "districtCode": "430104",
                "location": {
                    "latitude": 0,
                    "longitude": 0
                }
            }
        },
        "goodsList": [
            {
                "ruleId": "598806f570b99e2c84e6e60a",
                "quantity": 1
            }
        ],
        "orderNote":"222"
	}
}
```

返回结果
```json
"JFM20170812585702100001"
```

 **NOTICE**  
无

 
---


## 历史记录

### 1. 查询兑换记录 

- **接口描述**  
> 通过会员编号和凭证编码查询兑换记录

- **接口信息**  
> **接口地址：** {{serviceUrl}}/exchange/integralExchangeHistoryService/queryCustomerExchangeDataByVoucherNumbers
> **提交方式：** POST,GET  
> **方法名称：** queryCustomerExchangeDataByVoucherNumbers 

- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----:|

- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
||string|true|正常的返回结果|


 异常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 |  |
| message | String | | |




- **示例**

入参示例: 
```json
{
	"customerCode":"00000738-0E78-4A5E-B9DA-F0617CAB5748",
	"voucherNumbers":[
		"111","222"
		]
}
```

返回结果
```json

```

 **NOTICE**  
无

 
---


