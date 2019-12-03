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
`POST https://{API_DOMAIN}/api/v1/contact/{contact}/cz-col`

### Url Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
contact | true | NULL | Number | <a href="#contact">`客戶`</a> 的 id
