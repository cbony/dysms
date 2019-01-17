# SmsReport {#concept_np4_jcb_3gb .concept}

通过MNS消息队列可以拉取短信状态报告（SmsReport）。

**说明：** 如果使用JAVA或Node.js语言的SDK拉取短信状态报告（SmsReport），请分别使用[JAVA MNS SDK](http://ytx-sdk.oss-cn-shanghai.aliyuncs.com/dysms_mns_java_sdk.zip)和[原Node.js MNS SDK](http://alicom-fc-media.cn-hangzhou.oss.aliyun-inc.com/aliyun-dysms-sdk-master-c1b216773b098058f1bed5d3be97bd1d50eca9f3.zip?Expires=1861500764&OSSAccessKeyId=bypFNbGJVk73PsLI&Signature=4FarzYNea0EUnvdrq5bQvfcT11M%3D)。

**短信回执消息SmsReport消息体格式**

|名称|类型|描述|示例|
|:-|:-|:-|:-|
|phone\_number|String|短信接收号码|13000000000|
|success|Boolean|发送是否成功|true|
|biz\_id|String|发送回执ID|1234^345|
|out\_id|String|调用发送短信接口时传的outId|123456|
|send\_time|String|转发给运营商的时间|2017-06-01 10:00:00|
|report\_time|String|收到运营商回执的时间|2017-06-01 10:00:05|
|err\_code|String|错误码|UNKNOW|
|err\_msg|String|错误信息|未知异常|
|sms\_size|String|140字节算一条短信，短信长度超过140字节时会拆分成多条短信发送|1，2，3|

