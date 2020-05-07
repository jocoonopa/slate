# 電話號碼

## 搜尋電話號碼

搜尋電話號碼

```shell
curl -X GET
    -H "Content-Type: application/json"
    '{"type": 0, "number": "0928846763"}'
    https://{API_HOST}/api/v1/phone-number
```

> 回傳 json 格式

```json

{
    "data": [
        {
            "id": 245621,
            "type": 0,
            "extension": null,
            "number": "0928846763",
            "description": null,
            "profile_id": 1935008,
            "phone_contact": {
                "id": 480,
                "contact_id": 1935038,
                "phone_number_id": 245621,
                "is_visible": true
            }
        }
    ],
    "links": {
        "first": "https://firstline.localhost/api/phone-number?number=0928846763&contact_id=1935038&page=1",
        "last": "https://firstline.localhost/api/phone-number?number=0928846763&contact_id=1935038&page=1",
        "prev": null,
        "next": null
    },
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 1,
        "path": "https://firstline.localhost/api/phone-number",
        "per_page": 15,
        "to": 2,
        "total": 2
    }
}

```

### Http Request
`GET https://{API_DOMAIN}/api/v1/phone-number`

### Form Data

下表為可使用的過濾條件

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
contact_id | false | NULL | Number | 客戶的 **id** (可透過 `搜尋客戶` 取得客戶的 **id**)
type | false | NULL | Number | 0: 住家, 1: 公司, 2: 手機, 3: 傳真, 4: 其他
number | false | NULL | String | 電話號碼
extension | false | NULL | String | 分機號碼
description | false | NULL | String | 備註


### Response

Property | Type | Description
-------- | ---- | -----------
data | Array of objects | <a href="#phone-number">電話號碼陣列</a>
meta | Object | Pagination meta

<!-- ///開始分隔線 -->
## 取得電話號碼

```shell
curl -X GET
    -H "Content-Type: application/json"
    https://{API_HOST}/api/v1/245621
```

### Response

請參考<a href="#phone-number">電話號碼</a>的回應格式

Property | Type | Description
-------- | ---- | -----------
data | Object | <a href="#phone-number">電話號碼</a>

> 回傳 json 格式

```json

{
    "data": {
        "id": 245621,
        "type": 0,
        "extension": null,
        "number": "0928846763",
        "description": null,
        "profile_id": 1935008,
        "phone_contact": {
            "id": 480,
            "contact_id": 1935038,
            "phone_number_id": 245621,
            "is_visible": true
        }
    }
}

```

### Http Request
` https://{API_DOMAIN}/api/v1/phone-number/{phone_number}`

### URL Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
phone_number | true | NULL | Number | <<a href="#phone-number">電話號碼</a>的id

<!-- 結束分隔線/// -->


## 新增電話號碼

新增電話號碼

```shell
curl -X POST
    -H "Content-Type: application/json"
    '{"type": 0, "number": "23255780374507", "extension": "54 311", "description": "Up-sized mobile focusgroup"}'
    https://{API_HOST}/api/v1/phone-number
```

> 回傳 json 格式

```json
{
    "data": {
        "id": 1,
        "type": 0,
        "extension": "54 311",
        "number": "23255780374507",
        "description": "Up-sized mobile focusgroup",
        "profile_id": 1
    }
}
```

### Http Request
`POST https://{API_DOMAIN}/api/v1/phone-number`

### Form Data

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
contact_id | true | NULL | Number | 客戶的 **id** (可透過 `搜尋客戶` 取得客戶的 **id**)
type | true | NULL | Number | 0: 住家, 1: 公司, 2: 手機, 3: 傳真, 4: 其他
number | true | NULL | String | 電話號碼
extension | false | NULL | String | 分機號碼
description | false | NULL | String | 備註

## 更新電話號碼

更新電話號碼

```shell
curl -X PUT
    -H "Content-Type: application/json"
    '{"type": 2, "number": "0939888999", "extension": ""}'
    https://{API_HOST}/api/v1/phone-number/1
```

### Response

<a href="#phone-number">電話號碼</a>

> 回傳 json 格式

```json
{
    "data": {
        "id": 1,
        "type": 2,
        "extension": "",
        "number": "0939888999",
        "description": "Up-sized mobile focusgroup",
        "profile_id": 1
    }
}
```

### Http Request
`PUT https://{API_DOMAIN}/api/v1/phone-number/{phone_number}`

### URL Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
phone_number | true | NULL | Number | 電話號碼的id

### Form Data

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
contact_id | true | NULL | Number | 客戶的 id
type | false | NULL | Number | 0: 住家, 1: 公司, 2: 手機, 3: 傳真, 4: 其他
number | false | NULL | String | 電話號碼
extension | false | NULL | String | 分機號碼
description | false | NULL | String | 備註

## 刪除電話號碼

刪除電話號碼

```shell
curl -X DELETE
    -H "Content-Type: application/json"
    https://{API_HOST}/api/v1/phone-number/1
```

> 回傳 json 格式

Http status 為 204

```json
{}
```

### Http Request
`DELETE https://{API_DOMAIN}/api/v1/phone-number/{phone_number}`

### URL Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
phone_number | true | NULL | Number | 電話號碼的id