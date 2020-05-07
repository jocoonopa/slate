# 請求使用說明

`FIRST LINE API` 是使用 `RESTful` 風格設計的 API，使用到的 HTTP 請求方法共有四種:

- `GET` 方法，請求展示指定資源，即`瀏覽`
- `POST` 方法，用於提交指定資源的實體，即 `新增`
- `PUT` 方法，取代指定資源，即 `更新`
- `DELETE` 方法，刪除指定資源，即 `刪除`

## 請求示意圖

下方為使用 `POST` 請求新增一個客戶的 postman 示意圖:

### 請求主體
<img src="/images/post_example_1.png"></img>

這邊 postman 的 `Body` 我們選用 `raw` 直接撰寫 json，避免 postman 誤將數字包裹為字串，造成部分欄位驗證時會發生錯誤。


```json
{
    "membership_no":"R0000555",
    "identity_no":"A000000002",
    "gender":0,
    "first_name":"陳",
    "last_name":"大華",
    "birth_at":"1990-01-01"
}
```

### 表頭

<img src="/images/post_example_2.png"></img>

```json
{
    "Authorization":"YOUR_TOKEN",
    "Content-Type": "application/json",
    "Accept":"application/json",
}
```

表頭的部分有三個，下面逐一解釋:

#### Authorization

即 token，亦可使用 query string parameter 替代。

#### Content-Type

確保 server 端接收和回傳都會以 json 形式處理，因此這表頭是必要的。

#### Accept

為了確保 server 端接收和回傳都會以 json 形式處理，因此這表頭是必要的。

## 其他方法

`GET`，`DELETE` 依此類推，選用對應的 postman 請求方法即可。

`PUT` 請求方法較為特殊，請參考下方區塊之說明。

## PUT 請求示意圖

由於 **FIRST LINE API** 不支援直接使用 Http `PUT` 請求方法，
因此需要進行 `PUT` 請求時，請使用 `POST` 替代，
並且附帶參數 `_method="put"`。

下方為 postman 示意圖:

<img src="/images/put_example.png"></img>

```json
{
    "membership_no":"R0000567",
    "identity_no":"A000000001",
    "gender":0,
    "first_name":"王",
    "last_name":"小明",
    "birth_at":"1999-09-09"
}
```