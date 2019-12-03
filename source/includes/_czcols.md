# 動態欄位

鑑於客戶間商務邏輯的不同，勢必對於表單欄位的需求也會有差異，固定的表單欄位很難滿足所有客戶的需求，因此我們可以透過動態欄位讓客戶自行制定最適合自己使用的欄位。

## 類型

動態欄位共有整數，字串，布林值，日期，時間，日期時間，單選，多選等 8 種類別，依序對應數字
0,1,2,3,4,5,6,7

其中 `6(單選)` 以及 `7(多選)` 存在 options 欄位，此欄位以 json 格式紀錄選項，下面以血型為例

`[{"text":"A型", "value": "A"},{"text":"B型", "value": "B"},{"text":"AB型", "value": "AB"},{"text":"O型", "value": "O"}]`

`動態表單`或是`動態表格`最後儲存的值為 **value**

## 動態表單欄位 (延伸欄位)

即從原本的表單額外添加的欄位，例如 `客戶` 的 `體重`，此種欄位屬於 **動態表單欄位**

## 動態關聯表格 (關聯紀錄)

即從原本的表單添加 "一對多" 的關聯，例如 `客戶` 的 `購買紀錄`，即屬於 **動態關聯表格**

## 目前套用在 [客戶] 以及 [工單]

目前 FirstLine 的 **客戶** 以及 **工單** 皆支援 **動態欄位表單** 和 **動態關聯表格**

## 目前系統所有的動態欄位

目前系統所有的動態欄位，可根據 `category_id`, `types` 進行過濾篩選

```shell
curl -X GET
    -H "Content-Type: application/json:Authorization: Bearer eyJhbGciOiJIUzI1NiI..." https://{API_HOST}/api/v1/cz-col
```

### Response

Property | Type | Description
-------- | ---- | -----------
data | Array of objects | <a href="#czcol">`動態欄位`陣列</a>
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
category_id | false | NULL | Number | <a href="#czcolcategory">`動態欄位分類`</a> 的 id
types | false | NULL | Number | 0: 客戶動態表單欄位 1: 客戶動態關聯表格 2: 工單動態表單欄位 3: 工單動態關聯表格
