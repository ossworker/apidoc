# 商品中台 API
Java API
标签: 【商品中台】【栾锋】

version 1.7.0

---

## 一、【渠道】



### 1、通过经纬度定位渠道 （o2o模式使用）

**接口描述**

> 通过顶级渠道、经纬度和范围查询渠道

**接口信息**

> **接口地址：** /business/BusinessChannelService/queryChannelByPositionFilter  
> **提交方式：** POST,GET  
> **方法名称：** queryChannelByPositionFilter

**请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----:|
| channelCode | String | 是 | 顶级渠道编码 （O2O,XINGREN,BDWM等） |
| longitude | Double | 是 | 定位的经度,bd09 比如 112.84000 |
| latitude | Double | 是 | 定位的纬度 bd09 比如 28.22671 |
| distance | Double | 是 | 距离范围，单位m 比如 5000 |


---
**响应参数**

入参示例: 
```json
{
    "channelCode":"XINGREN",  
    "longitude":112.84000, 
    "latitude":28.22671, 
    "distance":5000
}
```

> **正常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| channelAddress | String | 湖南省长沙市望城区麓谷街道金洲大道68号 | 渠道地址 |
| channelCode | String | XINGREN_6369 | 渠道编码 |
| serviceTypeEnum | enum | O2O | 服务类型（现场(SCENE),近距离配送(O2O),指定城市配送(B2C)） |
| channelName | String | 杏仁金洲大道 | 渠道名称 |
| channelTypeEnum | enum | YF | 渠道类型(YF:自营，THIRD:三方渠道) |
| chequesTypeEnum | enum | YF | 收款类型(YF:自己配送，THIRD:三方配送) |
| provinceCode | String | 430000 | 省编码 |
| cityCode | String | 430100 | 市编码 |
| districtCode | String | 430104 | 区编码 |
| latitude | Double | 28.22671 | 纬度 |
| longitude | Double | 112.84831 | 经度 |
| distance | Double | 814 | 定位跟该渠道的距离，单位m |
| warehouseCode | String | 6369 | 仓库编码 |
| channelConfig.cashOnDeliveryEnum | enum | NO | 是否支持货到付款 YES NO |
| channelConfig.channelCode | String | XINGREN_6369 | 跟渠道编码一致 |
| channelConfig.customerPickUpEnum | enum | NO | 用户是否可以自提 |
| channelConfig.serviceTypeEnum | enum | O2O | 跟serviceTypeEnum一致 |
| openDate | String | 08:00 | 营业开始时间 |
| endDate | String | 21:00 | 营业结束时间 |


> **异常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 | [见异常附录](#goodsError) |
| message | String | |[见异常附录](#goodsError)|


---
**示例**

JSON 数据格式

```json
{
    "channelAddress": "湖南省长沙市望城区麓谷街道金洲大道68号",
    "channelCode": "XINGREN_6369",
    "channelConfig": {
        "cashOnDeliveryEnum": "NO",
        "channelCode": "XINGREN_6369",
        "customerPickUpEnum": "NO",
        "serviceTypeEnum": "O2O"
    },
    "channelDesc": "长沙金洲大道店",
    "channelName": "杏仁金洲大道",
    "channelTypeEnum": "THIRD",
    "chequesTypeEnum": "YF",
    "cityCode": "430100",
    "distance": 814,
    "distributionTypeEnum": "YF",
    "districtCode": "430104",
    "id": "5808713d70b99e27ec0e018c",
    "latitude": 28.22671,
    "longitude": 112.84831,
    "nodeLevel": 2,
    "parentId": "580870e070b99e275034ff7e",
    "provinceCode": "430000",
    "serviceTypeEnum": "O2O",
    "warehouseCode": "6369",
    "openDate":"7:30",
    "endDate":"21:00"
}
```

---
**特殊需求（说明）**

> 无

---

### 2、通过区域编码过滤渠道 （B2C模式使用）

**接口描述**

> 通过地区编码筛选支持这个区域服务的渠道

**接口信息**

> **接口地址：** /business/BusinessChannelService/queryChannelByAreaFilter
> **提交方式：** POST,GET
> **方法名称：** queryChannelByAreaFilter

**请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----:|
| channelCode | String | 是 | 顶级渠道编码 如（O2O,XINGREN,BDWM） |
| areaCode | String | 是 | 地区编码（国标）"0" 则为全国 |


---
**响应参数**

入参示例: 
```json
{
    "channelCode":"XINGREN",  
    "areaCode":"430104"
}
```

> **正常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| channelAddress | String | 湖南省长沙市望城区麓谷街道金洲大道68号 | 渠道地址 |
| channelCode | String | XINGREN_6369 | 渠道编码 |
| serviceTypeEnum | enum | B2C | 服务类型（现场(SCENE),近距离配送(O2O),指定城市配送(B2C)） |
| channelName | String | 杏仁金洲大道 | 渠道名称 |
| channelTypeEnum | enum | YF | 渠道类型(YF:自营，THIRD:三方渠道) |
| chequesTypeEnum | enum | YF | 收款类型(YF:自己配送，THIRD:三方配送) |
| provinceCode | String | 430000 | 省编码 |
| cityCode | String | 430100 | 市编码 |
| districtCode | String | 430104 | 区编码 |
| warehouseCode | String | 6369 | 仓库编码 |
| channelConfig.cashOnDeliveryEnum | enum | NO | 是否支持货到付款 YES NO |
| channelConfig.channelCode | String | XINGREN_6369 | 跟渠道编码一致 |
| channelConfig.customerPickUpEnum | enum | NO | 用户是否可以自提 |
| channelConfig.serviceTypeEnum | enum | B2C | 跟serviceTypeEnum一致 |
| openDate | String | 08:00 | 营业开始时间 |
| endDate | String | 21:00 | 营业结束时间 |

> **异常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 | [见异常附录](#goodsError) |
| message | String | |[见异常附录](#goodsError)|



---
**示例**

```json
{
    "channelAddress": "湖南省长沙市望城区麓谷街道金洲大道68号",
    "channelCode": "XINGREN_6369",
    "channelConfig": {
        "cashOnDeliveryEnum": "NO",
        "channelCode": "XINGREN_6369",
        "customerPickUpEnum": "NO",
        "serviceTypeEnum": "B2C"
    },
    "channelDesc": "长沙金洲大道店",
    "channelName": "杏仁金洲大道",
    "channelTypeEnum": "THIRD",
    "chequesTypeEnum": "YF",
    "cityCode": "430100",
    "distributionTypeEnum": "YF",
    "districtCode": "430104",
    "id": "5808713d70b99e27ec0e018c",
    "nodeLevel": 2,
    "parentId": "580870e070b99e275034ff7e",
    "provinceCode": "430000",
    "serviceTypeEnum": "B2C",
    "warehouseCode": "6369",
    "openDate":"7:30",
    "endDate":"21:00"
}

```

---
**特殊需求（说明）**

>无

---
## 三、【商品类目】通过顶级渠道编码查询一级类目

**接口描述**

> 通过顶级渠道编码查询其下所有一级类目

**接口信息**

> **接口地址：** /business/BusinessGoodsService/queryTopCategories  
> **提交方式：** POST,GET  
> **方法名称：** queryTopCategories

**请求参数**

|名称|类型|是否必填|描述|
|:----:|:----:|:----:|:----:|
|channel|String|是|顶级渠道编码|
|pageNo|int|是|当前页|
|limit|int|是|每页大小|


---
**响应参数**

入参示例: 
```json
{
    "channelCode":"XINGREN",
    "pageNo":1,
    "limit":100
}
```

> **正常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
|{i}.categoryCode|String|1|类目编码|
|{i}.categoryImg|String||分类图片url|
|{i}.categoryLevel|String|1|类目级别|
|{i}.categoryName|String|内科|类目名称|
|{i}.parentCategoryCode|String|0|父分类编码 0表示无|



> **异常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 | [见异常附录](#goodsError) |
| message | String | |[见异常附录](#goodsError)|


---
**示例**

```json
[
    {
        "categoryCode": "1",
        "categoryImg": "http://www.baidu.com/ss.png",
        "categoryLevel": "1",
        "categoryName": "内科",
        "parentCategoryCode": "0"
    },
    {
        "categoryCode": "2",
        "categoryImg": "http://www.baidu.com/ss.png",
        "categoryLevel": "1",
        "categoryName": "普外科",
        "parentCategoryCode": "0"
    }
]

```

---
**特殊需求（说明）**

>无

---
## 四、【商品类目】根据上级分类编码和渠道编码查询下级类目信息

**接口描述**

> 根据渠道编码上级分类编码查询下级类目列表

**接口信息**

> **接口地址：** /business/BusinessGoodsService/querySubCategory  
> **提交方式：** POST,GET  
> **方法名称：** querySubCategory  

**请求参数**

|名称|类型|是否必填|描述|
|:----:|:----:|:----:|:----:|
|categoryCode|String|是|上级分类编码|
|channel|String|是|渠道编码|
|pageNo|int|是|当前页|
|limit|int|是|每页大小|


---
**响应参数**

入参示例: 
```json
{
    "channel":"XINGREN",
    "categoryCode":"2",
    "pageNo":1,
    "limit":100
}
```

> **正常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
|{i}.categoryCode|String|1|类目编码|
|{i}.categoryImg|String||分类图片url|
|{i}.categoryLevel|String|1|类目级别|
|{i}.categoryName|String|内科|类目名称|
|{i}.parentCategoryCode|String|0|父分类编码 0表示无|



> **异常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 | [见异常附录](#goodsError) |
| message | String | |[见异常附录](#goodsError)|


---
**示例**

```json
[
    {
        "categoryCode": "1",
        "categoryImg": "http://www.baidu.com/ss.png",
        "categoryLevel": "1",
        "categoryName": "内科",
        "parentCategoryCode": "2"
    },
    {
        "categoryCode": "2",
        "categoryImg": "http://www.baidu.com/ss.png",
        "categoryLevel": "1",
        "categoryName": "普外科",
        "parentCategoryCode": "2"
    }
]

```

---
**特殊需求（说明）**

>无

---
## 五、【商品类目】通过渠道编码和商品编码查询商品类目

**接口描述**

> 通过渠道编码和商品编码查询商品类目

**接口信息**

> **接口地址：** /business/BusinessGoodsService/queryGoodsCategoryInfo  
> **提交方式：** POST,GET
> **方法名称：** queryGoodsCategoryInfo

**请求参数**

|名称|类型|是否必填|描述|
|:----:|:----:|:----:|:----:|
|goodsCode|String|是|渠道编码|
|channel|String|是|顶级渠道编码|


---
**响应参数**

> **正常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
|||||



> **异常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 | [见异常附录](#goodsError) |
| message | String | |[见异常附录](#goodsError)|


---
**示例**

```json
{}

```

---
**特殊需求（说明）**

>无

---
## 六、【商品类目】通过商品编码查询商品拓展属性

**接口描述**

> 通过商品编码查询商品拓展属性（比如通用名，规格，厂家，药品成分，用法用量，剂型，功能主治，包装，贮藏条件，包装等）

**接口信息**

> **接口地址：** /business/BusinessGoodsService/queryInstructionByGoodsCode
> **提交方式：** POST,GET
> **方法名称：** queryInstructionByGoodsCode

**请求参数**

|名称|类型|是否必填|描述|
|:----:|:----:|:----:|:----:|
|goodsCode|String|是|商品编码|


---
**响应参数**

> **正常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
|||||



> **异常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 | [见异常附录](#goodsError) |
| message | String | |[见异常附录](#goodsError)|


---
**示例**

```json
{}

```

---
**特殊需求（说明）**

>无

---
## 七、【商品类目】根据商品编码和渠道编码查询商品基本信息

**接口描述**

> 根据商品编码和渠道编码查询商品基本信息

**接口信息**

> **接口地址：** /business/BusinessGoodsService/queryBaseGoodsInfo
> **提交方式：** POST,GET
> **方法名称：** queryBaseGoodsInfo

**请求参数**

|名称|类型|是否必填|描述|
|:----:|:----:|:----:|:----:|
|goodsCode|String|是|商品编码|
|channel|String|是|渠道信息（叶子）|


---
**响应参数**

> **正常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
|||||



> **异常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 | [见异常附录](#goodsError) |
| message | String | |[见异常附录](#goodsError)|


---
**示例**

```json
{}

```

---
**特殊需求（说明）**

>无

---
## 八、【渠道类目】通过渠道编码和商品编码集合批量查询商品基本信息

**接口描述**

> 通过渠道编码和商品编码集合批量查询商品基本信息

**接口信息**

> **接口地址：** /business/BusinessGoodsService/queryBaseGoodsInfoList
> **提交方式：** POST,GET
> **方法名称：** queryBaseGoodsInfoList

**请求参数**

|名称|类型|是否必填|描述|
|:----:|:----:|:----:|:----:|
|goodsCodes[i]|String|是|商品编码|
|channel|String|是|渠道编码（叶子）|


---
**响应参数**

> **正常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
|||||



> **异常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 | [见异常附录](#goodsError) |
| message | String | |[见异常附录](#goodsError)|


---
**示例**

```json
{}

```

---
**特殊需求（说明）**

>无

---
## 十、【商品库存】通过商品编码和渠道编码查询库存

**接口描述**

> 通过商品编码和渠道编码查询库存

**接口信息**

> **接口地址：** /business/BusinessGoodsService/queryGoodsStock
> **提交方式：** POST,GET
> **方法名称：** queryGoodsStock

**请求参数**

|名称|类型|是否必填|描述|
|:----:|:----:|:----:|:----:|
|goodsCode|String|是|商品编码|
|channel|String|是|渠道编码（叶子）|


---
**响应参数**

> **正常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
|||||



> **异常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 | [见异常附录](#goodsError) |
| message | String | |[见异常附录](#goodsError)|


---
**示例**

```json
{}

```

---
**特殊需求（说明）**

>无

---
## 十一、【商品库存】商品编码列表和渠道查询商品库存

**接口描述**

> 商品编码列表和渠道查询商品库存

**接口信息**

> **接口地址：** /business/BusinessGoodsService/queryStockByGoodsListAndChannel
> **提交方式：** POST,GET
> **方法名称：** queryStockByGoodsListAndChannel

**请求参数**

|名称|类型|是否必填|描述|
|:----:|:----:|:----:|:----:|
|goodsCodeList[i]|String|是|商品编码|
|channel|String|是|渠道编码（叶子）|


---
**响应参数**

> **正常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
|||||



> **异常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 | [见异常附录](#goodsError) |
| message | String | |[见异常附录](#goodsError)|


---
**示例**

```json
{}

```

---
**特殊需求（说明）**

>无

---
## 十二、【渠道仓库】通过渠道编码查询该渠道的主仓库

**接口描述**

> 通过渠道编码查询该渠道的主仓库

**接口信息**

> **接口地址：** /business/BusinessChannelService/queryOneWarehouseByChannelCode
> **提交方式：** POST,GET
> **方法名称：** queryOneWarehouseByChannelCode

**请求参数**

|名称|类型|是否必填|描述|
|:----:|:----:|:----:|:----:|
|channelCode|String|是|渠道编码（叶子节点）|


---
**响应参数**

> **正常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
|||||



> **异常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 | [见异常附录](#goodsError) |
| message | String | |[见异常附录](#goodsError)|


---
**示例**

```json
{}

```

---
**特殊需求（说明）**

>无

---
## 十三、【渠道仓库】通过渠道编码查询该渠道的所有仓库

**接口描述**

> 通过渠道编码查询该渠道的所有仓库

**接口信息**

> **接口地址：** /business/BusinessChannelService/queryWarehouseByChannelCode
> **提交方式：** POST,GET
> **方法名称：** queryWarehouseByChannelCode

**请求参数**

|名称|类型|是否必填|描述|
|:----:|:----:|:----:|:----:|
|channelCode|String|是|渠道编码（叶子节点）|


---
**响应参数**

> **正常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
|||||



> **异常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 | [见异常附录](#goodsError) |
| message | String | |[见异常附录](#goodsError)|


---
**示例**

```json
{}

```

---
**特殊需求（说明）**

>无

---


## 十三、【渠道】通过渠道编码渠道路径

**接口描述**

> 通过渠道编码渠道归属路径

**接口信息**

> **接口地址：** /business/BusinessChannelService/queryChannelPathByChannelCode
> **提交方式：** POST,GET
> **方法名称：** queryChannelPathByChannelCode

**请求参数**

|名称|类型|是否必填|描述|
|:----:|:----:|:----:|:----:|
|channelCode|String|是|渠道编码（叶子）|


---
**响应参数**

入参示例

```json
{
	"channelCode":"BDWM_6369"
}
```

> **正常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
|  | String | BDWM,BDWM_CHANGSHA,BDWM_6369 | 渠道地址 |



> **异常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 | [见异常附录](#goodsError) |
| message | String | |[见异常附录](#goodsError)|


---
**示例**

```json
 "BDWM,BDWM_CHANGSHA,BDWM_6369"
```

---
**特殊需求（说明）**

>无

---

## 十四、【渠道】通过渠道编码查询渠道

**接口描述**

> 通过渠道编码查询渠道配置项 比如渠道类型，收款类型，配送类型，服务类型等

**接口信息**

> **接口地址：** /business/BusinessChannelService/queryChannelInfoByChannelCode
> **提交方式：** POST,GET
> **方法名称：** queryChannelByChannelCode

**请求参数**

|名称|类型|是否必填|描述|
|:----:|:----:|:----:|:----:|
|channelCode|String|是|渠道编码（叶子）|


---
**响应参数**

入参示例

```json
{
	"channelCode":"XINGREN_6369"
}
```

> **正常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| channelAddress | String | 湖南省长沙市望城区麓谷街道金洲大道68号 | 渠道地址 |
| channelCode | String | XINGREN_6369 | 渠道编码 |
| serviceTypeEnum | enum | O2O | 服务类型（现场(SCENE),近距离配送(O2O),指定城市配送(B2C)） |
| channelName | String | 杏仁金洲大道 | 渠道名称 |
| channelTypeEnum | enum | YF | 渠道类型(YF:自营，THIRD:三方渠道) |
| chequesTypeEnum | enum | YF | 收款类型(YF:自己配送，THIRD:三方配送) |
| provinceCode | String | 430000 | 省编码 |
| cityCode | String | 430100 | 市编码 |
| districtCode | String | 430104 | 区编码 |
| latitude | Double | 28.22671 | 纬度 |
| longitude | Double | 112.84831 | 经度 |
| warehouseCode | String | 6369 | 仓库编码 |
| channelConfig.cashOnDeliveryEnum | enum | NO | 是否支持货到付款 YES NO |
| channelConfig.channelCode | String | XINGREN_6369 | 跟渠道编码一致 |
| channelConfig.customerPickUpEnum | enum | NO | 用户是否可以自提 |
| channelConfig.serviceTypeEnum | enum | O2O | 跟serviceTypeEnum一致 |
| openDate | String | 08:00 | 营业开始时间 |
| endDate | String | 21:00 | 营业结束时间 |


> **异常**

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 | [见异常附录](#goodsError) |
| message | String | |[见异常附录](#goodsError)|


---
**示例**

```json
{
    "channelAddress": "湖南省长沙市望城区麓谷街道金洲大道68号",
    "channelCode": "XINGREN_6369",
    "channelConfig": {
        "cashOnDeliveryEnum": "NO",
        "channelCode": "XINGREN_6369",
        "customerPickUpEnum": "NO",
        "serviceTypeEnum": "O2O"
    },
    "channelDesc": "长沙金洲大道店",
    "channelName": "杏仁金洲大道",
    "channelTypeEnum": "THIRD",
    "chequesTypeEnum": "YF",
    "cityCode": "430100",
    "distributionTypeEnum": "YF",
    "districtCode": "430104",
    "id": "5808713d70b99e27ec0e018c",
    "latitude": 28.22671,
    "longitude": 112.8483,
    "nodeLevel": 2,
    "parentId": "580870e070b99e275034ff7e",
    "provinceCode": "430000",
    "serviceTypeEnum": "O2O",
    "warehouseCode": "6369",
    "openDate":"7:30",
    "endDate":"21:00"
}

```

---
**特殊需求（说明）**

>无



---
## 附录

**Exception 错误编码**

>  <span id="goodsError">商品中台错误</span>

|类别|异常code|异常message |
|:----:|:----:|:----:|:----:|
|通用|11000000|【入参有误】,参数为:%s,错误原因:%s|
|渠道|11020001|【渠道】,渠道（%s）下面没有仓库|
|渠道|11020002|【渠道】,渠道编码（%s)的渠道已经存在|
|商品|11030001|【商品】,批量插入商品失败,%s|
|商品|11030002|【商品】,更新商品信息失败,%s|
|商品|11050001|【商品】查询库存失败，错误原因：%s|
|类目|11030003|【类目】,批量插入类目失败,%s|
|类目|11030004|【类目】,类目更新失败,%s|
|类目|11030005|【类目】,类目删除失败,%s|
|仓库|11040001|【仓库】仓库(%s)有渠道(%s)正在使用,删除失败|
|geohash|11030006|【geohash】查询出错,%s|
|渠道|11030007|【渠道】渠道无该服务类型,%s|
|渠道|11030008|【渠道】没有找到该服务类型，%s|
|渠道|11030009|【渠道】该渠道不可用 %s|
|仓库|11030010|【仓库】该渠道( %s )下的主仓库找不到|


---






## API更新日志

> **1.7.2**

1. 移除queryChannelByChannelCode api
2. 新增queryChannelInfoByChannelCode 通过渠道编号查询渠道信息


> **1.7.1**

1. 新增queryChannelPathByChannelCode方法：根据渠道编码查询该渠道的树形路径

> **1.7.0**

1. queryChannelByAreaFilter 返回类型List<BusinessBaseChannel> -> BusinessChannel
2. queryChannelByPositionFilter 返回类型List<BusinessBaseChannel> -> BusinessChannel
3. queryChannelByChannelCode 入参增加serverType
4. queryWarehouseByChannelCode 返回类型List<BusinessWarehouse> -> BusinessWarehouse


> **1.6.0**

1. 初始化



[^footnote]: 这是一个 *注脚* 的 **文本**。
