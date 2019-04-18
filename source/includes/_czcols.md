# 動態欄位

## 目前系統所有的動態欄位

目前系統所有的動態欄位

```shell
curl -X GET
    -H "Content-Type: application/json:Authorization: Bearer eyJhbGciOiJIUzI1NiI..." https://{API_HOST}/api/v1/cz-col
```

### Response

Property | Type | Description
-------- | ---- | -----------
data | Array of objects | <a href="#cz-col">`動態欄位`陣列</a>
meta | Object | Pagination meta

> 回傳 json 格式

```json
{
    "data": [
        {
            "id": 1,
            "name": "Cyril223",
            "description": "Assumenda est corrupti voluptas aut. Beatae quisquam ex asperiores sit ullam.",
            "is_allowed_null": true,
            "default": null,
            "type": 4,
            "category_id": null,
            "category": null,
            "creater_id": null,
            "creater": null
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

### Http Request
` https://{API_DOMAIN}/api/v1/cz-col`

### Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
page | false | 1 | Number | 目前在第幾頁
per_page | false | 15 | Number | 每頁呈現多少筆


## 此客戶綁定的動態欄位

此客戶綁定的動態欄位

```shell
curl -X GET
    -H "Content-Type: application/json:Authorization: Bearer eyJhbGciOiJIUzI1NiI..." https://{API_HOST}/api/v1/contact/1/cz-col
```

### Response

<a href="#cz-col">`動態欄位`</a>

> 回傳 json 格式

```json
{
    "data": [
        {
            "id": 1,
            "name": "Cyril223",
            "default": null,
            "description": "Assumenda est corrupti voluptas aut. Beatae quisquam ex asperiores sit ullam.",
            "is_allowed_null": true,
            "type": 4,
            "created_at": "2019-04-10 04:09:27",
            "updated_at": "2019-04-10 04:09:27",
            "category_id": null,
            "creater_id": null,
            "pivot": {
                "contact_id": 1,
                "cz_col_id": 1,
                "value": null
            }
        },
        {
            "id": 2,
            "name": "Geovany63",
            "default": null,
            "description": "Dolorum rerum ut est quam unde recusandae consequatur. Nobis laudantium eum et voluptatem sunt sint. Et occaecati voluptas ut aliquid cum sed.",
            "is_allowed_null": true,
            "type": 1,
            "created_at": "2019-04-10 04:09:27",
            "updated_at": "2019-04-10 04:09:27",
            "category_id": null,
            "creater_id": null,
            "pivot": {
                "contact_id": 1,
                "cz_col_id": 2,
                "value": "5"
            }
        }
    ]
}
```

### Http Request
` https://{API_DOMAIN}/api/v1/contact/{contact}/cz-col`

### Url Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
contact | true | NULL | Number | 客戶 的 id

## 綁定並更新客戶的動態欄位之值

綁定並更新客戶的動態欄位之值

```shell
# POST|PUT

curl -X PUT
    -H "Content-Type: application/json"
    '{"value":"Updated"}'
    https://{API_HOST}/api/v1/contact/1/cz-col/1
```

### Response

<a href="#cz-col">`動態欄位`</a>

> 回傳 json 格式

```json
{
    "data": [
        {
            "id": 1,
            "name": "Cyril223",
            "default": null,
            "description": "Assumenda est corrupti voluptas aut. Beatae quisquam ex asperiores sit ullam.",
            "is_allowed_null": true,
            "type": 4,
            "created_at": "2019-04-10 04:09:27",
            "updated_at": "2019-04-10 04:09:27",
            "category_id": null,
            "creater_id": null,
            "pivot": {
                "contact_id": 1,
                "cz_col_id": 1,
                "value": "Updated"
            }
        },
        {
            "id": 2,
            "name": "Geovany63",
            "default": null,
            "description": "Dolorum rerum ut est quam unde recusandae consequatur. Nobis laudantium eum et voluptatem sunt sint. Et occaecati voluptas ut aliquid cum sed.",
            "is_allowed_null": true,
            "type": 1,
            "created_at": "2019-04-10 04:09:27",
            "updated_at": "2019-04-10 04:09:27",
            "category_id": null,
            "creater_id": null,
            "pivot": {
                "contact_id": 1,
                "cz_col_id": 2,
                "value": "5"
            }
        }
    ]
}
```

### Http Request
` https://{API_DOMAIN}/api/v1/contact/{contact}/cz-col/{cz_col}`

### URL Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
contact | true | NULL | Number | 客戶的 id
cz_col | true | NULL | Number | 動態欄位的 id

### Form Data
Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
value | false | NULL | mix | 此客戶該動態欄位的值
