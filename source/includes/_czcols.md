# 動態欄位

鑑於客戶間商務邏輯的不同，勢必對於表單欄位的需求也會有差異，固定的表單欄位很難滿足所有客戶的需求，因此我們可以透過動態欄位讓客戶自行制定最適合自己使用的欄位。

## 動態欄位表單 (延伸欄位)

即從原本的表單額外添加的欄位，例如 `客戶` 的 `體重`，此種欄位屬於 **動態欄位表單**

## 動態關聯表格 (關聯紀錄)

即從原本的表單添加 "一對多" 的關聯，例如 `客戶` 的 `購買紀錄`，即屬於 **動態關聯表格**

## 目前套用在 [客戶] 以及 [工單]

目前 FirstLine 的 **客戶** 以及 **工單** 皆支援 **動態欄位表單** 和 **動態關聯表格**

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
`GET https://{API_DOMAIN}/api/v1/cz-col`

### Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
page | false | 1 | Number | 目前在第幾頁
per_page | false | 15 | Number | 每頁呈現多少筆
types | false | NULL | Number | 0: 客戶表單 1: 客戶關聯表格 2: 工單表單 3: 工單關聯表格
