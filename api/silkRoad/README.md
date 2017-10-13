# 积分商城 API
Java API
标签: 【silk-road】【栾锋】

version 1.0.0



- **服务地址：**  

|环境|项目|原HOST|调用HOST|
|:----:|:----|:----|:----|
|开发环境|silk-road|http://192.168.7.41:9020|http://192.168.7.41:9020/rest|
|开发环境|member-open|http://192.168.7.68:9040|http://192.168.7.41:9020/proxy|
|开发环境|query|http://192.168.7.67:9060|http://192.168.7.41:9020/proxy|
|开发环境|trade|http://192.168.7.68:9020|http://192.168.7.41:9020/proxy|
|开发环境|coupon|http://192.167.7.62:8081|http://192.168.7.41:9020/proxy|
|  |  |  |  |
|测试环境|silk-road|||
|测试环境|member-open|||
|测试环境|query|||
|测试环境|trade|||
|测试环境|coupon|111||
|  |  |  |  |
|生产环境|silk-road|||
|生产环境|member-open|||
|生产环境|query|||
|生产环境|trade|||
|生产环境|coupon|111|111|


---

## 会员 【member-open】  

### 1. 【用户】通过openid/unionid comefrome查询会员  

- **接口描述**  
> 通过openid/unionid comefrome查询会员

- **接口信息**  
> **接口地址：** /openx/memberopen/customerInfoService/getCustomerByRefId  
> **提交方式：** POST  
> **方法名称：** getCustomerByRefId 

- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----|
|comeFrom|string|是|会员来源，对应业务中的顶级渠道|
|refId|string|是|关联ID，微信中对应为openid或unionid，杏仁为患者ID|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----:|:----:|:----|:----|
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
|:----:|:----:|:----:|:----:|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
    "comeFrom":"YFJX",
    "relateFrom":"MINIPG",
    "refId":"xxxxXXXX",
    "refId2":null
}
```

返回结果
```json
{
    "atStore": "5144",
    "cMobile": "13569863169",
    "cardCode": "M171011172604017",
    "comeFrom": "YFJX",
    "companyCode": "100B",
    "createTime": 1507713964000,
    "creator": "sys",
    "creatorName": "系统自动",
    "customerId": "3f0e26708e25434582fe098888c94569",
    "mobile": "13569863169",
    "modifier": "sys",
    "modifierName": "系统自动",
    "modifyTime": 1507713964000,
    "name": "未知",
    "name1": "未知",
    "relateAccountModel": {
        "comeFrom": "MINIPG",
        "createTime": 1507714765000,
        "creator": "系统自动",
        "customerId": "3f0e26708e25434582fe098888c94569",
        "id": "59dde6cc06776508e8cd1113",
        "isDelete": "0",
        "refId": "xxxxXXXX",
        "refId2": "fdsafsfa",
        "relateFrom": "YFJX"
    },
    "state": "EFC",
    "store": "5144"
}
```

 **NOTICE**  
无

 
---

### 2. 【收货地址】通过会员编号查询收货地址  

- **接口描述**  
> 通过会员编号查询收货地址

- **接口信息**  
> **接口地址：** /openx/memberopen/deliveryAddressService/listAddressByCustomerId  
> **提交方式：** POST  
> **方法名称：** listAddressByCustomerId  

- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----|
|customerId|string|是|会员编号|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----:|:----:|:----|:----|
|{i}.customerId|string|647958c21f03445a9bb8fbcadfc82f30|会员编号|
|{i}.uuid|string|419338db9358438ab59a7243bed3969c|收货人uuid|
|{i}.deliverySource|string|来源|顶级渠道|
|{i}.province|string|430000|省编码|
|{i}.provinceName|string|湖南省|省名称|
|{i}.city|string|430100|城市编码|
|{i}.cityName|string|长沙市|城市名称|
|{i}.district|string|430104|先/区编码|
|{i}.districtName|string|岳麓区|县/区名称|
|{i}.address|string|金洲大道68号|详细地址|
|{i}.storeCode|string|XINGREN_6369|渠道编码|
|{i}.idCard|string|130523197610281210||
|{i}.isDefault|string|1|是否默认收货地址|
|{i}.latitude|number|39.96583|纬度|
|{i}.longitude|number|116.391621|经度|
|{i}.linkPerson|string|xx|收货人姓名|
|{i}.linkPhone|string|18075389282|收货人联系方式|
|{i}.streetNumber|string|12343|街道编号|
|{i}.streetName|string|OTO|街道名称|




 异常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
    "customerId":"647958c21f03445a9bb8fbcadfc82f30"
}
```

返回结果
```json
[
    {
        "address": "岳麓区hahaha",
        "city": "430100",
        "cityName": "长沙市",
        "createDate": 1505289916000,
        "customerId": "647958c21f03445a9bb8fbcadfc82f30",
        "deliverySource": "O2O",
        "district": "430104",
        "districtName": "岳麓区",
        "idCard": "130523197610281210",
        "isDefault": "1",
        "latitude": 39.96583,
        "linkPerson": "xx",
        "linkPhone": "18075389282",
        "longitude": 116.391621,
        "province": "430000",
        "provinceName": "湖南省",
        "storeCode": "XINGREN_6369",
        "streetName": "OTO",
        "streetNumber": "12343",
        "uuid": "419338db9358438ab59a7243bed3969c"
    },
    {
        "address": "岳麓区某某某",
        "city": "430100",
        "cityName": "长沙市",
        "createDate": 1505290032000,
        "customerId": "647958c21f03445a9bb8fbcadfc82f30",
        "deliverySource": "O2O",
        "district": "430104",
        "districtName": "岳麓区",
        "idCard": "130523197610281210",
        "isDefault": "0",
        "latitude": 39.96583,
        "linkPerson": "xx",
        "linkPhone": "18075389282",
        "longitude": 116.391621,
        "province": "430000",
        "provinceName": "湖南省",
        "storeCode": "XINGREN_6369",
        "streetName": "OTO",
        "streetNumber": "12343",
        "uuid": "2bbd50695b83478799ab30298ab8fc65"
    },
    {
        "address": "杜鹃路12",
        "city": "430100",
        "cityName": "长沙市",
        "createDate": 1504861859000,
        "customerId": "647958c21f03445a9bb8fbcadfc82f30",
        "deliverySource": "WX",
        "district": "430104",
        "districtName": "岳麓区",
        "isDefault": "0",
        "latitude": 0,
        "linkPerson": "张三123",
        "linkPhone": "13725578963",
        "longitude": 0,
        "province": "430000",
        "provinceName": "湖南省",
        "uuid": "b797efae952641838f35c74f1c7b2d58"
    },
    {
        "address": "杜鹃路12",
        "city": "430100",
        "cityName": "长沙市",
        "createDate": 1504861812000,
        "customerId": "647958c21f03445a9bb8fbcadfc82f30",
        "deliverySource": "WX",
        "district": "430104",
        "districtName": "岳麓区",
        "isDefault": "0",
        "latitude": 0,
        "linkPerson": "张三123",
        "linkPhone": "13725578963",
        "longitude": 0,
        "province": "430000",
        "provinceName": "湖南省",
        "uuid": "75c32160aeb642d9a15bdba62b60402f"
    }
]
```

 **NOTICE**  
无

 
---

### 2. 【收货地址】创建会员收货地址  

- **接口描述**  
> 创建会员收货地址

- **接口信息**  
> **接口地址：** /openx/memberopen/deliveryAddressService/createAddress  
> **提交方式：** POST  
> **方法名称：** createAddress  

- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----|
|customerId|string|是|会员编号|
|deliverySource|string|是|收货地址来源 顶级渠道名称 YFJX|
|province|string|是|省编码|
|city|string|是|市编码|
|district|string|是|区编码|
|linkPerson|string|是|联系人姓名|
|linkPhone|string|是|联系人电话|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----:|:----:|:----|:----|
|uuid|string|053ee1b930b24f1b83979aedc1ffc653|收货地址主键|




 异常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"deliveryAddr":{
		 "address": "杜鹃路12",
    	"city": "430100",
    	"customerId": "647958c21f03445a9bb8fbcadfc82f30",
    	"deliverySource": "WX",
    	"district": "430104",
    	"linkPerson": "张三",
    	"linkPhone": "13725578963",
    	"province": "430000"
	}
}
```

返回结果
```json
"92db5a54c0b64d7aa698d9a30fc767e2"
```

 **NOTICE**  
无

 
---



## query服务  【query】  

### 1. 【搜索】联想词

### 2. 【搜索】关键词搜索

- **接口描述**  


- **接口信息**  
> **接口地址：** /openx/query/goodsQueryService/listGoodsByKeyWords    
> **提交方式：** POST  
> **方法名称：** listGoodsByKeyWords 

- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----|
|channelCode|string|是|渠道编码|
|searchCriteria|object|是|关键字 匹配度|
|searchCriteria.keyword|string|否|搜索关键字|
|searchCriteria.minMatch|string|是|搜索匹配度75%|
|searchCondition|object|是|查询条件|
|searchCondition.recommendIndices|array|是|推荐指数列表[1,2]|
|searchCondition.minChannelPrice|number|否|最低渠道价|
|searchCondition.maxChannelPrice|number|否|最高渠道价|
|searchCondition.categoryCodes|array|否|渠道栏目编码列表['','']|
|pageNo|int|是|当前页 1|
|pageSize|int|是|每页大小|




- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----:|:----:|:----|:----|
|customerId|string|598bc0f542559b20787e62e6|会员编号，唯一标识|


 异常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
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


### 3. 【商品】

### 4. 【物流】根据渠道查询可用物流方式

- **接口描述**  
根据收发城市信息及渠道信息、获取可用的物流信息  规则：①、在未拆单的情况下，直接去load可用物流信息。 ②、拆单情况下获取可用物流取2个城市的并集信息中价格最低物流。

- **接口信息**  
> **接口地址：** /openx/query/logisticsQueryService/listDeliveryType    
> **提交方式：** POST  
> **方法名称：** listDeliveryType 

- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----|
|topChannelCode|string|是|顶级渠道|
|receiverProvinceCode|string|是|收货人省级编码|
|receiverCityCode|是|收货人市级编码|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----:|:----:|:----|:----|
|{i}.default|boolean|true|是否默认|
|{i}.deliveryTypeCode|string|NORMAL,REAL_TIME,URGENT|配送类型编码 |
|{i}.deliveryTypeName|string|普通，实时，加急|配送类型描述|
|{i}.price|number|5|配送运费|

 异常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"topChannelCode":"YFJX",
	"receiverProvinceCode":"430000",
	"receiverCityCode":"430100"
}
```

返回结果
```json
[
    {
        "default": true,
        "deliveryTypeCode": "NORMAL",
        "deliveryTypeName": "普通",
        "price": 6
    },
    {
        "default": false,
        "deliveryTypeCode": "REAL_TIME",
        "deliveryTypeName": "实时",
        "price": 5
    },
    {
        "default": false,
        "deliveryTypeCode": "URGENT",
        "deliveryTypeName": "加急",
        "price": 10
    }
]
```

 **NOTICE**  
无

 
---


## 交易 【trade】  



## 券服务  【coupon】  

