# 聯絡地址

## 查詢國家

查詢國家

```shell
curl -X GET
    -H "Content-Type: application/json"
    "https://{API_HOST}/api/v1/country?per_page=3"
```

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
`GET https://{API_DOMAIN}/api/v1/city`

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
`GET https://{API_DOMAIN}/api/v1/city`

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
name | false | NULL | String | 區名稱

## 新增聯絡地址

新增聯絡地址

```shell
curl -X POST
    -H "Content-Type: application/json"
    '{"profile_id":1,"country_id":1,"state_id":1,"city_id":1,"address": "67, rue Michelle Jones 81785 Berge"}'
    https://{API_HOST}/api/v1/address
```

> 回傳 json 格式

```json
{
    "data": {
        "id": 1,
        "type": 3,
        "address": "67, rue Michelle Jones\n81785 Berge",
        "profile_id": 1,
        "state": {
            "id": 1,
            "country_id": 1,
            "name": "台北市"
        },
        "state_id": 1,
        "country": {
            "id": 1,
            "name": "台灣",
            "abbrev": null
        },
        "country_id": 1,
        "city": {
            "id": 1,
            "state_id": 1,
            "name": "仁愛區",
            "zipcode": "200"
        },
        "city_id": 1,
        "description": null
    }
}
```

### Http Request
`POST https://{API_DOMAIN}/api/v1/address`

### Form Data

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
profile_id | true | NULL | Number | 客戶的 **profile_id**
type | true | NULL | Number | 0:住家,1:郵寄,2:帳單,3:快遞,4:現居,5:其他
address | true | NULL | String | 地址
country_id | true | NULL | Number | 國家的id
state_id | true | NULL | Number | 城市的id
city_id | false | NULL | Number | 區域的id
description | false | NULL | String | 地址描述

## 修改聯絡地址

修改聯絡地址

```shell
curl -X PUT
    -H "Content-Type: application/json"
    '{"address": "仁愛路一段"}'
    https://{API_HOST}/api/v1/address/1
```

> 回傳 json 格式

```json
{
    "data": {
        "id": 1,
        "type": 3,
        "address": "信義路一段",
        "profile_id": 1,
        "state": {
            "id": 1,
            "country_id": 1,
            "name": "台北市"
        },
        "state_id": 1,
        "country": {
            "id": 1,
            "name": "台灣",
            "abbrev": null
        },
        "country_id": 1,
        "city": {
            "id": 1,
            "state_id": 1,
            "name": "仁愛區",
            "zipcode": "200"
        },
        "city_id": 1,
        "description": null
    }
}
```

### Http Request
`PUT https://{API_DOMAIN}/api/v1/address/{address}`

### URL Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
address | true | NULL| Number | 地址的id

### Form Data

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
profile_id | false | NULL | Number | 客戶的 **profile_id**
type | false | NULL | Number | 0:住家,1:郵寄,2:帳單,3:快遞,4:現居,5:其他
address | false | NULL | String | 地址
country_id | false | NULL | Number | 國家的id
state_id | false | NULL | Number | 城市的id
city_id | false | NULL | Number | 區域的id
description | false | NULL | String | 地址描述

## 刪除聯絡地址

刪除聯絡地址

```shell
curl -X DELETE
    -H "Content-Type: application/json"
    https://{API_HOST}/api/v1/address/1
```

> 回傳 json 格式

```json
{
    "data": {
        "status": 200
    }
}
```

### Http Request
`DELETE https://{API_DOMAIN}/api/v1/address/{address}`

### URL Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
address | true | NULL| Number | 地址的id