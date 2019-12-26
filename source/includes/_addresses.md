# 聯絡地址

## 搜尋聯絡地址

搜尋聯絡地址

```shell
curl -X GET
    -H "Content-Type: application/json"
    '{"city_id":1}'
    https://{API_HOST}/api/v1/address
```

> 回傳 json 格式

```json

{
    "data": [
        {
            "id": 2678,
            "type": 1,
            "enum_type": {
                "key": "MAILING",
                "value": 1,
                "description": "mail address"
            },
            "address": "基隆市仁愛區愛一路35號8樓之一",
            "contact_id": 1938277,
            "profile_id": 1938247,
            "state": {
                "id": 2,
                "country_id": 1,
                "name": "基隆市"
            },
            "state_id": 2,
            "country": {
                "id": 1,
                "name": "台灣",
                "abbrev": null
            },
            "country_id": 1,
            "city": {
                "id": 1,
                "state_id": 2,
                "name": "仁愛區",
                "zipcode": "200"
            },
            "city_id": 1,
            "description": null
        },
        {
            "id": 2830,
            "type": 1,
            "enum_type": {
                "key": "MAILING",
                "value": 1,
                "description": "mail address"
            },
            "address": "愛一路19號",
            "contact_id": 1938482,
            "profile_id": 1938452,
            "state": {
                "id": 2,
                "country_id": 1,
                "name": "基隆市"
            },
            "state_id": 2,
            "country": {
                "id": 1,
                "name": "台灣",
                "abbrev": null
            },
            "country_id": 1,
            "city": {
                "id": 1,
                "state_id": 2,
                "name": "仁愛區",
                "zipcode": "200"
            },
            "city_id": 1,
            "description": null
        }
    ],
    "links": {
        "first": "https://firstline.localhost/api/address?per_page=2&city_id=1&page=1",
        "last": "https://firstline.localhost/api/address?per_page=2&city_id=1&page=63",
        "prev": null,
        "next": "https://firstline.localhost/api/address?per_page=2&city_id=1&page=2"
    },
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 63,
        "path": "https://firstline.localhost/api/address",
        "per_page": "2",
        "to": 2,
        "total": 126
    }
}

```

### Http Request
`GET https://{API_DOMAIN}/api/v1/address`

### Form Data

下表為可使用的過濾條件

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
contact_id | false | NULL | Number | 客戶的 id
type | false | NULL | Number | 0:住家,1:郵寄,2:帳單,3:快遞,4:現居,5:其他
address | false | NULL | String | 地址
country_id | false | NULL | Number | 國家的id
state_id | false | NULL | Number | 城市的id
city_id | false | NULL | Number | 區域的id
description | false | NULL | String | 地址描述


### Response

Property | Type | Description
-------- | ---- | -----------
data | Array of objects | <a href="#address">`地址`陣列</a>
meta | Object | Pagination meta


## 取得指定客戶聯絡地址


<!-- ///開始分隔線 -->
## 取得指定聯絡地址

```shell
curl -X GET
    -H "Content-Type: application/json"
    https://{API_HOST}/api/v1/address/1
```

### Response

請參考<a href="#address">`地址`</a>回應格式

Property | Type | Description
-------- | ---- | -----------
data | Object | <a href="#address">`地址`</a>

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
` https://{API_DOMAIN}/api/v1/address/{address}`

### URL Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
address | True | Null | Number | <a href="address">地址</a> 的 id

<!-- 結束分隔線/// -->


## 新增指定客戶聯絡地址

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
contact_id | true | NULL | Number | 客戶的 id
type | true | NULL | Number | 0:住家,1:郵寄,2:帳單,3:快遞,4:現居,5:其他
address | true | NULL | String | 地址
country_id | false | NULL | Number | 國家的id
state_id | false | NULL | Number | 城市的id
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

### Response

<a href="#address">`地址`</a>

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
contact_id | false | NULL | Number | 客戶的 id
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

Http status 為 204

```json
{}
```

### Http Request
`DELETE https://{API_DOMAIN}/api/v1/address/{address}`

### URL Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
address | true | NULL| Number | 地址的id