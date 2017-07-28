# o2o-wms API
Java API
标签: 【o2o-wms】【栾锋】

version 1.0.0

---

## o2o-wms

### 1、推送订单信息给wms

- **接口描述**  
> 推送订单信息给wms  
  

- **接口信息**  
> **接口地址：** http://one.yfdyf.cn/IF/WMSO2O/Sale.aspx   
> **提交方式：** POST,GET  
> **方法名称：**   
  

- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----:|
|orderCode|string|是|订单编号|
|ticketNum|string|是|小票号|
|warehouseCode|string|是|仓库编号C018|
|goodsList|array|是|订单商品列表|
|goodsList[i].goodsCode|string|是|商品编码|
|goodsList[i].quantity|string|是|商品数量|
|goodsList[i].price|number|是|商品单价|
|goodsList[i].orderQuantity|number|是|订单商品数量|


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
    "orderCode":"JD20170712600305100521",
    "ticketNum":"12",
    "warehouseCode":"C018",
    "goodsList":[
        {
           "goodsCode":"1001123",
           "quantity":4,
           "orderQuantity":4,
           "price":25.6     
        },
        {
           "goodsCode":"1005749",
           "quantity":5,
           "orderQuantity":6,
           "price":12.5     
        }
    ]
}
```

返回结果
```json

```

!> **NOTICE**  
无

 
---

### 2、查询商品库存

- **接口描述**  
> 查询某仓库下的 某些商品的库存  
  

- **接口信息**  
> **接口地址：** http://one.yfdyf.cn/IF/WMSO2O/Stock.aspx     
> **提交方式：** POST,GET  
> **方法名称：**  
  

- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----:|
|warehouseCode| string | 是 | 仓库编号 |
|goodsCodes|array|是|商品编码列表 ["",""]|


- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
|warehouseCode|string|C018|仓库编码|
|goodsCodes.key|string|10001|商品编码|
|goodsCodes.value|number|20|库存数量|



 异常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 |  |
| message | String | | |



- **示例**

入参示例: 
```json
{
	"warehouseCode":"C018",
	"goodsCodes":[
	"1001123","1010360"
	]
}
```

返回结果
```json

{
    "warehouseCode": "C018",
    "goodsCodes": {
        "1001123": 47814,
        "1010360": 6330
    }
}

```

!> **NOTICE**  
无


---

## wms-o2o

### 1、接收wms推送的跑批次回执

- **接口描述**  
> 接收wms推送的跑批次回执  
  

- **接口信息**  
> **接口地址：** http://192.168.7.35:8082/openx/wms/wmsService/notifiedWmsBatchInfo  
> **提交方式：** POST,GET  
> **方法名称：** notifiedWmsBatchInfo  
  

- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----:|
|batchNum|string|是|批次号|
|warehouseCode|string|是|仓库编号C018|
|orderList|array|是|订单列表|
|orderList[i].orderCode|string|是|订单编号|
|orderList[i].ticketNum|string|是|小票号|
|orderList[i].orderCode|string|是|订单编号|
|orderList[i].goodsList|array|是|订单商品列表|
|orderList[i].goodsList[i].goodsCode|string|是|商品编号|
|orderList[i].goodsList[i].quantity|number|是|需要发的商品数量|
|orderList[i].goodsList[i].realQuantity|number|是|实际发的商品数量|
|orderList[i].goodsList[i].lotList|array|是|商品的批次信息|
|orderList[i].goodsList[i].lotList[i].lotNum|string|是|批次号|
|orderList[i].goodsList[i].lotList[i].stockQty|number|是|批次的数量|



- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
|code|String|0|正常0; >0 异常|
|message|String|success|返回描述|

 异常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String |  |  |
| message | String | | |




- **示例**

入参示例: 
```json
{
    "wmsBatchInfo": {
        "batchNum": "25544",
        "warehouseCode": "C018",
        "orderList": [
            {
                "orderCode": "JD20170712600305100522",
                "ticketNum": "12",
                "goodsList": [
                    {
                        "goodsCode": "10001",
                        "quantity": 20,
                        "realQuantity": 12,
                        "lotList": [
                            {
                                "lotNum": "25445",
                                "stockQty": 6
                            },
                            {
                                "lotNum": "25446",
                                "stockQty": 6
                            }
                        ]
                    },{
                        "goodsCode": "10003",
                        "quantity": 20,
                        "realQuantity": 12,
                        "lotList": [
                            {
                                "lotNum": "25448",
                                "stockQty": 6
                            },
                            {
                                "lotNum": "25456",
                                "stockQty": 6
                            }
                        ]
                    }
                ]
            },{
            	"orderCode": "JD20170712600305100535",
                "ticketNum": "12",
                "goodsList": [
                    {
                        "goodsCode": "10001",
                        "quantity": 20,
                        "realQuantity": 12,
                        "lotList": [
                            {
                                "lotNum": "25445",
                                "stockQty": 6
                            },
                            {
                                "lotNum": "25446",
                                "stockQty": 6
                            }
                        ]
                    },{
                        "goodsCode": "10003",
                        "quantity": 20,
                        "realQuantity": 12,
                        "lotList": [
                            {
                                "lotNum": "25448",
                                "stockQty": 6
                            },
                            {
                                "lotNum": "25456",
                                "stockQty": 6
                            }
                        ]
                    }
                ]
            }
        ]
    }
}
```

返回结果
```json
{
    "code": "0",
    "message": "success"  
}
```

!> **NOTICE**  
无
