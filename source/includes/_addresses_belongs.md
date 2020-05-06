# 國家，縣市，區

## 查詢國家

查詢國家

```shell
curl -X GET
    -H "Content-Type: application/json"
    "https://{API_HOST}/api/v1/country?per_page=3"
```

### Response

Property | Type | Description
-------- | ---- | -----------
data | Array of objects | <a href="#country">國家陣列</a>
meta | Object | Pagination meta

> 回傳 json 格式

```json
{
    "data": [
        {
            "id": 1,
            "name": "台灣",
            "abbrev": null
        }
    ],
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 1,
        "per_page": "3",
        "to": 1,
        "total": 1
    }
}
```

### Http Request
`GET https://{API_DOMAIN}/api/v1/state`

### Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
page | false | 1 | Number | 目前在第幾頁
per_page | false | 15 | Number | 每頁呈現多少筆

## 查詢縣市

查詢縣市

```shell
curl -X GET
    -H "Content-Type: application/json"
    "https://{API_HOST}/api/v1/state?per_page=3"
```

### Response

Property | Type | Description
-------- | ---- | -----------
data | Array of objects | <a href="#state">縣市陣列</a>
meta | Object | Pagination meta

> 回傳 json 格式

```json
{
    "data": [
        {
            "id": 2,
            "country_id": 1,
            "name": "基隆市",
            "country": {
                "id": 1,
                "name": "台灣",
                "abbrev": null
            }
        },
        {
            "id": 3,
            "country_id": 1,
            "name": "台北市",
            "country": {
                "id": 1,
                "name": "台灣",
                "abbrev": null
            }
        },
        {
            "id": 4,
            "country_id": 1,
            "name": "新北市",
            "country": {
                "id": 1,
                "name": "台灣",
                "abbrev": null
            }
        }
    ],
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 8,
        "per_page": "3",
        "to": 3,
        "total": 23
    }
}
```

### Http Request
`GET https://{API_DOMAIN}/api/v1/state`

### Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
page | false | 1 | Number | 目前在第幾頁
per_page | false | 15 | Number | 每頁呈現多少筆
name | false | NULL | String | 縣市名稱

## 查詢區

查詢區

```shell
curl -X GET
    -H "Content-Type: application/json"
    "https://{API_HOST}/api/v1/city?per_page=3"
```

### Response

Property | Type | Description
-------- | ---- | -----------
data | Array of objects | <a href="#city">區域陣列</a>
meta | Object | Pagination meta

> 回傳 json 格式

```json
{
    "data": [
        {
            "id": 1,
            "state_id": 2,
            "state": {
                "id": 2,
                "country_id": 1,
                "name": "基隆市"
            },
            "name": "仁愛區",
            "zipcode": "200"
        },
        {
            "id": 2,
            "state_id": 2,
            "state": {
                "id": 2,
                "country_id": 1,
                "name": "基隆市"
            },
            "name": "信義區",
            "zipcode": "201"
        },
        {
            "id": 3,
            "state_id": 2,
            "state": {
                "id": 2,
                "country_id": 1,
                "name": "基隆市"
            },
            "name": "中正區",
            "zipcode": "202"
        }
    ],
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 124,
        "per_page": "3",
        "to": 3,
        "total": 371
    }
}
```

### Http Request
`GET https://{API_DOMAIN}/api/v1/city`

### Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
page | false | 1 | Number | 目前在第幾頁
per_page | false | 15 | Number | 每頁呈現多少筆
state_id | false | NULL | Number | <a href="#state">縣市</a>的 id
zipcode | false | NULL | Number | 郵遞區號
name | false | NULL | String | 郵遞區名
