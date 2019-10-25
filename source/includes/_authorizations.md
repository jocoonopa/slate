# 驗證

<aside class="notice">使用此 api 前，您必須登入後台，前往 [系統設定] > [員工]，找到欲使用 api 之帳號，點擊 [編輯資料]，點擊 [產生金鑰]。 (每一次帳號產生新的金鑰，會將之前屬於該帳號的金鑰作廢)</aside>

取得金鑰，可透過此金鑰執行各種對應帳號具備之系統權限之 api 操作

FirstLine 的 api 請求皆會取得後以下面兩種方式任一驗證 `金鑰` **(access token)**

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