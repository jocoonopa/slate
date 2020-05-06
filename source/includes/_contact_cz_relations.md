# 客戶動態關聯表格

## 列出指定客戶關聯紀錄 ([客戶關聯紀錄] 即 [客戶動態關聯表格])

`GET https://{API_HOST}/api/v1/contact/{contact}/contact-cz-relation`

```shell
curl -X GET
    -H "Content-Type: application/json:Authorization: Bearer eyJhbGciOiJIUzI1NiI..." https://{API_HOST}/api/v1/contact/1/contact-cz-relation
```

假設目前有3個動態欄位，分別為

- id=1, type=1 (字串), name='體重'
- id=2, type=6 (單選), name='血型', options (選項)=[{"text": "A型", "value":"A"},{"text": "B型", "value":"B"},{"text": "O型", "value":"O"},{"text": "AB型", "value":"AB"}]
- id=3, type=7 (多選), name='檢查項目', options (選項)=[{"text": "X光", "value": 0}, {"text": "抽血", "value": 1}, {"text": "量身高", "value": 2}]

### Response

> 回傳 json 格式

<a href="#contactczrelation">客戶動態關聯表格</a>

```json

{
    "data": [
        {
            "id": 1,
            "relation_id": 1, // CzColCategory (動態關聯分類) 的 id
            "relation_name": "健康檢查",
            "information": [
                {
                    "id": 1,
                    "value": 70,
                    "col_id": 1,
                    "col_name": "體重"
                },
                {
                    "id": 2,
                    "value": "A",
                    "col_id": 2,
                    "col_name": "血型"
                },
                {
                    "id": 3,
                    "value": [0,1],
                    "col_id": 3,
                    "col_name": "檢查項目"
                }
            ],
            "created_at": "2019-11-24 22:58:21",
            "updated_at": "2019-11-24 22:58:21"
        }
    ],
    "links": {
        "first": "https://firstline.localhost/api/contact/2197607/contact-cz-relation?page=1",
        "last": "https://firstline.localhost/api/contact/2197607/contact-cz-relation?page=1",
        "prev": null,
        "next": null
    },
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 1,
        "path": "https://firstline.localhost/api/contact/2197607/contact-cz-relation",
        "per_page": 15,
        "to": 1,
        "total": 1
    }
}

```
### URL Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
contact | true | NULL | Number | <a href="#contact">客戶</a> 的 id

## 對指定客戶增加關聯紀錄 (即客戶動態關聯表格)

`POST https://{API_HOST}/api/v1/contact/{contact}/cz-col-category/{cz_col_category}/contact-cz-relation`

假設目前有3個動態欄位，分別為

- id=1, type=1 (字串), name='體重'
- id=2, type=6 (單選), name='血型', options (選項)=[{"text": "A型", "value":"A"},{"text": "B型", "value":"B"},{"text": "O型", "value":"O"},{"text": "AB型", "value":"AB"}]
- id=3, type=7 (多選), name='檢查項目', options (選項)=[{"text": "X光", "value": 0}, {"text": "抽血", "value": 1}, {"text": "量身高", "value": 2}]

```json

{
    "cz_cols": [
        {
            "id":1,
            "value":65
        },
        {
            "id":2,
            "value":"A"
        },
        {
            "id":3,
            "value":[1,2]
        }
    ]
}

```

### Response

<a href="#contactczrelation">客戶動態關聯表格</a>

<a href="#contactczrelationinformation">客戶動態關聯表格內容</a>

> 回傳 json 格式

```json

{
    "data": [
        {
            "id": 2,
            "relation_id": 1, // CzColCategory (動態關聯分類) 的 id
            "relation_name": "健康檢查",
            "information": [
                {
                    "id": 4,
                    "value": 65,
                    "col_id": 1,
                    "col_name": "體重"
                },
                {
                    "id": 5,
                    "value": "A",
                    "col_id": 2,
                    "col_name": "血型"
                },
                {
                    "id": 6,
                    "value": [1,2],
                    "col_id": 3,
                    "col_name": "檢查項目"
                }
            ],
            "created_at": "2019-11-25 22:58:21",
            "updated_at": "2019-11-25 22:58:21"
        }
    ],
    "links": {
        "first": "https://firstline.localhost/api/contact/2197607/contact-cz-relation?page=1",
        "last": "https://firstline.localhost/api/contact/2197607/contact-cz-relation?page=1",
        "prev": null,
        "next": null
    },
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 1,
        "path": "https://firstline.localhost/api/contact/2197607/contact-cz-relation",
        "per_page": 15,
        "to": 2,
        "total": 2
    }
}

```

### URL Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
contact | true | NULL | Number | <a href="#contact">客戶</a> 的 id
cz_col_category | true | NULL | Number | <a href="#czcolcategory">動態欄位分類</a> 的 id

### Form Data
Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
cz_cols | false | NULL | Array or Objects | 動態欄位，參數型態參考 **CzCol** 表格說明


**CzCol**

此欄位為包含以下格式之陣列

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
id | true | NULL | Number| 動態欄位的 id
value | true | NULL | String | 動態欄位的值

**範例**

- id=1, type=1 (字串), name='體重'
- id=2, type=6 (單選), name='血型', options (選項)=[{"text": "A型", "value":"A"},{"text": "B型", "value":"B"},{"text": "O型", "value":"O"},{"text": "AB型", "value":"AB"}]
- id=3, type=7 (多選), name='檢查項目', options (選項)=[{"text": "X光", "value": 0}, {"text": "抽血", "value": 1}, {"text": "量身高", "value": 2}]

參數範例如右: (注意不論是**單選**還是**多選**，都是丟 value，若誤丟 text 會導致前端顯示出現問題)

> Form Data cz_cols

```json
[
    {"id":1, "value":"65"}, // 1: 體重
    {"id":2, "value":"A"}, // 2: 血型
    {"id":3, "value": [1, 2]} // 3. 檢查項目: 抽血+量身高
]
```

## 對指定客戶更新關聯紀錄 (即客戶動態關聯表格)

`PUT https://{API_HOST}/api/v1/contact/{contact}/contact-cz-relation/{contact_cz_relation}`

> Form Data cz_cols

```json

{
    "cz_cols": [
        {
            "id": 1, // 體重欄位的 id
            "value": 55
        }
    ]
}


```

### Response

<a href="#czrelation">動態關聯表格</a>

> 回傳 json 格式

```json

{
    "data": {
        "id": 1,
        "relation_id": 1, // CzColCategory 的 id
        "relation_name": "寶寶資料",
        "information": [
            {
                "id": 4,
                "value": 55,
                "col_id": 1,
                "col_name": "體重"
            },
            {
                "id": 5,
                "value": "A",
                "col_id": 2,
                "col_name": "血型"
            },
            {
                "id": 6,
                "value": [1,2],
                "col_id": 3,
                "col_name": "檢查項目"
            }
        ]
    }
}

```

### URL Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
contact | true | NULL | Number | <a href="#contact">客戶</a> 的 id
contact_cz_relation | true | NULL | Number | <a href="#contactczrelation">客戶動態關聯表格</a> 的 id

### Form Data
Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
cz_cols | false | NULL | Array<Object> | 動態欄位，參數型態參考 **CzCol** 表格說明

**CzCol**

此欄位為包含以下格式之陣列

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
id | true | NULL | Number| 動態欄位的 id
value | true | NULL | String | 動態欄位的值

**範例**

- id=1, type=1 (字串), name='體重'
- id=2, type=6 (單選), name='血型', options (選項)=[{"text": "A型", "value":"A"},{"text": "B型", "value":"B"},{"text": "O型", "value":"O"},{"text": "AB型", "value":"AB"}]
- id=3, type=7 (多選), name='從事運動', options (選項)=[{"text": "籃球", "value": 0}, {"text": "跑步", "value": 1}, {"text": "游泳", "value": 2}]

參數範例如右: (注意不論是**單選**還是**多選**，都是丟 value，若誤丟 text 會導致前端顯示出現問題)

> Form Data cz_cols

```json
[
    {"id":1, "value":"70"}, // 1: 體重
    {"id":2, "value":"AB"}, // 2: 血型
    {"id":3, "value": [1, 2]} // 3. 運動: 跑步+游泳
]
```

## 對指定客戶刪除關聯紀錄 (即客戶動態關聯表格)

`DELETE https://{API_HOST}/api/v1/contact/{contact}/contact-cz-relation/{contact_cz_relation}`

```shell
curl -X DELETE
    -H "Content-Type: application/json:Authorization: Bearer eyJhbGciOiJIUzI1NiI..." https://{API_HOST}/api/v1/contact/1/contact-cz-relation/1
```


> 回應 204 http status

```json
```

### URL Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
contact | true | NULL | Number | <a href="#contact">客戶</a> 的 id
contact_cz_relation | true | NULL | Number | <a href="#contactczrelation">客戶動態關聯表格</a> 的 id


## 對指定客戶刪除所有指定分類下的關聯紀錄 (即客戶動態關聯表格)

`DELETE https://{API_HOST}/api/v1/contact/{contact}/cz-col-category/{cz_col_category}`

```shell
curl -X DELETE
    -H "Content-Type: application/json:Authorization: Bearer eyJhbGciOiJIUzI1NiI..." https://{API_HOST}/api/v1/contact/1/cz-col-category/1
```

> 回應 204 http status

```json
```

### URL Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
contact | true | NULL | Number | <a href="#contact">客戶</a> 的 id
cz_col_category | true | NULL | Number | <a href="#czcolcategory">動態欄位分類</a> 的 id


