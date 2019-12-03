# 動態欄位分類

## 所有動態欄位分類
`GET https://{API_HOST}/api/v1/cz-col-category`

**type** 0 表示 `客戶動態欄位`, 1 表示 `客戶動態關聯表格`, 2 表示 `工單動態欄位`, 3 表示 `工單動態關聯表格`


```shell
curl -X GET
    -H "Content-Type: application/json"
    https://{API_HOST}/api/v1/cz-col-category?xxxx
```

### Response

Property | Type | Description
-------- | ---- | -----------
data | Array of objects | <a href="#czcolcategory">`動態欄位分類` 陣列</a>
meta | Object | Pagination meta

> 回傳的 json 格式

```json
{
    "data": [
        {
            "id": 1,
            "name": "SF",
            "type": 0,
            "description": null,
            "cols": [
                {
                    "id": 1,
                    "name": "唯一碼",
                    "description": null,
                    "is_allowed_null": true,
                    "default": null,
                    "type": 1,
                    "options": null,
                    "category_id": 1,
                    "creater_id": null
                },
                {
                    "id": 2,
                    "name": "TESTCLICK__C",
                    "description": null,
                    "is_allowed_null": true,
                    "default": null,
                    "type": 2,
                    "options": null,
                    "category_id": 1,
                    "creater_id": null
                }
            ],
            "creater_id": null,
            "creater": null
        },
        {
            "id": 2,
            "name": "其他",
            "type": 0,
            "description": null,
            "cols": [
                {
                    "id": 3,
                    "name": "勿擾",
                    "description": null,
                    "is_allowed_null": true,
                    "default": null,
                    "type": 2,
                    "options": null,
                    "category_id": 2,
                    "creater_id": null
                },
                {
                    "id": 4,
                    "name": "最後活動日期",
                    "description": null,
                    "is_allowed_null": true,
                    "default": null,
                    "type": 1,
                    "options": null,
                    "category_id": 2,
                    "creater_id": null
                }
            ],
            "creater_id": null,
            "creater": null
        }
    ],
    "links": {
        "first": "https://firstline.localhost/api/cz-col-category?page=1",
        "last": "https://firstline.localhost/api/cz-col-category?page=1",
        "prev": null,
        "next": null
    },
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 1,
        "path": "https://firstline.localhost/api/cz-col-category",
        "per_page": 15,
        "to": 2,
        "total": 2
    }
}
```