# 工單

## 搜尋工單

根據各種條件搜尋工單，詳細介紹請參考下表

除了工單本身資訊以外，也包含關聯的客戶，分類，子分類，聯絡記錄，處理人員，業主等資訊。

```shell
curl -X GET
    -H "Content-Type: application/json"
    "https://{API_HOST}/api/v1/ticket?per_page=15&page=1"
```

### Response

Property | Type | Description
-------- | ---- | -----------
data | Array of objects | 包含工單物件的陣列，工單物件的屬性說明請參考下方表格
meta | Object | Pagination meta

#### 工單物件

Property | Type | Description
-------- | ---- | -----------
id | Number | 工單的 id
subject | String | 工單的標題
content | String | 工單的內容
due_at | Datetime | 工單的到期時間
status | Number | 工單狀態 < 0: 待處理 1: 處理中 2: 已解決 3: 已關閉 >
status_memo | String |
priority | Number |
contact | Object |
contact_id | Number |
sub_category | Object |
sub_category_id | Number |
creater | Object |
handler_id | Number |
handler | Object |
interact_collections | Array of objects |
sponsor_id | Number |
sponsor | Object |
created_at | Datetime |
updated_at | Datetime |
termination_code_id | Number |
termination_code | Object |
category | Object |
category_id | Number |

> 回傳 json 格式

```json
{
    "data": [
        {
            "id": 67,
            "subject": "無法通話",
            "content": "無法通話\n＃處理完成",
            "due_at": null,
            "status": 0,
            "status_memo": null,
            "priority": 0,
            "contact": null,
            "contact_id": null,
            "sub_category": {
                "id": 26,
                "name": "建議",
                "description": null,
                "category": {
                    "id": 1,
                    "name": "電話功能",
                    "description": null
                },
                "category_id": 1
            },
            "sub_category_id": 26,
            "creater": {
                "id": 7,
                "name": "Tommy Hsu",
                "first_name": "Tommy",
                "last_name": "Hsu",
                "employee_no": "tommy",
                "photo_url": "/employee/7/photo",
                "identity_no": null,
                "job_title_id": -1,
                "department_id": -1,
                "extension_id": 8,
                "extension": {
                    "id": 8,
                    "type": 3,
                    "extension": "8005",
                    "description": null,
                    "media_cluster_id": null
                },
                "group_id": 2,
                "group": {
                    "id": 2,
                    "name": "測試Ｂ組",
                    "description": null,
                    "supervisor_id": 1
                },
                "cti_agent_account": "ag8005",
                "cti_agent": {
                    "id": 5,
                    "account": "ag8005",
                    "group_id": null
                },
                "created_at": "2019-04-12 12:51:34",
                "updated_at": "2019-04-15 15:25:46"
            },
            "handler_id": 7,
            "handler": {
                "id": 7,
                "name": "Tommy Hsu",
                "first_name": "Tommy",
                "last_name": "Hsu",
                "employee_no": "tommy",
                "photo_url": "/employee/7/photo",
                "identity_no": null,
                "job_title_id": -1,
                "department_id": -1,
                "extension_id": 8,
                "extension": {
                    "id": 8,
                    "type": 3,
                    "extension": "8005",
                    "description": null,
                    "media_cluster_id": null
                },
                "group_id": 2,
                "group": {
                    "id": 2,
                    "name": "測試Ｂ組",
                    "description": null,
                    "supervisor_id": 1
                },
                "cti_agent_account": "ag8005",
                "cti_agent": {
                    "id": 5,
                    "account": "ag8005",
                    "group_id": null
                },
                "created_at": "2019-04-12 12:51:34",
                "updated_at": "2019-04-15 15:25:46"
            },
            "interact_collections": [
                {
                    "id": 149,
                    "is_acw_completed": true,
                    "first_enter_queue_at": "2019-04-18 16:51:57",
                    "acw_at": "2019-04-18 16:54:57",
                    "last_finished_at": "2019-04-18 16:52:10",
                    "handler_id": 7,
                    "handler": {
                        "id": 7,
                        "name": "Tommy Hsu",
                        "first_name": "Tommy",
                        "last_name": "Hsu",
                        "employee_no": "tommy",
                        "photo_url": "/employee/7/photo",
                        "identity_no": null,
                        "job_title_id": -1,
                        "department_id": -1,
                        "extension_id": 8,
                        "extension": {
                            "id": 8,
                            "type": 3,
                            "extension": "8005",
                            "description": null,
                            "media_cluster_id": null
                        },
                        "group_id": 2,
                        "group": {
                            "id": 2,
                            "name": "測試Ｂ組",
                            "description": null,
                            "supervisor_id": 1
                        },
                        "cti_agent_account": "ag8005",
                        "cti_agent": {
                            "id": 5,
                            "account": "ag8005",
                            "group_id": null
                        },
                        "created_at": "2019-04-12 12:51:34",
                        "updated_at": "2019-04-15 15:25:46"
                    },
                    "contact_id": null,
                    "memo": null,
                    "bound_type": 1,
                    "sponsor_id": 1,
                    "campaign_queue_id": null,
                    "result_id": 2
                }
            ],
            "sponsor_id": 1,
            "sponsor": {
                "id": 1,
                "name": "default",
                "description": null,
                "is_immortal": true,
                "mail_channels": []
            },
            "campaign_queue": null,
            "campaign_queue_id": null,
            "created_at": "2019-04-16 14:45:12",
            "updated_at": "2019-04-18 16:54:16",
            "termination_code_id": null,
            "termination_code": null,
            "category": {
                "id": 1,
                "name": "電話功能",
                "description": null
            },
            "category_id": 1
        },
        {
            "id": 66,
            "subject": "工單 for TEST",
            "content": "內容內容內容內容內容內容內容內容111111",
            "due_at": null,
            "status": 2,
            "status_memo": null,
            "priority": 0,
            "contact": {
                "id": 2,
                "name": "小 閎",
                "first_name": "小",
                "last_name": "閎",
                "membership_no": null,
                "identity_no": "A123456789",
                "gender": 0,
                "birth_at": "1987-10-10",
                "profile_id": 3,
                "sponsor_id": 1,
                "disturb_setting": null
            },
            "contact_id": 2,
            "sub_category": {
                "id": 23,
                "name": "時效",
                "description": null,
                "category": {
                    "id": 2,
                    "name": "理賠相關",
                    "description": null
                },
                "category_id": 2
            },
            "sub_category_id": 23,
            "creater": {
                "id": 6,
                "name": "Karick Tung",
                "first_name": "Karick",
                "last_name": "Tung",
                "employee_no": "karick",
                "photo_url": null,
                "identity_no": null,
                "job_title_id": -1,
                "department_id": -1,
                "extension_id": 5,
                "extension": {
                    "id": 5,
                    "type": 3,
                    "extension": "8004",
                    "description": "井井",
                    "media_cluster_id": null
                },
                "group_id": 2,
                "group": {
                    "id": 2,
                    "name": "測試Ｂ組",
                    "description": null,
                    "supervisor_id": 1
                },
                "cti_agent_account": "ag8004",
                "cti_agent": {
                    "id": 4,
                    "account": "ag8004",
                    "group_id": null
                },
                "created_at": "2019-03-08 22:51:25",
                "updated_at": "2019-04-17 13:31:00"
            },
            "handler_id": null,
            "handler": null,
            "interact_collections": [
                {
                    "id": 108,
                    "is_acw_completed": true,
                    "first_enter_queue_at": "2019-04-16 14:18:24",
                    "acw_at": "2019-04-16 14:23:06",
                    "last_finished_at": "2019-04-16 14:18:49",
                    "handler_id": 6,
                    "handler": {
                        "id": 6,
                        "name": "Karick Tung",
                        "first_name": "Karick",
                        "last_name": "Tung",
                        "employee_no": "karick",
                        "photo_url": null,
                        "identity_no": null,
                        "job_title_id": -1,
                        "department_id": -1,
                        "extension_id": 5,
                        "extension": {
                            "id": 5,
                            "type": 3,
                            "extension": "8004",
                            "description": "井井",
                            "media_cluster_id": null
                        },
                        "group_id": 2,
                        "group": {
                            "id": 2,
                            "name": "測試Ｂ組",
                            "description": null,
                            "supervisor_id": 1
                        },
                        "cti_agent_account": "ag8004",
                        "cti_agent": {
                            "id": 4,
                            "account": "ag8004",
                            "group_id": null
                        },
                        "created_at": "2019-03-08 22:51:25",
                        "updated_at": "2019-04-17 13:31:00"
                    },
                    "contact_id": 2,
                    "memo": null,
                    "bound_type": 1,
                    "sponsor_id": 1,
                    "campaign_queue_id": null,
                    "result_id": 2
                },
                {
                    "id": 121,
                    "is_acw_completed": true,
                    "first_enter_queue_at": "2019-04-16 15:36:59",
                    "acw_at": "2019-04-16 15:54:48",
                    "last_finished_at": "2019-04-16 15:54:48",
                    "handler_id": 2,
                    "handler": {
                        "id": 2,
                        "name": "eason d",
                        "first_name": "eason",
                        "last_name": "d",
                        "employee_no": "eason",
                        "photo_url": "/employee/2/photo",
                        "identity_no": null,
                        "job_title_id": -1,
                        "department_id": -1,
                        "extension_id": 2,
                        "extension": {
                            "id": 2,
                            "type": 3,
                            "extension": "8002",
                            "description": null,
                            "media_cluster_id": null
                        },
                        "group_id": 2,
                        "group": {
                            "id": 2,
                            "name": "測試Ｂ組",
                            "description": null,
                            "supervisor_id": 1
                        },
                        "cti_agent_account": "ag8002",
                        "cti_agent": {
                            "id": 2,
                            "account": "ag8002",
                            "group_id": null
                        },
                        "created_at": "2018-11-09 13:21:17",
                        "updated_at": "2019-04-15 15:10:10"
                    },
                    "contact_id": 2,
                    "memo": "這次不知道幹嘛",
                    "bound_type": 1,
                    "sponsor_id": 1,
                    "campaign_queue_id": null,
                    "result_id": 2
                }
            ],
            "sponsor_id": 1,
            "sponsor": {
                "id": 1,
                "name": "default",
                "description": null,
                "is_immortal": true,
                "mail_channels": []
            },
            "campaign_queue": null,
            "campaign_queue_id": null,
            "created_at": "2019-04-16 14:22:13",
            "updated_at": "2019-04-17 12:39:53",
            "termination_code_id": 5,
            "termination_code": {
                "id": 5,
                "name": "確認可否處理",
                "description": null,
                "status": 0,
                "creater_id": 1
            },
            "category": {
                "id": 2,
                "name": "理賠相關",
                "description": null
            },
            "category_id": 2
        }
    ],
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 8,
        "per_page": "2",
        "to": 2,
        "total": 16
    }
}
```

### Http Request
`GET https://{API_DOMAIN}/api/v1/ticket`

### Query Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
page | false | 1 | Number | 目前在第幾頁
per_page | false | 15 | Number | 每頁呈現多少筆
search | false | NULL | String | 模糊搜尋工單標題和內容
contact_id | false | NULL | Number | 客戶 id
statuses | false | NULL | Array<Number> | 工單狀態 < 0: 待處理 1: 處理中 2: 已解決 3: 已關閉 >
due_at__start | false | NULL | Datetime | 截止日期時間(起始)
due_at__end | false | NULL | Datetime | 截止日期時間(結束)
created_at__start | false | NULL | Datetime | 建立日期時間(起始)
created_at__end | false | NULL | Datetime | 建立日期時間(結束)
sponsor_id | false | NULL | Number | 業主 id
termination_code_ids | false | NULL | Array<Number> | 狀態細項 id 陣列
handler_ids | false | NULL |  Array<Number> | 處理工單的員工之 id 陣列
creater_ids | false | NULL |  Array<Number> | 建立工單的員工之 id 陣列

## 新建工單

新建工單

```shell
curl -X POST
    '{"subject":"標題","content":"內容","status":2,"contact_id":1,"sub_category_id":1,"termination_code":5}'
    -H "Content-Type: application/json"
    "https://{API_HOST}/api/v1/ticket"
```

> 回傳 json 格式

```json

{
    "id": 1,
    "subject": "標題",
    "content": "內容",
    "due_at": null,
    "status": 2,
    "status_memo": null,
    "priority": 0,
    "contact": {
        "id": 1,
        "name": "艾 魁爾",
        "first_name": "艾",
        "last_name": "魁爾",
        "membership_no": null,
        "identity_no": "A123456789",
        "gender": 0,
        "birth_at": "1987-10-10",
        "profile_id": 3,
        "sponsor_id": 1,
        "disturb_setting": null
    },
    "contact_id": 1,
    "sub_category": {
        "id": 1,
        "name": "時效",
        "description": null,
        "category": {
            "id": 1,
            "name": "理賠相關",
            "description": null
        },
        "category_id": 1
    },
    "sub_category_id": 1,
    "handler_id": null,
    "handler": null,
    "sponsor_id": null,
    "sponsor": null,
    "campaign_queue": null,
    "campaign_queue_id": null,
    "created_at": "2019-04-16 14:22:13",
    "updated_at": "2019-04-17 12:39:53",
    "termination_code_id": 5,
    "termination_code": {
        "id": 5,
        "name": "確認可否處理",
        "description": null,
        "status": 0,
        "creater_id": null
    },
    "category": {
        "id": 1,
        "name": "理賠相關",
        "description": null
    },
    "category_id": 1
}

```

### Http Request
`POST https://{API_DOMAIN}/api/v1/ticket`

### Form Data

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
sponsor_id | false | NULL | Number | 業主的 id
handler_id | false | NULL | Number | 處理員工的 id
termination_code_id | false | NULL | Number | 狀態細項的 id
subject | true | NULL | String | 工單標題
content | true | NULL | String | 工單內容
due_at | false | NULL | Datetime | 工單截止時間
priority | false | 0(最低) | Number | 工單優先等級
status | false | 0(待處理) | Number | 工單處理狀態
status_memo | false | NULL | String | 工單狀態備註
sub_category_id | false | NULL | Number | 子分類
contact_id | false | NULL | Number | 客戶的id

## 檢視工單

檢視工單

```shell
curl -X GET
    -H "Content-Type: application/json"
    "https://{API_HOST}/api/v1/ticket/1"
```

> 回傳 json 格式

```json

{
    "id": 1,
    "subject": "標題",
    "content": "內容",
    "due_at": null,
    "status": 2,
    "status_memo": null,
    "priority": 0,
    "contact": {
        "id": 1,
        "name": "艾 魁爾",
        "first_name": "艾",
        "last_name": "魁爾",
        "membership_no": null,
        "identity_no": "A123456789",
        "gender": 0,
        "birth_at": "1987-10-10",
        "profile_id": 3,
        "sponsor_id": 1,
        "disturb_setting": null
    },
    "contact_id": 1,
    "sub_category": {
        "id": 1,
        "name": "時效",
        "description": null,
        "category": {
            "id": 1,
            "name": "理賠相關",
            "description": null
        },
        "category_id": 1
    },
    "sub_category_id": 1,
    "handler_id": null,
    "handler": null,
    "sponsor_id": null,
    "sponsor": null,
    "campaign_queue": null,
    "campaign_queue_id": null,
    "created_at": "2019-04-16 14:22:13",
    "updated_at": "2019-04-17 12:39:53",
    "termination_code_id": 5,
    "termination_code": {
        "id": 5,
        "name": "確認可否處理",
        "description": null,
        "status": 0,
        "creater_id": null
    },
    "category": {
        "id": 1,
        "name": "理賠相關",
        "description": null
    },
    "category_id": 1
}

```

### Http Request
`GET https://{API_DOMAIN}/api/v1/ticket/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | 工單 id

## 更改工單

更改工單

```shell
curl -X PUT
    -H "Content-Type: application/json"
    '{"subject":"修改後的標題"}'
    "https://{API_HOST}/api/v1/ticket/1"
```

> 回傳 json 格式

```json

{
    "id": 1,
    "subject": "修改後的標題",
    "content": "內容",
    "due_at": null,
    "status": 2,
    "status_memo": null,
    "priority": 0,
    "contact": {
        "id": 1,
        "name": "艾 魁爾",
        "first_name": "艾",
        "last_name": "魁爾",
        "membership_no": null,
        "identity_no": "A123456789",
        "gender": 0,
        "birth_at": "1987-10-10",
        "profile_id": 3,
        "sponsor_id": 1,
        "disturb_setting": null
    },
    "contact_id": 1,
    "sub_category": {
        "id": 1,
        "name": "時效",
        "description": null,
        "category": {
            "id": 1,
            "name": "理賠相關",
            "description": null
        },
        "category_id": 1
    },
    "sub_category_id": 1,
    "handler_id": null,
    "handler": null,
    "sponsor_id": null,
    "sponsor": null,
    "campaign_queue": null,
    "campaign_queue_id": null,
    "created_at": "2019-04-16 14:22:13",
    "updated_at": "2019-04-17 12:39:53",
    "termination_code_id": 5,
    "termination_code": {
        "id": 5,
        "name": "確認可否處理",
        "description": null,
        "status": 0,
        "creater_id": null
    },
    "category": {
        "id": 1,
        "name": "理賠相關",
        "description": null
    },
    "category_id": 1
}

```

### Http Request
`PUT https://{API_DOMAIN}/api/v1/ticket/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | 工單 id

### Form Data

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
sponsor_id | false | NULL | Number | 業主的 id
handler_id | false | NULL | Number | 處理員工的 id
termination_code_id | false | NULL | Number | 狀態細項的 id
subject | false | NULL | String | 工單標題
content | false | NULL | String | 工單內容
due_at | false | NULL | Datetime | 工單截止時間
priority | false | 0(最低) | Number | 工單優先等級
status | false | 0(待處理) | Number | 工單處理狀態
status_memo | false | NULL | String | 工單狀態備註
sub_category_id | false | NULL | Number | 子分類
contact_id | false | NULL | Number | 客戶的id

## 刪除工單

刪除工單

```shell
curl -X DELETE
    -H "Content-Type: application/json"
    "https://{API_HOST}/api/v1/ticket/1"
```

> 回傳 json 格式

```json

{
    "data": {
        "status": 200,
    }
}

```

### Http Request
`DELETE https://{API_DOMAIN}/api/v1/ticket/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | 工單 id

## 查詢員工

查詢員工

```shell
curl -X GET
    -H "Content-Type: application/json"
    "https://{API_HOST}/api/v1/employee"
```

> json

```json
{
    "data": [
        {
            "id": 17,
            "name": "AG 8018",
            "first_name": "AG",
            "last_name": "8018",
            "employee_no": "ag8018",
            "photo_url": null,
            "identity_no": null,
            "job_title_id": 21,
            "job_title": {
                "id": 21,
                "abbrev": null,
                "name": "銷售專員",
                "description": null
            },
            "department_id": -1,
            "department": null,
            "extension_id": -1,
            "extension": null,
            "profile": {
                "id": 29,
                "phones": []
            },
            "is_active": true,
            "role": "",
            "email": null,
            "group_id": 3,
            "group": {
                "id": 3,
                "name": "SUN1",
                "description": null,
                "supervisor_id": 9
            },
            "is_immortal": false,
            "cti_agent_account": null,
            "cti_agent": null,
            "created_at": "2019-04-18 06:13:43",
            "updated_at": "2019-04-18 06:16:51"
        },
        {
            "id": 16,
            "name": "AG 8017",
            "first_name": "AG",
            "last_name": "8017",
            "employee_no": "ag8017",
            "photo_url": null,
            "identity_no": null,
            "job_title_id": 21,
            "job_title": {
                "id": 21,
                "abbrev": null,
                "name": "銷售專員",
                "description": null
            },
            "department_id": -1,
            "department": null,
            "extension_id": -1,
            "extension": null,
            "profile": {
                "id": 30,
                "phones": []
            },
            "is_active": true,
            "role": "",
            "email": null,
            "group_id": 3,
            "group": {
                "id": 3,
                "name": "SUN1",
                "description": null,
                "supervisor_id": 9
            },
            "is_immortal": false,
            "cti_agent_account": null,
            "cti_agent": null,
            "created_at": "2019-04-18 06:13:24",
            "updated_at": "2019-04-18 06:17:02"
        },
        {
            "id": 15,
            "name": "AG 8016",
            "first_name": "AG",
            "last_name": "8016",
            "employee_no": "ag8016",
            "photo_url": null,
            "identity_no": null,
            "job_title_id": 21,
            "job_title": {
                "id": 21,
                "abbrev": null,
                "name": "銷售專員",
                "description": null
            },
            "department_id": -1,
            "department": null,
            "extension_id": -1,
            "extension": null,
            "profile": {
                "id": 31,
                "phones": []
            },
            "is_active": true,
            "role": "",
            "email": null,
            "group_id": 3,
            "group": {
                "id": 3,
                "name": "SUN1",
                "description": null,
                "supervisor_id": 9
            },
            "is_immortal": false,
            "cti_agent_account": null,
            "cti_agent": null,
            "created_at": "2019-04-18 06:13:02",
            "updated_at": "2019-04-18 06:17:13"
        }
    ],
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 6,
        "per_page": "3",
        "to": 3,
        "total": 17
    }
}
```

### Query Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
page | false | 1 | Number | 目前在第幾頁
per_page | false | 15 | Number | 每頁呈現多少筆
search | false | NULL | String | 模糊搜尋員工姓名，身分證，員工編號

### Http Request
`GET https://{API_DOMAIN}/api/v1/employee`

## 查詢業主

查詢業主

```shell
curl -X GET
    -H "Content-Type: application/json"
    "https://{API_HOST}/api/v1/sponsor"
```

> json

```json
{
    "data": [
        {
            "id": 1,
            "name": "default",
            "description": null,
            "is_immortal": true,
            "mail_channels": []
        }
    ],
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 1,
        "per_page": 15,
        "to": 1,
        "total": 1
    }
}

```

### Http Request
`GET https://{API_DOMAIN}/api/v1/sponsor`

## 查詢工單狀態細項

查詢工單狀態細項

```shell
curl -X GET
    -H "Content-Type: application/json"
    "https://{API_HOST}/api/v1/ticket-termination-code"
```

### Response

Property | Type | Description
-------- | ---- | -----------
id | Number | 狀態細項 id
name | String | 狀態細項名稱
description | String | 狀態細項敘述
status | Number | 對應的工單狀態 <0: 待處理 1: 處理中 2: 已完成 3: 已關閉>
creater_id | Number | 該狀態細項的建立員工之id

> json 回傳格式

```json
{
    "data": [
        {
            "id": 1,
            "name": "尚未知曉",
            "description": null,
            "status": 0,
            "creater_id": 1
        },
        {
            "id": 2,
            "name": "已知曉",
            "description": null,
            "status": 0,
            "creater_id": 1
        },
        {
            "id": 3,
            "name": "討論中",
            "description": null,
            "status": 1,
            "creater_id": 1
        },
        {
            "id": 4,
            "name": "正在寫",
            "description": null,
            "status": 1,
            "creater_id": 1
        },
        {
            "id": 5,
            "name": "確認可否處理",
            "description": null,
            "status": 0,
            "creater_id": 1
        },
        {
            "id": 6,
            "name": "放棄",
            "description": null,
            "status": 3,
            "creater_id": 1
        },
        {
            "id": 7,
            "name": "還有些東西未來處理",
            "description": null,
            "status": 2,
            "creater_id": 1
        },
        {
            "id": 8,
            "name": "搞定",
            "description": null,
            "status": 2,
            "creater_id": 1
        }
    ],
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 1,
        "per_page": 15,
        "to": 8,
        "total": 8
    }
}
```

### Query Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
page | false | 1 | Number | 目前在第幾頁
per_page | false | 15 | Number | 每頁呈現多少筆
search | false | NULL | String | 模糊搜尋員工姓名，身分證，員工編號

### Http Request
`GET https://{API_DOMAIN}/api/v1/ticket-termination-code`

## 查詢主分類

查詢主分類

```shell
curl -X GET
    -H "Content-Type: application/json"
    "https://{API_HOST}/api/v1/category"
```

> json 回傳格式

```json
{
    "data": [
        {
            "id": 1,
            "name": "電話功能",
            "description": null,
            "children": [
                {
                    "id": 26,
                    "name": "建議",
                    "description": null
                }
            ]
        },
        {
            "id": 2,
            "name": "理賠相關",
            "description": null,
            "children": [
                {
                    "id": 23,
                    "name": "時效",
                    "description": null
                }
            ]
        },
        {
            "id": 3,
            "name": "PA 相關",
            "description": null,
            "children": [
                {
                    "id": 21,
                    "name": "保費計算方式",
                    "description": null
                },
                {
                    "id": 22,
                    "name": "最新優惠",
                    "description": null
                }
            ]
        },
        {
            "id": 4,
            "name": "配送",
            "description": null,
            "children": [
                {
                    "id": 25,
                    "name": "地區",
                    "description": null
                }
            ]
        },
        {
            "id": 5,
            "name": "電子郵件",
            "description": "電子郵件相關的功能",
            "children": [
                {
                    "id": 27,
                    "name": "後端程式BUG",
                    "description": "待修正處理的 BUG"
                }
            ]
        }
    ],
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 1,
        "per_page": 15,
        "to": 5,
        "total": 5
    }
}

```

### Query Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
page | false | 1 | Number | 目前在第幾頁
per_page | false | 15 | Number | 每頁呈現多少筆

### Http Request
`GET https://{API_DOMAIN}/api/v1/category`

## 查詢子分類

查詢子分類

```shell
curl -X GET
    -H "Content-Type: application/json"
    "https://{API_HOST}/api/v1/subcategory"
```

> json 回傳格式

```json

{
    "data": [
        {
            "id": 21,
            "name": "保費計算方式",
            "description": null,
            "category": {
                "id": 3,
                "name": "PA 相關",
                "description": null
            },
            "category_id": 3
        },
        {
            "id": 22,
            "name": "最新優惠",
            "description": null,
            "category": {
                "id": 3,
                "name": "PA 相關",
                "description": null
            },
            "category_id": 3
        },
        {
            "id": 23,
            "name": "時效",
            "description": null,
            "category": {
                "id": 2,
                "name": "理賠相關",
                "description": null
            },
            "category_id": 2
        },
        {
            "id": 24,
            "name": "測試子分類",
            "description": "測試子分類",
            "category": null,
            "category_id": null
        },
        {
            "id": 25,
            "name": "地區",
            "description": null,
            "category": {
                "id": 4,
                "name": "配送",
                "description": null
            },
            "category_id": 4
        },
        {
            "id": 26,
            "name": "建議",
            "description": null,
            "category": {
                "id": 1,
                "name": "電話功能",
                "description": null
            },
            "category_id": 1
        },
        {
            "id": 27,
            "name": "後端程式BUG",
            "description": "待修正處理的 BUG",
            "category": {
                "id": 5,
                "name": "電子郵件",
                "description": "電子郵件相關的功能"
            },
            "category_id": 5
        }
    ],
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 1,
        "per_page": 15,
        "to": 7,
        "total": 7
    }
}

```

### Query Parameters

Parameter | Required | Default | Type | Description
--------- | -------- | ------- | ---- | -----------
page | false | 1 | Number | 目前在第幾頁
per_page | false | 15 | Number | 每頁呈現多少筆
category_id | false | Number | 所屬的主分類id

### Http Request
`GET https://{API_DOMAIN}/api/v1/subcategory`







