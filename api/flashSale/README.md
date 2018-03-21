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

```

返回结果
```json

```

 **NOTICE**  
无

 
---




### 2. 【star】点亮会员某商品



- **接口描述**  
> 新增点亮记录

- **接口信息**  
> **接口地址：** /openx/memberopen/customerInfoService/getCustomerByRefId  
> **提交方式：** POST  
> **方法名称：** getCustomerByRefId 

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|comeFrom|string|是|会员来源，对应业务中的顶级渠道|
|relateFrom|string|是|MINIPG|
|refId|string|是|关联ID，微信中对应为openid，杏仁为患者ID|
|refId2|string|否|unionid|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|customerId|string|598bc0f542559b20787e62e6|会员编号，唯一标识|
|name|string|李四|会员姓名|
|cardCode|string|W123456985|卡号|
|mobile|string|13725579628|手机号码|
|birthday|number|20174566666|出生日期|
|sex|string|男,女|性别|
|status|string|EFC,FST,CNL|状态：正常,冻结,冻结|
|statusName|string|正常,冻结,冻结|状态名|



 异常

|名称|类型|示例值|描述|
|:----|:----:|:----:|:----:|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json

```

返回结果
```json

```

 **NOTICE**  
无

 
---


## 【goods】- 抢购商品服务  

### 1. 【goods】查询抢购活动段  


### 2. 【goods】分页查询某时段抢购商品  


### 3. 【goods】查询抢购商品详细信息  



## 【order】 - 抢购订单  

### 1. 【order】创建抢购商品订单  



