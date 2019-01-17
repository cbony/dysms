# PHP Demo {#concept_mcx_zjl_3gb .concept}

依赖OpenAPI PHP Client包和OpenAPI PHP SDK包。

-   OpenAPI PHP Client

-   下载地址：[openapi-sdk-php-client](https://github.com/aliyun/openapi-sdk-php-client)

-   安装说明[OpenAPI PHP Client 安装说明](https://github.com/aliyun/openapi-sdk-php-client/blob/master/README-CN.md)

-   OpenAPI PHP SDK

-   下载地址：[openapi-sdk-php](https://github.com/aliyun/openapi-sdk-php)

-   安装说明[OpenAPI PHP SDK 安装说明](https://github.com/aliyun/openapi-sdk-php/blob/master/README-CN.md)


Demo如下：

```
<?
use AlibabaCloud\Client\AlibabaCloud;
use AlibabaCloud\Client\Exception\ClientException;
use AlibabaCloud\Client\Exception\ServerException;
use AlibabaCloud\Dybaseapi\MNS\Requests\BatchReceiveMessageRequest;
use AlibabaCloud\Dybaseapi\MNS\Requests\BatchDeleteMessageRequest;
use AlibabaCloud\Dybaseapi\MNS\Exception\MnsException;

AlibabaCloud::accessKeyClient('<AccessKeyId>', '<AccessSecret>')
    ->regionId('cn-hangzhou') // replace regionId as you need
    ->asGlobalClient();

$queueName = '<QueueName>'; // 队列名称
$messageType = '<MessageType>'; // SmsReport短信通知

$response = null;
$token = null;
$i = 0;

do {
    if (null == $token || strtotime($token['ExpireTime']) - time() > 2 * 60) {
        $response = AlibabaCloud::rpcRequest()
            ->product('Dybaseapi')
            ->version('2017-05-25')
            ->action('QueryTokenForMnsQueue')
            ->method('POST')
            ->host("dybaseapi.aliyuncs.com")
            ->options([
                'query' => [
                    'MessageType' => $messageType,
                    'QueueName' => $queueName,
                ],
            ])
            ->request()
            ->toArray();
    }

    $token = $response['MessageTokenDTO'];

    $mnsClient = new \AlibabaCloud\Dybaseapi\MNS\Client(
        "http://1943695596114318.mns.cn-hangzhou.aliyuncs.com",
        $token['AccessKeyId'],
        $token['AccessKeySecret'],
        $token['SecurityToken']
    );

    try {
        $mnsRequest = new BatchReceiveMessageRequest(10, 5);
        $mnsRequest->setQueueName($queueName);
        $mnsResponse = $mnsClient->sendRequest($mnsRequest);

        print_r($mnsResponse);

        $receiptHandles = Array();
        foreach ($mnsResponse->Message as $message) {
            // 用户逻辑：
            // $receiptHandles[] = $message->ReceiptHandle; // 加入$receiptHandles数组中的记录将会被删除
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
    } catch (ClientException $e) {
        echo $e->getErrorMessage() . PHP_EOL;
        exit;
    } catch (ServerException $e) {
        echo $e->getErrorMessage() . PHP_EOL;
        exit;
    }
} while ($i < 3);
```

