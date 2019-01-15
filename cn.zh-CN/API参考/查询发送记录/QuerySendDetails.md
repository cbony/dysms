# QuerySendDetails {#doc_api_915983 .reference}

调用QuerySendDetails接口查看短信发送记录和发送状态。

通过调用QuerySendDetails接口，可以根据短信发送日期查看发送记录和短信内容，也可以添加发送流水号，根据流水号查询指定日期指定请求的发送详情。

如果指定日期短信发送量较大，可以分页查看。指定每页显示的短信详情数量和查看的页数，即可分页查看发送记录。

## 调试 {#apiExplorer .section}

单击[这里](https://api.aliyun.com/#product=Dysmsapi&api=QuerySendDetails)在OpenAPI Explorer中进行可视化调试，并生成SDK代码示例。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|CurrentPage|Long|是|1|分页查看发送记录，指定发送记录的的当前页码。

 |
|PageSize|Long|是|10|分页查看发送记录，指定每页显示的短信记录数量。

 取值范围为1~50。

 |
|PhoneNumber|String|是|15900000000|接收短信的手机号码。

 格式：

 -   国内短信：11位手机号码，例如15900000000。
-   国际/港澳台消息：国际区号+号码，例如85200000000。

 |
|SendDate|String|是|20181228|短信发送日期，支持查询最近30天的记录。

 格式为yyyyMMdd，例如20181225。

 |
|AccessKeyId|String|否|LTAIP00vvvvvvvvv|主账号AccessKey的ID，即Key。

 |
|Action|String|否|QuerySendDetails|系统规定参数。取值：QuerySendDetails。

 |
|BizId|String|否|134523^4351232|发送回执ID，即发送流水号。调用发送接口SendSms或SendBatchSms发送短信时，返回值中的BizId字段。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|请求状态码。

 -   返回OK代表请求成功。
-   其他错误码详见[错误码列表](~~101346~~)。

 |
|Message|String|OK|状态码的描述。

 |
|RequestId|String|819BE656-D2E0-4858-8B21-B2E477085AAF|请求ID。

 |
|SmsSendDetailDTOs| | |短信发送明细。

 |
|└Content|String|【阿里云】验证码为：123，您正在登录，若非本人操作，请勿泄露|短信内容。

 |
|└ErrCode|String|DELIVRD|运营商短信状态码。

 -   短信发送成功：DELIVRD。
-   短信发送失败：失败错误码请参考[错误码文档](~~101347~~)。

 |
|└OutId|String|123|外部流水扩展字段。

 |
|└PhoneNum|String|15200000000|接收短信的手机号码。

 |
|└ReceiveDate|String|2019-01-08 16:44:13|短信接收日期和时间。

 |
|└SendDate|String|2019-01-08 16:44:10|短信发送日期和时间。

 |
|└SendStatus|Long|3|短信发送状态，包括：

 -   1：等待回执。
-   2：发送失败。
-   3：发送成功。

 |
|└TemplateCode|String|SMS\_122310183|短信模板ID。

 |
|TotalCount|String|1|短信发送总条数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?CurrentPage=1
&PageSize=10
&PhoneNumber=15900000000
&SendDate=20181228
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<QuerySendDetailsResponse>
  <TotalCount>1</TotalCount>
  <Message>OK</Message>
  <RequestId>908D868C-D35E-438B-9632-9D7F3E440F6D</RequestId>
  <SmsSendDetailDTOs>
    <SmsSendDetailDTO>
      <OutId>123</OutId>
      <SendDate>2019-01-08 16:44:10</SendDate>
      <SendStatus>3</SendStatus>
      <ReceiveDate>2019-01-08 16:44:13</ReceiveDate>
      <ErrCode>DELIVRD</ErrCode>
      <TemplateCode>SMS_122310183</TemplateCode>
      <Content>【阿里云】验证码为：123，您正在登录，若非本人操作，请勿泄露</Content>
      <PhoneNum>15200000000</PhoneNum>
    </SmsSendDetailDTO>
  </SmsSendDetailDTOs>
  <Code>OK</Code>
</QuerySendDetailsResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"TotalCount":1,
	"Message":"OK",
	"RequestId":"819BE656-D2E0-4858-8B21-B2E477085AAF",
	"SmsSendDetailDTOs":{
		"SmsSendDetailDTO":[
			{
				"SendDate":"2019-01-08 16:44:10",
				"OutId":"123",
				"SendStatus":3,
				"ReceiveDate":"2019-01-08 16:44:13",
				"ErrCode":"DELIVRD",
				"TemplateCode":"SMS_122310183",
				"Content":"【阿里云】验证码为：123，您正在登录，若非本人操作，请勿泄露",
				"PhoneNum":"15298356881"
			}
		]
	},
	"Code":"OK"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Dysmsapi)

