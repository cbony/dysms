# SendBatchSms {#doc_api_931980 .reference}

调用SendBatchSms接口批量发送短信。

**SendBatchSms**接口是短信批量发送接口，支持在一次请求中分别向多个不同的手机号码发送不同签名的短信。手机号码等参数均为JSON格式，字段个数相同，一一对应，短信服务根据字段在JSON中的顺序判断发往指定手机号码的签名。

如果您需要往多个手机号码中发送同样签名的短信，请使用**SendSms**接口实现。

调用该接口发送短信时，请注意：

-   发送短信会根据发送量计费，价格请参考[计费说明](https://www.aliyun.com/price/product#/sms/detail)。
-   在一次请求中，最多可以向100个手机号码分别发送短信。

## 调试 {#apiExplorer .section}

单击[这里](https://api.aliyun.com/#product=Dysmsapi&api=SendBatchSms)在OpenAPI Explorer中进行可视化调试，并生成SDK代码示例。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|PhoneNumberJson|String|是|\["15900000000","13500000000"\]|接收短信的手机号码，JSON数组格式。

 手机号码格式：

 -   国内短信：11位手机号码，例如15900000000。
-   国际/港澳台消息：国际区号+号码，例如85200000000。

 **说明：** 验证码类型短信，建议使用接口SendSms单独发送。

 |
|SignNameJson|String|是|\["阿里云","阿里巴巴"\]|短信签名名称，JSON数组格式。

 请在控制台**签名管理**页面**签名名称**一列查看。

 **说明：** 必须是已添加、并通过审核的短信签名；且短信签名的个数必须与手机号码的个数相同、内容一一对应。

 |
|TemplateCode|String|是|SMS\_152550005|短信模板CODE。请在控制台**模板管理**页面**模板CODE**一列查看。

 **说明：** 必须是已添加、并通过审核的模板CODE；且发送国际/港澳台消息时，请使用国际/港澳台短信模版。

 |
|AccessKeyId|String|否|LTAIP00vvvvvvvvv|主账号AccessKey的ID。

 |
|Action|String|否|SendBatchSms|系统规定参数。取值：**SendBatchSms**。

 |
|SmsUpExtendCodeJson|String|否|\["90999","90998"\]|上行短信扩展码，JSON数组格式。无特殊需要此字段的用户请忽略此字段。

 |
|TemplateParamJson|String|否|\[\{"name":"TemplateParamJson"\},\{"name":"TemplateParamJson"\}\]|短信模板变量对应的实际值，JSON格式。

 **说明：** 如果JSON中需要带换行符，请参照标准的JSON协议处理；且模板变量值的个数必须与手机号码、签名的个数相同、内容一一对应，表示向指定手机号码中发对应签名的短信，且短信模板中的变量参数替换为对应的值。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|BizId|String|900619746936498440^0|发送回执ID，可根据该ID在接口QuerySendDetails中查询具体的发送状态。

 |
|Code|String|OK|请求状态码。

 -   返回OK代表请求成功。
-   其他错误码详见[错误码列表](~~101346~~)。

 |
|Message|String|OK|状态码的描述。

 |
|RequestId|String|F655A8D5-B967-440B-8683-DAD6FF8DE990|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?PhoneNumberJson=["15900000000","13500000000"]
&SignNameJson=["阿里云","阿里巴巴"]
&TemplateCode=SMS_152550005
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<SendSmsResponse>
  <Message>OK</Message>
  <RequestId>44DF7A95-603F-4651-9298-BE1850BEB53F</RequestId>
  <BizId>336006646937050335^0</BizId>
  <Code>OK</Code>
</SendSmsResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Message":"OK",
	"RequestId":"2184201F-BFB3-446B-B1F2-C746B7BF0657",
	"BizId":"197703245997295588^0",
	"Code":"OK"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Dysmsapi)

