# SmsUp {#concept_qjg_wlk_3gb .concept}

通过HTTP批量推送方式可以拉取上行短信消息（SmsUp）。

## 协议说明 {#section_qz1_ylk_3gb .section}

|参数|说明|
|:-|:-|
|协议|HTTP + JSON|
|编码|UTF-8|

## 请求说明 {#section_ert_j4k_3gb .section}

请求内容为JSON Array格式，单次请求可能会包含多个上行短信内容。

-   请求样例

    ```
    [
      {
        "phone_number" : "18612345678",
        "send_time" : "2017-09-01 00:00:00",
        "content" : "内容",
        "sign_name" : "签名",
        "dest_code" : "1234",
        "sequence_id" : 1234567890
      }
    ]
    ```

-   字段说明

    |名称|类型|描述|示例值|是否必须|
    |:-|:-|:-|:--|:---|
    |phone\_number|String|手机号码|13900000001|必须|
    |send\_time|String|发送时间|2017-01-01 00:00:00|必须|
    |content|String|发送内容|这是一条上行短信|必须|
    |sign\_name|String|签名信息|xxxx|可选|
    |dest\_code|String|扩展号码|1234|必须|
    |sequence\_id|Number|序列号|1234567890|必须|


## 响应说明 {#section_m1d_r4k_3gb .section}

-   响应样例

    ```
    {
      "code" : 0,
      "msg" : "接收成功"
    }
    ```

-   字段说明

    |名称|类型|是否必须|说明|示例值|
    |:-|:-|:---|:-|:--|
    |code|Number|必须|应答编码|0|
    |msg|String|可选|描述信息|接收成功|


## 重新推送 {#section_ush_ptk_3gb .section}

第一次推送失败后，间隔1分钟、5分钟、10分钟、30分钟、60分钟、60分钟、60分钟、60分钟、60分钟后会进行重推，直至推送成功为止。如果推送10次后仍失败，不再重试。

