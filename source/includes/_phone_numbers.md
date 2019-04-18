# 電話號碼

透過 `搜尋客戶` 取得客戶的 **profile_id**，使用此數值進行 `電話號碼` 的 api 操作

## 新增電話號碼

新增電話號碼

```shell
curl -X POST
    -H "Content-Type: application/json"
    '{"type": 0, "number": "23255780374507", "extension": "54 311", "description": "Up-sized mobile focusgroup"}'
    https://{API_HOST}/api/v1/phone-number
```

### Response

Property | Type | Description
-------- | ---- | -----------
data | Array of objects | <a href="#phone-number">`電話號碼`陣列</a>
meta | Object | Pagination meta

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
profile_id | true | NULL | Number | 客戶的 **profile_id**
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

<a href="#phone-number">`電話號碼`</a>

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
profile_id | true | NULL | Number | 客戶的 **profile_id**
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

```json
{
    "data": {
        "status": 200
    }
}
```

### Http Request
`DELETE https://{API_DOMAIN}/api/v1/phone-number/{phone_number}`

### URL Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
phone_number | true | NULL | Number | 電話號碼的id