# 积分商城 API
Java API
标签: 【silk-road】【栾锋】

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


