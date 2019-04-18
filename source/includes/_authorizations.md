# 驗證

<aside class="notice">使用此 api 前，您必須先行索取 api 專用帳號密碼以及註冊 IP 白名單</aside>

FirstLine 的 api 請求皆會取得後以下面兩種方式任一驗證 `權杖` **(access token)**

**Authorization header**
`Authorization: Bearer eyJhbGciOiJIUzI1NiI...`

**Query string parameter**
`https://{API_HOST}/api/v1/some-what?token=eyJhbGciOiJIUzI1NiI...`

因此在訪問 api 之前一定要先取得 `權杖`

## 取得權杖

```shell
curl -X POST
    -H "Content-Type: application/json" -d '{"name":"your_username","password":"your_password"}'
    https://{API_HOST}/api/v1/auth
```

### Response

Property | Type | Description
-------- | ---- | -----------
access_token | String | 權杖
token_type | String | 類型，可忽視
expires_in | Number | 過期時間

> 回傳 json 格式

```json
{
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vYnNvLmxvY2FsaG9zdDo4MDAwL2FwaS92MS9hdXRoIiwiaWF0IjoxNTU0ODMxOTkyLCJleHAiOjE1NTUwNDc5OTIsIm5iZiI6MTU1NDgzMTk5MiwianRpIjoiTmlPOWhHanpDSng5SEpBSyIsInN1YiI6MSwicHJ2IjoiODdlMGFmMWVmOWZkMTU4MTJmZGVjOTcxNTNhMTRlMGIwNDc1NDZhYSIsImVtYWlsIjoib3JlaWxseS5zYWJyeW5hQGV4YW1wbGUub3JnIn0.3a88Iik_FIV9mUioDFVlm9n6U40HrlcEGNwawp8xWgc",
    "token_type": "bearer",
    "expires_in": 216000, // 216000 毫秒後過期
}
```

取得權杖，可透過此權杖執行各種對應帳號具備之系統權限之 api 操作

### Http Request
`POST https://{API_HOST}/api/v1/auth`

### Post Parameters

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
name | true | NULL | 使用者帳號
password | true | NULL | 使用者密碼

## 刷新權杖

```shell
curl -X PUT
    -H "Content-Type: application/json:Authorization: Bearer eyJhbGciOiJIUzI1NiI..." https://{API_HOST}/api/v1/auth
```

> 回傳 json 格式

```json
{
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vYnNvLmxvY2FsaG9zdDo4MDAwL2FwaS92MS9hdXRoIiwiaWF0IjoxNTU0ODMxOTkyLCJleHAiOjE1NTUwNDgwNzksIm5iZiI6MTU1NDgzMjA3OSwianRpIjoiNzV2elE2cFVid2haTGU4UyIsInN1YiI6MSwicHJ2IjoiODdlMGFmMWVmOWZkMTU4MTJmZGVjOTcxNTNhMTRlMGIwNDc1NDZhYSIsImVtYWlsIjoib3JlaWxseS5zYWJyeW5hQGV4YW1wbGUub3JnIn0.-sQWox84CRUEtgTxKguPzDXe8kcZW4nArRDiveeiNt8",
    "token_type": "bearer",
    "expires_in": 216000
}
```

刷新權杖

### Http Request
`PUT https://{API_HOST}/api/v1/auth`

## 註銷權杖

```shell
curl -X POST
    -H "Content-Type: application/json:Authorization: Bearer eyJhbGciOiJIUzI1NiI..." https://{API_HOST}/api/v1/auth/logout
```

> 回傳 json 格式

```json
{
    "message": "Successfully logged out"
}
```

註銷當前使用之權杖，相當於登出此使用者

### Http Request
`POST https://{API_HOST}/api/v1/auth/logout`


## 取得目前使用者資訊

回傳當前權杖對應之使用者資訊

```shell
curl -X GET
    -H "Content-Type: application/json:Authorization: Bearer eyJhbGciOiJIUzI1NiI..." https://{API_HOST}/api/v1/auth/me
```

### Http Request
`GET https://{API_HOST}/api/v1/auth/me`

> 回傳 json 格式

```json
{
    "id": 1,
    "name": "api-user",
    "email": "oreilly.sabryna@example.org",
    "created_at": "2019-04-10 00:11:22",
    "updated_at": "2019-04-10 01:09:13",
    "login_at": "2019-04-10 01:09:13",
    "is_active": true,
    "instance_id": 1,
    "instance_type": "App\\Employee",
    "is_immortal": false,
    "leave_at": "2019-02-10 01:04:36",
    "bi_token": null
}
```