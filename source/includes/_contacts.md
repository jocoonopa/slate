# 客戶

## 搜尋客戶
`GET https://{API_HOST}/api/v1/contact?xxxx`

考根據下方的 **Query Parameters** 表單的參數進行過濾篩選

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
            "cz_cols": [
                {
                    "id": 1,
                    "value": "19999",
                    "category_id": 1
                },
                {
                    "id": 4,
                    "value": "51",
                    "category_id": 1
                },
                {
                    "id": 5,
                    "value": null,
                    "category_id": 1
                },
                {
                    "id": 6,
                    "value": null,
                    "category_id": 1
                },
                {
                    "id": 7,
                    "value": null,
                    "category_id": 1
                },
                {
                    "id": 8,
                    "value": null,
                    "category_id": 1
                },
                {
                    "id": 12,
                    "value": null,
                    "category_id": 1
                },
                {
                    "id": 21,
                    "value": null,
                    "category_id": 1
                },
                {
                    "id": 2,
                    "value": null,
                    "category_id": 2
                },
                {
                    "id": 20,
                    "value": null,
                    "category_id": 2
                },
                {
                    "id": 3,
                    "value": null,
                    "category_id": 6
                },
                {
                    "id": 9,
                    "value": null,
                    "category_id": 7
                },
                {
                    "id": 10,
                    "value": null,
                    "category_id": 7
                },
                {
                    "id": 11,
                    "value": null,
                    "category_id": 7
                },
                {
                    "id": 13,
                    "value": null,
                    "category_id": 8
                },
                {
                    "id": 14,
                    "value": null,
                    "category_id": 8
                },
                {
                    "id": 15,
                    "value": null,
                    "category_id": 8
                },
                {
                    "id": 16,
                    "value": "0",
                    "category_id": 9
                }
            ],
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
email | false | NULL |String | 電子郵件地址
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
cz_cols | false | NULL | Array<Object> | 動態欄位，參數型態參考下方 **CzCol** 表格說明


**CzCol**

此欄位為包含以下格式之陣列

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
id | true | NULL | Number| 動態欄位的 id
value | true | NULL | String | 動態欄位的值

**範例**

假設目前有兩個動態欄位，分別為

id=1, name='體重'
id=2, name='血型'

則參數範例如右:

> Form Data cz_cols

```json
[
    {"id":1, "value":"18KG"}, // 1: 體重
    {"id":2, "value": "AB型"} // 2: 血型
]
```

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
cz_cols | false | NULL | Array<Object> | 動態欄位，參數型態參考下方 **CzCol** 表格說明


**CzCol**

此欄位為包含以下格式之陣列

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
id | true | NULL | Number| 動態欄位的 id
value | true | NULL | String | 動態欄位的值

**範例**

假設目前有3個動態欄位，分別為

- id=1, type=1 (字串), name='體重'
- id=2, type=6 (單選), name='血型', options (選項)=[{"text": "A型", "value":"A"},{"text": "B型", "value":"B"},{"text": "O型", "value":"O"},{"text": "AB型", "value":"AB"}]
- id=3, type=7 (多選), name='從事運動', options (選項)=[{"text": "籃球", "value": 0}, {"text": "跑步", "value": 1}, {"text": "游泳", "value": 2}]

則參數範例如右: (注意不論是**單選**還是**多選**，都是丟 value，若誤丟 text 會導致前端顯示出現問題)

> Form Data cz_cols

```json
[
    {"id":1, "value":"70"}, // 1: 體重
    {"id":2, "value":"AB"}, // 2: 血型
    {"id":3, "value": [1, 2]} // 3. 運動: 跑步+游泳
]
```



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
        "status": 204,
    }
}

```

### Http Request
`DELETE https://{API_HOST}/api/v1/contact/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | <<a href="#contact">`客戶`</a>的 id

