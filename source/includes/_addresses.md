# 聯絡地址

## 搜尋聯絡地址

搜尋聯絡地址

```shell
curl -X GET
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