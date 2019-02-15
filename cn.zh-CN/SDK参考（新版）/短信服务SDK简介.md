# 短信服务SDK简介 {#concept_zc3_ryk_3gb .concept}

 短信服务新版SDK源码已经托管至开源平台Github，您使用GitHub clone的方式使用SDK，也可以使用依赖管理工具安装（PHP除外），Demo代码可通过OpenAPI Explorer生成，所有SDK均只依赖SDK核心库，使用通用的Request及Response来处理接口请求及响应。

目前，短信服务提供以下编程语言的SDK。

**说明：** 

-   通过JAVA SDK拉取[消息回执](../../../../../cn.zh-CN/API参考/回执消息/简介.md)，请使用[JAVA MNS SDK](http://ytx-sdk.oss-cn-shanghai.aliyuncs.com/dysms_mns_java_sdk.zip)。
-   通过Node.js SDK拉取[消息回执](../../../../../cn.zh-CN/API参考/回执消息/简介.md)，请使用[原Node.js MNS SDK](https://www.npmjs.com/package/@alicloud/sms-sdk)。

|SDK|GitHub下载地址|说明文档|DEMO|
|:--|:---------|:---|:---|
|Java SDK|[短信服务Java SDK](https://github.com/aliyun/aliyun-openapi-java-sdk/tree/master/aliyun-java-sdk-core)|[快速开始](../../../../../cn.zh-CN/Java SDK/快速开始.md)|[Java SDK DEMO](https://api.aliyun.com/#/?product=Dysmsapi&lang=JAVA)|
|.NET SDK|[短信服务.NET SDK](https://github.com/aliyun/aliyun-openapi-net-sdk/tree/master/aliyun-net-sdk-core)|[快速开始](../../../../../cn.zh-CN/.NET SDK/快速开始.md)|-|
|PHP SDK|[短信服务PHP SDK](https://github.com/aliyun/openapi-sdk-php-client)|[使用说明](https://github.com/aliyun/openapi-sdk-php-client/blob/master/README-CN.md)|[PHP SDK DEMO](https://api.aliyun.com/#/?product=Dysmsapi&lang=PHP)|
|Python SDK|[短信服务Python SDK](https://github.com/aliyun/aliyun-openapi-python-sdk/tree/master/aliyun-python-sdk-core)|[快速开始](../../../../../cn.zh-CN/Python SDK/快速开始.md)|[Python SDK DEMO](https://api.aliyun.com/#/?product=Dysmsapi&lang=PYTHON)|
|Node.js SDK|[短信服务Node.js SDK](https://www.npmjs.com/package/@alicloud/pop-core)|[快速开始](../../../../../cn.zh-CN/Node.js SDK/快速开始.md)|[Node.js SDK DEMO](https://api.aliyun.com/#/?product=Dysmsapi&lang=NODEJS)|
|Go SDK|[短信服务Go SDK](https://github.com/aliyun/alibaba-cloud-sdk-go/)|[快速开始](../../../../../cn.zh-CN/Go SDK/快速开始.md)|[Go SDK DEMO](https://api.aliyun.com/#/?product=Dysmsapi&lang=GO)|

## 短信服务SDK升级说明 {#section_c4y_5sr_pgb .section}

2019年1月22日，短信服务发布了新版SDK，此日期后接入SDK的用户使用的均为新版SDK；2019年1月22日前接入的SDK的用户使用的是旧版SDK。相较于旧版SDK，新版SDK有以下优势：

-   融入阿里云OpenAPI技术体系，改善用户体验。通过新版短信服务SDK，用户可以使用阿里云资源如API Explorer、CloudShell等工具体验API。
-   阿里云统一维护，降低故障风险。新版短信服务SDK由阿里云SDK统一维护，同时支持自动更新及故障预警，包括Github通知和Deprecated提示等。

新版短信服务SDK提供了更稳定、完善的开发环境，建议您尽快[升级SDK](cn.zh-CN/SDK参考（新版）/升级SDK.md)。

