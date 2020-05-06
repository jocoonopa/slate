# 驗證

<aside class="notice">使用此 api 前，您必須登入後台，前往 [系統設定] > [員工]，找到欲使用 api 之帳號，點擊 [編輯資料]，點擊 [產生金鑰]。 (每一次帳號產生新的金鑰，會將之前屬於該帳號的金鑰作廢)</aside>

取得金鑰，可透過此金鑰執行各種對應帳號具備之系統權限之 api 操作

FIRST LINE 的 api 請求皆會取得後以下面兩種方式任一驗證 `金鑰` **(access token)**

**Authorization header**
`Authorization: Bearer eyJhbGciOiJIUzI1NiI...`

**Query string parameter**
`https://{API_HOST}/api/v1/some-what?token=eyJhbGciOiJIUzI1NiI...`

### Http Request
`POST https://{API_HOST}/api/v1/auth`

### Post Parameters

Parameter | Required | Default | Description
--------- | -------- | ------- | -----------
name | true | NULL | 使用者帳號
password | true | NULL | 使用者密碼
ttl | false | 60 | 金鑰過期時間，單位為分鐘，預設 60 分鐘過期


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

### Http Request
`PUT https://{API_HOST}/api/v1/auth`

## 註銷權杖

```shell
curl -X POST
    -H "Accept: application/json"
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
