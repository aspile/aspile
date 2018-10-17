## teleapi documentation

Welcome to the teleapi documentation. teleapi was written to be the easiest API to integrate with, taking the positive attributes of a RESTFUL api and combining that with the simplicity that the web was created on.

Note: At the top right of the screen on many of the API doc help pages you can select the language to use. Some infrequently used pages do not have code samples.

All API commands can be sent using GET or POST, and no username, or special attributes are required, just your token.

We support JSON, XML and PHP serialize natively, just pass format=xml or format=php in your GET or POST request.

Many pages are outlined with the coding Method and a sample from a few different programming languages. These should get you started immediately.

## Coding Samples

Most pages will look like this, with the URL and coding examples.

URL:

> [https://sms.teleapi.net/sms/send?token=XXXXXXX](https://sms.teleapi.net/sms/send?token=XXXXXXX)

## Response Codes

At the top right of the screen, you will have RESPONSE for response expectations.

CURL

```
curl -v -X POST  "https://sms.teleapi.net/sms/send?token=XXXX" \
   -d "source=13035551212&destination=13038884444&message=hello+there"
```

PHP - file_get_contents

```
<?php
$data = array("source" => "13035551212",
"destination" => "13038884444",
"message" => "hey there");

$data = http_build_query($data);

$x = file_get_contents("https://sms.teleapi.net/sms/send?token=XXXX&$data");
$object = json_decode($x);
print_r($object);
```

## Responses from API

## Successfully Sent

> data
>> This is your unique tracking ID for this SMS message. You can track this in delivery notifications.

```
{
   "code":200,
   "status":"success",
   "data":"ea19aa71-4590-4e6b-a8ce-47e2b84c8091"
}
```

## Failed to Send

```
{
   "code":400,
   "status":"error",
   "data":"Invalid source number"
}
```