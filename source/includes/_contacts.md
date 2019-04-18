# 客戶

## 搜尋客戶
`GET https://{API_HOST}/api/v1/contact?xxxx`

```shell
curl -X GET
    -H "Content-Type: application/json"
    https://{API_HOST}/api/v1/contact?xxxx
```

### Response

Property | Type | Description
-------- | ---- | -----------
data | Array of objects | <a href="#contact">`客戶`陣列</a>
meta | Object | Pagination meta

> 回傳的 json 格式

```json

{
    "data": [
        {
            "id": 1,
            "name": "Angelita D'Amore",
            "first_name": "Angelita",
            "last_name": "D'Amore",
            "membership_no": "8771639",
            "identity_no": "418099",
            "gender": 0,
            "birth_at": "1985-08-27",
            "profile_id": 1,
            "profile": {
                "id": 1,
                "phones": []
            },
            "cz_cols": [],
        }
    ],
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 10,
        "per_page": 1,
        "to": 1,
        "total": 10
    }
}

```

### Query Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
page | false | 1 | Number | 目前在第幾頁
per_page | false | 15 | Number | 每頁呈現多少筆
id | false | NULL | Number|Array | 客戶的 id
gender | false | NULL | Number | 0: 女性, 1: 男性
birth_at__start | false | NULL | Date |生日(開始)
birth_at__end | false | NULL | Date | 生日(結束)
search | false | NULL | String | 針對電話號碼，會員編號，身分證，姓名進行模糊搜尋
cz_cols | false | NULL | Array<Object> | 動態欄位，參數型態參考下方 **CzCol** 表格說明
phone_number | false | NULL | String | 電話號碼
created_at__start | false | NULL | DateTime | 客戶建立時間(開始)
created_at__end | false | NULL | DateTime | 客戶建立時間(結束)
birth_months | false | NULL | String | 壽星月份，example: 1,2,3 表示查詢 1,2,3月的壽星
identity_no | false | NULL | String | 身分證

**CzCol**

此欄位為包含以下格式之陣列

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
id | true | NULL | Number| 動態欄位的 id
op | true | NULL | String | 比較方式: '>', '<', '=', '>=', '<=', '<>', 'in', 'not_in', 'is_null', 'is_not_null'
val | false | NULL | Number|String | 欲比對的值

**範例**
`[{"id":1, "op":">", "val": 10}, {"id":1, "op":"<", "val": 20}]`

## 新增客戶

新增客戶

```shell
curl -X POST
    -H "Content-Type: application/json"
    '{"first_name":"abc","last_name":"cde"}'
    https://{API_HOST}/api/v1/contact?xxxx
```

### Response

<a href="#contact">`客戶`</a>

> 回應的 json 格式

```json

{
    "data": {
        "id": 2,
        "name": "abc cde",
        "first_name": "abc",
        "last_name": "cde",
        "membership_no": null,
        "identity_no": null,
        "gender": null,
        "birth_at": null,
        "profile_id": 1,
        "profile": {
            "id": 1,
            "phones": []
        },
        "cz_cols": [],
    }
}

```

### Http Request
`POST https://{API_HOST}/api/v1/contact`

### Form Data

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
membership_no | false | NULL | String | 會員編號
identity_no | false | NULL | String | 身分證
gender | false | NULL | Number | 性別, 0: 女, 1: 男
first_name | true | NULL | String | 姓
last_name | false | NULL | String | 名
birth_at | false | NULL | Date | 出生日期

## 更新客戶

更新客戶

```shell
curl -X PUT
    -H "Content-Type: application/json"
    '{"first_name":"First","last_name":"Line"}'
    https://{API_HOST}/api/v1/contact/2
```

### Response

<a href="#contact">`客戶`</a>

> 回應的 json 格式

```json

{
    "data": {
        "id": 2,
        "name": "First Line",
        "first_name": "First",
        "last_name": "Line",
        "membership_no": null,
        "identity_no": null,
        "gender": null,
        "birth_at": null,
        "profile_id": 1,
        "profile": {
            "id": 1,
            "phones": []
        },
        "cz_cols": [],
    }
}

```

### Http Request
`PUT https://{API_HOST}/api/v1/contact/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | 客戶的 id

### Form Data

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
membership_no | false | NULL | String | 會員編號
identity_no | false | NULL | String | 身分證
gender | false | NULL | Number | 性別, 0: 女, 1: 男
first_name | false | NULL | String | 姓
last_name | false | NULL | String | 名
birth_at | false | NULL | Date | 出生日期

## 刪除客戶

刪除客戶

```shell
curl -X DELETE
    -H "Content-Type: application/json"
    https://{API_HOST}/api/v1/contact/2
```

> 回應的 json 格式

```json

{
    "data": {
        "status": 200,
    }
}

```

### Http Request
`DELETE https://{API_HOST}/api/v1/contact/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | 客戶的 id

