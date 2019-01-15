# API 错误码 {#concept_cw4_vfs_ggb .concept}

调用API接口失败时，会返回接口调用错误码。

常见接口调用错误码、错误信息和解决方案，请参考下表：

|错误码（Code）|错误信息（Message）|原因及解决方案|
|:--------|:------------|:------|
|OK|OK|表示接口调用成功。|
|isv.EXTEND\_CODE\_ERROR|扩展码使用错误，相同的扩展码不可用于多个签名|**原因**：发送短信时不同签名的短信使用了相同扩展码。**解决方案**：在调用短信发送接口时，不同的短信签名使用不同的扩展码。

|
|isv.DOMESTIC\_NUMBER\_NOT\_SUPPORTED|国际/港澳台消息模板不支持发送境内号码|**原因**：国际/港澳台消息模板仅支持发送国际、港澳台地区的号码。**解决方案**：如果想发送境内短信，请申请国内短信模版。

|
|isv.DAY\_LIMIT\_CONTROL|触发日发送限额|**原因**：已经达到您在控制台设置的短信日发送量限额值。**解决方案**：如需修改限额，请在短信服务控制台左侧导航栏中单击**国内消息设置** \> **安全设置**，修改**发送总量阈值**。

|
|isv.SMS\_CONTENT\_ILLEGAL|短信内容包含禁止发送内容|**原因**：短信内容包含禁止发送内容。**解决方案**：修改短信文案。

|
|isv.SMS\_SIGN\_ILLEGAL|签名禁止使用|**原因**：签名禁止使用。**解决方案**：请在短信服务控制台中申请符合规定的签名。

|
|isp.RAM\_PERMISSION\_DENY|RAM权限DENY|**原因**：RAM权限不足。**解决方案**：请为当前使用的AK对应子账号进行授权：AliyunDysmsFullAccess（管理权限）。具体操作请参考：[访问权限控制](https://help.aliyun.com/document_detail/55764.html)。

|
|isv.OUT\_OF\_SERVICE|业务停机|**原因**：余额不足。余额不足时，套餐包中即使有短信额度也无法发送短信。**解决方案**：请及时充值。

如果余额大于零仍报此错误，请通过工单联系工程师处理。|
|isv.PRODUCT\_UN\_SUBSCRIPT|未开通云通信产品的阿里云客户|**原因**： 该AK所属的账号尚未开通云通信的服务，包括短信、语音、流量等服务。**解决方案**：当出现此类提示报错需要检查当前AK是否已经开通阿里云云通信短信服务，如已开通消息服务，则参照消息服务文档调用接口。

|
|isv.PRODUCT\_UNSUBSCRIBE|产品未开通|**原因**： 该AK所属的账号尚未开通当前接口的产品，例如仅开通了短信服务的用户调用语音接口时会产生此报错信息。**解决方案**：检查AK对应账号是否已开通调用接口对应的服务。开通短信服务请单击[短信服务产品介绍](https://www.aliyun.com/product/sms)。

|
|isv.ACCOUNT\_NOT\_EXISTS|账户不存在|**原因**： 使用了错误的账户名称或AK。**解决方案**：请确认账号信息。

|
|isv.ACCOUNT\_ABNORMAL|账户异常|**原因**：账户异常。 **解决方案**： 请确认账号信息。

|
|isv.SMS\_TEMPLATE\_ILLEGAL|短信模版不合法|**原因**： 短信模板不存在，或未经审核通过。**解决方案**： 参数TemplateCode请传入审核通过的模版ID，模版ID请在[控制台**模板管理**](https://dysms.console.aliyun.com/dysms.htm#/template)页面中查看。

|
|isv.SMS\_SIGNATURE\_ILLEGAL|短信签名不合法|**原因**： 签名不存在，或未经审核通过。**解决方案**：参数SignName请传入审核通过的签名名称，签名请在[控制台**签名管理**](https://dysms.console.aliyun.com/dysms.htm#/sign)页面中查看。

|
|isv.INVALID\_PARAMETERS|参数异常|**原因**： 参数格式不正确。**解决方案**：请根据对应的API文档检查参数格式。

例如，短信查询接口QuerySendDetails的参数SendDate日期格式为yyyyMMdd，正确格式为20170101，错误格式为2017-01-01。

|
|isp.SYSTEM\_ERROR|isp.SYSTEM\_ERROR|**原因**： 系统错误。**解决方案**：请重新调用接口，如仍存在此情况请创建工单反馈工程师查看。

|
|isv.MOBILE\_NUMBER\_ILLEGAL|非法手机号|**原因**：手机号码格式错误。 **解决方案**：参数PhoneNumbers请传入正确的格式。

-   国内短信：11位手机号码，例如15951955195。
-   国际/港澳台消息：国际区号+号码，例如85200000000。

|
|isv.MOBILE\_COUNT\_OVER\_LIMIT|手机号码数量超过限制|**原因**：参数PhoneNumbers中指定的手机号码数量超出限制。**解决方案**：请将手机号码数量限制在1000个以内。

|
|isv.TEMPLATE\_MISSING\_PARAMETERS|模版缺少变量|**原因**： 参数TemplateParam中，变量未全部赋值。**解决方案**： 请JSON格式字符串为模板变量赋值。

例如，模版为`您好${name}，验证码${code}`，则参数TemplateParam可以指定为`{"name":"Tom","code":"123"}`。

|
|isv.BUSINESS\_LIMIT\_CONTROL|业务限流|**原因**： 短信发送频率超限。**解决方案**： 请将短信发送频率限制在正常的业务流控范围内。默认流控：使用同一个签名，对同一个手机号码发送**短信验证码**，支持1条/分钟，5条/小时 ，累计10条/天。

|
|isv.INVALID\_JSON\_PARAM|JSON参数不合法，只接受字符串值|**原因**：参数格式错误，不是合法的JSON格式。 **解决方案**： 请在参数TemplateParam中指定正确的JSON格式字符串，例如`{"code":"123"}`。

|
|isv.BLACK\_KEY\_CONTROL\_LIMIT|黑名单管控|**原因**： 黑名单管控是指变量内容含有限制发送的内容，例如变量中不允许透传URL。**解决方案**： 请检查通过变量是否透传了一些敏感信息。

|
|isv.PARAM\_LENGTH\_LIMIT|参数超出长度限制|**原因**：参数超出长度限制。**解决方案**：每个变量的长度限制为1~20字符。请修改参数长度。

|
|isv.PARAM\_NOT\_SUPPORT\_URL|不支持URL|**原因**： 黑名单管控是指变量内容含有限制发送的内容，例如变量中不允许透传URL。**解决方案**： 请检查通过变量是否透传了URL或敏感信息。

|
|isv.AMOUNT\_NOT\_ENOUGH|账户余额不足|**原因**： 当前账户余额不足。**解决方案**：请及时充值。调用接口前请确认当前账户余额是否足以支付预计发送的短信量。

|
|isv.TEMPLATE\_PARAMS\_ILLEGAL|模版变量里包含非法关键字|**原因**：变量内容含有限制发送的内容，例如变量中不允许透传URL。**解决方案**： 请检查通过变量是否透传了URL或敏感信息。

|
|SignatureDoesNotMatch|Specified signature is not matched with our calculation.|**原因**： 签名（Signature）加密错误。**解决方案**：

-   如果使用SDK调用接口，请注意accessKeyId和accessKeySecret字符串赋值正确。
-   如果自行加密签名（Signature），请对照[文档](cn.zh-CN/API参考/公共信息/请求签名.md)检查加密逻辑。

|
|InvalidTimeStamp.Expired|Specified time stamp or date value is expired.|**原因**： 一般由于时区差异造成时间戳错误，发出请求的时间和服务器接收到请求的时间不在15分钟内。阿里云网关使用的时间是GMT时间。

**解决方案**：请使用GMT时间。

|
|SignatureNonceUsed|Specified signature nonce was used already.|**原因**： 唯一随机数重复，SignatureNonce为唯一随机数，用于防止网络重放攻击。**解决方案**： 不同请求请使用不同的随机数值。

|
|InvalidVersion|Specified parameter Version is not valid.|**原因**： 版本号（Version）错误。**解决方案**：请确认接口的版本号，短信服务的API版本号（Version）为2017-05-25。

|
|InvalidAction.NotFound|Specified api is not found, please check your url and method|**原因**： 参数Action中指定的接口名错误。**解决方案**： 请在参数Action中使用正确的接口地址和接口名。

|

