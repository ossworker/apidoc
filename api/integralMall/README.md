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
> **接口地址：** {serviceUrl}/rest/goods/integralGoodsService/queryGoods  
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
> **接口地址：** {serviceUrl}/rest/goods/integralGoodsService/queryGoodsDetail  
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
> **接口地址：** {serviceUrl}/rest/coupon/integralCouponService/queryCoupons  
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
> **接口地址：** {serviceUrl}/rest/coupon/integralCouponService/queryCouponDetail   
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
|redirectUrl|string||跳转url|


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
    "redirectUrl": "http://www.baidu.com",
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
> **接口地址：** {serviceUrl}/rest/order/integralOrderService/calcPointsAndStock  
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
		"quantity":2
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
> **接口地址：** {serviceUrl}/rest/order/integralOrderService/createGoodsOrder  
> **提交方式：** POST  
> **方法名称：** createGoodsOrder 

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|order|object|是|订单对象|
|order.topChannelCode|string|是|顶级渠道编码|
|order.channelCode|string|是|渠道编码|
|order.customerCode|string|是|会员编号|
|order.freightAmount|string|否|服务模式B2C 必填 运费|
|order.remark|string|否|订单备注|
|order.goodsList|array|是|订单商品列表|
|order.goodsList[i].ruleId|string|是|订单商品规则id|
|order.goodsList[i].quantity|number|是|商品数量|
|order.logisticInfo|object|是|物流信息|
|order.logisticInfo.deliveryType|string|是|物流类型NORMAL普通 URGENT加急 REAL_TIME实时 SELF_PICK自提  |
|order.logisticInfo.name|string|是|收货人姓名|
|order.logisticInfo.phone|string|是|收货人手机号码|
|order.logisticInfo|object|是|收货人地址|
|order.logisticInfo.detailAddress|string|是|收货人详细地址|
|order.logisticInfo.provinceCode|string|是|收货人地址省编码|
|order.logisticInfo.provinceName|string|是|收货人地址省名称|
|order.logisticInfo.cityCode|string|是|收货人地址市编码|
|order.logisticInfo.cityName|string|是|收货人地址市名称|
|order.logisticInfo.districtCode|string|是|收货人地址区编码|
|order.logisticInfo.districtName|string|是|收货人地址区名称|


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
		"topChannelCode":"JFM",
		"channelCode":"JFM_6369",
		"customerCode":"647958c21f03445a9bb8fbcadfc82f30",
		"freightAmount":0.00,
		"logisticInfo": {
			"deliveryType":"NORMAL",
            "name": "蒋玲娥1",
            "phone": "18673107936",
                "detailAddress": "中房F联邦",
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
            
        },
        "goodsList": [
            {
                "ruleId": "59917cb46b46692c9051c4b2",
                "quantity": 1
            }
        ],
        "remark":"222"
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
> **接口地址：** {serviceUrl}/rest/order/integralOrderService/createCouponOrder  
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

### 1. 【兑换列表】查询兑换记录 

- **接口描述**  
> 通过会员编号查询兑换记录

- **接口信息**  
> **接口地址：** {serviceUrl}/rest/history/integralHistoryService/queryHistoryDataPage  
> **提交方式：** POST  
> **方法名称：** queryHistoryDataPage 


- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|customerCode|string|是|会员编号|
|pageNo|int|是|页码|
|pageSize|int|是|每页大小|


-  **响应结果** 


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|[i].channelCode|string||渠道编号|
|[i].costMoney|number||消耗金钱|
|[i].costPoints|number||消耗积分|
|[i].createTime|number||创建时间|
|[i].exchangeType|string|EXCHANGE_COUPON,EXCHANGE_COUPON,PRIZE_GOODS,PRIZE_COUPON,PRIZE_POINTS,PRIZE_VIRTUAL|兑换类型|
|[i].id|string||历史记录id|
|[i].quantity|number|1|数目|
|[i].voucherumber|string|||


 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
| code | String | 11000000 |  |
| message | String | |异常信息|




- **示例**

入参示例: 
```json
{
	"pageNo":1,
	"pageSize":10,
	"customerCode":"647958c21f03445a9bb8fbcadfc82f30"
}
```

返回结果
```json
[
    {
        "channelCode": "JFM_6369",
        "costMoney": 0,
        "costPoints": 30,
        "createTime": 1503126770000,
        "exchangeType": "EXCHANGE_COUPON",
        "id": "5997e4f16b46692a059e2b20",
        "quantity": 1,
        "voucherumber": "309128139662"
    },
    {
        "channelCode": "JFM_6369",
        "costMoney": 0,
        "costPoints": 30,
        "createTime": 1503125833000,
        "exchangeType": "EXCHANGE_COUPON",
        "id": "5997e1496b46692a059e2b1f",
        "quantity": 1,
        "voucherumber": "307658905047"
    },
    {
        "channelCode": "JFM_5857",
        "costMoney": 0,
        "costPoints": 30,
        "createTime": 1503115630000,
        "exchangeType": "EXCHANGE_COUPON",
        "id": "5997b96dcff77321d8d4fd85",
        "quantity": 1,
        "voucherumber": "307658905046"
    },
    {
        "channelCode": "JFM_5857",
        "costMoney": 0,
        "costPoints": 30,
        "createTime": 1503115403000,
        "exchangeType": "EXCHANGE_COUPON",
        "id": "5997b88bcff77321d8d4fd84",
        "quantity": 1,
        "voucherumber": "304702931525"
    },
    {
        "channelCode": "JFM_6369",
        "costMoney": 0.1,
        "costPoints": 5,
        "createTime": 1503113414000,
        "exchangeType": "EXCHANGE_GOODS",
        "id": "5997b0c56b46694c6ec17c52",
        "quantity": 1,
        "voucherumber": "JFM20170819636903100008"
    },
    {
        "channelCode": "JFM_6369",
        "costMoney": 0.1,
        "costPoints": 5,
        "createTime": 1503112666000,
        "exchangeType": "EXCHANGE_GOODS",
        "id": "5997add96b46694c6ec17c51",
        "quantity": 1,
        "voucherumber": "JFM20170819636903100007"
    },
    {
        "channelCode": "JFM_6369",
        "costMoney": 0.1,
        "costPoints": 5,
        "createTime": 1503106924000,
        "exchangeType": "EXCHANGE_GOODS",
        "id": "5997976b6b46694c6ec17c50",
        "quantity": 1,
        "voucherumber": "JFM20170819636903100006"
    },
    {
        "channelCode": "JFM_6369",
        "costMoney": 2,
        "costPoints": 9,
        "createTime": 1502939169000,
        "exchangeType": "EXCHANGE_GOODS",
        "id": "599508216b4669362978a5ff",
        "quantity": 1,
        "voucherumber": "JFM20170817636903100001"
    },
    {
        "channelCode": "JFM_6369",
        "costMoney": 2,
        "costPoints": 9,
        "createTime": 1502879636000,
        "exchangeType": "EXCHANGE_GOODS",
        "id": "59941f936b4669362978a5fe",
        "quantity": 1,
        "voucherumber": "JFM20170816636903100006"
    },
    {
        "channelCode": "JFM_6369",
        "costMoney": 2,
        "costPoints": 9,
        "createTime": 1502872547000,
        "exchangeType": "EXCHANGE_GOODS",
        "id": "5993f578cff7732cd895b6be",
        "quantity": 1,
        "voucherumber": "JFM20170816636903100005"
    }
]
```

 **NOTICE**  
无

 
---


### 2. 【兑换详情】查询兑换记录 

- **接口描述**  
> 通过会员编号查询券兑换记录

- **接口信息**  
> **接口地址：** {serviceUrl}/rest/history/integralHistoryService/queryHistoryDetail  
> **提交方式：** POST  
> **方法名称：** queryHistoryDetail  


- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|customerCode|string|是|会员编号|
|id|string|是|兑换记录id|



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


## 活动

### 1. 【抽奖】抽奖活动查询 

- **接口描述**  
> 通过活动id查抽奖活动

- **接口信息**  
> **接口地址：** {serviceUrl}/rest/activity/lotteryService/queryLottery   
> **提交方式：** POST  
> **方法名称：** queryLottery 


- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|actId|string|否|不填写则为最新活动|


-  **响应结果** 


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|actId|string||活动id|
|actName|string||活动名称|
|actDesc|string||活动描述|
|actType|string||NINE_GRID九宫格|
|costPoints|number||消耗积分/次|
|limitNum|number||限制次数|
|limitType|string||限制类别 DAY,MONTH,ALL|
|createTime|number||创建时间|
|prizeList[i].id|string||奖品id|
|prizeList[i].imgUrl|string||奖品图片|
|prizeList[i].prizeType|string|PRIZE_GOODS,PRIZE_COUPON,\n PRIZE_POINTS,PRIZE_VIRTUAL|奖品类型|
|prizeList[i].prizePrice|number||奖品渠道价|
|prizeList[i].prizeName|string||奖品名称|
|prizeList[i].prizeDesc|string||奖品描述|


 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
| code | String | 11000000 |  |
| message | String | |异常信息|




- **示例**

入参示例: 
```json
{
	"actId":null
}
```

返回结果
```json
{
    "actDesc": "1.送阿的房价阿凡达啊飞 \n 2.Daod fad fda aldfld ",
    "actId": "5a39bc106b46692b454eda35",
    "actName": "九宫格抽奖活动",
    "actType": "NINE_GRID",
    "costPoints": 5,
    "createTime": 1510329600000,
    "endTime": 1514649540000,
    "limitNum": 3,
    "limitType": "DAY",
    "prizeList": [
        {
            "id": "11111",
            "imgUrl": "http://yf-base.oss-cn-shenzhen.aliyuncs.com/product/1000001/1000001a1.jpg",
            "prizeDesc": "奖品1描述",
            "prizeName": "奖品1",
            "prizeType": "PRIZE_GOODS"
        },
        {
            "id": "22222",
            "imgUrl": "http://yf-base.oss-cn-shenzhen.aliyuncs.com/product/1000001/1000001a1.jpg",
            "prizeDesc": "奖品2描述",
            "prizeName": "奖品2",
            "prizeType": "PRIZE_COUPON"
        },
        {
            "id": "33333",
            "imgUrl": "http://yf-base.oss-cn-shenzhen.aliyuncs.com/product/1000001/1000001a1.jpg",
            "prizeDesc": "奖品3描述",
            "prizeName": "奖品3",
            "prizeType": "PRIZE_POINTS",
            "prizeValue": 10
        },
        {
            "id": "44444",
            "imgUrl": "http://yf-base.oss-cn-shenzhen.aliyuncs.com/product/1000001/1000001a1.jpg",
            "prizeDesc": "奖品4描述",
            "prizeName": "奖品4",
            "prizeType": "PRIZE_GOODS"
        },
        {
            "id": "55555",
            "imgUrl": "http://yf-base.oss-cn-shenzhen.aliyuncs.com/product/1000001/1000001a1.jpg",
            "prizeDesc": "奖品5描述",
            "prizeName": "谢谢参与",
            "prizeType": "PRIZE_SYSTEM"
        },
        {
            "id": "66666",
            "imgUrl": "http://yf-base.oss-cn-shenzhen.aliyuncs.com/product/1000001/1000001a1.jpg",
            "prizeDesc": "奖品6描述",
            "prizeName": "奖品6",
            "prizeType": "PRIZE_GOODS"
        },
        {
            "id": "77777",
            "imgUrl": "http://yf-base.oss-cn-shenzhen.aliyuncs.com/product/1000001/1000001a1.jpg",
            "prizeDesc": "奖品5描述",
            "prizeName": "奖品5",
            "prizeType": "PRIZE_VIRTUAL"
        },
        {
            "id": "88888",
            "imgUrl": "http://yf-base.oss-cn-shenzhen.aliyuncs.com/product/1000001/1000001a1.jpg",
            "prizeDesc": "奖品8描述",
            "prizeName": "谢谢参与",
            "prizeType": "PRIZE_SYSTEM"
        }
    ],
    "startTime": 1510329600000
}
```

 **NOTICE**  
无

 
---

### 2. 【抽奖】抽奖 

- **接口描述**  
> 会员抽奖

- **接口信息**  
> **接口地址：** {serviceUrl}/rest/activity/lotteryService/lottery   
> **提交方式：** POST  
> **方法名称：** lottery 


- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|actId|string|是|活动id|
|customerCode|string|是|会员编号|


-  **响应结果** 


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|prizeId|string||中奖奖品id|
|winning|boolean||是否中奖|
|code|string||中奖后返回商品编码/券编码/虚拟商品兑换码|


 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
| code | String | 11000000 |  |
| message | String | |异常信息|




- **示例**

入参示例: 
```json
{
	"actId":"5a39bc106b46692b454eda35",
	"customerCode":"647958c21f03445a9bb8fbcadfc82f30"
}
```

返回结果
```json
{
    "code": "ABCDE111111",
    "prizeId": "44444",
    "winning": true
}
```

 **NOTICE**  
无

 
---

### 3. 【抽奖】中奖商品 完善订单信息  

- **接口描述**  
> 完善订单信息 收货人信息

- **接口信息**  
> **接口地址：** {serviceUrl}/rest/activity/lotteryService/fillReceiver   
> **提交方式：** POST  
> **方法名称：** fillReceiver 


- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|customerCode|string|是|会员编号|
|orderCode|string|是|订单编号|
|logisticInfo.name|string|是|收货人姓名|
|logisticInfo.phone|string|是|收货人手机号码|
|logisticInfo|object|是|收货人地址|
|logisticInfo.detailAddress|string|是|收货人详细地址|
|logisticInfo.provinceCode|string|是|收货人地址省编码|
|logisticInfo.provinceName|string|是|收货人地址省名称|
|logisticInfo.cityCode|string|是|收货人地址市编码|
|logisticInfo.cityName|string|是|收货人地址市名称|
|logisticInfo.districtCode|string|是|收货人地址区编码|
|logisticInfo.districtName|string|是|收货人地址区名称|
|remark|string|是|订单备注 可为空|


-  **响应结果** 


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
    "customerCode": "647958c21f03445a9bb8fbcadfc82f30",
    "orderCode":"JFM2017122501100034",
    "logisticInfo": {
        "name": "蒋玲娥1",
        "phone": "18673107936",
        "detailAddress": "中房F联邦",
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
    },
    "remark": "周末请不要送货"
}
```

返回结果
```json

```

 **NOTICE**  
无

 
---


### 4. 【抽奖】抽奖剩余次数 

- **接口描述**  
> 会员抽奖

- **接口信息**  
> **接口地址：** {serviceUrl}/rest/activity/lotteryService/lotteryLeftTimes   
> **提交方式：** POST  
> **方法名称：** lotteryLeftTimes 


- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|actId|string|是|活动id|
|customerCode|string|是|会员编号|


-  **响应结果** 


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
||number||剩余抽奖次数|


 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
| code | String | 11000000 |  |
| message | String | |异常信息|




- **示例**

入参示例: 
```json
{
	"actId":"5a39bc106b46692b454eda35",
	"customerCode":"647958c21f03445a9bb8fbcadfc82f30"
}
```

返回结果
```json
1
```

 **NOTICE**  
无

 
---

### 5. 【抽奖】最新中奖记录 

- **接口描述**  
> 会员抽奖

- **接口信息**  
> **接口地址：** {serviceUrl}/rest/activity/lotteryService/queryLatestWinning   
> **提交方式：** POST  
> **方法名称：** queryLatestWinning 


- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|actId|string|是|活动id|
|customerCode|string|是|会员编号|


-  **响应结果** 


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|[i].name|string||中奖人姓名|
|[i].lotteryTime|number||中奖时间|
|[i].prize|object||中奖奖品|
|[i].prize.id|string||奖品id|
|[i].prize.imgUrl|string||奖品url|
|[i].prize.prizeDesc|string||奖品描述|
|[i].prize.prizeName|string||奖品名称|
|[i].prize.prizeType|string||奖品类型|


 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
| code | String | 11000000 |  |
| message | String | |异常信息|




- **示例**

入参示例: 
```json
{
	"actId":"5a39bc106b46692b454eda35",
	"lastTime":null
}
```

返回结果
```json
[
    {
        "lotteryTime": 1514445369811,
        "name": "张**",
        "prize": {
            "id": "77777",
            "imgUrl": "http://yf-base.oss-cn-shenzhen.aliyuncs.com/product/1000001/1000001a1.jpg",
            "prizeDesc": "奖品5描述",
            "prizeName": "奖品5",
            "prizeType": "PRIZE_VIRTUAL"
        }
    },
    {
        "lotteryTime": 1514445540880,
        "name": "张**",
        "prize": {
            "id": "11111",
            "imgUrl": "http://yf-base.oss-cn-shenzhen.aliyuncs.com/product/1000001/1000001a1.jpg",
            "prizeDesc": "奖品1描述",
            "prizeName": "奖品1",
            "prizePrice": 0.1,
            "prizeType": "PRIZE_GOODS"
        }
    }
]
```

 **NOTICE**  
无

 
---