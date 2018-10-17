## Sending SMS with restful API

Sending SMS with teleapi is a breeze.

##Post/ Get Information

URL:
> [https://sms.teleapi.net/sms/send?token=XXXXXXX](https://sms.teleapi.net/sms/send?token=XXXXXXX)


| Argument  | Required  | Type  |
| ----------| --------  |  ---- |
| source    |   yes     |   int |
| destination    |   yes     |   int |
| message	    |   yes     |   string |

## Character Limitations

SMS Messages are limited to 140 characters, however you can send up to 910 characters. teleapi will split the messages into smaller messages, which may increase your message count.

Sending emojis embedded in your messages will cause the character set to be changed and your messages to be split into 70 character chunks.

CURL

```
curl -v -X POST  "https://sms.teleapi.net/sms/send?token=XXXX" \
   -d "source=13035551212&destination=13038884444&message=hello+there"
```

PHP + Curl

```
<?php
$data = array("source" => "13035551212",
"destination" => "13038884444",
"message" => "hey there");

$data = http_build_query($data);
$baseurl = "https://sms.teleapi.net/sms/send?token=XXXX";
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS, $data);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
$retval = curl_exec($ch);
curl_close($ch);

$object = json_decode($retval);
print_r($object);
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