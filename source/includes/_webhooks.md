# Webhook

請於 FirstLine 系統填寫您的回呼網址。

填寫完成後，客戶、地址、電話、電子郵件信箱有`新增`、`更新`、或是`刪除`的動作發生，
FirstLine 都會對您填寫的回呼網址進行呼叫，通知異動。

## 驗證

回呼網址建立後系統會自動產生一個 secret 值。

FirstLine 在呼叫回呼網址時，會在 Header `X_FIRSTLINE_SIGNATURE` 附帶簽章，
回呼網址收到 FirstLine 請求時，應該按照以下步驟進行驗證，確認請求確實來自 FirstLine。

**檢查流程**

1. 請將 secret 和 body 進行連接
2. 將連接後的字串進行 md5 加密
3. 用 base64 加密 2. 的字串
4. 比對 3. 的字串和簽章是否吻合

**範例**

假設 secret 為 'A-Cup-of-coffee'
body 為 '12345678'
檢查流程每個步驟的數值如下:

1. 'A-Cup-of-coffee12345678'
2. '10af1f0d0b8af9c0c476bc84a0ac39ce'
3. 'MTBhZjFmMGQwYjhhZjljMGM0NzZiYzg0YTBhYzM5Y2U='

## 異動通知格式

異動格式共有 `客戶異動`、`電話號碼異動`、`地址異動`、`電子信箱異動` 四種

其中 `action` 欄位有 `created`、`updated`、`deleted` 三種值，
對應 `新增`，`修改`，`刪除`

>  客戶異動通知 json 格式

```json

{
    "data": {
        "id": 1,
        "name": "Angelita D'Amore",
        "first_name": "Angelita",
        "last_name": "D'Amore",
        "membership_no": "8771639",
        "identity_no": "418099",
        "gender": 0,
        "birth_at": "1985-08-27",
        "profile_id": 1,
        "profile": {
            "id": 1,
            "phones": []
        },
        "cz_cols": [],
    },
    "model": "contact",
    "action": "created"
}

```

>  電話號碼異動通知 json 格式

```json

{
    "data": {
        "id": 1,
        "type": 2,
        "extension": "",
        "number": "0939888999",
        "description": "Up-sized mobile focusgroup",
        "profile_id": 1
    },
    "model": "phonenumber",
    "action": "created"
}

```

>  地址異動通知 json 格式

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
    },
    "model": "address",
    "action": "created"
}

```

>  電子信箱異動通知 json 格式

```json

{
    "data": {
        "id": 5,
        "address": "shyanne47@hotmail.com",
        "contact_id": 1,
        "draft": null,
        "name": "Mikayla Funk",
        "description": "Possimus optio molestiae perspiciatis distinctio. Vel incidunt ut unde. Laudantium eaque distinctio officia eum error odit.",
        "contact": {
            "id": 1,
            "membership_no": "8771639",
            "identity_no": "418099",
            "first_name": "Angelita",
            "last_name": "D'Amore",
            "gender": 0,
            "birth_at": "1985-08-27 00:00:00",
            "created_at": "2019-04-10 03:01:41",
            "updated_at": "2019-04-10 03:01:41",
            "profile_id": 1,
            "sponsor_id": null,
            "disturb_setting": null
        }
    },
    "model": "email_contact",
    "action": "created",
}

```