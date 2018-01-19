# 益丰精选 API
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
|开发环境|customer|http://192.168.7.40:8090|http://192.168.7.41:9020/proxy|
|  |  |  |  |
|测试环境|silk-road|http://silk-road-te.yifengx.com|http://silk-road-te.yifengx.com/rest|
|测试环境|member-open|http://member-open-te.yifengx.com|http://silk-road-te.yifengx.com/proxy|
|测试环境|query|http://ecp-query-te.yifengx.com|http://silk-road-te.yifengx.com/proxy|
|测试环境|trade|http://ecp-trade-te.yifengx.com|http://silk-road-te.yifengx.com/proxy|
|测试环境|coupon|http://coupon-te.yifengx.com|http://silk-road-te.yifengx.com/proxy|
|测试环境|customer|http://customer-te.yifengx.com|http://silk-road-te.yifengx.com/proxy|
|  |  |  |  |
|生产环境|silk-road|||
|生产环境|member-open|||
|生产环境|query|||
|生产环境|trade|||
|生产环境|coupon|111|111|
|生产环境|customer|111|111|


---

## 【member-open】-proxy 会员   

### 1. 【用户】通过openid/unionid comefrome查询会员  

- **接口描述**  
> 通过openid/unionid comefrome查询会员

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
{
    "comeFrom":"YFJX",
    "relateFrom":"MINIPG",
    "refId":"o3F_q0FWoE-wQFRvvbDTtx88XsGU",
    "refId2":"oXZ0xwUEgUFZDfegCyjAd17_CYf0"
}
```

返回结果
```json
{
    "atStore": "5144",
    "cMobile": "15116451260",
    "cardCode": "M171031142852489",
    "comeFrom": "YFJX",
    "companyCode": "100B",
    "createTime": 1509431332000,
    "creator": "sys",
    "creatorName": "系统自动",
    "customerId": "ac1bf6b19ddf40619b9a4fc54d428153",
    "mobile": "15116451260",
    "modifier": "sys",
    "modifierName": "系统自动",
    "modifyTime": 1509431332000,
    "name": "未知",
    "name1": "未知",
    "relateAccountModel": {
        "comeFrom": "MINIPG",
        "createTime": 1509431332000,
        "creator": "sys",
        "customerId": "ac1bf6b19ddf40619b9a4fc54d428153",
        "id": "59f8182406776508e8cd114f",
        "isDelete": "0",
        "refId": "o3F_q0FWoE-wQFRvvbDTtx88XsGU",
        "refId2": "oXZ0xwUEgUFZDfegCyjAd17_CYf0",
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
|:----|:----:|:----:|:----|
|customerId|string|是|会员编号|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|[i].customerId|string|647958c21f03445a9bb8fbcadfc82f30|会员编号|
|[i].uuid|string|419338db9358438ab59a7243bed3969c|收货人uuid|
|[i].deliverySource|string|来源|顶级渠道|
|[i].province|string|430000|省编码|
|[i].provinceName|string|湖南省|省名称|
|[i].city|string|430100|城市编码|
|[i].cityName|string|长沙市|城市名称|
|[i].district|string|430104|先/区编码|
|[i].districtName|string|岳麓区|县/区名称|
|[i].address|string|金洲大道68号|详细地址|
|[i].storeCode|string|XINGREN_6369|渠道编码|
|[i].idCard|string|130523197610281210||
|[i].isDefault|string|1|是否默认收货地址|
|[i].latitude|number|39.96583|纬度|
|[i].longitude|number|116.391621|经度|
|[i].linkPerson|string|xx|收货人姓名|
|[i].linkPhone|string|18075389282|收货人联系方式|
|[i].streetNumber|string|12343|街道编号|
|[i].streetName|string|OTO|街道名称|




 异常

|名称|类型|示例值|描述|
|:----|:----:|:----:|:----:|
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

### 3. 【收货地址】创建会员收货地址  

- **接口描述**  
> 创建会员收货地址

- **接口信息**  
> **接口地址：** /openx/memberopen/deliveryAddressService/createAddress  
> **提交方式：** POST  
> **方法名称：** createAddress  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|deliveryAddr|object|是|对象|
|deliveryAddr.customerId|string|是|会员编号|
|deliveryAddr.deliverySource|string|是|收货地址来源 顶级渠道名称 YFJX|
|deliveryAddr.province|string|是|省编码|
|deliveryAddr.city|string|是|市编码|
|district|string|是|区编码|
|deliveryAddr.linkPerson|string|是|联系人姓名|
|deliveryAddr.linkPhone|string|是|联系人电话|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|uuid|string|053ee1b930b24f1b83979aedc1ffc653|收货地址主键|




 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
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


### 4. 【收货地址】删除会员收货地址  

- **接口描述**  
> 删除会员收货地址

- **接口信息**  
> **接口地址：** /openx/memberopen/deliveryAddressService/deleteAddress  
> **提交方式：** POST  
> **方法名称：** deleteAddress  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|id|string|是|收货人信息id|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
||string|3db822fd8dc24cd49e8b2d40bbd3aab2|删除的id|



 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"id":"3db822fd8dc24cd49e8b2d40bbd3aab2"
}
```

返回结果
```json
"3db822fd8dc24cd49e8b2d40bbd3aab2"
```

 **NOTICE**  
无

 
---

### 5. 【收货地址】修改会员收货地址  

- **接口描述**  
> 修改会员收货地址

- **接口信息**  
> **接口地址：** /openx/memberopen/deliveryAddressService/updateAddress  
> **提交方式：** POST  
> **方法名称：** updateAddress  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|deliveryAddr|object|是|对象|
|deliveryAddr.uuid|string|是|收货人信息id|
|deliveryAddr.customerId|string|是|会员编号|
|deliveryAddr.deliverySource|string|是|收货地址来源 顶级渠道名称 YFJX|
|deliveryAddr.province|string|是|省编码|
|deliveryAddr.city|string|是|市编码|
|district|string|是|区编码|
|deliveryAddr.linkPerson|string|是|联系人姓名|
|deliveryAddr.linkPhone|string|是|联系人电话|

- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|




 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"deliveryAddr":{
		"uuid":"974440810cd049fd8a33f93d7612aece",
		 "address": "杜鹃路12",
    	"city": "430100",
    	"customerId": "647958c21f03445a9bb8fbcadfc82f30",
    	"deliverySource": "WX",
    	"district": "430104",
    	"linkPerson": "张三1111",
    	"linkPhone": "13725578963",
    	"province": "430000"
	}
   
}
```

返回结果
```json

```

 **NOTICE**  
无

 
---


### 6. 【收货地址】会员默认收货地址  

- **接口描述**  
> 会员默认收货地址 

- **接口信息**  
> **接口地址：** /openx/memberopen/deliveryAddressService/getDefaultAddress  
> **提交方式：** POST  
> **方法名称：** getDefaultAddress  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|customerId|string|是|会员id|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|uuid|string|是|收货人信息id|
|customerId|string|是|会员编号|
|deliverySource|string|是|收货地址来源 顶级渠道名称 YFJX|
|province|string|是|省编码|
|city|string|是|市编码|
|district|string|是|区编码|
|linkPerson|string|是|联系人姓名|
|linkPhone|string|是|联系人电话|



 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
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
}
```

 **NOTICE**  
无

 
---


## 【query】-proxy query服务    

### 1. 【搜索】联想词  

- **接口描述**  
通过关键词搜索联想词

- **接口信息**  
> **接口地址：** /openx/query/goodsQueryService/listAssociatedWords    
> **提交方式：** POST  
> **方法名称：** listAssociatedWords 

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|keyWords|string|是|关键词|
|size|int|是|多少|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|[i]|string|感冒|联想词|




 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"keyWords":"感",
	"size":10
}
```

返回结果
```json
[
    "感冒",
    "感冒康",
    "感冒止咳",
    "感冒清",
    "感冒清热",
    "感冒灵",
    "感冒炎咳灵",
    "感冒药",
    "感冒退烧",
    "感冒退热"
]
```

 **NOTICE**  
无

 
---

### 2. 【搜索】关键词搜索  

- **接口描述**  
通过关键词搜索

- **接口信息**  
> **接口地址：** /openx/query/goodsQueryService/listGoodsByKeyWords    
> **提交方式：** POST  
> **方法名称：** listGoodsByKeyWords 

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
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
|:----|:----:|:----|:----|
|[i].channelCode|string|XINGREN_6369|渠道编号|
|[i].channelGoodsCode|string|1001044|渠道商品编码|
|[i].channelGoodsName|string|复方氨酚烷胺片..|渠道商品名称|
|[i].channelGoodsStatus|string|ON_LINE|状态|
|[i].channelPrice|number|11.5|渠道价格|
|[i].commonName|string|复方氨酚烷胺片|通用名|
|[i].drugCategory|string|Y01010901|分类编码|
|[i].effect|string|适用于缓解普通...|功能主治|
|[i].goodsCode|string|1001044|商品编码|
|[i].goodsName|string|复方氨酚烷胺...|商品名称|
|[i].guidePrice|number|11.5|原价|
|[i].imageUrl|array|['','']|商品图片|
|[i].manufacturer|string|吉林省吴太感康药业|生产厂家|



 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"channelCode":"XINGREN_6369",
	"searchCriteria":{
		"keyword":"感",
		"minMatch":"75%"
	},
	"searchCondition":{
		
	},
	"pageNo":1,
	"pageSize":10
}
```

返回结果
```json
[
    {
        "channelCode": "XINGREN_6369",
        "channelGoodsCode": "1001044",
        "channelGoodsName": "复方氨酚烷胺片 (感康) 12片 吉林省吴太感康药业有限公司",
        "channelGoodsStatus": "ON_LINE",
        "channelPrice": 11.5,
        "commonName": "复方氨酚烷胺片",
        "drugCategory": "Y01010901",
        "effect": "适用于缓解普通感冒及流行性感冒引起的发热、头痛、四肢酸痛、打喷嚏、流鼻涕、鼻塞、咽痛等症状。",
        "goodsCode": "1001044",
        "goodsName": "复方氨酚烷胺片 (感康) 12片 吉林省吴太感康药业有限公司",
        "guidePrice": 11.5,
        "imageUrl": [
            "https://img.yifengx.com/product/1001044/1001044a1.jpg!f120",
            "https://img.yifengx.com/product/1001044/1001044a2.jpg!f120",
            "https://img.yifengx.com/product/1001044/1001044a3.jpg!f120"
        ],
        "manufacturer": "吉林省吴太感康药业有限公司"
    },
    {
        "channelCode": "XINGREN_6369",
        "channelGoodsCode": "1002473",
        "channelGoodsName": "小儿氨酚黄那敏颗粒 (新感力克新) 6克*9袋 武汉东信医药科技有限责任公司",
        "channelGoodsStatus": "ON_LINE",
        "channelPrice": 3.5,
        "commonName": "小儿氨酚黄那敏颗粒",
        "drugCategory": "Y08010203",
        "effect": "适用于缓解儿童普通感冒及流行性感冒引起的发热、头痛、四肢酸痛、打喷嚏、流鼻涕、鼻塞、咽痛等症状。",
        "goodsCode": "1002473",
        "goodsName": "小儿氨酚黄那敏颗粒 (新感力克新) 6克*9袋 武汉东信医药科技有限责任公司",
        "guidePrice": 3.5,
        "imageUrl": [
            "https://img.yifengx.com/product/1002473/1002473a1.jpg!f120",
            "https://img.yifengx.com/product/1002473/1002473a2.jpg!f120",
            "https://img.yifengx.com/product/1002473/1002473a3.jpg!f120"
        ],
        "manufacturer": "武汉东信医药科技有限责任公司"
    },
    {
        "channelCode": "XINGREN_6369",
        "channelGoodsCode": "1005976",
        "channelGoodsName": "咽炎片 0.26克*30片 吉林省吴太感康药业有限公司",
        "channelGoodsStatus": "ON_LINE",
        "channelPrice": 12.5,
        "commonName": "咽炎片",
        "drugCategory": "Y01011205",
        "effect": "养阴润肺，清热解毒，清利咽喉，镇咳止痒。用于慢性咽炎引起咽干，咽痒，刺激性咳嗽。",
        "goodsCode": "1005976",
        "goodsName": "咽炎片 0.26克*30片 吉林省吴太感康药业有限公司",
        "guidePrice": 12.5,
        "imageUrl": [
            "https://img.yifengx.com/product/1005976/1005976a1.jpg!f120",
            "https://img.yifengx.com/product/1005976/1005976a2.jpg!f120",
            "https://img.yifengx.com/product/1005976/1005976a3.jpg!f120"
        ],
        "manufacturer": "吉林省吴太感康药业有限公司"
    },
    {
        "channelCode": "XINGREN_6369",
        "channelGoodsCode": "1016990",
        "channelGoodsName": "复方氨酚烷胺片 (感康)  16片 吉林省吴太感康药业有限公司",
        "channelGoodsStatus": "ON_LINE",
        "channelPrice": 21,
        "commonName": "复方氨酚烷胺片",
        "drugCategory": "Y01010901",
        "effect": "用于缓解普通感冒或流行性感冒引起的发热、头痛、咽痛、鼻塞、打喷嚏等症状。",
        "goodsCode": "1016990",
        "goodsName": "复方氨酚烷胺片 (感康)  16片 吉林省吴太感康药业有限公司",
        "guidePrice": 21,
        "imageUrl": [
            "https://img.yifengx.com/product/1016990/1016990a1.jpg!f120",
            "https://img.yifengx.com/product/1016990/1016990a2.jpg!f120",
            "https://img.yifengx.com/product/1016990/1016990a3.jpg!f120"
        ],
        "manufacturer": "吉林省吴太感康药业有限公司"
    },
    {
        "channelCode": "XINGREN_6369",
        "channelGoodsCode": "7000142",
        "channelGoodsName": "天然胶乳橡胶避孕套(6合1) (第六感) 24只 马来西亚",
        "channelGoodsStatus": "ON_LINE",
        "channelPrice": 39,
        "commonName": "天然胶乳橡胶避孕套(6合1)",
        "drugCategory": "Y05060101",
        "goodsCode": "7000142",
        "goodsName": "天然胶乳橡胶避孕套(6合1) (第六感) 24只 马来西亚",
        "guidePrice": 39,
        "imageUrl": [
            "https://img.yifengx.com/product/7000142/7000142a1.jpg!f120",
            "https://img.yifengx.com/product/7000142/7000142a2.jpg!f120",
            "https://img.yifengx.com/product/7000142/7000142a3.jpg!f120"
        ]
    },
    {
        "channelCode": "XINGREN_6369",
        "channelGoodsCode": "7000158",
        "channelGoodsName": "天然胶乳橡胶避孕套(超薄超滑) (第六感) 12只 马来西亚",
        "channelGoodsStatus": "ON_LINE",
        "channelPrice": 24,
        "commonName": "天然胶乳橡胶避孕套(超薄超滑)",
        "drugCategory": "Y05060101",
        "effect": "原系统说明书：导入时说明书：计生用品",
        "goodsCode": "7000158",
        "goodsName": "天然胶乳橡胶避孕套(超薄超滑) (第六感) 12只 马来西亚",
        "guidePrice": 24,
        "imageUrl": [
            "https://img.yifengx.com/product/7000158/7000158a1.jpg!f120",
            "https://img.yifengx.com/product/7000158/7000158a2.jpg!f120",
            "https://img.yifengx.com/product/7000158/7000158a3.jpg!f120"
        ]
    },
    {
        "channelCode": "XINGREN_6369",
        "channelGoodsCode": "7000714",
        "channelGoodsName": "天然胶乳橡胶避孕套(纤薄螺纹) (第六感) 12只(诱感装) 马来西亚",
        "channelGoodsStatus": "ON_LINE",
        "channelPrice": 21.8,
        "commonName": "天然胶乳橡胶避孕套(纤薄螺纹)",
        "drugCategory": "Y05060101",
        "effect": "",
        "goodsCode": "7000714",
        "goodsName": "天然胶乳橡胶避孕套(纤薄螺纹) (第六感) 12只(诱感装) 马来西亚",
        "guidePrice": 21.8,
        "imageUrl": [
            "https://img.yifengx.com/product/7000714/7000714a1.jpg!f120",
            "https://img.yifengx.com/product/7000714/7000714a2.jpg!f120",
            "https://img.yifengx.com/product/7000714/7000714a3.jpg!f120"
        ]
    }
]
```

 **NOTICE**  
无

--- 


### 3. 【渠道】 区域编码获取城市渠道 

- **接口描述**  
根据城市编码获取城市渠道

- **接口信息**  
> **接口地址：** /openx/query/channelQueryService/getCityChannelByRegionCode   
> **提交方式：** POST  
> **方法名称：** getCityChannelByRegionCode 

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|channelCode|string|是|顶级渠道编码|
|regionCode|string|是|城市编码 必填|

- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|name|string|益丰精选长沙城市渠道|城市渠道名称|
|channelCode|string|YFJX_CS|城市渠道渠道编码|




 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"channelCode":"YFJX",
	"regionCode":"430100"
}
```

返回结果
```json
{
    "address": "",
    "cashOnDelivery": false,
    "channelCode": "YFJX_CS",
    "customerPickUp": false,
    "location": {},
    "name": "益丰精选长沙",
    "parentCode": "YFJX",
    "serviceTime": "",
    "warehouseCode": "VWC6369"
}
```

 **NOTICE**  
无

 
---


### 3. 【渠道】 区域编码获取b2c渠道 

- **接口描述**  
根据城市编码获取城市渠道

- **接口信息**  
> **接口地址：** /openx/query/channelQueryService/getB2cChannelByRegionCode   
> **提交方式：** POST  
> **方法名称：** getB2cChannelByRegionCode 

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|topChannelCode|string|是|顶级渠道编码|
|regionCode|string|是|城市编码 必填|

- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|name|string|益丰精选长沙城市渠道|城市渠道名称|
|channelCode|string|YFJX_CS|城市渠道渠道编码|




 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"topChannelCode":"YFJX",
	"regionCode":"430100"
}
```

返回结果
```json
{
    "address": "",
    "cashOnDelivery": false,
    "channelCode": "YFJX_CS",
    "customerPickUp": false,
    "location": {},
    "name": "益丰精选长沙",
    "parentCode": "YFJX",
    "serviceTime": "",
    "warehouseCode": "VWC6369"
}
```

 **NOTICE**  
无

 
---

### 4. 【渠道】 根据城市渠道查询最近门店渠道 

- **接口描述**  
城市渠道编码 经纬度 范围 过滤渠道

- **接口信息**  
> **接口地址：** /openx/query/channelQueryService/getChannelByChannelCodeAndLocation    
> **提交方式：** POST  
> **方法名称：** getChannelByChannelCodeAndLocation  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|channelCode|string|是|城市渠道编码|
|range|number|是|周边距离单位m|
|location|object|是|经纬度|
|location.longitude|number|是|经度|
|location.latitude|number|是|纬度|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|name|string|益丰精选长沙城市渠道|城市渠道名称|
|channelCode|string|YFJX_CSZD|城市渠道渠道编码|
|status|string|ENABLE|状态|
|type|string|OWNED|自营|
|location|object|{}|经纬度|
|location.longitude|112.88512|是|经度|
|location.latitude|28.2267|是|纬度|
|address|string||地址|
|cashOnDelivery|boolean|false|货到付款|
|customerPickUp|boolean|false|自提|
|remark|string||备注|
|serviceModel|string||服务模式 O2O B2C|




 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
    "channelCode": "YFJX_CS",
    "location": {
        "longitude": "112.88512",
        "latitude": "28.2267"
    },
    "range": "30000"
}
```

返回结果
```json
{
    "address": "益丰精选长沙城市渠道1",
    "cashOnDelivery": false,
    "channelCode": "YFJX_CSZD",
    "customerPickUp": false,
    "location": {
        "latitude": 28.2267,
        "longitude": 112.88512
    },
    "name": "益丰精选长沙城市渠道",
    "parentCode": "YFJX_CS",
    "remark": "益丰精选长沙城市渠道",
    "serviceModel": "O2O",
    "status": "ENABLE",
    "type": "OWNED"
}
```

 **NOTICE**  
无

 
---

### 4. 【渠道】 查询附近渠道列表

- **接口描述**  
顶级渠道编码 经纬度 范围 过滤渠道

- **接口信息**  
> **接口地址：** /openx/query/channelQueryService/locateChannelByLocation    
> **提交方式：** POST  
> **方法名称：** locateChannelByLocation  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|topChannelCode|string|是|顶级渠道编码|
|range|number|是|周边距离单位m|
|location|object|是|经纬度|
|location.longitude|number|是|经度|
|location.latitude|number|是|纬度|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|[i].name|string|益丰精选长沙城市渠道|城市渠道名称|
|[i].channelCode|string|YFJX_CSZD|城市渠道渠道编码|
|[i].status|string|ENABLE|状态|
|[i].type|string|OWNED|自营|
|[i].location|object|{}|经纬度|
|[i].location.longitude|112.88512|是|经度|
|[i].location.latitude|28.2267|是|纬度|
|[i].address|string||地址|
|[i].cashOnDelivery|boolean|false|货到付款|
|[i].customerPickUp|boolean|false|自提|
|[i].remark|string||备注|
|[i].serviceModel|string||服务模式 O2O B2C|




 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
    "topChannelCode": "YFJX",
    "location": {
        "longitude": "112.88512",
        "latitude": "28.2267"
    },
    "range": "30000"
}
```

返回结果
```json
[{
    "address": "益丰精选长沙城市渠道1",
    "cashOnDelivery": false,
    "channelCode": "YFJX_CSZD",
    "customerPickUp": false,
    "location": {
        "latitude": 28.2267,
        "longitude": 112.88512
    },
    "name": "益丰精选长沙城市渠道",
    "parentCode": "YFJX_CS",
    "remark": "益丰精选长沙城市渠道",
    "serviceModel": "O2O",
    "status": "ENABLE",
    "type": "OWNED"
}]
```

 **NOTICE**  
无

 
---
 

### 5. 【渠道】 根据渠道编码批量查询渠道 

- **接口描述**  


- **接口信息**  
> **接口地址：** /openx/query/channelQueryService/listChannelByCodes    
> **提交方式：** listChannelByCodes  
> **方法名称：**  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|channelCodes|array|是|渠道编码列表[""]|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|[i].name|string|益丰精选长沙城市渠道|渠道名称|
|[i].channelCode|string|XINGREN_6369|渠道编码|
|[i].serviceTime|string||服务时间|
|[i].address|string||渠道地址|
|[i].warehouseCode|string||仓库编码|
|[i].cashOnDelivery|boolean|false|货到付款|
|[i].customerPickUp|boolean|false|自提|



 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"channelCodes":["XINGREN_6369"]
}
```

返回结果
```json
[
    {
        "address": "湖南省长沙市望城区麓谷街道金洲大道68号",
        "cashOnDelivery": false,
        "channelCode": "XINGREN_6369",
        "customerPickUp": false,
        "name": "杏仁金洲大道店",
        "parentCode": "XINGREN",
        "serviceTime": "",
        "warehouseCode": "6369+C018+6801+C048"
    }
]
```

 **NOTICE**  
无

 
--- 

### 6. 【渠道】 根据渠道编码查询渠道路径 

- **接口描述**  
根据渠道编码查询渠道路径

- **接口信息**  
> **接口地址：** /openx/query/channelQueryService/getChannelPath    
> **提交方式：** getChannelPath  
> **方法名称：**  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|channelCode|string|是|渠道编码|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
||string|YFJX,YFJX_CS,YFJX_CSZD|渠道路径|



 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"channelCode":"YFJX_CSZD"
}
```

返回结果
```json
"YFJX,YFJX_CS,YFJX_CSZD"
```

 **NOTICE**  
无

 
--- 



### 7. 【商品】通过渠道编码和商品编码查询商品

- **接口描述**  


- **接口信息**  
> **接口地址：** /openx/query/goodsQueryService/listChannelGoods    
> **提交方式：** POST  
> **方法名称：** listChannelGoods 

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|channelCode|string|是|渠道编码|
|goodsCodes|array|是|商品编码列表|





- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|[i].channelCode|string|XINGREN_6369|渠道编码|
|[i].channelGoodsCode|string|1011252|渠道商品编码|
|[i].channelGoodsName|string|奥美拉唑肠溶胶囊|渠道商品名称|
|[i].channelGoodsStatus|string|ON_LINE|渠道商品状态|
|[i].channelPrice|number|17.8|渠道商品价格|
|[i].commonName|string|奥美拉唑肠溶胶囊|通用名|
|[i].drugCategory|string|Y01010301|类目|
|[i].effect|string|适应用于胃溃疡|功能主治|
|[i].goodsCode|string|1011252|商品编码|
|[i].goodsName|string|奥美拉唑肠溶胶囊|商品名称|
|[i].guidePrice|number|17.8|原价|
|[i].imageUrl|array||商品图片|
|[i].stock|number|0|商品库存|



 异常

|名称|类型|示例值|描述|
|:----|:----:|:----:|:----:|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"channelCode":"XINGREN_6369",
	"goodsCodes":["1011252","1000002"]
}
```

返回结果
```json
[
    {
        "channelCode": "XINGREN_6369",
        "channelGoodsCode": "1011252",
        "channelGoodsName": "奥美拉唑肠溶胶囊 20毫克*21粒 山东罗欣药业集团股份有限公司(原山东罗欣药业",
        "channelGoodsStatus": "ON_LINE",
        "channelPrice": 17.8,
        "commonName": "奥美拉唑肠溶胶囊",
        "drugCategory": "Y01010301",
        "effect": "适应用于胃溃疡，十二指肠溃疡，应激性溃疡，反流性食管炎和卓-艾综合症（胃泌素瘤）。",
        "goodsCode": "1011252",
        "goodsName": "奥美拉唑肠溶胶囊 20毫克*21粒 山东罗欣药业集团股份有限公司(原山东罗欣药业",
        "guidePrice": 17.8,
        "imageUrl": [
            "https://img.yifengx.com/product/1011252/1011252a1.jpg!f120",
            "https://img.yifengx.com/product/1011252/1011252a2.jpg!f120",
            "https://img.yifengx.com/product/1011252/1011252a3.jpg!f120"
        ],
        "stock": 0
    }
]
```

 **NOTICE**  
无

---


### 8. 【商品】商品编码查询商品说明书

- **接口描述**  
渠道编码查询商品说明书

- **接口信息**  
> **接口地址：** /openx/query/goodsQueryService/getGoodsInstructions    
> **提交方式：** POST  
> **方法名称：** getGoodsInstructions  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|channelCode|string|是|渠道编码|
|goodsCode|string|是|商品编码|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|genericName|string|奥美拉唑肠溶胶囊|通用名|
|specifications|string|20毫克*21粒|规格|
|approvalNumber|string|国药准字H20033444|批准文号|
|manufacturer|string||生产厂家|
|composition|string||药品成分|
|dosage|string||用法用量|
|dosageForm|string||剂型|
|adverseReactions|string||不良反应|
|contraindications|string||禁忌|
|drugDescription|string||药品性状|
|indications|string||功能主治|
|packing|string||包装|
|interactions|string||药品相互作用|
|storageCondition|string||贮藏条件|
|validityTerm|number||有效期|
|attention|string||注意事项|



 异常

|名称|类型|示例值|描述|
|:----|:----:|:----:|:----:|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"channelCode":"XINGREN_6369",
	"goodsCode":"1011252"
}
```

返回结果
```json
{
    "adverseReactions": "本品耐受性良好,常见不良反应是腹泻,头痛,恶心,便秘等。",
    "approvalNumber": "国药准字H20033444",
    "attention": "使用本品应先排除胃癌的可能，肝肾功能不全者及孕妇，哺乳期妇女慎用。",
    "composition": "",
    "contraindications": "对本品过敏者、严重肾功能不全者及婴幼儿禁用。",
    "dosage": "口服，不可咀嚼。（1）消化性溃疡：一次1粒，一日1－2次。每日晨起吞服或早晚各一次。（2）反流性食管炎：一次1－3粒。一日1－2次。晨起吞服或早晚各一次，（3）卓－艾综合征：一次3粒，一日1次；(4)十二指肠溃疡，疗程为2-4周；胃溃疡，反流性食管炎疗程为4-8周。",
    "dosageForm": "",
    "drugDescription": "本品内容物为白色或类白色肠溶小丸或颗粒。",
    "genericName": "奥美拉唑肠溶胶囊",
    "indications": "适应用于胃溃疡，十二指肠溃疡，应激性溃疡，反流性食管炎和卓-艾综合症（胃泌素瘤）。",
    "interactions": "本品可延缓经肝脏代谢药物在体内的消除，如安定、苯妥英钠、华法令、硝苯啶等，当本品和上述药物一起使用时，应减少后者的用量。",
    "packing": "纸盒",
    "specifications": "20毫克*21粒",
    "storageCondition": "常温:10-30℃"
}
```

 **NOTICE**  
无

---


### 9. 【商品】商品编码查询商品详情

- **接口描述**  
渠道编码查询商品详情 包括说明书

- **接口信息**  
> **接口地址：** /openx/query/goodsQueryService/getChannelGoodsDetail    
> **提交方式：** POST  
> **方法名称：** getChannelGoodsDetail  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|channelCode|string|是|渠道编码|
|goodsCodes|string|是|商品编码|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|channelCode|string|YFJX_5742|渠道编码|
|goodsCode|string|1000001|商品编码|
|goodsName|string|阿莫西 ... 石药集团中(石家庄)有限公|商品名称|
|channelGoodsCode|string|YF1000001|渠道商品编码|
|channelGoodsName|string|大写的药品名|渠道商品名称|
|channelGoodsStatus|string|ON_LINE|渠道商品状态|
|channelPrice|number|3.6|渠道商品价格|
|guidePrice|number|2.8|渠道商品原价|
|commonName|string|阿莫西林分散片||
|goodsMark|string|角标66|角标|
|imageUrl|array|[""]|商品图片|
|recommendIndex|int|2|推荐指数|
|standard|string||规格|
|manufacturer|string||生产企业|
|ingredients|string||成份|
|dosage|string||用法用量|
|dosageForm|string||剂型|
|adr|string||不良反应|
|taboo|string|对青霉素类药物过敏者禁用|禁忌|
|drugTrait|string||性状|
|effect|string||功能作用|
|packagingMaterial|string||包装|
|drugInteraction|string||药品相互作用|
|storageCondition|string||储藏条件|
|approvalNumber|string|国药准字H20033444|批准文号|
|expiryDate|number||有效期|
|attention|string||注意事项|
|drugCategory|string|1|药品类型|

drugCategory

|value|desc|
|:---|:---|
|1|单轨处方药1|
|2|单轨处方药2|
|3|双轨处方药|
|4|甲类非处方|
|5|乙类非处方|
|6|非药品|
|7|配方饮片|
|8|精制饮片|


 异常

|名称|类型|示例值|描述|
|:----|:----:|:----:|:----:|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"channelCode":"YFJX_5742",
	"goodsCodes":"1000001"
}
```

返回结果
```json
{
    "adr": "少数患者可出现恶心、呕吐、食欲减退、腹泻等消化道反应，一般不影响治疗。偶可出现皮疹、斑疹、紫癜等，应立即停药。",
    "approvalNumber": "国药准字H10980075",
    "attention": "1．用药前必须进行青霉素皮内敏感试验，阳性反应者禁用。\r\n2．伴有单核细胞增多和淋巴细胞增多的患者，出现皮疹的机会多一些。3．与青霉素类和头孢菌素类之间存在交叉过敏性和交叉耐药性。4．类似其它广谱抗生素，有可能发生由白念珠菌等非敏感微生物引起的二重感染。尤其是慢性病患者和自身免疫功能失调者。",
    "channelCode": "YFJX_5742",
    "channelGoodsCode": "YF1000001",
    "channelGoodsName": "大写的药品名",
    "channelGoodsStatus": "ON_LINE",
    "channelPrice": 3.6,
    "commonName": "阿莫西林分散片",
    "dosage": "本品既可直接用水吞服，也可放入牛奶或果汁中，搅拌至混悬状态后服用。口服：1.成人一次0.5～1g，一日3～4次；小儿每日按体重50～100mg/kg，分3～4次服用。2.治疗无并发症的急性尿路感染可予以单次口服3g即可，也可于10～12小时后再增加一次3g剂量。单次3g剂量也可用以预防感染性心内膜炎或治疗淋病，前者于口腔内手术(如拔牙)前1小时给予，后者常加用丙磺舒1g。",
    "dosageForm": "",
    "drugCategory": "1",
    "drugInteraction": "如与其他药物同时使用可能会发生药物相互作用，详情请咨询医师或药师。",
    "drugTrait": "本品为白色或类白色片 \r\n",
    "effect": "抗生素，其抗菌谱与氨苄青霉素相同，\r\n对敏感的革兰氏阳性球菌和杆菌及革兰氏阴性菌均有明显的抑制作用。适用于敏感菌所致呼吸道感染、尿路感染、胃肠道感染、败血症、皮肤及软组织感染等症。",
    "goodsCode": "1000001",
    "goodsMark": "角标66",
    "goodsName": "阿莫西林分散片 (阿林新) 0.25克*12片 石药集团中诺药业(石家庄)有限公",
    "guidePrice": 3.8,
    "imageUrl": [
        "https://img.yifengx.com/product/1000001/1000001a1.jpg!f120",
        "https://img.yifengx.com/product/1000001/1000001a2.jpg!f120",
        "https://img.yifengx.com/product/1000001/1000001a3.jpg!f120"
    ],
    "ingredients": "",
    "manufacturer": "石药集团中诺药业(石家庄)有限公司(石药集团欧意药业有限公司",
    "packagingMaterial": "纸盒",
    "recommendIndex": 2,
    "standard": "0.25克*12片",
    "storageCondition": "常温:10-30℃",
    "taboo": "对青霉素类药物过敏者禁用"
}
```

 **NOTICE**  
无

---


### 10. 【商品】计算商品合计

- **接口描述**  
根据渠道和商品 计算价格合计

- **接口信息**  
> **接口地址：** /openx/query/goodsQueryService/calGoodsPrice    
> **提交方式：** POST  
> **方法名称：** calGoodsPrice  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|channelCode|string|是|城市渠道/价格渠道 YFJX_CS|
|goodsList|array|是|[{}]|
|goodsList[i].goodsCode|string|是|商品编码|
|goodsList[i].quantity|int|是|商品数量|

- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
||number|10|合计金额|




 异常

|名称|类型|示例值|描述|
|:----|:----:|:----:|:----:|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"channelCode":"YFJX_CS",
	"goodsList":[{
		"goodsCode":"1000001",
		"quantity":20000
	}]
}
```

返回结果
```json
72000
```

 **NOTICE**  
无

---

### 11. 【商品】查询可用库存

- **接口描述**  
渠道编码和商品列表查询可用库存

- **接口信息**  
> **接口地址：** /openx/query/goodsQueryService/listUsableStock    
> **提交方式：** POST  
> **方法名称：** listUsableStock  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|channelCode|string|是|门店渠道 YFJX_5742|
|cityChannelCode|string|是|城市渠道/价格渠道 YFJX_CS|
|goodsCodeList|array|是|[""]|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|[i].channelCode|string|XINGREN_6369|渠道编码|
|[i].channelGoodsCode|string|1011252|渠道商品编码|
|[i].channelGoodsName|string|奥美拉唑肠溶胶囊|渠道商品名称|
|[i].channelGoodsStatus|string|ON_LINE|渠道商品状态|
|[i].channelPrice|number|17.8|渠道商品价格|
|[i].commonName|string|奥美拉唑肠溶胶囊|通用名|
|[i].drugCategory|string|Y01010301|类目|
|[i].effect|string|适应用于胃溃疡|功能主治|
|[i].goodsCode|string|1011252|商品编码|
|[i].goodsName|string|奥美拉唑肠溶胶囊|商品名称|
|[i].goodsMark|string||商品角标|
|[i].guidePrice|number|17.8|原价|
|[i].imageUrl|array||商品图片|
|[i].stock|number|0|商品库存|
|[i].manufacturer|string||生产厂家|
|[i].recommendIndex|int||推荐指数|



 异常

|名称|类型|示例值|描述|
|:----|:----:|:----:|:----:|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"channelCode":"YFJX_5742",
	"cityChannelCode":"YFJX_CS",
	"goodsCodeList":["1000013","1000001"]
}
```

返回结果
```json
[
    {
        "channelCode": "YFJX_CS",
        "channelGoodsCode": "YF1000001",
        "channelGoodsName": "大写的药品名",
        "channelGoodsStatus": "ON_LINE",
        "channelPrice": 3.6,
        "commonName": "阿莫西林分散片",
        "drugCategory": "1",
        "effect": "抗生素，其抗菌谱与氨苄青霉素相同，\r\n对敏感的革兰氏阳性球菌和杆菌及革兰氏阴性菌均有明显的抑制作用。适用于敏感菌所致呼吸道感染、尿路感染、胃肠道感染、败血症、皮肤及软组织感染等症。",
        "goodsCode": "1000001",
        "goodsMark": "角标66",
        "goodsName": "阿莫西林分散片 (阿林新) 0.25克*12片 石药集团中诺药业(石家庄)有限公",
        "guidePrice": 3.8,
        "imageUrl": [
            "https://img.yifengx.com/product/1000001/1000001a1.jpg!f120",
            "https://img.yifengx.com/product/1000001/1000001a2.jpg!f120",
            "https://img.yifengx.com/product/1000001/1000001a3.jpg!f120"
        ],
        "manufacturer": "石药集团中诺药业(石家庄)有限公司(石药集团欧意药业有限公司",
        "recommendIndex": 2,
        "stock": 989
    },
    {
        "channelCode": "YFJX_CS",
        "channelGoodsCode": "YF10000013",
        "channelGoodsName": "小写的药品名",
        "channelGoodsStatus": "ON_LINE",
        "channelPrice": 13.3,
        "commonName": "阿莫西林胶囊",
        "drugCategory": "Y01010101",
        "effect": "阿莫西林适用于敏感菌(不产β内酰胺酶菌株)所致的下列感染：1. 溶血链球菌、肺炎链球菌、葡萄球菌或流感嗜血杆菌所致中耳炎、鼻窦炎、咽炎、扁桃体炎等上呼吸道感染。2. 大肠埃希菌、奇异变形杆菌或粪肠球菌所致的泌尿生殖道感染。3. 溶血链球菌、葡萄球菌或大肠埃希菌所致的皮肤软组织感染。4. 溶血链球菌、肺炎链球菌、葡萄球菌或流感嗜血杆菌所致急性支气管炎、肺炎等下呼吸道感染。5. 急性单纯性淋病。6. 本品尚可用于治疗伤寒、伤寒带菌者及钩端螺旋体病;阿莫西林亦可与克拉霉素、兰索拉唑三联用药根除胃、十二指肠幽门螺杆菌，降低消化道溃疡复发率。",
        "goodsCode": "1000013",
        "goodsName": "阿莫西林胶囊 0.25克*24粒 海口奇力制药股份有限公司",
        "guidePrice": 2.5,
        "imageUrl": [
            "https://img.yifengx.com/product/1000013/1000013a1.jpg!f120",
            "https://img.yifengx.com/product/1000013/1000013a2.jpg!f120",
            "https://img.yifengx.com/product/1000013/1000013a3.jpg!f120"
        ],
        "manufacturer": "海口奇力制药股份有限公司",
        "stock": 985
    }
]
```

 **NOTICE**  
无

---


### 12. 【物流】根据渠道查询可用物流方式

- **接口描述**  
根据收发城市信息及渠道信息、获取可用的物流信息  规则：①、在未拆单的情况下，直接去load可用物流信息。 ②、拆单情况下获取可用物流取2个城市的并集信息中价格最低物流。

- **接口信息**  
> **接口地址：** /openx/query/logisticsQueryService/listDeliveryType    
> **提交方式：** POST  
> **方法名称：** listDeliveryType  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|topChannelCode|string|是|顶级渠道|
|receiverProvinceCode|string|是|收货人省级编码|
|receiverCityCode|string|是|收货人市级编码|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|[i].default|boolean|true|是否默认|
|[i].deliveryTypeCode|string|NORMAL,REAL_TIME,URGENT|配送类型编码 |
|[i].deliveryTypeName|string|普通，实时，加急|配送类型描述|
|[i].price|number|5|配送运费|

 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
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


### 13. 【物流】订单编号查询物流节点信息

- **接口描述**  
订单编号查询物流跟踪信息

- **接口信息**  
> **接口地址：** /openx/query/logisticsQueryService/getDeliveryTaskByOrderCode  
> **提交方式：** POST  
> **方法名称：** getDeliveryTaskByOrderCode  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|orderCode|string|是|订单编号|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|waybillCode|string|810733629993|快递单号|
|deliveryStatusCode|string|DELIVERY_FINISHED|配送状态|
|deliveryStatusDesc|string|配送完成|配送状态描述|
|deliveryTime|number|1500257047000|配送时间|
|finishedTime|number|1500446937000|配送完成时间|
|logisticsId|string|YTO|配送公司标识|
|logisticsName|string|圆通快递|配送公司名称|
|traceInfos|array|[{}]|物流节点信息|
|traceInfos[i].nodeCode|string||物流节点编码|
|traceInfos[i].nodeDesc|string||物流节点名称|
|traceInfos[i].nodeTime|string||物流节点时间|

 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"orderCode":"XR201707176369041000191"
}
```

返回结果
```json
{
    "deliveryStatusCode": "DELIVERY_FINISHED",
    "deliveryStatusDesc": "配送完成",
    "deliveryTime": 1500257047000,
    "finishedTime": 1500446937000,
    "logisticsId": "YTO",
    "logisticsName": "圆通快递",
    "traceInfos": [
        {
            "nodeCode": "810733629993",
            "nodeDesc": "【湖南省长沙市岳麓区公司】  已收件",
            "nodeTime": "2017-7-17 19:27:54"
        },
        {
            "nodeCode": "810733629993",
            "nodeDesc": "【湖南省长沙市岳麓区公司】 已收件",
            "nodeTime": "2017-7-17 21:20:01"
        },
        {
            "nodeCode": "810733629993",
            "nodeDesc": "【湖南省长沙市岳麓区公司】 已打包",
            "nodeTime": "2017-7-17 21:52:59"
        },
        {
            "nodeCode": "810733629993",
            "nodeDesc": "【湖南省长沙市岳麓区公司】 已发出 下一站 【长沙转运中心】",
            "nodeTime": "2017-7-17 22:23:06"
        },
        {
            "nodeCode": "810733629993",
            "nodeDesc": "【长沙转运中心】 已收入",
            "nodeTime": "2017-7-18 1:07:42"
        },
        {
            "nodeCode": "810733629993",
            "nodeDesc": "【长沙转运中心】 已发出 下一站 【天津转运中心】",
            "nodeTime": "2017-7-18 1:11:03"
        },
        {
            "nodeCode": "810733629993",
            "nodeDesc": "【天津转运中心】 已收入",
            "nodeTime": "2017-7-19 2:02:52"
        },
        {
            "nodeCode": "810733629993",
            "nodeDesc": "【天津转运中心】 已收入",
            "nodeTime": "2017-7-19 2:08:16"
        },
        {
            "nodeCode": "810733629993",
            "nodeDesc": "【天津转运中心】 已发出 下一站 【天津市河东区万达公司】",
            "nodeTime": "2017-7-19 2:13:30"
        },
        {
            "nodeCode": "810733629993",
            "nodeDesc": "【天津市河东区万达公司】 派件人 :杨丙 派件中 派件员电话15620269807",
            "nodeTime": "2017-7-19 9:30:02"
        },
        {
            "nodeCode": "810733629993",
            "nodeDesc": "客户 签收人 :null 已签收 感谢使用圆通速递，期待再次为您服务",
            "nodeTime": "2017-7-19 14:48:46"
        }
    ],
    "waybillCode": "810733629993"
}
```

 **NOTICE**  
无

 
---


### 14. 【物流】查询物流收货人信息

- **接口描述**  
订单编号查询收货人信息

- **接口信息**  
> **接口地址：** /openx/query/logisticsQueryService/getReceiver  
> **提交方式：** POST  
> **方法名称：** getReceiver  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|orderCode|string|是|订单编号|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|name|string|刘佳梅|姓名|
|phone|string||收货人电话|
|location|object|{}|收货人地址经纬度|
|location.longitude|number||经度|
|location.longitude|number||纬度|
|provinceCode|string|120000|省级编码|
|provinceName|string|天津|省级名称|
|cityCode|string|120100|市级编码|
|cityName|string|天津市|市级名称|
|districtCode|string|120102|县级编码|
|districtName|string|河东区|县级名称|
|detailAddress|string||详细地址|



 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"orderCode":"XR201707176369041000191"
}
```

返回结果
```json
{
    "cityCode": "120100",
    "cityName": "天津市",
    "districtCode": "120102",
    "districtName": "河东区",
    "location": {
        "latitude": 27.9878,
        "longitude": 86.925
    },
    "name": "刘佳美",
    "phone": "15510828460",
    "provinceCode": "120000",
    "provinceName": "天津",
    "detailAddress":"xx路"
}
```

 **NOTICE**  
无

 
---



### 15. 【订单】统计订单数目

- **接口描述**  
根据顶级渠道和用户编码查询各状态下的订单数目

- **接口信息**  
> **接口地址：** /openx/query/orderQueryService/listOrderStatisticsByCustomer      
> **提交方式：** POST  
> **方法名称：** listOrderStatisticsByCustomer    

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|topChannelCode|string|是|顶级渠道|
|customerCode|string|是|会员编号|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|[i].orderState|string|ORDER_CANCEL|订单状态|
|[i].quantity|int|8|订单数目|

 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"topChannelCode":"XINGREN",
	"customerCode":"S00001"
}
```

返回结果
```json
[
    {
        "orderState": "AUDIT_WAITING",
        "quantity": 1
    },
    {
        "orderState": "DELIVERY_WAITING",
        "quantity": 7
    },
    {
        "orderState": "ORDER_CANCEL",
        "quantity": 32
    },
    {
        "orderState": "ORDER_CLOSE",
        "quantity": 12
    },
    {
        "orderState": "ORDER_FINISH",
        "quantity": 5
    },
    {
        "orderState": "PAYMENT_WAITING",
        "quantity": 4
    },
    {
        "orderState": "RECEIVE_WAITING",
        "quantity": 10
    },
    {
        "orderState": "SHIPMENT_WAITING",
        "quantity": 4
    }
]
```

 **NOTICE**  
无

 
---

### 16. 【订单】查询所有订单

- **接口描述**  
查询所有订单

- **接口信息**  
> **接口地址：** /openx/query/orderQueryService/listAllCustomerOrder          
> **提交方式：** POST  
> **方法名称：** listAllCustomerOrder    

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|topChannelCode|string|是|顶级渠道|
|customerCode|string|是|会员编号|
|pageNo|int|是|当前页|
|pageSize|int|是|每页大小|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|[i].topChannelCode|string|WXM|顶级渠道编号|
|[i].channelCode|string|WXM_6369|渠道编号|
|[i].createTime|number|1504858027000|创建时间|
|[i].customerCode|string|S00001|会员编号|
|[i].orderCode|string|WXM_63692017090801100010|订单编号|
|[i].orderState|string|29|会员支付金额|
|[i].ordonnanceId|string|000000001||
|[i].outTradeCode|string|BD000001|三方交易号|
|[i].parentOrderCode|string|WXM_63692017090801100010|父订单编号|
|[i].payee|string|PAYEE_YIFENG|收款类型 益丰收款|
|[i].deliveryServiceType|string|DELIVERY_YIFENG|物流类型|
|[i].warehouseCode|string|6369|仓库编码|
|[i].goodsTotalAmount|number|22|商品金额|
|[i].customerNeedPayAmount|number|29|会员支付金额|
|[i].subsidyTotalAmount|number|2||
|[i].remark|string||备注|
|[i].goods|array|[{}]|订单商品|
|[i].goods[i].goodsCode|string|1000000|商品编码|
|[i].goods[i].goodsName|string|东阿阿胶|商品名称|
|[i].goods[i].gift|boolean|false|是否礼品|
|[i].goods[i].exercisePrice|number|10|执行价|
|[i].goods[i].quantity|number|1|数量|
|[i].goods[i].channelPrice|number||渠道商品价格|
|[i].goods[i].guidePrice|number||原价|


 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
  "topChannelCode":"XINGREN",
  "customerCode":"3daa789d5165408f84fa706a5fd24c64",
  "pageNo":1,
  "pageSize":10
}
```

返回结果
```json
[
    {
        "channelCode": "XINGREN_6369",
        "createTime": 1508988633000,
        "customerCode": "3daa789d5165408f84fa706a5fd24c64",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goods": [
            {
                "channelPrice": 2.5,
                "exercisePrice": 10,
                "gift": false,
                "goodsCode": "1000013",
                "goodsName": "阿莫西林分散片 (利莎林)",
                "guidePrice": 2.5,
                "quantity": 1
            },
            {
                "channelPrice": 23.8,
                "exercisePrice": 12,
                "gift": false,
                "goodsCode": "1000008",
                "goodsName": "阿莫西林分散片 (阿林新)",
                "guidePrice": 23.8,
                "quantity": 1
            }
        ],
        "goodsTotalAmount": 22,
        "orderCode": "XR2017102601100002",
        "orderState": "PAYMENT_WAITING",
        "outTradeCode": "BD000001",
        "parentOrderCode": "XR2017102601100002",
        "payee": "PAYEE_YIFENG",
        "preferentialTotalAmount": 5,
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "XINGREN"
    },
    {
        "channelCode": "XINGREN_6369",
        "createTime": 1508394038000,
        "customerCode": "3daa789d5165408f84fa706a5fd24c64",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goods": [
            {
                "channelPrice": 2.5,
                "exercisePrice": 10,
                "gift": false,
                "goodsCode": "1000013",
                "goodsName": "阿莫西林分散片 (利莎林)",
                "quantity": 1
            },
            {
                "channelPrice": 23.8,
                "exercisePrice": 12,
                "gift": false,
                "goodsCode": "1000008",
                "goodsName": "阿莫西林分散片 (阿林新)",
                "quantity": 1
            }
        ],
        "goodsTotalAmount": 22,
        "orderCode": "XR2017101901100001",
        "orderState": "ORDER_CANCEL",
        "outTradeCode": "BD000001",
        "parentOrderCode": "XR2017101901100001",
        "payee": "PAYEE_YIFENG",
        "preferentialTotalAmount": 5,
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "XINGREN"
    },
    {
        "channelCode": "XINGREN_6369",
        "createTime": 1508232206000,
        "customerCode": "3daa789d5165408f84fa706a5fd24c64",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goods": [
            {
                "channelPrice": 2.5,
                "exercisePrice": 10,
                "gift": false,
                "goodsCode": "1000013",
                "goodsName": "阿莫西林分散片 (利莎林)",
                "quantity": 1
            },
            {
                "channelPrice": 23.8,
                "exercisePrice": 12,
                "gift": false,
                "goodsCode": "1000008",
                "goodsName": "阿莫西林分散片 (阿林新)",
                "quantity": 1
            }
        ],
        "goodsTotalAmount": 22,
        "orderCode": "XR2017101701100011",
        "orderState": "ORDER_CANCEL",
        "outTradeCode": "BD000001",
        "parentOrderCode": "XR2017101701100011",
        "payee": "PAYEE_YIFENG",
        "preferentialTotalAmount": 5,
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "XINGREN"
    },
    {
        "channelCode": "XINGREN_6369",
        "createTime": 1508225435000,
        "customerCode": "3daa789d5165408f84fa706a5fd24c64",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goods": [
            {
                "accountPrice": 10,
                "channelPrice": 2.5,
                "exercisePrice": 10,
                "gift": false,
                "goodsCode": "1000013",
                "goodsName": "阿莫西林分散片 (利莎林)",
                "quantity": 1
            },
            {
                "accountPrice": 12,
                "channelPrice": 23.8,
                "exercisePrice": 12,
                "gift": false,
                "goodsCode": "1000008",
                "goodsName": "阿莫西林分散片 (阿林新)",
                "quantity": 1
            }
        ],
        "goodsTotalAmount": 22,
        "orderCode": "XR20171017011000101",
        "orderState": "RECEIVE_WAITING",
        "outTradeCode": "BD000001",
        "parentOrderCode": "XR2017101701100010",
        "payee": "PAYEE_YIFENG",
        "preferentialTotalAmount": 5,
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "XINGREN",
        "warehouseCode": "6369"
    },
    {
        "channelCode": "XINGREN_6369",
        "createTime": 1508225426000,
        "customerCode": "3daa789d5165408f84fa706a5fd24c64",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goods": [
            {
                "accountPrice": 10,
                "channelPrice": 2.5,
                "exercisePrice": 10,
                "gift": false,
                "goodsCode": "1000013",
                "goodsName": "阿莫西林分散片 (利莎林)",
                "quantity": 1
            },
            {
                "accountPrice": 12,
                "channelPrice": 23.8,
                "exercisePrice": 12,
                "gift": false,
                "goodsCode": "1000008",
                "goodsName": "阿莫西林分散片 (阿林新)",
                "quantity": 1
            }
        ],
        "goodsTotalAmount": 22,
        "orderCode": "XR20171017011000091",
        "orderState": "ORDER_FINISH",
        "outTradeCode": "BD000001",
        "parentOrderCode": "XR2017101701100009",
        "payee": "PAYEE_YIFENG",
        "preferentialTotalAmount": 5,
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "XINGREN",
        "warehouseCode": "6369"
    },
    {
        "channelCode": "XINGREN_6369",
        "createTime": 1508225415000,
        "customerCode": "3daa789d5165408f84fa706a5fd24c64",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goods": [
            {
                "accountPrice": 10,
                "channelPrice": 2.5,
                "exercisePrice": 10,
                "gift": false,
                "goodsCode": "1000013",
                "goodsName": "阿莫西林分散片 (利莎林)",
                "quantity": 1
            },
            {
                "accountPrice": 12,
                "channelPrice": 23.8,
                "exercisePrice": 12,
                "gift": false,
                "goodsCode": "1000008",
                "goodsName": "阿莫西林分散片 (阿林新)",
                "quantity": 1
            }
        ],
        "goodsTotalAmount": 22,
        "orderCode": "XR20171017011000081",
        "orderState": "ORDER_FINISH",
        "outTradeCode": "BD000001",
        "parentOrderCode": "XR2017101701100008",
        "payee": "PAYEE_YIFENG",
        "preferentialTotalAmount": 5,
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "XINGREN",
        "warehouseCode": "6369"
    },
    {
        "channelCode": "XINGREN_6369",
        "createTime": 1508225406000,
        "customerCode": "3daa789d5165408f84fa706a5fd24c64",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goods": [
            {
                "accountPrice": 10,
                "channelPrice": 2.5,
                "exercisePrice": 10,
                "gift": false,
                "goodsCode": "1000013",
                "goodsName": "阿莫西林分散片 (利莎林)",
                "quantity": 1
            },
            {
                "accountPrice": 12,
                "channelPrice": 23.8,
                "exercisePrice": 12,
                "gift": false,
                "goodsCode": "1000008",
                "goodsName": "阿莫西林分散片 (阿林新)",
                "quantity": 1
            }
        ],
        "goodsTotalAmount": 22,
        "orderCode": "XR20171017011000071",
        "orderState": "ORDER_FINISH",
        "outTradeCode": "BD000001",
        "parentOrderCode": "XR2017101701100007",
        "payee": "PAYEE_YIFENG",
        "preferentialTotalAmount": 5,
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "XINGREN",
        "warehouseCode": "6369"
    },
    {
        "channelCode": "XINGREN_6369",
        "createTime": 1508225397000,
        "customerCode": "3daa789d5165408f84fa706a5fd24c64",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goods": [
            {
                "accountPrice": 10,
                "channelPrice": 2.5,
                "exercisePrice": 10,
                "gift": false,
                "goodsCode": "1000013",
                "goodsName": "阿莫西林分散片 (利莎林)",
                "quantity": 1
            },
            {
                "accountPrice": 12,
                "channelPrice": 23.8,
                "exercisePrice": 12,
                "gift": false,
                "goodsCode": "1000008",
                "goodsName": "阿莫西林分散片 (阿林新)",
                "quantity": 1
            }
        ],
        "goodsTotalAmount": 22,
        "orderCode": "XR20171017011000061",
        "orderState": "ORDER_FINISH",
        "outTradeCode": "BD000001",
        "parentOrderCode": "XR2017101701100006",
        "payee": "PAYEE_YIFENG",
        "preferentialTotalAmount": 5,
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "XINGREN",
        "warehouseCode": "6369"
    },
    {
        "channelCode": "XINGREN_6369",
        "createTime": 1508225388000,
        "customerCode": "3daa789d5165408f84fa706a5fd24c64",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goods": [
            {
                "accountPrice": 10,
                "channelPrice": 2.5,
                "exercisePrice": 10,
                "gift": false,
                "goodsCode": "1000013",
                "goodsName": "阿莫西林分散片 (利莎林)",
                "quantity": 1
            },
            {
                "accountPrice": 12,
                "channelPrice": 23.8,
                "exercisePrice": 12,
                "gift": false,
                "goodsCode": "1000008",
                "goodsName": "阿莫西林分散片 (阿林新)",
                "quantity": 1
            }
        ],
        "goodsTotalAmount": 22,
        "orderCode": "XR20171017011000051",
        "orderState": "ORDER_FINISH",
        "outTradeCode": "BD000001",
        "parentOrderCode": "XR2017101701100005",
        "payee": "PAYEE_YIFENG",
        "preferentialTotalAmount": 5,
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "XINGREN",
        "warehouseCode": "6369"
    },
    {
        "channelCode": "XINGREN_6369",
        "createTime": 1508225378000,
        "customerCode": "3daa789d5165408f84fa706a5fd24c64",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goods": [
            {
                "accountPrice": 10,
                "channelPrice": 2.5,
                "exercisePrice": 10,
                "gift": false,
                "goodsCode": "1000013",
                "goodsName": "阿莫西林分散片 (利莎林)",
                "quantity": 1
            },
            {
                "accountPrice": 12,
                "channelPrice": 23.8,
                "exercisePrice": 12,
                "gift": false,
                "goodsCode": "1000008",
                "goodsName": "阿莫西林分散片 (阿林新)",
                "quantity": 1
            }
        ],
        "goodsTotalAmount": 22,
        "orderCode": "XR20171017011000041",
        "orderState": "RECEIVE_WAITING",
        "outTradeCode": "BD000001",
        "parentOrderCode": "XR2017101701100004",
        "payee": "PAYEE_YIFENG",
        "preferentialTotalAmount": 5,
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "XINGREN",
        "warehouseCode": "6369"
    }
]
```

 **NOTICE**  
无

 
---


### 17. 【订单】查询订单状态下订单

- **接口描述**  
查询各状态下订单

- **接口信息**  
> **接口地址：** /openx/query/orderQueryService/listCustomerOrderByState        
> **提交方式：** POST  
> **方法名称：** listCustomerOrderByState    

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|topChannelCode|string|是|顶级渠道|
|customerCode|string|是|会员编号|
|orderState|string|是|订单状态|
|pageNo|int|是|当前页|
|pageSize|int|是|每页大小|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|[i].topChannelCode|string|WXM|顶级渠道编号|
|[i].channelCode|string|WXM_6369|渠道编号|
|[i].createTime|number|1504858027000|创建时间|
|[i].customerCode|string|S00001|会员编号|
|[i].orderCode|string|WXM_63692017090801100010|订单编号|
|[i].orderState|string|29|会员支付金额|
|[i].ordonnanceId|string|000000001||
|[i].outTradeCode|string|BD000001|三方交易号|
|[i].parentOrderCode|string|WXM_63692017090801100010|父订单编号|
|[i].payee|string|PAYEE_YIFENG|收款类型 益丰收款|
|[i].deliveryServiceType|string|DELIVERY_YIFENG|物流类型|
|[i].warehouseCode|string|6369|仓库编码|
|[i].goodsTotalAmount|number|22|商品金额|
|[i].customerNeedPayAmount|number|29|会员支付金额|
|[i].subsidyTotalAmount|number|2||
|[i].remark|string||备注|
|[i].goods|array|[{}]|订单商品|
|[i].goods[i].goodsCode|string|1000000|商品编码|
|[i].goods[i].goodsName|string|东阿阿胶|商品名称|
|[i].goods[i].gift|boolean|false|是否礼品|
|[i].goods[i].exercisePrice|number|10|执行价|
|[i].goods[i].quantity|number|1|数量|
|[i].goods[i].channelPrice|number||渠道商品价格|
|[i].goods[i].guidePrice|number||原价|



 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
  "topChannelCode":"XINGREN",
  "customerCode":"3daa789d5165408f84fa706a5fd24c64",
  "orderState":"RECEIVE_WAITING",
  "pageNo":1,
  "pageSize":10
}
```

返回结果
```json
[
    {
        "channelCode": "XINGREN_6369",
        "createTime": 1508225435000,
        "customerCode": "3daa789d5165408f84fa706a5fd24c64",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goods": [
            {
                "accountPrice": 10,
                "channelPrice": 2.5,
                "exercisePrice": 10,
                "gift": false,
                "goodsCode": "1000013",
                "goodsName": "阿莫西林分散片 (利莎林)",
                "quantity": 1
            },
            {
                "accountPrice": 12,
                "channelPrice": 23.8,
                "exercisePrice": 12,
                "gift": false,
                "goodsCode": "1000008",
                "goodsName": "阿莫西林分散片 (阿林新)",
                "quantity": 1
            }
        ],
        "goodsTotalAmount": 22,
        "orderCode": "XR20171017011000101",
        "orderState": "RECEIVE_WAITING",
        "outTradeCode": "BD000001",
        "parentOrderCode": "XR2017101701100010",
        "payee": "PAYEE_YIFENG",
        "preferentialTotalAmount": 5,
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "XINGREN",
        "warehouseCode": "6369"
    },
    {
        "channelCode": "XINGREN_6369",
        "createTime": 1508225378000,
        "customerCode": "3daa789d5165408f84fa706a5fd24c64",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goods": [
            {
                "accountPrice": 10,
                "channelPrice": 2.5,
                "exercisePrice": 10,
                "gift": false,
                "goodsCode": "1000013",
                "goodsName": "阿莫西林分散片 (利莎林)",
                "quantity": 1
            },
            {
                "accountPrice": 12,
                "channelPrice": 23.8,
                "exercisePrice": 12,
                "gift": false,
                "goodsCode": "1000008",
                "goodsName": "阿莫西林分散片 (阿林新)",
                "quantity": 1
            }
        ],
        "goodsTotalAmount": 22,
        "orderCode": "XR20171017011000041",
        "orderState": "RECEIVE_WAITING",
        "outTradeCode": "BD000001",
        "parentOrderCode": "XR2017101701100004",
        "payee": "PAYEE_YIFENG",
        "preferentialTotalAmount": 5,
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "XINGREN",
        "warehouseCode": "6369"
    },
    {
        "channelCode": "XINGREN_6369",
        "createTime": 1508225370000,
        "customerCode": "3daa789d5165408f84fa706a5fd24c64",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goods": [
            {
                "accountPrice": 10,
                "channelPrice": 2.5,
                "exercisePrice": 10,
                "gift": false,
                "goodsCode": "1000013",
                "goodsName": "阿莫西林分散片 (利莎林)",
                "quantity": 1
            },
            {
                "accountPrice": 12,
                "channelPrice": 23.8,
                "exercisePrice": 12,
                "gift": false,
                "goodsCode": "1000008",
                "goodsName": "阿莫西林分散片 (阿林新)",
                "quantity": 1
            }
        ],
        "goodsTotalAmount": 22,
        "orderCode": "XR20171017011000031",
        "orderState": "RECEIVE_WAITING",
        "outTradeCode": "BD000001",
        "parentOrderCode": "XR2017101701100003",
        "payee": "PAYEE_YIFENG",
        "preferentialTotalAmount": 5,
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "XINGREN",
        "warehouseCode": "6369"
    },
    {
        "channelCode": "XINGREN_6369",
        "createTime": 1508225355000,
        "customerCode": "3daa789d5165408f84fa706a5fd24c64",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goods": [
            {
                "accountPrice": 10,
                "channelPrice": 2.5,
                "exercisePrice": 10,
                "gift": false,
                "goodsCode": "1000013",
                "goodsName": "阿莫西林分散片 (利莎林)",
                "quantity": 1
            },
            {
                "accountPrice": 12,
                "channelPrice": 23.8,
                "exercisePrice": 12,
                "gift": false,
                "goodsCode": "1000008",
                "goodsName": "阿莫西林分散片 (阿林新)",
                "quantity": 1
            }
        ],
        "goodsTotalAmount": 22,
        "orderCode": "XR20171017011000021",
        "orderState": "RECEIVE_WAITING",
        "outTradeCode": "BD000001",
        "parentOrderCode": "XR2017101701100002",
        "payee": "PAYEE_YIFENG",
        "preferentialTotalAmount": 5,
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "XINGREN",
        "warehouseCode": "6369"
    },
    {
        "channelCode": "XINGREN_6369",
        "createTime": 1505890159000,
        "customerCode": "3daa789d5165408f84fa706a5fd24c64",
        "customerNeedPayAmount": 0.12,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goods": [
            {
                "exercisePrice": 0.01,
                "gift": false,
                "goodsCode": "1000000",
                "goodsName": "阿莫西林分散片 (利莎林) 0.25克*12片 华北制药股份有限公司",
                "quantity": 2
            }
        ],
        "goodsTotalAmount": 0.02,
        "orderCode": "XINGREN20170920011000041",
        "orderState": "RECEIVE_WAITING",
        "parentOrderCode": "XINGREN2017092001100004",
        "payee": "PAYEE_YIFENG",
        "preferentialTotalAmount": 0,
        "remark": "",
        "subsidyTotalAmount": 0,
        "topChannelCode": "XINGREN",
        "warehouseCode": "6369"
    },
    {
        "channelCode": "XINGREN_6369",
        "createTime": 1505809857000,
        "customerCode": "3daa789d5165408f84fa706a5fd24c64",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goods": [
            {
                "exercisePrice": 10,
                "gift": false,
                "goodsCode": "1000000",
                "goodsName": "阿莫西林分散片 (利莎林)",
                "quantity": 1
            },
            {
                "exercisePrice": 12,
                "gift": false,
                "goodsCode": "1000001",
                "goodsName": "阿莫西林分散片 (阿林新)",
                "quantity": 1
            }
        ],
        "goodsTotalAmount": 22,
        "orderCode": "XINGREN2017091901100011_1",
        "orderState": "RECEIVE_WAITING",
        "outTradeCode": "BD000001",
        "parentOrderCode": "XINGREN2017091901100011",
        "payee": "PAYEE_YIFENG",
        "preferentialTotalAmount": 5,
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "XINGREN",
        "warehouseCode": "6369"
    },
    {
        "channelCode": "XINGREN_6369",
        "createTime": 1505808246000,
        "customerCode": "3daa789d5165408f84fa706a5fd24c64",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goods": [
            {
                "exercisePrice": 10,
                "gift": false,
                "goodsCode": "1000000",
                "goodsName": "阿莫西林分散片 (利莎林)",
                "quantity": 1
            },
            {
                "exercisePrice": 12,
                "gift": false,
                "goodsCode": "1000001",
                "goodsName": "阿莫西林分散片 (阿林新)",
                "quantity": 1
            }
        ],
        "goodsTotalAmount": 22,
        "orderCode": "XINGREN2017091901100010_1",
        "orderState": "RECEIVE_WAITING",
        "outTradeCode": "BD000001",
        "parentOrderCode": "XINGREN2017091901100010",
        "payee": "PAYEE_YIFENG",
        "preferentialTotalAmount": 5,
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "XINGREN",
        "warehouseCode": "6369"
    },
    {
        "channelCode": "XINGREN_6369",
        "createTime": 1505807667000,
        "customerCode": "3daa789d5165408f84fa706a5fd24c64",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goods": [
            {
                "exercisePrice": 10,
                "gift": false,
                "goodsCode": "1000000",
                "goodsName": "阿莫西林分散片 (利莎林)",
                "quantity": 1
            },
            {
                "exercisePrice": 12,
                "gift": false,
                "goodsCode": "1000001",
                "goodsName": "阿莫西林分散片 (阿林新)",
                "quantity": 1
            }
        ],
        "goodsTotalAmount": 22,
        "orderCode": "XINGREN2017091901100009_1",
        "orderState": "RECEIVE_WAITING",
        "outTradeCode": "BD000001",
        "parentOrderCode": "XINGREN2017091901100009",
        "payee": "PAYEE_YIFENG",
        "preferentialTotalAmount": 5,
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "XINGREN",
        "warehouseCode": "6369"
    },
    {
        "channelCode": "XINGREN_6369",
        "createTime": 1505805276000,
        "customerCode": "3daa789d5165408f84fa706a5fd24c64",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goods": [
            {
                "exercisePrice": 10,
                "gift": false,
                "goodsCode": "1000000",
                "goodsName": "阿莫西林分散片 (利莎林)",
                "quantity": 1
            },
            {
                "exercisePrice": 12,
                "gift": false,
                "goodsCode": "1000001",
                "goodsName": "阿莫西林分散片 (阿林新)",
                "quantity": 1
            }
        ],
        "goodsTotalAmount": 22,
        "orderCode": "XINGREN2017091901100008_1",
        "orderState": "RECEIVE_WAITING",
        "outTradeCode": "BD000001",
        "parentOrderCode": "XINGREN2017091901100008",
        "payee": "PAYEE_YIFENG",
        "preferentialTotalAmount": 5,
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "XINGREN",
        "warehouseCode": "6369"
    },
    {
        "channelCode": "XINGREN_6369",
        "createTime": 1505798849000,
        "customerCode": "3daa789d5165408f84fa706a5fd24c64",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goods": [
            {
                "accountPrice": 12,
                "exercisePrice": 12,
                "gift": false,
                "goodsCode": "1007566",
                "goodsName": "阿莫西林分散片 (阿林新)",
                "quantity": 1
            }
        ],
        "goodsTotalAmount": 22,
        "orderCode": "XINGREN2017091901100006_1",
        "orderState": "RECEIVE_WAITING",
        "outTradeCode": "BD000001",
        "parentOrderCode": "XINGREN2017091901100006",
        "payee": "PAYEE_YIFENG",
        "preferentialTotalAmount": 5,
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "XINGREN",
        "warehouseCode": "6369"
    }
]
```

 **NOTICE**  
无

 
---

### 18. 【订单】查询订单详情

- **接口描述**  
查询订单详情

- **接口信息**  
> **接口地址：** /openx/query/orderQueryService/getOrderDetail          
> **提交方式：** POST  
> **方法名称：** getOrderDetail    

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|orderCode|string|是|渠道编码|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|topChannelCode|string|WXM|顶级渠道编号|
|channelCode|string|WXM_6369|渠道编号|
|createTime|number|1504858027000|创建时间|
|customerCode|string|S00001|会员编号|
|orderCode|string|WXM_63692017090801100010|订单编号|
|orderState|string|29|会员支付金额|
|ordonnanceId|string|000000001||
|outTradeCode|string|BD000001|三方交易号|
|parentOrderCode|string|WXM_63692017090801100010|父订单编号|
|payee|string|PAYEE_YIFENG|收款类型 益丰收款|
|deliveryServiceType|string|DELIVERY_YIFENG|物流类型|
|warehouseCode|string|6369|仓库编码|
|goodsTotalAmount|number|22|商品金额|
|customerNeedPayAmount|number|29|会员支付金额|
|subsidyTotalAmount|number|2||
|preferentialTotalAmount|number|5|优惠总金额|
|remark|string||备注|
|goods|array|[{}]|订单商品|
|goods[i].goodsCode|string|1000000|商品编码|
|goods[i].goodsName|string|东阿阿胶|商品名称|
|goods[i].gift|boolean|false|是否礼品|
|goods[i].accountPrice|number|10|下账金额|
|goods[i].exercisePrice|number|10|执行价|
|goods[i].quantity|number|1|数量|
|goods[i].channelPrice|number||渠道商品价格|
|goods[i].guidePrice|number||原价|
|charges|array|[{}]|费用|
|charges[i].chargeType|string|DEDUCT,FREIGHT,NORMAL,PREFERENTIAL,SUBSIDY|费用类型:运费,补贴,打包费,优惠|
|charges[i].chargeCode|string|freight,PACKING,preferitial,subsidy|费用编码|
|charges[i].amount|number|9|金额|
|charges[i].remark|string||备注|
|referrer|object|{}||
|referrer.referrerId|string|referid1||
|referrer.referrerName|string|refername||
|additionalInfo|array|[{}]|额外信息|
|additionalInfo[i].infoCode|string|小票号|额外信息key|
|additionalInfo[i].infoValue|string|BD000001|额外信息value|


 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"orderCode":"XR2017102601100002"
}
```

返回结果
```json
{
    "additionalInfo": [
        {
            "infoCode": "小票号",
            "infoValue": "BD000001"
        }
    ],
    "channelCode": "XINGREN_6369",
    "charges": [
        {
            "amount": 5,
            "chargeCode": "couponId",
            "chargeType": "PREFERENTIAL",
            "remark": "优惠"
        },
        {
            "amount": 9,
            "chargeCode": "freight",
            "chargeType": "DEDUCT",
            "remark": "运费"
        },
        {
            "amount": 9,
            "chargeCode": "freight",
            "chargeType": "FREIGHT",
            "remark": "补贴"
        },
        {
            "amount": 3,
            "chargeCode": "PACKING",
            "chargeType": "NORMAL",
            "remark": "打包费"
        },
        {
            "amount": 2,
            "chargeCode": "subsidy",
            "chargeType": "SUBSIDY"
        }
    ],
    "createTime": 1508988633000,
    "customerCode": "3daa789d5165408f84fa706a5fd24c64",
    "customerNeedPayAmount": 29,
    "deliveryServiceType": "DELIVERY_YIFENG",
    "goods": [
        {
            "channelPrice": 2.5,
            "exercisePrice": 10,
            "gift": false,
            "goodsCode": "1000013",
            "goodsName": "阿莫西林分散片 (利莎林)",
            "guidePrice": 2.5,
            "quantity": 1
        },
        {
            "channelPrice": 23.8,
            "exercisePrice": 12,
            "gift": false,
            "goodsCode": "1000008",
            "goodsName": "阿莫西林分散片 (阿林新)",
            "guidePrice": 23.8,
            "quantity": 1
        }
    ],
    "goodsTotalAmount": 22,
    "invoice": {
        "content": "comtent",
        "invoiceCode": "ddddd",
        "orderCode": "XR2017102601100002",
        "title": "个人发票"
    },
    "orderCode": "XR2017102601100002",
    "orderState": "PAYMENT_WAITING",
    "outTradeCode": "BD000001",
    "parentOrderCode": "XR2017102601100002",
    "payee": "PAYEE_YIFENG",
    "preferentialTotalAmount": 5,
    "referrer": {
        "referrerId": "referid1",
        "referrerName": "refername"
    },
    "remark": "Remark",
    "subsidyTotalAmount": 2,
    "topChannelCode": "XINGREN"
}
```

 **NOTICE**  
无

 
---



## 【customer】-proxy 个人中心  


### 1. 【购物车】查询购物车商品数量总和  

- **接口描述**  
根据会员编号和顶级渠道查询购物车商品数量 

- **接口信息**  
> **接口地址：** /openx/customer/shopcartService/queryGoodsCount   
> **提交方式：** POST  
> **方法名称：** queryGoodsCount  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|customerId|string|是|会员编号|
|channel|string|是|顶级渠道编码|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|


 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"customerId":"647958c21f03445a9bb8fbcadfc82f30",
	"channel":"WXM"
}
```

返回结果
```json
0
```

 **NOTICE**  
无

 
---

### 2. 【购物车】查询购物车商品信息  

- **接口描述**  
查询会员某渠道的购物车详情

- **接口信息**  
> **接口地址：** /openx/customer/shopcartService/queryShopcartInfo    
> **提交方式：** POST  
> **方法名称：** queryShopcartInfo  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|customerId|string|是|会员编号|
|channel|string|是|顶级渠道编码|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|[i].goodsCode|string|1012396|商品编码|
|[i].quantity|int|1|商品数量|

 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"customerId":"647958c21f03445a9bb8fbcadfc82f30",
	"channel":"WXM"
}
```

返回结果
```json
[
    {
        "goodsCode": "1012396",
        "quantity": 1
    }
]
```

 **NOTICE**  
无

 
---

### 3. 【购物车】添加商品/增加商品数量  

- **接口描述**  
新增商品到购物车或者新增商品数量  

- **接口信息**  
> **接口地址：** /openx/customer/shopcartService/addGoods    
> **提交方式：** POST  
> **方法名称：** addGoods  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|customerId|string|是|会员编号|
|channel|string|是|顶级渠道编号|
|goodsList|array|是|商品列表|
|goodsList[i].goodsCode|string|是|商品编码|
|goodsList[i].quantity|int|是|商品数量|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|


 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"customerId":"647958c21f03445a9bb8fbcadfc82f30",
	"channel":"WXM",
	"goodsList":[{
		"goodsCode":"1012396",
		"quantity":1
	}]
}
```

返回结果
```json

```

 **NOTICE**  
无

 
---

### 4. 【购物车】减少商品数量  

- **接口描述**  
购物车中商品数量减少

- **接口信息**  
> **接口地址：** /openx/customer/shopcartService/subGoods      
> **提交方式：** POST  
> **方法名称：** subGoods    

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|customerId|string|是|会员编号|
|channel|string|是|顶级渠道编号|
|goodsList|array|是|商品列表|
|goodsList[i].goodsCode|string|是|商品编码|
|goodsList[i].quantity|int|是|商品数量|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|


 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"customerId":"647958c21f03445a9bb8fbcadfc82f30",
	"channel":"WXM",
	"goodsList":[{
		"goodsCode":"1012396",
		"quantity":1
	}]
}
```

返回结果
```json

```

 **NOTICE**  
无

 
---


### 5. 【购物车】删除购物车商品  

- **接口描述**  
购物车商品删除  

- **接口信息**  
> **接口地址：** /openx/customer/shopcartService/deleteGoods    
> **提交方式：** POST  
> **方法名称：** deleteGoods  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|customerId|string|是|会员编号|
|channel|string|是|顶级渠道编号|
|goodsCodeList|array|是|商品编码列表|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|


 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"customerId":"647958c21f03445a9bb8fbcadfc82f30",
	"channel":"WXM",
	"goodsCodeList":["1012396"]
}
```

返回结果
```json

```

 **NOTICE**  
无

 
---


## 【trade】-proxy 交易   

### 1. 【订单】创建订单  

- **接口描述**  
购物车商品删除  

- **接口信息**  
> **接口地址：** /proxy/openx/trade/orderService/submitNormalOrder    
> **提交方式：** POST  
> **方法名称：** submitNormalOrder   

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|orderRequest|object|true|订单请求对象|
|orderRequest.order|object|是|订单对象|
|orderRequest.order.topChannelCode|string|是|顶级渠道编码|
|orderRequest.order.channelCode|string|是|渠道编码|
|orderRequest.order.customerCode|string|是|会员编号|
|orderRequest.order.customerNeedPayAmount|number|是|会员实付|
|orderRequest.order.goodsTotalAmount|number|是|商品总额|
|orderRequest.order.deliveryServiceType|string|是|物流配送类型 DELIVERY_YIFENG|
|orderRequest.order.payee|string|是|支付方式 PAYEE_YIFENG|
|orderRequest.order.remark|string|是|订单备注|
|orderRequest.order.goods|array|是|订单商品|
|orderRequest.order.goods[i].exercisePrice|number|是|订单商品执行价 这里 channelPrice|
|orderRequest.order.goods[i].gift|boolean|是|订单商品是否礼品 false|
|orderRequest.order.goods[i].goodsCode|string|是|订单商品编码|
|orderRequest.order.goods[i].goodsName|string|是|订单商品名称|
|orderRequest.order.goods[i].quantity|number|是|订单商品数量|
|orderRequest.order.charges|array|是|订单各项费用|
|orderRequest.order.charges[i].amount|string|是|费用金额|
|orderRequest.order.charges[i].chargeCode|string|是|费用编码这里券可以用Q+券编码|
|orderRequest.order.charges[i].chargeType|string|是|费用类型 PREFERENTIAL:券优惠 FREIGHT:运费 |
|orderRequest.order.charges[i].remark|string|是|费用备注|
|orderRequest.order.invoice|object|是|发票|
|orderRequest.order.invoice.title|string|是|发票抬头|
|orderRequest.order.invoice.content|string|是|发票内容|
|orderRequest.couponCodes|array|否|券编码列表[""]|
|orderRequest.logisticInfo|object|是|物流对象|
|orderRequest.logisticInfo.deliveryType|string|是|物流类型 NORMAL:普通快递 SELF_PICK:自提|
|orderRequest.logisticInfo.receiver|object|是|收货人信息|
|orderRequest.logisticInfo.receiver.name|string|是|收货人姓名|
|orderRequest.logisticInfo.receiver.phone|string|是|收货人电话|
|orderRequest.logisticInfo.receiver.provinceCode|string|是|收货人省级编码|
|orderRequest.logisticInfo.receiver.provinceName|string|是|收货人市级编码|
|orderRequest.logisticInfo.receiver.cityCode|string|是|收货人市级编码|
|orderRequest.logisticInfo.receiver.cityName|string|是|收货人市级名称|
|orderRequest.logisticInfo.receiver.districtCode|string|是|收货人地区编码|
|orderRequest.logisticInfo.receiver.districtName|string|是|收货人地区名称|
|orderRequest.logisticInfo.receiver.detailAddress|string|是|收货人详细地址|
|orderRequest.logisticInfo.receiver.location|object|是|收货人地址经纬度|
|orderRequest.logisticInfo.receiver.location.latitude|number|是|收货人地址纬度|
|orderRequest.logisticInfo.receiver.location.longitude|number|是|收货人地址经度|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
||string|YFJX2017103001100006|订单编号|

 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
    "orderRequest": {
        "couponCodes": [
            "301382552066"
        ],
        "logisticInfo": {
            "deliveryType": "NORMAL",
            "receiver": {
                "cityCode": "430100",
                "cityName": "长沙市",
                "detailAddress": "金洲大道68号",
                "districtCode": "430104",
                "districtName": "岳麓区",
                "name": "测试",
                "phone": "13392460103",
                "provinceCode": "430000",
                "provinceName": "湖南省",
                "location": {
                    "latitude": 20.12121,
                    "longitude": 34.890808
                 }
            }
        },
        "order": {
            "channelCode": "YFJX_5742",
            "charges": [
                {
                    "amount": 10,
                    "chargeCode": "Q300135566398",
                    "chargeType": "PREFERENTIAL",
                    "remark": "券优惠"
                },
                {
                    "amount": 6,
                    "chargeCode": "freight",
                    "chargeType": "FREIGHT",
                    "remark": "运费"
                }
            ],
            "customerCode": "3daa789d5165408f84fa706a5fd24c64",
            "customerNeedPayAmount": 50.3,
            "deliveryServiceType": "DELIVERY_YIFENG",
            "goods": [
                {
                    "exercisePrice": 13.3,
                    "gift": false,
                    "goodsCode": "1000013",
                    "goodsName": "阿莫西林分散片 (利莎林)",
                    "quantity": 3
                },
                {
                    "exercisePrice": 3.6,
                    "gift": false,
                    "goodsCode": "1000001",
                    "goodsName": "大写的药品名",
                    "quantity": 4
                }
            ],
            "goodsTotalAmount": 54.3,
            "invoice": {
                "content": "发票内容",
                "title": "发票抬头"
            },
            "payee": "PAYEE_YIFENG",
            "referrer": {
                "referrerId": "推荐人ID",
                "referrerName": "推荐人姓名"
            },
            "remark": "测试创建订单备注",
            "topChannelCode": "YFJX",
            "goodsChannelCode":"YFJX_CS"
        }
    }
}
```

返回结果
```json
"YFJX2017103001100006"
```

 **NOTICE**  
 > 物流类型 deliveryType：SELF_PICK 费用无运费

 
---

### 2. 【订单】 取消订单  

- **接口描述**  
用户取消订单  

- **接口信息**  
> **接口地址：** /openx/trade/orderService/cancelOrder    
> **提交方式：** POST  
> **方法名称：** cancelOrder   

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|orderCode|string|是|订单编号|
|remark|string|是|取消订单原因备注|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
||boolean|true|取消订单结果|

 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"orderCode":"YFJX2017103001100006",
	"remark":"测试取消"
}
```

返回结果
```json
true
```

 **NOTICE**  
无

 
---


### 3. 【订单】 删除订单  

- **接口描述**  
  

- **接口信息**  
> **接口地址：** /openx/trade/orderService/deleteOrder    
> **提交方式：** POST  
> **方法名称：** deleteOrder  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|order|string|是|订单编号|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
||boolean|true|取消订单结果|

 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"order":"YFJX2017103001100006"
}
```

返回结果
```json
true
```

 **NOTICE**  
无

 
---


### 4. 【订单】 确认收货订单  

- **接口描述**  
  

- **接口信息**  
> **接口地址：** /openx/trade/orderService/confirmReceived    
> **提交方式：** POST  
> **方法名称：** confirmReceived   

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|orderCode|string|true|订单编号|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
||boolean|true|返回结果|

 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"orderCode":"YFJX2017103001100006"
}
```

返回结果
```json
true
```

 **NOTICE**  
无

 
---.


### 5. 【支付】预支付

- **接口描述**  
  申请预支付 获取调用微信支付api的参数

- **接口信息**  
> **接口地址：** /openx/trade/paymentService/createPrePayment    
> **提交方式：** POST  
> **方法名称：** createPrePayment   

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|prePayment|object|是|预支付对象|
|prePayment.channelCode|string|是|顶级渠道编码|
|prePayment.outTradeCode|string|是|订单编码|
|prePayment.paymentType|string|是|支付类型 WX_H5:公众号H5 WX_WCX:小程序|
|prePayment.thirdPartyCode|string|是|openid等|
|prePayment.title|string|是|支付标题|
|prePayment.amount|number|是|金额|
|prePayment.remark|string|是|备注|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|paymentCode|string|59f6d2d179290f756d47c3f4|交易流水|
|tradeCode|string||订单编号|
|preStr|string||预支付编码|

 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
    "prePayment": {
        "amount": 10,
        "channelCode": "YFJX",
        "outTradeCode": "YFJX2017103001100002",
        "paymentType": "WX_H5",
        "remark": "订单备注",
        "thirdPartyCode": "oxy7kwI3xBovydQbsDQzKbCwZIl8",
        "title": "订单给钱"
    }
}
```

返回结果
```json
{
    "paymentCode": "59f6d2d179290f756d47c3f4",
    "preStr": "{\"appId\":\"wx8df2c1ef060c79fd\",\"timeStamp\":\"1509348049\",\"signType\":\"MD5\",\"package\":\"prepay_id=wx20171030152126f6bc3070940101485356\",\"nonceStr\":\"fvb0p773ycx84vzj15n538nvasnbtd8x\",\"paySign\":\"1114BD49D71BDBB901AFA2EC6C7E05DE\"}",
    "tradeCode": "YFJX2017103001100002"
}
```

 **NOTICE**  
无

 
---

### 6. 【支付】 获取支付结果  

- **接口描述**  
获取支付结果 结果空表示 没有支付 或者 状态为 NOPAY 

- **接口信息**  
> **接口地址：** /openx/trade/paymentService/getOrderPaymentStatus    
> **提交方式：** POST  
> **方法名称：** getOrderPaymentStatus   

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|orderCode|string|true|订单编号|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|paymentStatus|string|NOTPAY|支付状态 NOTPAY:未支付 PAID:已支付 FAILED:失败 REFUND:已退款 CLOSE:关闭|
|paymentCode|string||支付编码|

 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"orderCode":"YFJX2017103001100002"
}
```

返回结果
```json
{
    "paymentCode": "59f6d2d179290f756d47c3f4",
    "paymentStatus": "NOTPAY"
}
```

 **NOTICE**  
无

 
---

## 【coupon】-proxy 券服务    

### 1. 【我的券】 查询用户有效券的数量

- **接口描述**  
查询用户有效券的数量   

- **接口信息**  
> **接口地址：** /coupon/useCouponService/queryCouponCount    
> **提交方式：** POST  
> **方法名称：** queryCouponCount  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|customerCode|string|是|会员编号|
|channelPath|string|是|渠道路径YFJX,YFJX_CS,YFJX_CSZD  这里业务为YFJX 顶级渠道|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
||number|1|用户可用券数目|

 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"customerCode":"3daa789d5165408f84fa706a5fd24c64",
	"channelPath":"YFJX"
}
```

返回结果
```json
1
```

 **NOTICE**  
无

 
---


### 2. 【我的券】查询用户所有券  

- **接口描述**  
查询用户券 按照状态(待用>已用>失效)，类型(整单>品类)，时间倒序)排序  

- **接口信息**  
> **接口地址：** /coupon/useCouponService/queryCouponListPage    
> **提交方式：** POST  
> **方法名称：** queryCouponListPage  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|customerCode|string|是|会员编号|
|channelPath|string|是|渠道路径 这里是顶级渠道|
|status|string|是|AVAILABLE, 可为null|
|page|int|是|页码|
|pageSize|int|是|每页大小|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|beginDate|number|1509033601000|开始日期|
|expireDate|number|1512057599000|过期日期|
|code|string|300135566398|券编码|
|couponMoney|number|20|券值|
|createDate|number|1509075398000|创建时间|
|title|string|益丰精选 满30-20|标题|
|type|string|ALL|全部|
|ruleDesc|string|满30-20 全渠道通用|券规则描述|
|desc|string|益丰精选 满30-20|券描述|
|status|string|AVAILABLE,USED,EXPIRED,LOCKED|状态 待用 已用 过期 锁定|


 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"customerCode":"3daa789d5165408f84fa706a5fd24c64",
	"channelPath":"YFJX",
	"status":"AVAILABLE",
	"page":1,
	"pageSize":10
	
}
```

返回结果
```json
[
    {
        "beginDate": 1509033601000,
        "code": "300135566398",
        "couponMoney": 20,
        "createDate": 1509075398000,
        "desc": "益丰精选 满30-20",
        "expireDate": 1512057599000,
        "ruleDesc": "满30-20 全渠道通用",
        "status": "AVAILABLE",
        "title": "益丰精选 满30-20 1",
        "type": "ALL"
    },
    {
        "beginDate": 1509033601000,
        "code": "301382552066",
        "couponMoney": 20,
        "createDate": 1509093462000,
        "desc": "满30-20 说明",
        "expireDate": 1512057599000,
        "ruleDesc": "YFJX_5742 使用",
        "status": "AVAILABLE",
        "title": "满30-20 名称",
        "type": "ALL"
    }
]
```

 **NOTICE**  
无

 
---



### 3. 【券】领券  

- **接口描述**  
用户领券   

- **接口信息**  
> **接口地址：** /coupon/useCouponService/autoGetCoupon    
> **提交方式：** POST  
> **方法名称：** autoGetCoupon  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|customerCode|string|是|会员编号|
|phone|string|否|手机号码|
|channelPath|string|YFJX,YFJX_CS,YFJX_CSZD|渠道路径|
|templateId|string||券模版id|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
||string|"300135566398"|领取到的券的密码|

 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"customerCode":"3daa789d5165408f84fa706a5fd24c64",
	"channelPath":"YFJX,YFJX_CS,YFJX_CSZD",
	"phone":null,
	"templateId":"59f2a8e84f89b21ae9ded24d"
}
```

返回结果
```json
"300135566398"
```

 **NOTICE**  
无

 
---


### 4. 【券】查询用户可以领用的券  

- **接口描述**  
查询用户可以领用的券    

- **接口信息**  
> **接口地址：** /coupon/useCouponService/listReceivableCouponPage   
> **提交方式：** POST  
> **方法名称：** listReceivableCouponPage  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|channelPathList|string|是|渠道路径列表|
|customerCode|string|是|会员编号|
|page|int|是|当前页|
|pageSize|int|是|每页大小|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|availableCouponStatus|string|AVAILABLE,UNAVAILABLE,NONE|可用券状态 可领 已领 已领完|
|availableNumber|number||可用数量|
|couponDesc|string||券面描述|
|couponMoney|number||券面值|
|couponName|string||方案名称|
|couponRuleDesc|string||券规则描述|
|couponTakeStartDate|string||券领取开始时间|
|couponTakeStopDate|string||券领取结束时间|
|couponTitle|string||券面名称|
|couponType|string||券类型|
|maxValidityDate|number||券有效期|
|maxValidityDateType|string||时间类型|
|scopeList|string||券适用范围|
|takeEffectType|string||生效方式|
|templateStartDate|number||模板生效开始时间|
|templateStopDate|number||模板生效结束时间|
|useCondition|string||满减条件|
|uuid|string||券模板编码|

 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"channelPathList":["YFJX,YFJX_CS,YFJX_5742"],
	"customerCode":"3daa789d5165408f84fa706a5fd24c64",
	"page":1,
	"pageSize":10
}
```

返回结果
```json
[
    {
        "availableCouponStatus": "AVAILABLE",
        "availableNumber": 0,
        "couponDesc": "满30-20 说明",
        "couponMoney": 20,
        "couponName": "益丰精选券模版2",
        "couponRuleDesc": "YFJX_5742 使用",
        "couponTakeStartDate": 1509033601000,
        "couponTakeStopDate": 1512057599000,
        "couponTitle": "满30-20 名称",
        "couponType": "ALL",
        "maxValidityDate": 3,
        "maxValidityDateType": "MONTH",
        "scopeList": [
            "YFJX,YFJX_CS,YFJX_5742"
        ],
        "takeEffectType": "RIGHTNOW",
        "templateStartDate": 1509033601000,
        "templateStopDate": 1512057599000,
        "useCondition": 30,
        "uuid": "59f2f0454f89b21ae9ded24e"
    },
    {
        "availableCouponStatus": "AVAILABLE",
        "availableNumber": 0,
        "couponDesc": "益丰精选 满30-20",
        "couponMoney": 20,
        "couponName": "益丰精选券模版1",
        "couponRuleDesc": "满30-20 全渠道通用",
        "couponTakeStartDate": 1509033601000,
        "couponTakeStopDate": 1511971199000,
        "couponTitle": "益丰精选 满30-20 1",
        "couponType": "ALL",
        "maxValidityDate": 3,
        "maxValidityDateType": "MONTH",
        "scopeList": [
            "YFJX,YFJX_CS,YFJX_5742"
        ],
        "takeEffectType": "RIGHTNOW",
        "templateStartDate": 1509033601000,
        "templateStopDate": 1512057599000,
        "useCondition": 32,
        "uuid": "59f2a8e84f89b21ae9ded24d"
    }
]
```

 **NOTICE**  
无

 
---


### 5. 【券】订单可用券  

- **接口描述**  
订单信息查询可用券  

- **接口信息**  
> **接口地址：** /coupon/useCouponService/listCouponByOrderInfo  
> **提交方式：** POST  
> **方法名称：** listCouponByOrderInfo  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|customerCode|string|是|会员编号|
|channelPath|string|YFJX,YFJX_CS,YFJX_CSZD|渠道路径|
|goodsList|array|是|订单商品列表|
|goodsList[i].goodsCode|string||商品编码|
|goodsList[i].quantity|number||订单商品数量|
|goodsList[i].price|number||订单商品单价|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|beginDate|number|1509033601000|开始日期|
|expireDate|number|1512057599000|过期日期|
|code|string|300135566398|券编码|
|couponMoney|number|20|券值|
|createDate|number|1509075398000|创建时间|
|title|string|益丰精选 满30-20|标题|
|type|string|ALL|全部|
|ruleDesc|string|满30-20 全渠道通用|券规则描述|
|desc|string|益丰精选 满30-20|券描述|
|status|string|AVAILABLE,USED,EXPIRED,LOCKED|状态 待用 已用 过期 锁定|



 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"customerCode":"3daa789d5165408f84fa706a5fd24c64",
	"channelPath":"YFJX,YFJX_CS,YFJX_5742",
	"goodsList":[{
		"goodsCode":"1000013",
		"quantity":3,
		"price":13.3
	}]
}
```

返回结果
```json
[
    {
        "beginDate": 1509033601000,
        "code": "300135566398",
        "couponMoney": 20,
        "createDate": 1509075398000,
        "desc": "益丰精选 满30-20",
        "expireDate": 1512057599000,
        "ruleDesc": "满30-20 全渠道通用",
        "status": "AVAILABLE",
        "title": "益丰精选 满30-20 1",
        "type": "ALL"
    },
    {
        "beginDate": 1509033601000,
        "code": "301382552066",
        "couponMoney": 20,
        "createDate": 1509093462000,
        "desc": "满30-20 说明",
        "expireDate": 1512057599000,
        "ruleDesc": "YFJX_5742 使用",
        "status": "AVAILABLE",
        "title": "满30-20 名称",
        "type": "ALL"
    }
]
```

 **NOTICE**  
无

 
---


### 6. 【券】商品可领券  

- **接口描述**  
商品信息查询可领取的券  

- **接口信息**  
> **接口地址：** /coupon/couponCaseService/listCouponCaseByGoods   
> **提交方式：** POST  
> **方法名称：** listCouponCaseByGoods  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|customerCode|string|是|会员编号|
|channelPath|string|YFJX,YFJX_CS,YFJX_CSZD|渠道路径|
|goodsCode|string|是|商品编码|
|page|object|是|分页对象|
|page.page|int|是|当前页|
|page.pageNum|int|是|每页大小|
|sortList|array|是|[""],可为null|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|availableCouponStatus|string|AVAILABLE,UNAVAILABLE,NONE|可用券状态 可领 已领 已领完|
|availableNumber|number||可用数量|
|couponDesc|string||券面描述|
|couponMoney|number||券面值|
|couponName|string||方案名称|
|couponRuleDesc|string||券规则描述|
|couponTakeStartDate|string||券领取开始时间|
|couponTakeStopDate|string||券领取结束时间|
|couponTitle|string||券面名称|
|couponType|string||券类型|
|maxValidityDate|number||券有效期|
|maxValidityDateType|string||时间类型|
|takeEffectType|string||生效方式|
|templateStartDate|number||模板生效开始时间|
|templateStopDate|number||模板生效结束时间|
|useCondition|string||满减条件|
|uuid|string||券模板编码|

 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"customerCode":"3daa789d5165408f84fa706a5fd24c64",
	"channelPath":"YFJX,YFJX_CS,YFJX_5742",
	"goodsCode":"1000013",
	"page":{
		"page":1,
		"pageNum":10
	},
	"sortList":["COUPON_AMOUNT_DESC","CRT_TIME_DESC"]
}
```

返回结果
```json
[
    {
        "availableCouponStatus": "AVAILABLE",
        "availableNumber": 0,
        "couponDesc": "满30-20 说明",
        "couponMoney": 20,
        "couponName": "益丰精选券模版2",
        "couponRuleDesc": "YFJX_5742 使用",
        "couponTakeStartDate": 1509033601000,
        "couponTakeStopDate": 1512057599000,
        "couponTitle": "满30-20 名称",
        "couponType": "ALL",
        "maxValidityDate": 3,
        "maxValidityDateType": "MONTH",
        "takeEffectType": "RIGHTNOW",
        "templateStartDate": 1509033601000,
        "templateStopDate": 1512057599000,
        "useCondition": 30,
        "uuid": "59f2f0454f89b21ae9ded24e"
    },
    {
        "availableCouponStatus": "AVAILABLE",
        "availableNumber": 0,
        "couponDesc": "益丰精选 满30-20",
        "couponMoney": 20,
        "couponName": "益丰精选券模版1",
        "couponRuleDesc": "满30-20 全渠道通用",
        "couponTakeStartDate": 1509033601000,
        "couponTakeStopDate": 1511971199000,
        "couponTitle": "益丰精选 满30-20 1",
        "couponType": "ALL",
        "maxValidityDate": 3,
        "maxValidityDateType": "MONTH",
        "takeEffectType": "RIGHTNOW",
        "templateStartDate": 1509033601000,
        "templateStopDate": 1512057599000,
        "useCondition": 32,
        "uuid": "59f2a8e84f89b21ae9ded24d"
    }
]
```

 **NOTICE**  
无

 
---

### 7. 【券】商品可用券  

- **接口描述**  
商品信息查询可用券  

- **接口信息**  
> **接口地址：** /coupon/myCouponService/listCouponPageByGoods  
> **提交方式：** POST  
> **方法名称：** listCouponPageByGoods  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|customerCode|string|是|会员编号|
|channelPath|string|YFJX,YFJX_CS,YFJX_CSZD|渠道路径|
|goodsCode|string|是|商品编码|
|page|object|是|分页对象|
|page.page|int|是|当前页|
|page.pageNum|int|是|每页大小|
|sortList|array|是|[""],可为null|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|beginDate|number|1509033601000|开始日期|
|expireDate|number|1512057599000|过期日期|
|code|string|300135566398|券编码|
|couponMoney|number|20|券值|
|createDate|number|1509075398000|创建时间|
|title|string|益丰精选 满30-20|标题|
|type|string|ALL|全部|
|ruleDesc|string|满30-20 全渠道通用|券规则描述|
|desc|string|益丰精选 满30-20|券描述|
|status|string|AVAILABLE,USED,EXPIRED,LOCKED|状态 待用 已用 过期 锁定|

 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"customerCode":"3daa789d5165408f84fa706a5fd24c64",
	"channelPath":"YFJX,YFJX_CS,YFJX_5742",
	"goodsCode":"1000013",
	"page":{
		"page":1,
		"pageNum":10
	},
	"sortList":["COUPON_AMOUNT_DESC","CRT_TIME_DESC"]
}
```

返回结果
```json
[
    {
        "beginDate": 1509033601000,
        "code": "300135566398",
        "couponMoney": 20,
        "createDate": 1509075398000,
        "desc": "益丰精选 满30-20",
        "expireDate": 1512057599000,
        "ruleDesc": "满30-20 全渠道通用",
        "status": "AVAILABLE",
        "title": "益丰精选 满30-20 1",
        "type": "ALL"
    }
]
```

 **NOTICE**  
无

---  

## 【配置中心】-proxy 配置中心服务

### 1. 【查询配置】查询配置  

- **接口描述**  
> 查询配置  

- **接口信息**  
> **接口地址：** /conf/apps/conf/ConfManageService/query  
> **提交方式：** POST  
> **方法名称：** sendCode  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|appId|string|是|应用id silk-road|
|stage|string|是|阶段 develop testing product|
|verNo|string|是|版本 1.0|

- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|


 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"appId":"silk-road",
	"stage":"testing",
	"verNo":"1.0"
}
```

返回结果
```json
{
    "appId": "silk-road",
    "id": "5a0040974a63900a8a2bf788",
    "items": [
        {
            "confId": "5a0040974a63900a8a2bf788",
            "id": "5a0040974a63900a8a2bf789",
            "key": "const.couponNewUser",
            "lastModify": 1509965975000,
            "value": "59feb37947422372661b142b"
        },
        {
            "confId": "5a0040974a63900a8a2bf788",
            "id": "5a0040974a63900a8a2bf78f",
            "key": "const.serverCityCode",
            "lastModify": 1509965975000,
            "value": "430100,430200,430300,430400,430500,430600,430700,430800,430900,431000,431100,431200,431300,420100,320100,310100,360000"
        },
        {
            "confId": "5a0040974a63900a8a2bf788",
            "id": "5a0040974a63900a8a2bf78a",
            "key": "proxy.rule",
            "lastModify": 1509965975000,
            "value": "[{\"pattern\":\"/openx/geohash/GeoService/*\",\"host\":\"http://tss-lbs.yifengx.com\",\"desc\":\"geohash 服务\"},{\"pattern\":\"/openx/memberopen/**\",\"host\":\"http://member-open-te.yifengx.com\",\"desc\":\"member-open\"},{\"pattern\":\"/openx/query/**\",\"host\":\"http://ecp-query-te.yifengx.com\",\"desc\":\"query 查询服务\"},{\"pattern\":\"/openx/trade/**\",\"host\":\"http://ecp-trade-te.yifengx.com\",\"desc\":\"trade 交易服务\"},{\"pattern\":\"/openx/customer/shopcartService/*\",\"host\":\"http://customer-te.yifengx.com\",\"desc\":\"个人中心 购物车\"},{\"pattern\":\"/coupon/**\",\"host\":\"http://coupon-te.yifengx.com\",\"desc\":\"券系统\"},{\"pattern\":\"/lbs/RegionService/**\",\"host\":\"https://lbs.talkyun.com:9981\",\"desc\":\"lbs\"},{\"pattern\":\"/conf/apps/conf/**\",\"host\":\"https://next.yifengx.com\",\"desc\":\"conf 配置中心\"}]"
        },
        {
            "confId": "5a0040974a63900a8a2bf788",
            "id": "5a0040974a63900a8a2bf78b",
            "key": "rest.memeberPreServiceUrl",
            "lastModify": 1509965975000,
            "remark": "batch import",
            "value": "http://member-open-te.yifengx.com/openx/"
        },
        {
            "confId": "5a0040974a63900a8a2bf788",
            "id": "5a0040974a63900a8a2bf78c",
            "key": "sms.url",
            "lastModify": 1509965975000,
            "remark": "batch import",
            "value": "https://sms-tss.yifengx.com"
        },
        {
            "confId": "5a0040974a63900a8a2bf788",
            "id": "5a0040974a63900a8a2bf78d",
            "key": "wechat.appId",
            "lastModify": 1509965975000,
            "remark": "batch import",
            "value": "wx422fef2fa3820229"
        },
        {
            "confId": "5a0040974a63900a8a2bf788",
            "id": "5a0040974a63900a8a2bf78e",
            "key": "wechat.appSecret",
            "lastModify": 1509965975000,
            "remark": "batch import",
            "value": "2b6e3ae73b739a783013d7357b43f207"
        }
    ],
    "lastModify": 1509965975000,
    "revNo": 7,
    "stage": "testing",
    "verNo": "1.0"
}
```

 **NOTICE**  
无

--- 

 
## 【silk-road】-rest 益丰精选服务  

### 1. 【短信】发送短信  

- **接口描述**  
发送短信  

- **接口信息**  
> **接口地址：** /user/userService/sendCode  
> **提交方式：** POST  
> **方法名称：** sendCode  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|phone|string|是|手机号码|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|


 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"phone":"15116451260"
}
```

返回结果
```json
null
```

 **NOTICE**  
无

---  


### 2. 【用户】绑定或者注册会员  

- **接口描述**  
发送短信  

- **接口信息**  
> **接口地址：** /user/userService/login  
> **提交方式：** POST  
> **方法名称：** login  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|code|string|是|验证码|
|user|object|是|注册绑定用户对象|
|user.phone|string|是|手机号码|
|user.openId|string|否|微信openId|
|user.unionId|string|否|微信unionId|
|user.comeFrom|string|是|顶级渠道|
|user.refComeFrom|string|否|MINIPG:小程序 WX 默认WX|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|customerCode|string||会员编号|
|cardCode|string||会员卡号|
|phone|string||手机号码|
|openId|string||会员微信openId|
|unionId|string||会员微信unionId|
|name|string||姓名 未知相当于空|
|state|string|EFC|正常:EFC 冻结:FST 冻结:CNL|
|sex|string||性别|
|birthday|string||出生日期|
|age|int||年龄|


 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"user":{
		"phone":"15116451260",
		"openId":"o3F_q0FWoE-wQFRvvbDTtx88XsGU",
		"unionId":"oXZ0xwUEgUFZDfegCyjAd17_CYf0",
		"comeFrom":"WXM"
	},
	"code":"244553"
}
```

返回结果
```json
{
    "cardCode": "M171031142852489",
    "customerCode": "ac1bf6b19ddf40619b9a4fc54d428153",
    "name": "未知",
    "openId": "o3F_q0FWoE-wQFRvvbDTtx88XsGU",
    "phone": "15116451260",
    "state": "EFC",
    "unionId": "oXZ0xwUEgUFZDfegCyjAd17_CYf0"
}
```

 **NOTICE**  
无

---  

### 3. 【公众号】jscode转session  

- **接口描述**  
小程序jscode 转换 session 获取 openId 和 unionId  

- **接口信息**  
> **接口地址：** /wechat/wechatService/jscode2session  
> **提交方式：** POST  
> **方法名称：** jscode2session  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|code|string|是|小程序login 获取jscode|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|openId|string||会员微信openId|
|unionId|string||会员微信unionId|



 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"code":"021cgu6d0rBeCv1Ulj4d0JFk6d0cgu6z"
}
```

返回结果
```json
{
    "openId": "o3F_q0FWoE-wQFRvvbDTtx88XsGU",
    "unionId": "oXZ0xwUEgUFZDfegCyjAd17_CYf0"
}
```

 **NOTICE**  
无

---

### 4. 【券】获取新人券模版ID   

- **接口描述**  
获取新人券模版ID    

- **接口信息**  
> **接口地址：** /coupon/couponService/getCouponTemplateForNewUser  
> **提交方式：** POST  
> **方法名称：** getCouponTemplateForNewUser  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
|customerCode|string|是|会员编号|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
||array|["59fa596b4f89b21ae9ded250"]|券模版ID|




 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"customerCode":"3daa789d5165408f84fa706a5fd24c64"
}
```

返回结果
```json
["59fa596b4f89b21ae9ded250","59fa59564f89b21ae9ded24f","59a7b8da4742236bf5368000"]
```

 **NOTICE**  
无
