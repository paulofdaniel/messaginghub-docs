### User input
| MIME type                            | C#                                   |
|--------------------------------------|--------------------------------------|
| application/vnd.lime.input+json      | [Lime.Messaging.Contents.Input](https://github.com/takenet/lime-csharp/blob/master/src/Lime.Messaging/Contents/Input.cs) |

Allows send structured information request to the user, where is possible to define validations rules. This is useful to build questions forms or get specific user information like name, phone number or typed information like an image or location. The execution of validation rules depends of channel support.

#### Examples
1 - Requesting user name:
```json
{
    "id": "1",
    "to": "553199991111@0mn.io",
    "type": "application/vnd.lime.input+json",
    "content": {
        "label": {
          "type": "text/plain",
          "value": "What is your name?"
        },
        "validation": {
          "rule": "text"          
        }
    }
}
```

2 - Requesting user location:
```json
{
    "id": "2",
    "to": "1334448323284655@messenger.gw.msging.net",
    "type": "application/vnd.lime.input+json",
    "content": {
        "label": {
          "type": "text/plain",
          "value": "Send your location please!"
        },
        "validation": {
          "rule": "type",
          "type": "application/vnd.lime.location+json"
        }
    }
}
```

For more details, check the [LIME protocol](http://limeprotocol.org/content-types.html#input) specification.

#### Channel mapping

| Channel              | Type                         | 
|--------------------|--------------------------------|
| BLiP Chat          | Uer input (for Location type only) |
| Messenger          | [Location](https://developers.facebook.com/docs/messenger-platform/send-api-reference/quick-replies) |
| SMS                | Text                   |
| Skype              | [Activity](https://docs.botframework.com/en-us/skype/chat/#sending-messages-1)|
| Telegram           | [Message](https://core.telegram.org/bots/api#message)|

