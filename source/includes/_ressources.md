# 回應物件格式

## 地址 (Address)

Property | Type | Description
-------- | ---- | -----------
id | Number | 地址 id
type | Number| 地址類型 <ul><li>0: 住家</li><li>1: 郵寄</li><li>2: 帳單</li><li>3: 寄送</li><li>4: 現居</li><li>5: 其他</li></ul>
address | String | 地址內容
profile_id | Number | **客戶個資物件 的 id**
state | Object | <a href="#city">`縣市`</a>
state_id | Number | 縣市的id
country | Object | <a href="#country">`國家`</a>
country_id | Number | 國家的id
city | Object | <a href="#city">`區`</a>
city_id | Number | 區的id
description | String | 地址描述說明

## 國家 (Country)

Property | Type | Description
-------- | ---- | -----------
id | Number | id
name | String | 名稱

## 城市 (State)

Property | Type | Description
-------- | ---- | -----------
id | Number | id
name | String | 名稱

## 區 (City)

Property | Type | Description
-------- | ---- | -----------
id | Number | id
name | String | 名稱

## 客戶 (Contact)

Property | Type | Description
-------- | ---- | -----------
id | Number | 客戶的 id
name | String | 全名
first_name | String | 姓氏
last_namt | String | 名字
membership_no | String | 會員編號
identity_no | String | 身分證字號
gender | Number | 性別
birth_at | Datetime | 生日
profile_id | Number | 客戶個資物件 的 id
profile | Object | <a href="#profile">`客戶個資物件`</a>
sponsor | Object | <a href="#sponsor">`業主`</a>
sponsor_id | Number | 業主id
campaign_queues | Array of objects | **此欄位請忽略，尚未具備正式功能**
fbs | Array of objects | **此欄位請忽略，尚未具備正式功能**
lines | Array of objects | **此欄位請忽略，尚未具備正式功能**
cz_cols | Array of objects | <a href="#cz-col">`客戶的動態欄位`陣列</a>
tags | Array of objects | <a href="#contact-tag">`標籤`陣列</a>
disturb_setting | Object | <a href="#disturb-setting">`勿擾`</a>

## 客戶個資物件 (Profile)

Property | Type | Description
-------- | ---- | -----------
id | Number | 客戶個資物件的 id，會被用來撈取住址，電話
phones | Array of object | <a href="#phone-number">`電話`陣列</a>

## 動態欄位 (CzCol)

Property | Type | Description
-------- | ---- | -----------
id | Number | 動態欄位的 id
name | String | 動態欄位的名稱
description | String | 動態欄位的描述說明
is_allowed_null | Boolean | 是否允許空值
default | Object | 此動態欄位的預設值
type | Number | 動態欄位的類型 <ul><li>0: 數字</li><li>1: 字串</li><li>2: 布林值</li><li>3: 日期</li><li>4: 時間</li><li>5: 日期時間</li><li>6: 單選</li><li>7: 多選</li></ul>
category_id | Number | 主分類的 id
category | Object | <a href="#category">`主分類`</a>
creater_id | Number | 建立此動態欄位的員工id
creater | Object | 建立此動態欄位的 <a href="#employee">`員工`</a>

## 動態欄位分類 (CzColCategory)

Property | Type | Description
-------- | ---- | -----------
id | Number | 動態欄位分類 的 id
name | String | 動態欄位分類名稱
type | Number | 動態欄位分類類型 {0: 客戶動態關聯表單 1: 客戶動態關聯表格 2: 工單動態關聯表單 3: 工單動態關聯表格}
description | String | 動態欄位分類描述
cols | Array of objects | <a href="#czcol">`動態欄位`</a>

## 客戶動態關聯表格 (ContactCzRelation)

Property | Type | Description
-------- | ---- | -----------
id | Number | `客戶動態關聯表格` id
relation_id | Number | <a href="#czcolcategory">`動態欄位分類`</a> 的 id
relation_name | String | <a href="#czcolcategory">`動態欄位分類`</a> 的名稱
information | Array of Objects | <a href="#contactczrelationinformation">`客戶動態關聯表格內容`</a> 的陣列

## 客戶動態關聯表格內容 (ContactCzRelationInformation)

Property | Type | Description
-------- | ---- | -----------
id | Number | `客戶動態關聯表格內容`的 id
value | String | `客戶動態關聯表格內容`的值
col_id | Number | <a href="#czcol">`動態欄位` </a>的 id
col_name | String | <a href="#czcol">`動態欄位` </a>的名稱

## 客戶標籤 (Contact Tag)

Property | Type | Description
-------- | ---- | -----------
id | Number | id
name | String | 名稱
description | String | 說明

## 客戶勿擾設定 (Disturb Setting)

Property | Type | Description
-------- | ---- | -----------
id | Number | id
type | Array of string | 勿擾設定的類型，包含電話，Fb，Line
no_disturb_start_at | Time | 勿擾設定起始時間
no_disturb_end_at | Time | 勿擾設定結束時間
reason | String | 勿擾理由

## 員工 (Employee)

Property | Type | Description
-------- | ---- | -----------
id | Number | 員工的id
name | String | 姓名
first_name | String | 姓氏
last_name | String | 名字
employee_no | String | 員工編號
photo_url | String | 照片路徑
identity_no | String | 身分證字號
job_title_id | Number | 職稱 id
job_title | Object | <a href="#job-title">`職稱`</a>
department_id | Number | 部門 id
department | Object | <a href="#department">`部門`</a>
extension_id | Number | 分機 id
extension | Object | <a href="#extension">`分機`</a>
profile | Object | <a href="#profile">`客戶個資`</a>
is_active | Boolean | 是否啟用
role | String | 權限
email | String | 信箱地址
group_id | Number | 員工群組 id
group | Object | <a href="#employee-group">`員工群組`</a>
is_immortal | Boolean | 不可被修改
cti_agent_account | String | cti 帳號名稱
cti_agent | Object | <a href="#cti-agent">`電話專員`</a>
created_at | Datetime | 初始建立時間
updated_at | Datetime | 最後更新時間

## 職稱 (Job Title)

Property | Type | Description
-------- | ---- | -----------
id | Number | id
abbrev | String | 簡稱
name | String | 名稱
description | String | 說明

## 分機 (Extension)

Property | Type | Description
-------- | ---- | -----------
id | Number | id
type | Number | 類型 <0: 分機, 1: ACD, 2: IVR, 3: WEBRTC>
extension | String | 分機號碼
description | String | 說明
media_cluster_id | Number | **待補**
media_cluster | Object | **待補**
employee_id | Number |  <a href="#employee">`員工`</a>
employee | Object | 員工 id

## 電話專員 (CtiAgent)

Property | Type | Description
-------- | ---- | -----------
id | Number | id
account | String | 帳號
employee | Object | <a href="#employee">`員工`</a>
group_id | Number | 員工群組 id
group | Object | <a href="#employee-group">`員工群組`</a>

## 員工群組 (Employee Group)

Property | Type | Description
-------- | ---- | -----------
id | Number | 員工的id
name | String | 姓名
description | String | 說明
supervisor_id | Number | 督導的 id
supervisor | Object | 督導，格式為<a href="#employee">`員工`</a>
members | Array of object | 群組成員，格式為<a href="#employee">`員工`</a>的陣列

## 部門 (Deaprtment)

Property | Type | Description
-------- | ---- | -----------
id | Number | id
name | String | 名稱
abbrev | String | 簡稱
number | Number | 代號
description | String | 說明

## 電話 (Phone Number)

Property | Type | Description
-------- | ---- | -----------
id | Number | id
type | Number | 0: 住家, 1: 公司, 2: 手機, 3: 傳真, 4: 其他
extension | String | 分機
number | String | 號碼
description | String | 說明

## 工單 (Ticket)

Property | Type | Description
-------- | ---- | -----------
id | Number | id
subject | String | 標題
content | String | 內容
due_at | Datetime | 截止時間
status | Number | 工單狀態 < 0: 待處理 1: 處理中 2: 已解決 3: 已關閉 >
status_memo | String | 狀態備註
priority | Number | 優先順序
termination_code_id | Number | 狀態細項 id
termination_code | Object | <a href="#ticket-termination-code">狀態細項</a>
contact | Object | <a href="#contact">`客戶`</a>
contact_id | Number | 客戶 id
sub_category | Object | <a href="#sub-category">`子分類`</a>
sub_category_id | Number | 子分類 id
creater | Object |  <a href="#employee">建立此工單的`員工`</a>
handler_id | Number | 建立此工單的員工 id
handler | Object | <a href="#employee">負責此工單的`員工`</a>
sponsor_id | Number | 負責此工單的員工 id
sponsor | Object | <a href="#sponsor">此工單所屬的`業主`</a>
created_at | Datetime | 初始建立時間
updated_at | Datetime | 最後更新時間

## 工單狀態細項代碼 (Ticket Termination Code)

Property | Type | Description
-------- | ---- | -----------
id | Number | id
name | String | 名稱
description | String | 說明
status | Number | 對應工單狀態 < 0: 待處理 1: 處理中 2: 已解決 3: 已關閉 >
creater_id | Number |  建立此狀態細項的`員工` id
creater | Object |  <a href="#employee">建立此狀態細項的`員工`</a>

## 主分類 (Category)

Property | Type | Description
-------- | ---- | -----------
id | Number | id
name | String | 名稱
description | String | 說明
children | Array of objects | <a href="#sub-category">`子分類`陣列</a>

## 子分類 (SubCategory)

Property | Type | Description
-------- | ---- | -----------
id | Number | id
name | String | 名稱
description | String | 說明
category | Object | <a href="#category">`母分類`</a>
category_id | Number | 母分類 id

## 業主 (Sponsor)

Property | Type | Description
-------- | ---- | -----------
id | Number | id
name | String | 名稱
description | String | 說明
is_immortal | Boolean | 是否不可更改
kbs | Array of objects | **待補**
mail_channels | Array of objects | **待補**

