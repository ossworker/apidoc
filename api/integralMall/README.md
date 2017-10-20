# 积分商城 API
Java API
标签: 【integral-mall】【栾锋】

version 1.1.0



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
> **接口地址：** {serviceUrl}/goods/integralGoodsService/queryGoods  
> **提交方式：** POST  
> **方法名称：** queryGoods 

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|channelCode|string|是|渠道编码 JFM_6369|
|pageInfo|object|是|分页对象|
|pageInfo.page|int|否|分页页码|
|pageInfo.limit|int|是|每页大小|
|pageInfo.lastId|string|是|最后一个值id 第一页不填|
|goods|object|是|过滤参数|
|goods.price|number|是|商品价格大于|
|goods.points|number|是|积分大于*的商品|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|



 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
| code | String | 11000000 |  |
| message | String | |异常信息|




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
> **接口地址：** {serviceUrl}/goods/integralGoodsService/queryGoodsDetail  
> **提交方式：** POST  
> **方法名称：** queryGoodsDetail 

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|channelCode|string|是|渠道编码 JFM_5857|
|ruleId|string|是|规则id|




- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|



 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
| code | String | 11000000 |  |
| message | String | |异常信息|




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


## 券  

### 1. 券列表  

- **接口描述**  
> 分页查询券列表 不过滤库存 不实时过滤状态

- **接口信息**  
> **接口地址：** {serviceUrl}/coupon/integralCouponService/queryCoupons  
> **提交方式：** POST  
> **方法名称：** queryCoupons  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|pageInfo|object|是|分页对象|
|pageInfo.page|int|否|分页页码|
|pageInfo.limit|int|是|每页大小|
|coupon|object|是|券过滤对象|
|coupon.points|number|否|大于积分的券|
|customerCode|string|否|会员编号|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|limit|number|10|每页大小|
|page|number|1|当前页|
|rows|array|[]|分页数据|
|rows[i].beginDate|number|1503676801000|券开始日期|
|rows[i].endDate|number|1514735999000|券结束日期|
|rows[i].points|number|14|积分|
|rows[i].ruleDesc|string||规则描述|
|rows[i].ruleId|string||规则id|
|rows[i].templateId|string||券模版id|
|rows[i].title|string||券title|
|rows[i].type|string||券类型 GOODS/ITEM/ALL|
|rows[i].value|number|1|券面值|



 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
| code | String | 11000000 |  |
| message | String | |异常信息|




- **示例**

入参示例: 
```json
{
	"pageInfo":{
		"page":1,
		"limit":10
	},
	"coupon":null,
	"customerCode":"111111"
}
```

返回结果
```json
{
    "limit": 10,
    "offset": 0,
    "page": 1,
    "rows": [
        {
            "beginDate": 1503504001000,
            "desc": "",
            "endDate": 1504281599000,
            "points": 6,
            "ruleDesc": "活动推广单品券，当日生效，无限制",
            "ruleId": "59e5a2116b46697bce372cb6",
            "templateId": "599fc7e947422338d16ab313",
            "title": "活动推广单品券",
            "type": "ITEM",
            "value": 1
        },
        {
            "beginDate": 1503676801000,
            "desc": "",
            "endDate": 1514735999000,
            "points": 14,
            "ruleDesc": "每人限领1张，",
            "ruleId": "59e5a2436b46697bce372cb7",
            "templateId": "59a0cdd7474223625e7f9b01",
            "title": "线下活动推广品类糖尿病券满100减90",
            "type": "GOODS",
            "value": 90
        },
        {
            "beginDate": 1503676801000,
            "desc": "",
            "endDate": 1514735999000,
            "points": 20,
            "ruleDesc": "唤醒单品券",
            "ruleId": "59e5a2946b46697bce372cb9",
            "templateId": "59a113bd474223625e7f9b10",
            "title": "唤醒单品券",
            "type": "ITEM",
            "value": 2
        },
        {
            "beginDate": 1503676801000,
            "desc": "",
            "endDate": 1514735999000,
            "points": 25,
            "ruleDesc": "长沙门店单品券",
            "ruleId": "59e5a2c66b46697bce372cba",
            "templateId": "59a4b569474223168adf963a",
            "title": "长沙门店单品券",
            "type": "ITEM",
            "value": 2
        },
        {
            "beginDate": 1503676801000,
            "desc": "",
            "endDate": 1514735999000,
            "points": 55,
            "ruleDesc": "唤醒整单券",
            "ruleId": "59e5a2776b46697bce372cb8",
            "templateId": "59a113f1474223625e7f9b11",
            "title": "唤醒整单券",
            "type": "ALL",
            "value": 10
        }
    ]
}
```

 **NOTICE**  
无

 
---



### 2. 券详情  

- **接口描述**  
> 根据规则id和会员编号查询券详细信息

- **接口信息**  
> **接口地址：** {serviceUrl}/coupon/integralCouponService/queryCouponDetail   
> **提交方式：** POST  
> **方法名称：** queryCouponDetail  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|ruleId|string|是|规则id|
|customerCode|string|是|会员编号|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|beginDate|number|1503676801000|券开始日期|
|endDate|number|1514735999000|券结束日期|
|points|number|14|积分|
|ruleDesc|string||规则描述|
|ruleId|string||规则id|
|templateId|string||券模版id|
|title|string||券title|
|type|string||券类型 GOODS/ITEM/ALL|
|value|number|1|券面值|
|status|string|INVALID,AVAILABLE,UNAVAILABLE,NONE|过期，可用，已领，已领完|


 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
| code | String | 11000000 |  |
| message | String | |异常信息|




- **示例**

入参示例: 
```json
{
	"ruleId":"59e5a2436b46697bce372cb7",
	"customerCode":"00000738-0E78-4A5E-B9DA-F0617CAB5748"
}
```

返回结果
```json
{
    "beginDate": 1503676801000,
    "endDate": 1514735999000,
    "points": 14,
    "ruleDesc": "每人限领1张，",
    "ruleId": "59e5a2436b46697bce372cb7",
    "status": "AVAILABLE",
    "templateId": "59a0cdd7474223625e7f9b01",
    "title": "线下活动推广品类糖尿病券满100减90",
    "type": "GOODS",
    "value": 90
}
```

 **NOTICE**  
无

 
---


## 交易

### 1. 【商品】判断商品积分库存

- **接口描述**  
> 根据商品编码数量，渠道和会员检查积分和库存

- **接口信息**  
> **接口地址：** {serviceUrl}/order/integralOrderService/calcPointsAndStock  
> **提交方式：** POST,GET  
> **方法名称：** calcPointsAndStock 

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|goods|object|是|商品对象|
|goods.ruleId|string|是|规则编码|
|goods.quantity|string|是|商品数量|
|channelCode|string|是|渠道编码|
|customerCode|string|是|会员编号|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
||string|true|正常的返回结果|


 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
| code | String | 11000000 |  |
| message | String | |异常信息|




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



### 2. 【商品】创建订单

- **接口描述**  
> 创建订单

- **接口信息**  
> **接口地址：** {serviceUrl}/order/integralOrderService/createGoodsOrder  
> **提交方式：** POST  
> **方法名称：** createGoodsOrder 

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|order|object|是|订单对象|
|order.channelCode|string|是|渠道编码|
|order.channelServiceMode|string|是|服务模式 B2C O2O|
|order.customerCode|string|是|会员编号|
|order.deliveryArea|string|否|服务模式B2C 必填 配送区域 COUNTRY：全国；O2O:self:自提|
|order.deliveryType|string|否|服务模式B2C 必填 配送方式公司 ytoexpress|
|order.freightAmount|string|否|服务模式B2C 必填 运费|
|order.orderNote|string|否|订单备注|
|order.goodsList|array|是|订单商品列表|
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
|order.contact.address.cityName|string|是|收货人地址市名称|O2O:
|order.contact.address.districtCode|string|是|收货人地址区编码|
|order.contact.address.districtName|string|是|收货人地址区名称|


-  **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
||string|true|正常的返回结果|


 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
| code | String | 11000000 |  |
| message | String | |异常信息|




- **示例**

入参示例: 
```json
{
	"order":{
		"channelCode":"JFM_6369",
		"channelServiceMode":"B2C",
		"customerCode":"647958c21f03445a9bb8fbcadfc82f30",
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
                "ruleId": "59917cb46b46692c9051c4b2",
                "quantity": 1
            }
        ],
        "orderNote":"222"
	}
}
```

返回结果
```json
"JFM20170816636903100005"
```

 **NOTICE**  
无

 
---


### 3. 【券】创建订单

- **接口描述**  
> 创建积分兑券订单（不实际创建订单）

- **接口信息**  
> **接口地址：** {serviceUrl}/order/integralOrderService/createCouponOrder  
> **提交方式：** POST  
> **方法名称：** createCouponOrder 

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|order|object|是|订单对象|
|order.channelCode|string|是|渠道编码|
|order.customerCode|string|是|会员编号|
|order.ruleIds|array|是|规则id列表|




-  **响应结果**


 正常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
||string|true|正常的返回结果|


 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
| code | String | 11000000 |  |
| message | String | |异常信息|




- **示例**

入参示例: 
```json
{
   "order":{
       "customerCode":"00000738-0E78-4A5E-B9DA-F0617CAB5748",
       "channelCode":"JFM_6369",
       "ruleIds":[
           "59e5a2436b46697bce372cb7"
       ]
   }
}
```

返回结果
```json
"59e7fb24cff77324ec356c0b"
```

 **NOTICE**  
无

 
---





## 历史记录

### 1. 【商品】查询兑换记录 

- **接口描述**  
> 通过会员编号和凭证编码查询兑换记录

- **接口信息**  
> **接口地址：** {serviceUrl}/exchange/integralExchangeHistoryService/queryCustomerExchangeDataByVoucherNumbers  
> **提交方式：** POST  
> **方法名称：** queryCustomerExchangeDataByVoucherNumbers 


- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|customerCode|string|是|会员编号|
|voucherNumbers[i]|string|是|订单编号或者券编号|


-  **响应结果** 


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
||string|true|正常的返回结果|


 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
| code | String | 11000000 |  |
| message | String | |异常信息|




- **示例**

入参示例: 
```json
{
	"customerCode":"647958c21f03445a9bb8fbcadfc82f30",
	"voucherNumbers":[
		"JFM20170815636903100001"
		]
}
```

返回结果
```json
[
    {
        "channelCode": "JFM_6369",
        "code": "1000971",
        "createTime": 1502792807000,
        "points": 101,
        "price": 7.5,
        "quantity": 1,
        "ruleType": 0,
        "voucherumber": "JFM20170815636903100001"
    }
]
```

 **NOTICE**  
无

 
---


### 2. 【券】查询兑换记录 

- **接口描述**  
> 通过会员编号查询券兑换记录

- **接口信息**  
> **接口地址：** {serviceUrl}/exchange/integralExchangeHistoryService/queryCouponExchangeHistory  
> **提交方式：** POST  
> **方法名称：** queryCouponExchangeHistory  


- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|customerCode|string|是|会员编号|
|page|int|是|当前页|
|size|int|是|每页大小|



-  **响应结果** 


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|[i].beginDate|number|1508428801000|开始时间|
|[i].endDate|number|1508221508000|结束时间|
|[i].createTime|number|1508221508000|领取时间|
|[i].ruleId|string|59e5a2436b46697bce372cb7|规则id|
|[i].templateId|string|59a0cdd7474223625e7f9b01|券模版id|
|[i].couponCode|string|309257548417|券号|
|[i].points|number||单个积分|
|[i].quantity|number|1|兑换数量|
|[i].redirectUrl|string|http://www.baidu.com|券跳转url|
|[i].title|string|满100减90|标题|
|[i].ruleDesc|string||规则描述|
|[i].desc|string||描述|
|[i].type|string|ALL,GOODS,ITEM,BATCH_ITEM|整单券,组合,单品,批量单品|
|[i].status|string|AVAILABLE,LOCKED,USED,EXPIRED|可用,锁定,已使用,失效|
|[i].ruleType|string|COUPON|券|
|[i].value|number|90|券面值|



 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
| code | String | 11000000 |  |
| message | String | |异常信息|




- **示例**

入参示例: 
```json
{
	"customerCode":"00000738-0E78-4A5E-B9DA-F0617CAB5748",
	"page":1,
	"size":10
}
```

返回结果
```json
[
    {
        "beginDate": 1508428801000,
        "channelCode": "JFM_6369",
        "createTime": 1508221508000,
        "desc": "每人限领1张，",
        "endDate": 1508687999000,
        "points": 14,
        "quantity": 1,
        "redirectUrl": "http://www.baidu.com",
        "ruleDesc": "",
        "ruleId": "59e5a2436b46697bce372cb7",
        "ruleType": "COUPON",
        "status": "AVAILABLE",
        "templateId": "59a0cdd7474223625e7f9b01",
        "title": "线下活动推广品类糖尿病券满100减90",
        "type": "GOODS",
        "value": 90
    },
    {
        "channelCode": "JFM_6369",
        "createTime": 1508221508000,
        "points": 14,
        "quantity": 1,
        "redirectUrl": "http://www.baidu.com",
        "ruleId": "59e5a2436b46697bce372cb7",
        "ruleType": "COUPON",
        "title": "线下活动推广品类糖尿病券满100减90"
    }
]
```

 **NOTICE**  
无

 
---


