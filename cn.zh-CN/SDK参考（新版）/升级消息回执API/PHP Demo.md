# PHP Demo {#concept_mcx_zjl_3gb .concept}

依赖PHP语言的阿里云核心库及dybaseapi，其中dybaseapi包用于拉取MNS消息。

-   [阿里云SDK核心库](https://github.com/aliyun/aliyun-openapi-php-sdk/tree/master/aliyun-php-sdk-core)
-   [dybaseapi](https://github.com/aliyun/aliyun-openapi-php-sdk/tree/master/aliyun-php-sdk-dybaseapi)

Demo如下：

```
<?php
include_once 'aliyun-php-sdk-core/Config.php';
Autoloader::addAutoloadPath("aliyun-php-sdk-dybaseapi");


use Dybaseapi\Request\V20170525\QueryTokenForMnsQueueRequest;
use Dybaseapi\MNS\Requests\BatchReceiveMessageRequest;
use Dybaseapi\MNS\Requests\BatchDeleteMessageRequest;
use Dybaseapi\MNS\Exception\MnsException;

DefaultProfile::addEndpoint("cn-hangzhou", "cn-hangzhou", "Dybaseapi", "dybaseapi.aliyuncs.com");
$iClientProfile = DefaultProfile::getProfile("cn-hangzhou", "<AccessKeyId>", "<AccessKeySecret>");
$client = new DefaultAcsClient($iClientProfile);

$queueName = "<QueueName>";
$messageType = "<MessageType>";

$request = new QueryTokenForMnsQueueRequest();
$request->setMessageType($messageType);
$request->setQueueName($queueName);

$response = null;
$token = null;

$i = 0;

do {
    if (null == $token || strtotime($token->ExpireTime) - time() > 2 * 60) {
        $response = $client->getAcsResponse($request);
    }

    $token = $response->MessageTokenDTO;

    $mnsClient = new Dybaseapi\MNS\Client(
        "http://1943695596114318.mns.cn-hangzhou.aliyuncs.com",
        $token->AccessKeyId,
        $token->AccessKeySecret,
        $token->SecurityToken
    );

    try {
        $mnsRequest = new BatchReceiveMessageRequest(10, 5);
        $mnsRequest->setQueueName($queueName);
        $mnsResponse = $mnsClient->sendRequest($mnsRequest);

        print_r($mnsResponse);

        $receiptHandles = Array();
        foreach ($mnsResponse->Message as $message) {
            // 用户逻辑：
            $receiptHandles[] = $message->ReceiptHandle; // 加入$receiptHandles数组中的记录将会被删除
            $messageBody = base64_decode($message->MessageBody); // base64解码后的JSON字符串
            print_r($messageBody . "\n");
        }

        if (count($receiptHandles) > 0) {
            $deleteRequest = new BatchDeleteMessageRequest($queueName, $receiptHandles);
            $mnsClient->sendRequest($deleteRequest);
        }
    } catch (MnsException $e) {
        $i++;
        echo "ex:{$e->getMnsErrorCode()}\n";
        echo "ReceiveMessage Failed: {$e}\n";
    }
} while ($i < 3);
```

