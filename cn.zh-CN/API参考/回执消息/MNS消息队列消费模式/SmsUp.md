# SmsUp {#concept_ixx_ggb_3gb .concept}

通过MNS消息队列可以拉取上行短信消息（SmsUp）。

**说明：** 如果使用JAVA或Node.js语言的SDK上行短信消息（SmsUp），请分别使用[JAVA MNS SDK](http://ytx-sdk.oss-cn-shanghai.aliyuncs.com/dysms_mns_java_sdk.zip)和[原Node.js MNS SDK](https://www.npmjs.com/package/@alicloud/sms-sdk)。

**上行短信消息SmsUp**

|名称|类型|描述|示例|
|:-|:-|:-|:-|
|phone\_number|String|短信接收号码|13000000000|
|content|String|短信内容|true|
|sign\_name|String|短信签名|【阿里云】|
|send\_time|String|时间|20150101120000|
|dest\_code|String|扩展码|123456|
|sequence\_id|Double|消息序列ID|123456|

