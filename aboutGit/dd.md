## 5G消息V3.14

  

### 一、客户资料列表查询

  

> 原接口改动

  

#### 请求参数

  

|参数名称 | 参数 | 类型 | 描述|

| ---- | ---- | ---- | ---- |

|客户类型 | customerType | Integer | 0 第三方CSP(梦网)客户、1 官方CSP客户、2 梦网合作伙伴CSP客户|

|入网类型  | chargObj   | Integer | 0：直签入网 1：云控台入网  |

|创建人  | createUid   | String ||

|创建时间-开始时间  | createStarttm   | String ||

|创建时间-结束时间  | createEndtm   | String ||

|更新时间-开始时间  | updateStarttm   | String ||

|更新时间-结束时间  | updateEndtm   | String ||

|最后操作人  | updateUid   | String ||

  

> 请求示例

``` js

GET http://localhost:9780/5gos/api/rcsCustomerMaterial/page?pageIndex=1&pageSize=10&ecNameOrId=100013&customerType=1&chargObj=0

Authorization: {{Authorization}}

```

  

#### 响应参数

  

| 参数名称 | 参数 | 类型 |描述|

| ---- | ---- | ---- | ---- |

|客户类型 | customerType | Integer | 0 第三方CSP(梦网)客户、1 官方CSP客户、2 梦网合作伙伴CSP客户|

|入网类型  | chargObj   | Integer | 0：直签入网 1：云控台入网  |

|创建人  | createUid   | String ||

|最后操作人  | updateUid   | String ||

> 响应示例

  

``` json

{

  "content": [

     {

      "auditDesc": "",

      "auditStatus": "",

      "belongAgentCode": "MC5053626574",

      "belongAgentName": "梦网天慧5G消息云平台客户测试01",

      "belongReginCode": "01,311,3110",

      "carrier": "1",

      "chargObj": 0,

      "createTime": "2022-03-25 14:22:55",

      "createUid": "sysadmin",

      "cspId": "C20075500006",

      "customerName": "dl0001    ",

      "customerType": 0,

      "ecId": 100013,

      "id": 718,

      "messageSend": 1,

      "opType": 1,

      "serviceCodeStatus": "1",

      "statusName": "运营商审核中",

      "updateTime": "2022-08-03 19:25:47",

      "updateUid": "sysadmin",

      "usable": 1

    }

  ],

  "total": 1

}

```

  

> 对象定义

``` java

@Data

@EqualsAndHashCode(callSuper = true)

public class RcsCustomerMaterialListDTO extends BaseDTO implements Serializable {

  

    private static final long serialVersionUID = -2253772916048600159L;

    /**

     * 自增ID

     */

    private Long id;

  

    /**

     * cspId

     */

    private String cspId;

  

    /**

     * 企业ID

     */

    private Integer ecId;

  

    /**

     * 客户名称

     */

    private String customerName;

  

    /**

     * 1新增，2修改

     */

    private Integer opType;

  

    /**

     * 审核状态

     */

    private String auditStatus;

  

    /**

     * 审核意见

     */

    private String auditDesc;

  

    /**

     * 运营商 0-移动,1-联通,21-电信,5-海外

     */

    private String carrier;

  

    /**

     * 是否可用 0可用，1不可用

     */

    private Integer usable;

  

    /**

     * 服务代码状态（0正常，1异常）

     */

    private String serviceCodeStatus;

  

    /**

     * 状态名称

     */

    private String statusName;

  

    /**

     * 主服务代码

     */

    private String serviceCode;

  

    /**

     * 落户地编码 大区,省,市   05,200,7550

     */

    private String belongReginCode;

  

    /**

     * 代理商

     */

    private String belongAgentName;

  

    /**

     * 代理商编码

     */

    private String belongAgentCode;

  

    /**

     * 0：待发送 1：已发送

     */

    private Integer messageSend;

  

    /**

     * 入网类型 0：直签入网  1：云控台入网

     */

    private Integer chargObj;

  

    /**

     *  客户类型 0梦网客户 1运营商直签客户 2 梦网合作伙伴客户

     */

    private Integer customerType;

  

    /**

     * 创建人

     */

    private String createUid;

  

    /**

     * 最后操作人

     */

    private String updateUid;

}

```

  

#### 描述

  

V3.14 删除chatbotNumber(chatbot数量)、tplNumber(模板数量),原chargObj(客户类型) -> chargObj(入网类型),新增customerType(客户类型)、创建人、创建时间-开始时间、创建时间-结束时间、更新时间-开始时间、更新时间-结束时间、最后操作人

  
  

### 二、根据运营商和客户类型查询代理商

  

> 新增接口

  

#### 请求参数

  

| 参数名称 | 参数        | 类型 | 描述                                  |

|------|-----------| ---- |-------------------------------------|

| 运营商  | carrier   | Integer | 0移动 1联通 21电信                        |

| 客户类型 | agentType | Integer | 0 第三方CSP(梦网)客户、1 官方CSP客户、2 梦网合作伙伴CSP客户 |

  

> 请求示例

``` js

GET http://localhost:9780/5gos/api/rcsAgent/getByAgentTypeAndCarrier?carrier=0&agentType=0

Authorization: {{Authorization}}

```

  

#### 响应参数

  

| 参数名称 | 参数 | 类型 |描述|

| ---- | ---- | ---- | ---- |

|客户类型 | customerType | Integer | 0 第三方CSP(梦网)客户、1 官方CSP客户、2 梦网合作伙伴CSP客户|

|入网类型  | chargObj   | Integer | 0：直签入网 1：云控台入网  |

|创建人  | createUid   | String ||

|最后操作人  | updateUid   | String ||

> 响应示例

``` json

[

  {

    "belongAgentCode": "MIKE1996",

    "belongAgentName": "华庚专用代理商",

    "carrier": 0,

    "createTime": "2022-08-05 19:09:17",

    "createUid": "sysadmin",

    "cspId": "C20075500003",

    "ecId": 0,

    "envTag": "PRD",

    "finalStatus": "NORMAL",

    "id": 39,

    "officeCode": "05",

    "provinceCode": "200",

    "remarks": "",

    "updateTime": "2022-08-05 19:09:17",

    "updateUid": "sysadmin"

  }

]

```

  

> 对象定义

``` java

@Data

@EqualsAndHashCode(callSuper = true)

public class RcsAgentDTO extends BaseDTO {

  

    /**

     * 自增ID

     */

    private Long id;

  

    /**

     * 企业ID

     */

    private Integer ecId;

  

    /**

     * CSP_ID

     */

    private String cspId;

  

    /**

     * 运营商 0-移动,1-联通,21-电信,5-海外

     */

    private Integer carrier;

  

    /**

     * 代理商名称

     */

    private String belongAgentName;

  

    /**

     * 代理商编码

     */

    private String belongAgentCode;

  

    /**

     * 最终状态 NORMAL-正常可用;FORBIDDEN-已禁用

     */

    private String finalStatus;

  

    /**

     * 归属大区编码：01-华北02-东北03-华东北04-华东南05-华南06-华中07-西南08-西北

     */

    private String officeCode;

  

    /**

     * 归属省份编号

     */

    private String provinceCode;

  

    /**

     * 环境

     */

    private String envTag;

}

```

  

#### 描述

  

V3.14 新增客户资料页面，根据运营商和客户类型查询代理商

![img.png](5gos_lhj.access/img.png)

  

### 三、新增客户资料（新增官方CSP客户/梦网合作伙伴CSP客户）

  

> 原接口改动

  

#### 请求参数

  

| 参数名称 | 参数           | 类型                        | 描述                                     |

|------|--------------|---------------------------|----------------------------------------|

| 客户名称 | mwCustomerName      | String                    |                                        |

| 客户编码 | ecId         | Integer                   |                                        |

| 运营商  | carrier      | Integer                   | 0移动 1联通 21电信                           |

| 客户类型 | customerType | Integer                   | 0 第三方CSP(梦网)客户、1 官方CSP客户、2 梦网合作伙伴CSP客户 |

| 服务代码列表 | customerServiceCodes | List<CustomerServiceCode> | CustomerServiceCode定义见下                |

  

>  CustomerServiceCode

```java

@Data

public static class CustomerServiceCode{

    /**

     * 运营商

     */

    private Integer carrier;

  

    /**

     * 代理商编码

     */

    private String belongAgentCode;

  

    /**

     * 服务代码

     */

    private String serviceCode;

  

    /**

     * 扩展码

     */

    private String extCode;

}

```

  

> 请求示例

``` js

POST http://localhost:9780/5gos/api/rcsCustomerMaterial/add

Content-Type: application/json

Authorization: {{Authorization}}

```