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

## 【member-open】 会员   

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

### 2. 【收货地址】创建会员收货地址  

- **接口描述**  
> 创建会员收货地址

- **接口信息**  
> **接口地址：** /openx/memberopen/deliveryAddressService/createAddress  
> **提交方式：** POST  
> **方法名称：** createAddress  

- **请求参数**

|名称|类型|是否必须|描述|
|:----|:----:|:----:|:----|
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



## 【query】 query服务    

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


### 3. 【商品】通过渠道编码和商品编码查询商品

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



### 4. 【物流】根据渠道查询可用物流方式

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


### 5. 【订单】统计订单数目

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
	"topChannelCode":"WXM",
	"customerCode":"S00001"
}
```

返回结果
```json
[
    {
        "orderState": "ORDER_CANCEL",
        "quantity": 4
    },
    {
        "orderState": "ORDER_CLOSE",
        "quantity": 2
    },
    {
        "orderState": "PAYMENT_WAITING",
        "quantity": 8
    },
    {
        "orderState": "RECEIVE_WAITING",
        "quantity": 2
    },
    {
        "orderState": "SHIPMENT_WAITING",
        "quantity": 1
    }
]
```

 **NOTICE**  
无

 
---

### 6. 【订单】查询所有订单

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



 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"topChannelCode":"WXM",
	"customerCode":"S00001",
	"pageNo":1,
	"pageSize":10
}
```

返回结果
```json
[
    {
        "channelCode": "WXM_6399",
        "createTime": 1508116725000,
        "customerCode": "S00001",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goods": [
            {
                "exercisePrice": 10,
                "gift": false,
                "goodsCode": "116000",
                "goodsName": "东阿阿胶",
                "quantity": 1
            },
            {
                "exercisePrice": 12,
                "gift": false,
                "goodsCode": "116001",
                "goodsName": "小阿胶",
                "quantity": 1
            }
        ],
        "goodsTotalAmount": 22,
        "orderCode": "WXM2017101601100001",
        "orderState": "PAYMENT_WAITING",
        "ordonnanceId": "00000w0001",
        "outTradeCode": "OUT000w01",
        "parentOrderCode": "WXM2017101601100001",
        "payee": "PAYEE_YIFENG",
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "WXM"
    },
    {
        "channelCode": "WXM_6399",
        "createTime": 1506504993000,
        "customerCode": "S00001",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goodsTotalAmount": 22,
        "orderCode": "WXM2017092701100010",
        "orderState": "PAYMENT_WAITING",
        "ordonnanceId": "00000w0001",
        "outTradeCode": "OUT000w01",
        "parentOrderCode": "WXM2017092701100010",
        "payee": "PAYEE_YIFENG",
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "WXM"
    },
    {
        "channelCode": "WXM_6399",
        "createTime": 1506504161000,
        "customerCode": "S00001",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goodsTotalAmount": 22,
        "orderCode": "WXM2017092701100009",
        "orderState": "PAYMENT_WAITING",
        "ordonnanceId": "00000w0001",
        "outTradeCode": "OUT000w01",
        "parentOrderCode": "WXM2017092701100009",
        "payee": "PAYEE_YIFENG",
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "WXM"
    },
    {
        "channelCode": "WXM_6399",
        "createTime": 1506504134000,
        "customerCode": "S00001",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goods": [
            {
                "exercisePrice": 10,
                "gift": false,
                "goodsCode": "116000",
                "goodsName": "东阿阿胶",
                "quantity": 1
            },
            {
                "exercisePrice": 12,
                "gift": false,
                "goodsCode": "116001",
                "goodsName": "小阿胶",
                "quantity": 1
            }
        ],
        "goodsTotalAmount": 22,
        "orderCode": "WXM2017092701100008",
        "orderState": "PAYMENT_WAITING",
        "ordonnanceId": "00000w0001",
        "outTradeCode": "OUT000w01",
        "parentOrderCode": "WXM2017092701100008",
        "payee": "PAYEE_YIFENG",
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "WXM"
    },
    {
        "channelCode": "WXM_6399",
        "createTime": 1506502524000,
        "customerCode": "S00001",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goodsTotalAmount": 22,
        "orderCode": "WXM2017092701100007",
        "orderState": "PAYMENT_WAITING",
        "ordonnanceId": "00000w0001",
        "outTradeCode": "OUT000w01",
        "parentOrderCode": "WXM2017092701100007",
        "payee": "PAYEE_YIFENG",
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "WXM"
    },
    {
        "channelCode": "WXM_6399",
        "createTime": 1506502503000,
        "customerCode": "S00001",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goodsTotalAmount": 22,
        "orderCode": "WXM2017092701100006",
        "orderState": "PAYMENT_WAITING",
        "ordonnanceId": "00000w0001",
        "outTradeCode": "OUT000w01",
        "parentOrderCode": "WXM2017092701100006",
        "payee": "PAYEE_YIFENG",
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "WXM"
    },
    {
        "channelCode": "WXM_6399",
        "createTime": 1506502451000,
        "customerCode": "S00001",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goods": [
            {
                "exercisePrice": 10,
                "gift": false,
                "goodsCode": "116000",
                "goodsName": "东阿阿胶",
                "quantity": 1
            },
            {
                "exercisePrice": 12,
                "gift": false,
                "goodsCode": "116001",
                "goodsName": "小阿胶",
                "quantity": 1
            }
        ],
        "goodsTotalAmount": 22,
        "orderCode": "WXM2017092701100005",
        "orderState": "PAYMENT_WAITING",
        "ordonnanceId": "00000w0001",
        "outTradeCode": "OUT000w01",
        "parentOrderCode": "WXM2017092701100005",
        "payee": "PAYEE_YIFENG",
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "WXM"
    },
    {
        "channelCode": "WXM_6399",
        "createTime": 1506500324000,
        "customerCode": "S00001",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goodsTotalAmount": 22,
        "orderCode": "null2017092701100004",
        "orderState": "PAYMENT_WAITING",
        "ordonnanceId": "00000w0001",
        "outTradeCode": "OUT000w01",
        "parentOrderCode": "null2017092701100004",
        "payee": "PAYEE_YIFENG",
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "WXM"
    },
    {
        "channelCode": "WXM_6369",
        "createTime": 1505295731000,
        "customerCode": "S00001",
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
        "orderCode": "WXM_63692017091301100009_1",
        "orderState": "SHIPMENT_WAITING",
        "ordonnanceId": "000000001",
        "outTradeCode": "BD000001",
        "parentOrderCode": "WXM_63692017091301100009",
        "payee": "PAYEE_YIFENG",
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "WXM"
    },
    {
        "channelCode": "WXM_6369",
        "createTime": 1505295266000,
        "customerCode": "S00001",
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
        "orderCode": "WXM_63692017091301100009",
        "orderState": "ORDER_CLOSE",
        "ordonnanceId": "000000001",
        "outTradeCode": "BD000001",
        "parentOrderCode": "WXM_63692017091301100009",
        "payee": "PAYEE_YIFENG",
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "WXM"
    }
]
```

 **NOTICE**  
无

 
---


### 7. 【订单】查询订单状态下订单

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



 异常

|名称|类型|示例值|描述|
|:----|:----:|:----|:----|
|code|string|11000000|错误编码|
|message|string||异常信息|




- **示例**

入参示例:  
```json
{
	"topChannelCode":"WXM",
	"customerCode":"S00001",
	"orderState":"RECEIVE_WAITING",
	"pageNo":1,
	"pageSize":10
}
```

返回结果
```json
[
    {
        "channelCode": "WXM_6369",
        "createTime": 1504858027000,
        "customerCode": "S00001",
        "customerNeedPayAmount": 29,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goods": [
            {
                "exercisePrice": 10,
                "gift": false,
                "goodsCode": "1000000",
                "goodsName": "东阿阿胶",
                "quantity": 1
            },
            {
                "exercisePrice": 12,
                "gift": false,
                "goodsCode": "1000001",
                "goodsName": "小阿胶",
                "quantity": 1
            }
        ],
        "goodsTotalAmount": 22,
        "orderCode": "WXM_63692017090801100010",
        "orderState": "RECEIVE_WAITING",
        "ordonnanceId": "000000001",
        "outTradeCode": "BD000001",
        "parentOrderCode": "WXM_63692017090801100010",
        "payee": "PAYEE_YIFENG",
        "remark": "Remark",
        "subsidyTotalAmount": 2,
        "topChannelCode": "WXM"
    },
    {
        "channelCode": "WXM_6369",
        "createTime": 1504844345000,
        "customerCode": "S00001",
        "customerNeedPayAmount": 19.75,
        "deliveryServiceType": "DELIVERY_YIFENG",
        "goods": [
            {
                "accountPrice": 10,
                "exercisePrice": 10,
                "gift": false,
                "goodsCode": "1000000",
                "goodsName": "东阿阿胶",
                "quantity": 1
            }
        ],
        "goodsTotalAmount": 10,
        "orderCode": "WXM_63692017090801100005_1",
        "orderState": "RECEIVE_WAITING",
        "outTradeCode": "BD000001",
        "parentOrderCode": "WXM_63692017090801100005",
        "payee": "PAYEE_YIFENG",
        "remark": "请送最近日期的货品",
        "subsidyTotalAmount": 0.9,
        "topChannelCode": "WXM",
        "warehouseCode": "5026"
    }
]
```

 **NOTICE**  
无

 
---



## 【customer】个人中心  


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
> **接口地址：**     
> **提交方式：** POST  
> **方法名称：**   

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


## 【trade】 交易   

### 1. 创建订单  

### 2. 预支付



## 【coupon】 券服务    



