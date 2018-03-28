# 限时抢购 API
Java API
标签: 【flash-sale】【栾锋】

version 1.0.0



- **服务地址：**  

|环境|项目|调用HOST|
|:----:|:----|:----|:----|
|开发环境|flash-sale|http://192.168.7.41:9020|http://192.168.7.41:9020/rest|
|测试环境|flash-sale|http://silk-road-te.yifengx.com|http://silk-road-te.yifengx.com/rest|
|生产环境|flash-sale|||


---

## 【star】- 点亮   

### 1. 【star】查询会员点亮记录  

- **接口描述**  
> 通过会员编号，抢购商品id 查询某会员某商品点亮记录

- **接口信息**  
> **接口地址：** /star/flashStarService/queryStar  
> **提交方式：** POST  
> **方法名称：** queryStar 

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|flashGoodsId|string|是|抢购商品id|
|customerCode|string|是|会员编号|
|pageNo|int|是|页码 |
|pageSize|int|是|每页大小|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|[i].id|string||点亮记录id|
|[i].flashGoodsId|string||被点亮商品id|
|[i].starSource|string||点亮操作人|
|[i].starTarget|string||被点亮人|
|[i].createTime|number||点亮时间|
|[i].starHeadImg|string||点亮人头像地址|


 异常

|名称|类型|示例值|描述|
|:----|:----:|:----:|:----:|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"flashGoodsId":"1111",
	"customerCode":"0c40eae2319842bf802788da69ea8336",
	"pageNo":1,
	"pageSize":10
}
```

返回结果
```json
[
    {
        "comeFrom": "MSM_YFJX",
        "createTime": 1521684691000,
        "flashGoodsId": "1111",
        "id": "5ab310d3cff7732a08649cf9",
        "starHeadImg": "https://wx.qlogo.cn/mmopen/vi_32/Q0j4TwGTfTLTM4hZsQ4qhnAqJpWrbsY4VZBoBzia9NR34E2S8jic8CGHu4XliawiboUqMbmeXgQElRlyoT5OXGn86g/132",
        "starSource": "0c40eae2319842bf802788da69ea8336",
        "starTarget": "0c40eae2319842bf802788da69ea8336"
    }
]
```

 **NOTICE**  
无

 
---




### 2. 【star】点亮会员某商品



- **接口描述**  
> 新增点亮记录

- **接口信息**  
> **接口地址：** /star/flashStarService/addGoodsStar    
> **提交方式：** POST  
> **方法名称：** addGoodsStar 

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|flashGoodsId|string|是|被点亮商品id|
|starSource|string|是|点亮操作人|
|starTarget|string|是|被点亮人|
|starHeadImg|string|是|点亮人头像地址|
|comeFrom|string|是|来源  MSM_YFJX, MSM_WXM,|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|||||



 异常

|名称|类型|示例值|描述|
|:----|:----:|:----:|:----:|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
    "record": {
        "comeFrom": "MSM_YFJX",
        "flashGoodsId": "1111",
        "starHeadImg": "https://wx.qlogo.cn/mmopen/vi_32/Q0j4TwGTfTLTM4hZsQ4qhnAqJpWrbsY4VZBoBzia9NR34E2S8jic8CGHu4XliawiboUqMbmeXgQElRlyoT5OXGn86g/132",
        "starSource": "0c40eae2319842bf802788da69ea8336",
        "starTarget": "0c40eae2319842bf802788da69ea8336"
    }
}
```

返回结果
```json
null
```

 **NOTICE**  
无

 
---


## 【goods】- 抢购商品服务  

### 1. 【goods】查询抢购活动段  

- **接口描述**  
> 根据渠道查询时间段

- **接口信息**  
> **接口地址：** /goods/flashGoodsService/queryActivity    
> **提交方式：** POST  
> **方法名称：** queryActivity 

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|channel|string|是|渠道 MSM_YFJX|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|activities|array||活动列表|
|activities[i].flashTimePeriod|int||时间段|
|activities[i].status|string||状态 COMING:未开始 IN:活动中 FINISH:结束|
|nowTime|number||当前时间|



 异常

|名称|类型|示例值|描述|
|:----|:----:|:----:|:----:|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"channel":"MSM_YFJX"
}
```

返回结果
```json
{
    "activities": [
        {
            "flashTimePeriod": 6,
            "status": "FINISH"
        },
        {
            "flashTimePeriod": 9,
            "status": "FINISH"
        },
        {
            "flashTimePeriod": 15,
            "status": "IN"
        }
    ],
    "nowTime": 1521702396907
}
```

 **NOTICE**  
无

 
---

### 2. 【goods】分页查询某时段抢购商品  

- **接口描述**  
> 根据渠道查询时间段

- **接口信息**  
> **接口地址：** /goods/flashGoodsService/queryGoodsPage    
> **提交方式：** POST  
> **方法名称：** queryGoodsPage 

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|goods|object|是|商品对象|
|goods.flashTimePeriod|int|15|秒杀时间段|
|channel|string|MSM_YFJX|渠道编号|
|pageNo|int|是|页码 |
|pageSize|int|是|每页大小|

- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|[i].availableStock|int||可用库存|
|[i].id|string||id|
|[i].goodsCode|string||商品编码|
|[i].goodsName|string||商品名称|
|[i].flashPrice|string||商品秒杀价格|
|[i].flashTimePeriod|string||时段|
|[i].flashStartTime|string||开始时间|
|[i].flashEndTime|string||结束时间|
|[i].flashLimitMin|string||最小限购|
|[i].flashLimitMax|string||最多限购|
|[i].flashPrivilegeNum|string||需要点亮人数|
|[i].status|string||状态 ENABLE DISABLE|




 异常

|名称|类型|示例值|描述|
|:----|:----:|:----:|:----:|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"goods":{
		"flashTimePeriod":15
	},
	"channel":"MSM_YFJX",
	"pageNo":1,
	"pageSize":10
}
```

返回结果
```json
[
    {
        "availableStock": 60,
        "flashCycleDay": 3,
        "flashEndTime": 1521993599000,
        "flashLimitAccount": "THIRD",
        "flashLimitMax": 5,
        "flashLimitMin": 2,
        "flashLimitTimes": 3,
        "flashPrice": 0.5,
        "flashPrivilegeNum": 5,
        "flashStartTime": 1521648013000,
        "flashTimePeriod": 15,
        "goodsCode": "1014791",
        "goodsName": "开塞露 20毫升 安徽新和成皖南药业有",
        "id": "3333",
        "status": "ENABLE"
    }
]
```

 **NOTICE**  
无

 
---


### 3. 【goods】查询抢购商品详细信息  



## 【order】 - 抢购订单  

### 1. 【order】创建抢购商品订单  



