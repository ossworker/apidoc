# 积分商城 API
Java API
标签: 【silk-road】【栾锋】

version 1.0.0



- **服务地址：**  

|环境|项目|原HOST|调用HOST|
|:----:|:----|:----|:----|
|开发环境|silk-road|http://192.168.7.41:9020|http://192.168.7.41:9020/rest/|
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
|customerId|string|598bc0f542559b20787e62e6|会员编号，唯一标识|




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
    },
    {
        "address": "杜鹃路12",
        "city": "430100",
        "cityName": "长沙市",
        "createDate": 1504600238000,
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
        "uuid": "17c08238b53c4966a06a143484534b73"
    },
    {
        "address": "杜鹃路fdaafsadf",
        "city": "430100",
        "cityName": "长沙市",
        "createDate": 1504230914000,
        "customerId": "647958c21f03445a9bb8fbcadfc82f30",
        "deliverySource": "WX",
        "district": "430104",
        "districtName": "岳麓区",
        "isDefault": "0",
        "latitude": 0,
        "linkPerson": "张三xfdsa",
        "linkPhone": "13725578963",
        "longitude": 0,
        "province": "430000",
        "provinceName": "湖南省",
        "uuid": "ca7dce3c7cf549baa82f4a3dcc36b3d3"
    },
    {
        "address": "杜鹃路",
        "city": "430100",
        "cityName": "长沙市",
        "createDate": 1504230830000,
        "customerId": "647958c21f03445a9bb8fbcadfc82f30",
        "deliverySource": "WX",
        "district": "430104",
        "districtName": "岳麓区",
        "isDefault": "0",
        "latitude": 0,
        "linkPerson": "张三",
        "linkPhone": "13725578963",
        "longitude": 0,
        "province": "430000",
        "provinceName": "湖南省",
        "uuid": "76e84e9b2f8c4b27b006e9de4d6a1e00"
    },
    {
        "address": "惠福西路合富置业",
        "city": "440100",
        "cityName": "广州市",
        "createDate": 1503987029000,
        "customerId": "647958c21f03445a9bb8fbcadfc82f30",
        "deliverySource": "WXM",
        "district": "440104",
        "districtName": "越秀区",
        "isDefault": "0",
        "latitude": 23.127229,
        "linkPerson": "信息",
        "linkPhone": "18873208972",
        "longitude": 113.260292,
        "province": "440000",
        "provinceName": "广东省",
        "uuid": "1d329269fb4d451ab15e85a2419236c2"
    },
    {
        "address": "杜鹃路保利",
        "city": "430100",
        "cityName": "长沙市",
        "createDate": 1503307822000,
        "customerId": "647958c21f03445a9bb8fbcadfc82f30",
        "deliverySource": "JFM",
        "district": "430104",
        "districtName": "岳麓区",
        "isDefault": "0",
        "latitude": 28.237902,
        "linkPerson": "杨柳",
        "linkPhone": "18873208972",
        "longitude": 112.943282,
        "province": "430000",
        "provinceName": "湖南省",
        "uuid": "9fff41708cb447ae98f4f113286e611a"
    },
    {
        "address": "桐梓坡西路保利·麓谷体育公园",
        "city": "430100",
        "cityName": "长沙市",
        "createDate": 1503306166000,
        "customerId": "647958c21f03445a9bb8fbcadfc82f30",
        "deliverySource": "JFM",
        "district": "430104",
        "districtName": "岳麓区",
        "isDefault": "0",
        "latitude": 28.22627,
        "linkPerson": "杨柳",
        "linkPhone": "18873208972",
        "longitude": 112.890365,
        "province": "430000",
        "provinceName": "湖南省",
        "uuid": "151c8672a694458e995b91ba2e0f7179"
    },
    {
        "address": "桐梓坡西路保利·麓谷体育公园",
        "city": "430100",
        "cityName": "长沙市",
        "createDate": 1503305721000,
        "customerId": "647958c21f03445a9bb8fbcadfc82f30",
        "deliverySource": "JFM",
        "district": "430104",
        "districtName": "岳麓区",
        "isDefault": "0",
        "latitude": 28.22627,
        "linkPerson": "杨柳",
        "linkPhone": "18873208972",
        "longitude": 112.890365,
        "province": "430000",
        "provinceName": "湖南省",
        "uuid": "1bcd6d09aded4cc3ba91159003eeef0f"
    },
    {
        "address": "杜鹃路杨柳",
        "city": "430100",
        "cityName": "长沙市",
        "createDate": 1503294308000,
        "customerId": "647958c21f03445a9bb8fbcadfc82f30",
        "deliverySource": "JFM",
        "district": "430104",
        "districtName": "岳麓区",
        "isDefault": "0",
        "latitude": 28.237902,
        "linkPerson": "杨柳",
        "linkPhone": "18873208972",
        "longitude": 112.943282,
        "province": "430000",
        "provinceName": "湖南省",
        "uuid": "a9fb3dd936fa4e0a8d205fd49ff2a5f4"
    },
    {
        "address": "杜鹃路啊啊啊啊",
        "city": "430100",
        "cityName": "长沙市",
        "createDate": 1502950108000,
        "customerId": "647958c21f03445a9bb8fbcadfc82f30",
        "deliverySource": "WXM",
        "district": "430104",
        "districtName": "岳麓区",
        "isDefault": "0",
        "latitude": 28.237902,
        "linkPerson": "嘟嘟嘟",
        "linkPhone": "18873208972",
        "longitude": 112.943282,
        "province": "430000",
        "provinceName": "湖南省",
        "uuid": "97c5f8d9d0d941dbb898ce5ca810f07d"
    },
    {
        "address": "杜鹃路三生三世",
        "city": "430100",
        "cityName": "长沙市",
        "createDate": 1502950045000,
        "customerId": "647958c21f03445a9bb8fbcadfc82f30",
        "deliverySource": "WXM",
        "district": "430104",
        "districtName": "岳麓区",
        "isDefault": "0",
        "latitude": 28.237902,
        "linkPerson": "嘟嘟嘟",
        "linkPhone": "18873208972",
        "longitude": 112.943282,
        "province": "430000",
        "provinceName": "湖南省",
        "uuid": "8873eebf2f7643089f8a8837e58f34e1"
    },
    {
        "address": "杜鹃路",
        "city": "430100",
        "cityName": "长沙市",
        "createDate": 1497496161000,
        "customerId": "647958c21f03445a9bb8fbcadfc82f30",
        "deliverySource": "CYYSWX",
        "district": "430104",
        "districtName": "岳麓区",
        "isDefault": "0",
        "latitude": 0,
        "linkPerson": "张三",
        "linkPhone": "13725578963",
        "longitude": 0,
        "province": "430000",
        "provinceName": "湖南省",
        "uuid": "1e7c6f0ca2264b0fbad5c6989924f49d"
    },
    {
        "address": "文心六路",
        "city": "440300",
        "cityName": "深圳市",
        "createDate": 1495075814000,
        "customerId": "647958c21f03445a9bb8fbcadfc82f30",
        "deliverySource": "WXM",
        "district": "440305",
        "districtName": "南山区",
        "isDefault": "0",
        "latitude": 22.52301,
        "linkPerson": "cece",
        "linkPhone": "18873208972",
        "longitude": 113.945246,
        "province": "440000",
        "provinceName": "广东省",
        "uuid": "cd6411e157324405ad0ed3811c58ae6b"
    },
    {
        "address": "文心六路",
        "city": "440300",
        "cityName": "深圳市",
        "createDate": 1495071603000,
        "customerId": "647958c21f03445a9bb8fbcadfc82f30",
        "deliverySource": "WXM",
        "district": "440305",
        "districtName": "南山区",
        "isDefault": "0",
        "latitude": 22.52301,
        "linkPerson": "121212",
        "linkPhone": "18873208972",
        "longitude": 113.945246,
        "province": "440000",
        "provinceName": "广东省",
        "uuid": "40f3ba273a814ff2ae8781c25cc132aa"
    },
    {
        "address": "文心六路",
        "city": "440300",
        "cityName": "深圳市",
        "createDate": 1495060793000,
        "customerId": "647958c21f03445a9bb8fbcadfc82f30",
        "deliverySource": "WXM",
        "district": "440305",
        "districtName": "南山区",
        "isDefault": "0",
        "latitude": 22.52301,
        "linkPerson": "cecece",
        "linkPhone": "18873208972",
        "longitude": 113.945246,
        "province": "440000",
        "provinceName": "广东省",
        "uuid": "da8d8b55be814ec8bc815b6dd6600701"
    },
    {
        "address": "文心六路",
        "city": "440300",
        "cityName": "深圳市",
        "createDate": 1495001935000,
        "customerId": "647958c21f03445a9bb8fbcadfc82f30",
        "deliverySource": "WXM",
        "district": "440305",
        "districtName": "南山区",
        "isDefault": "0",
        "latitude": 22.52301,
        "linkPerson": "cece",
        "linkPhone": "18873208972",
        "longitude": 113.945246,
        "province": "440000",
        "provinceName": "广东省",
        "uuid": "e044429fcfab4edc83ab1a33644cb242"
    },
    {
        "address": "TENGTEA",
        "city": "440300",
        "cityName": "深圳市",
        "createDate": 1492694910000,
        "customerId": "647958c21f03445a9bb8fbcadfc82f30",
        "deliverySource": "WXM",
        "district": "440305",
        "districtName": "南山区",
        "isDefault": "0",
        "latitude": 22.52301,
        "linkPerson": "cecece",
        "linkPhone": "18873208972",
        "longitude": 113.945246,
        "province": "440000",
        "provinceName": "广东省",
        "uuid": "1ff537f7f6e14877b6a1c7566c5622c2"
    }
]
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


## 交易 【trade】  



## 券服务  【coupon】  

