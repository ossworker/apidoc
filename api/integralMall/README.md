# 积分商城 API
Java API
标签: 【integral-mall】【栾锋】

version 1.0.0

---

## 广告

### 1. 广告位  

- **接口描述**  
> 利用openId/unionId/phone 登录  

- **接口信息**  
> **接口地址：** http://192.168.7.65:8082/openx/advertise/BusinessAdvertService/queryAdvertByChannel 
> **提交方式：** POST,GET  
> **方法名称：** queryAdvertByChannel 

- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----:|
|channelCode|string|是|渠道编码 JFM_6369|
|pageCode|string|是|广告位编码 SY01|
|pageLocation|string|是|TOP01 位置 |



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
	"channelCode":"JFM_6369",
	"pageCode":"SY01",
	"pageLocation":"TOP01"
}
```

返回结果
```json

```

!> **NOTICE**  
无

 
---



## 用户


### 1. 检查三方是否存在  

- **接口描述**  
> 检查第三方用户是否存在  
  

- **接口信息**  
> **接口地址：** http://192.168.7.33:8080/customer/CustomerService/checkThirdPartyCustomer  
> **提交方式：** POST,GET  
> **方法名称：** checkThirdPartyCustomer  
  

- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----:|
|thirdPartyType|object|是|第三方账号的类型,值为XINGREN,BPTJ,WX,YSZX|
|thirdPartyId|string|是|第三方账号的id|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
|isExist|boolean|是|是否存在|


 异常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 |  |
| message | String | | |




- **示例**

入参示例: 
```json

```

返回结果
```json

```

!> **NOTICE**  
无

 
---


### 2. 自动登录

- **接口描述**  
> 利用openId/unionId/phone 登录  
  

- **接口信息**  
> **接口地址：** http://192.168.7.33:8080/customer/CustomerService/autoRegistLogin  
> **提交方式：** POST,GET  
> **方法名称：** autoRegistLogin  
  

- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----:|
|loginInfo|object|是|登录信息|
|loginInfo.channel|string|是|渠道 JSM,DZG|
|loginInfo.thirdPartyType|string|是|第三方账号的类型,值为XINGREN |
|loginInfo.thirdPartyId|string|是|unionid 与openid 二选一|
|loginInfo.thirdPartySubId|string|是|unionid 与openid 二选一|
|loginInfo.phone|string|否|手机号码 注册时需要|
|loginInfo.loginType|string|是|登录类型 weixin|
|loginInfo.loginDevType|string|是|登录设备 weixin|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| customer     | Customer  |        | 用户信息|
| customer.customerCode     | String  |    是    | 客户账号（000013F9-7B31-49C4-A904-489F19DBFAF1）|
| customer.source     | String  |       | 用戶來源|
| customer.name     | String  |       | 联系人姓名|
| customer.phone     | String  |       | 电话号码|
| customer.accessToken     | String  |       | 接入的token|


 异常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 |  |
| message | String | | |




- **示例**

入参示例: 
```json

```

返回结果
```json

```

!> **NOTICE**  
无

 
---

### 3. 通过会员编号查询收货人地址

- **接口描述**  
> 通过会员编号查询地址  
  

- **接口信息**  
> **接口地址：** http://192.168.7.33:8080/customer/CustomerService/queryDeliveryAddressByCustomerCode  
> **提交方式：** POST,GET  
> **方法名称：** queryDeliveryAddressByCustomerCode  
  

- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----:|
|customerCode|string|是|会员编号|



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

```

返回结果
```json

```

!> **NOTICE**  
无

 
---


### 4. 修改收货地址

- **接口描述**  
> 通过收货人地址uuid 修改收货人信息  
  

- **接口信息**  
> **接口地址：** http://192.168.7.33:8080/customer/CustomerService/updateDeliveryAddress  
> **提交方式：** POST,GET  
> **方法名称：** updateDeliveryAddress  
  

- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----:|
| contact     | Contact  |   是     | 地址信息|
| contact.customerCode     | String  |    是    | 联系人ID|
| contact.source     | String  |       | 用戶來源（值为顶级渠道编号）|
| contact.name     | String  |       | 联系人姓名|
| contact.phone     | String  |       | 电话号码|
| contact.idCard     | String  |       | 联系人身份证|
| contact.address     | Address  |       | 联系人地址|
| contact.address.uuid     | String  |        | CRM会员地址UUID|
| contact.address.provinceCode     | String  |       | 省份编号|
| contact.address.cityCode     | String  |       | 城市编号|
| contact.address.districtCode     | String  |       | 区编号|
| contact.address.address     | String  |       | 详细地址|
| contact.address.provinceName     | String  |       | 省名称|
| contact.address.cityName     | String  |       | 市名称，地级市级别|
| contact.address.districtName     | String  |       | 区名称，区县级别，县级市也属于该级别|
| contact.address.location     | Location  |       | 经纬度|
| contact.address.location.longitude     | Number  |       |经度|
| contact.address.location.latitude     | Number  |      |纬度|


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

```

返回结果
```json

```

!> **NOTICE**  
无

 
---

### 5. 设置会员默认地址

- **接口描述**  
> 设置会员默认地址 
  

- **接口信息**  
> **接口地址：** http://192.168.7.33:8080/customer/CustomerService/setCustomerDefaultAddress  
> **提交方式：** POST,GET  
> **方法名称：** setCustomerDefaultAddress  
  

- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----:|
| id     | String  |   是     | CRM会员地址UUID|
| customerCode     | String  |   是     | 客户账号|


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

```

返回结果
```json

```

!> **NOTICE**  
无

 
---


### 6. 查询用户积分

- **接口描述**  
> 查询用户积分 
  

- **接口信息**  
> **接口地址：** http://192.168.7.33:8080/payment/PaymentService/queryPoints  
> **提交方式：** POST,GET  
> **方法名称：** queryPoints  
  

- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----:|
| customerCode     | string  |   是     | 客户账号|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| points     | number  |        | 可用积分|


 异常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 |  |
| message | String | | |




- **示例**

入参示例: 
```json
   {
    "customerCode": "82D52D26-6339-4489-82E1-EF77273BA237"
 }
```

返回结果
```json
3000
```

!> **NOTICE**  
无

 
---


