#電子信箱

## 搜尋電子信箱

搜尋電子信箱

```shell
curl -X GET
    -H "Content-Type: application/json"
    "https://{API_HOST}/api/v1/email-contact?contact_id=1"
```

> 回傳 json 格式

```json
{
    "data": [
        {
            "id": 1,
            "address": "harvey.bartholome@gmail.com",
            "contact_id": 1,
            "draft": null,
            "name": "Jaiden Champlin III",
            "description": "Pariatur dolorem aut voluptatibus. Aut pariatur voluptatum ratione atque sit. Et inventore quo voluptates animi.",
            "contact": {
                "id": 1,
                "membership_no": "8771639",
                "identity_no": "418099",
                "first_name": "Angelita",
                "last_name": "D'Amore",
                "gender": 0,
                "birth_at": "1985-08-27 00:00:00",
                "created_at": "2019-04-10 03:01:41",
                "updated_at": "2019-04-10 03:01:41",
                "profile_id": 1,
                "sponsor_id": null,
                "disturb_setting": null
            }
        },
        {
            "id": 5,
            "address": "shyanne47@hotmail.com",
            "contact_id": 1,
            "draft": null,
            "name": "Mikayla Funk",
            "description": "Possimus optio molestiae perspiciatis distinctio. Vel incidunt ut unde. Laudantium eaque distinctio officia eum error odit.",
            "contact": {
                "id": 1,
                "membership_no": "8771639",
                "identity_no": "418099",
                "first_name": "Angelita",
                "last_name": "D'Amore",
                "gender": 0,
                "birth_at": "1985-08-27 00:00:00",
                "created_at": "2019-04-10 03:01:41",
                "updated_at": "2019-04-10 03:01:41",
                "profile_id": 1,
                "sponsor_id": null,
                "disturb_setting": null
            }
        }
    ],
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 1,
        "per_page": 15,
        "to": 2,
        "total": 2
    }
}
```

### Http Request
`GET https://{API_DOMAIN}/api/v1/email-contact`

### Query Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
page | false | 1 | Number | 目前在第幾頁
per_page | false | 15 | Number | 每頁呈現多少筆
contact_id | false | NULL | Number | 客戶的id
name | false | NULL | String | 定義的 Email 名稱
description | false | NULL | String | Email 備註
address | false | NULL | String | Email 位址

### Response

Property | Type | Description
-------- | ---- | -----------
data | Array of objects | <a href="#emailcontact">`電子信箱`陣列</a>
meta | Object | Pagination meta

<!-- ///開始分隔線 -->
## 取得指定電子信箱

```shell
curl -X GET
    -H "Content-Type: application/json"
    https://{API_HOST}/api/v1/email-contact/1
```

### Response

請參考<a href="#emailcontact">`電子信箱`</a>回應格式

Property | Type | Description
-------- | ---- | -----------
data | Object | <a href="#emailcontact">`電子信箱`</a>

> 回傳 json 格式

```json

{
    "data": {
        "id": 1,
        "address": "harvey.bartholome@gmail.com",
        "contact_id": 1,
        "draft": null,
        "name": "Jaiden Champlin III",
        "description": "Pariatur dolorem aut voluptatibus. Aut pariatur voluptatum ratione atque sit. Et inventore quo voluptates animi.",
        "contact": {
            "id": 1,
            "membership_no": "8771639",
            "identity_no": "418099",
            "first_name": "Angelita",
            "last_name": "D'Amore",
            "gender": 0,
            "birth_at": "1985-08-27 00:00:00",
            "created_at": "2019-04-10 03:01:41",
            "updated_at": "2019-04-10 03:01:41",
            "profile_id": 1,
            "sponsor_id": null,
            "disturb_setting": null
        }
    }
}

```

### Http Request
` https://{API_DOMAIN}/api/v1/email-contact/{email_contact}`

### URL Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
email_contact | True | Null | Number | <a href="#emailcontact">電子信箱</a>的 id

<!-- 結束分隔線/// -->


## 新增電子信箱

指定客戶新增電子信箱

```shell
curl -X POST
    -H "Content-Type: application/json"
    '{"contact_id":1,"address":"loren18@ortiz.biz","name":"Theresia Zieme"}'
    https://{API_HOST}/api/v1/email-contact
```

### Response

<a href="#email">`電子信箱`</a>

> 回傳 json 格式

```json
{
    "data": {
        "id": 3,
        "address": "loren18@ortiz.biz",
        "contact_id": 1,
        "draft": null,
        "name": "Theresia Zieme",
        "description": null,
        "contact": {
            "id": 1,
            "membership_no": "8771639",
            "identity_no": "418099",
            "first_name": "Angelita",
            "last_name": "D'Amore",
            "gender": 0,
            "birth_at": "1985-08-27 00:00:00",
            "created_at": "2019-04-10 03:01:41",
            "updated_at": "2019-04-10 03:01:41",
            "profile_id": 1,
            "sponsor_id": null,
            "disturb_setting": null
        }
    }
}
```

### Http Request
`POST https://{API_DOMAIN}/api/v1/email-contact`

### Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
contact_id | true | NULL | Number | 客戶的id
address | true | NULL | String | 電子信箱地址
name | false | NULL | String | 電子信箱自定義名稱
description | false | NULL | String | 電子信箱自定義描述

## 更新指定電子信箱

更新指定電子信箱

```shell
curl -X PUT
    -H "Content-Type: application/json"
    '{"name":"Sharon"}'
    https://{API_HOST}/api/v1/email-contact/1
```

### Response

<a href="#email">`電子信箱`</a>

> 回傳 json 格式

```json
{
    "data": {
        "id": 3,
        "address": "loren18@ortiz.biz",
        "contact_id": 1,
        "draft": null,
        "name": "Sharon",
        "description": null,
        "contact": {
            "id": 1,
            "membership_no": "8771639",
            "identity_no": "418099",
            "first_name": "Angelita",
            "last_name": "D'Amore",
            "gender": 0,
            "birth_at": "1985-08-27 00:00:00",
            "created_at": "2019-04-10 03:01:41",
            "updated_at": "2019-11-10 03:01:41",
            "profile_id": 1,
            "sponsor_id": null,
            "disturb_setting": null
        }
    }
}
```

### Http Request
`PUT https://{API_DOMAIN}/api/v1/email-contact/{email_contact}`

### Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
address | true | NULL | String | 電子信箱地址
name | false | NULL | String | 電子信箱自定義名稱
description | false | NULL | String | 電子信箱自定義描述

## 刪除電子信箱

刪除指定客戶的電子信箱

```shell
curl -X DELETE
    -H "Content-Type: application/json"
    "https://{API_HOST}/api/v1/email-contact?contact_id=1"
```

> 回傳 json 格式

http status: 204

```json
{}
```

### Http Request
` https://{API_DOMAIN}/api/v1/email-contact/{email_contact}`

### URL Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
email_contact | true | NULL | Number | 電子信箱的id