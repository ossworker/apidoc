# 校园招聘 API
Java API
标签: 【integral-mall】【栾锋】

version 1.0.0



- **服务地址：** serviceUrl  
> **开发环境：** http://192.168.7.65:8083/  
> **测试环境：**  
> **生产环境：**

---

## 用户

### 1. 发送验证码  

- **接口描述**  
> 通过手机号码发送验证码

- **接口信息**  
> **接口地址：** {{serviceUrl}}/openx/user/jobUserService/sendCode
> **提交方式：** POST,GET  
> **方法名称：** sendCode  

- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----:|
|phone|string|是|手机号码 校验手机号码|




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
    "phone":"15116451260"
}
```

返回结果
```json

```

 **NOTICE**  
 手机号码前台需要校验

 
---


### 2. 登录  

- **接口描述**  
> 通过手机号码，验证码登录

- **接口信息**  
> **接口地址：** {{serviceUrl}}/openx/user/jobUserService/login  
> **提交方式：** POST,GET  
> **方法名称：** login

- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----:|
|phone|string|是|手机号码，前台需要校验|
|code|string|是|验证码|




- **响应结果**


 正常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
|userId|string|59a69c51cff7733a24323458|用户id|
|phone|string|15116451260|手机号码|
|createTime|number|1504091218000|创建时间|
|modifyTime|number|1504091218000|修改时间|


 异常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
| code | String | 11000000 |  |
| message | String | | |




- **示例**

入参示例: 
```json
{
    "phone":"15116451260",
    "code":"805759"
}
```

返回结果
```json

```

 **NOTICE**  
无

 
---




## 职位

### 1. 发布的职位 

- **接口描述**  
> 分页查询发布的职位

- **接口信息**  
> **接口地址：** {{serviceUrl}}/openx/position/jobPositionService/queryPositionForPage
> **提交方式：** POST,GET  
> **方法名称：** queryPositionForPage  


- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----:|
|position|object|是|职位对象|
|pageInfo|object|是|分页对象|
|pageInfo.page|int|是|当前页|
|pageInfo.limit|int|是|每页大小|

-  **响应结果** 


 正常

|名称|类型|示例值|描述|
|:----:|:----:|:----:|:----:|
|jobNum|int|2017080001|岗位编号|
|jobNature|string|CAMPUS|job属性 全职FULL-TIME 兼职PART-TIME 实习INTERNSHIP 校园 CAMPUS|
|jobName|string|行政专员|岗位名称|
|jobCategory|string|行政类|岗位类别|
|jobPeopleLimit|int|0|岗位招聘人数限制 0表示无限|
|jobEducationRequirement|string|本科以上|岗位学历要求|
|jobExperienceRequirement|string|无限制|岗位经验要求|
|jobSalary|string|3000-4000|岗位薪资范围|
|jobDesc|string||岗位描述|
|jobRequirement|string||岗位要求|
|jobHighlightLabel|string|五险一金,带薪休假|岗位亮点标签|
|jobPublishArea|string|长沙，武汉|岗位发布地点|
|jobDepartment|string|行政部|岗位所属部门|
|jobWorkAddress|string|湖南省长沙市岳麓区桐梓坡路68号|岗位地点|
|jobEndTime|number||招聘截止日期|
|createTime|number||创建时间|
|modifyTime|number||修改时间|

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
		"page":1,
		"limit":20
	},
	"position":{}
}
```

返回结果
```json
[
    {
        "id": "59a7afb6cff7731dd8ef747d",
        "jobCategory": "JAVA开发工程师",
        "jobDepartment": "益丰大药房连锁股份有限公司",
        "jobDesc": "岗位职责: 处理日常公司事务；\n任职要求：需要细心，认真",
        "jobEducationRequirement": "本科",
        "jobEndTime": 61467576118000,
        "jobExperienceRequirement": "2-3年",
        "jobHighlightLabel": "五险一金,年底双薪,绩效奖金,包吃包住,免费班车,节日福利,",
        "jobName": "技术类",
        "jobNature": "CAMPUS",
        "jobNum": 2017080003,
        "jobPeopleLimit": 1,
        "jobPublishArea": "长沙,武汉,上海",
        "jobSalary": "6000-10000",
        "jobWorkAddress": "长沙市麓谷高新区金洲大道68号益丰医药园",
        "modifyTime": 1504161718000
    },
    {
        "id": "59a7af52cff7732d0802d229",
        "jobCategory": "财务类",
        "jobDepartment": "益丰大药房连锁股份有限公司",
        "jobDesc": "岗位职责: 处理日常公司事务；\n任职要求：需要细心，认真",
        "jobEducationRequirement": "本科",
        "jobEndTime": 61467576019000,
        "jobExperienceRequirement": "1年以下",
        "jobHighlightLabel": "五险一金,年底双薪,绩效奖金,包吃包住,免费班车,节日福利,",
        "jobName": "财务会计",
        "jobNature": "CAMPUS",
        "jobNum": 2017080002,
        "jobPeopleLimit": 1,
        "jobPublishArea": "长沙",
        "jobSalary": "5000-6000",
        "jobWorkAddress": "长沙市麓谷高新区金洲大道68号益丰医药园",
        "modifyTime": 1504161619000
    },
    {
        "id": "59a7aefacff77331f085765f",
        "jobCategory": "行政类",
        "jobDepartment": "益丰大药房连锁股份有限公司",
        "jobDesc": "岗位职责: 处理日常公司事务；\n任职要求：需要细心，认真",
        "jobEducationRequirement": "本科",
        "jobEndTime": 61467575930000,
        "jobExperienceRequirement": "1年以下",
        "jobHighlightLabel": "五险一金,年底双薪,绩效奖金,包吃包住,免费班车,节日福利,",
        "jobName": "行政专员",
        "jobNature": "CAMPUS",
        "jobNum": 2017080001,
        "jobPeopleLimit": 1,
        "jobPublishArea": "长沙，武汉",
        "jobSalary": "4000-6000",
        "jobWorkAddress": "长沙市麓谷高新区金洲大道68号益丰医药园",
        "modifyTime": 1504161530000
    }
]
```

 **NOTICE**  
无

 
---




## OSS

### 1. oss签名  

- **接口描述**  
> 通过文件名称和文件类型获取oss签名  

- **接口信息**  
> **接口地址：** {{serviceUrl}}/openx/oss/ossService/sign
> **提交方式：** POST,GET  
> **方法名称：** sign  


- **请求参数**

|名称|类型|是否必须|描述|
|:----:|:----:|:----:|:----:|
|filename|string|是|文件名称|
|type|string|是|类型IMG:头像 DOC:简历附件|


-  **响应结果** 


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
	"filename":"1.png",
	"type":"IMG"
}
```

返回结果
```json
{
    "accessID": "LTAIm55NJbtNXqeW",
    "expire": "1504184102",
    "host": "http://yf-example.oss-cn-shenzhen.aliyuncs.com",
    "key": "test-env/yf-recruitment/img/1.png",
    "policy": "eyJleHBpcmF0aW9uIjoiMjAxNy0wOC0zMVQxMjo1NTowMi43ODNaIiwiY29uZGl0aW9ucyI6W1siY29udGVudC1sZW5ndGgtcmFuZ2UiLDAsMTA0ODU3NjAwMF0seyJrZXkiOiJ0ZXN0LWVudi95Zi1yZWNydWl0bWVudC9pbWcvMS5wbmcifV19",
    "signature": "eKdtAaaFGxEg+vb5Cjwu/NwIoVs="
}
```

 **NOTICE**  
无

 
---