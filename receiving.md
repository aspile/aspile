## Receiving SMS and MMS messages

In order to receive SMS or MMS messages we need somewhere to send them. In your "My Settings" page in the user portal, there is a settings for "Incoming SMS Post URL". All messages that come to any of your phone numbers will get sent to this URL via HTTP POST. So, all you need is a script that will consume these web calls and do something with it.

A sample HTTP POST message coming from teleapi will look like this:

## SMS

```
source=3035551212
destination=3039991111
message=Hello+World
type=sms
```

## MMS

```
source=3035551212
destination=3039991111
message=http://picmsg.org/[unique_identifier].jpg
type=mms
```