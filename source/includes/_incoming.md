# API Manual: IncomingMessages

Your bot must be connected and authenticated over the WebSocket session to receive incoming messages. The Bot Server does not store any messages for bots for later retrieval.

The following table lists the different incoming JSON messages for the bot.

## Incoming Messages

## Message

Incoming message represent new incoming, edited or deleted message from server

| Field   | Type                | Required | Description                                  |
| ------- | ------------------- | -------- | -------------------------------------------- |
| method  | String              | Yes      | "message"                                    |
| message | [Message](#_nmf14n) | Yes      | Object represents the content of the message |

## User Details

Incoming message represent new or updated user or bot profile. This inbound message returned as a reply to [GetUser](#_2nusc19) .

| Field  | Type              | Required | Description                                     |
| ------ | ----------------- | -------- | ----------------------------------------------- |
| method | String            | Yes      | "userDetails"                                   |
| user   | [User](#_3tbugp1) | Yes      | Object represents a nandbox user or bot account |

## Chat Details

Incoming message represent new or updated Group or Channel profile This inbound message returned as a reply to [GetChat](#_1302m92)

| Field  | Type              | Required | Description                                                   |
| ------ | ----------------- | -------- | ------------------------------------------------------------- |
| method | String            | Yes      | "chatDetails"                                                 |
| chat   | [Chat](#_28h4qwu) | Yes      | This object represents a nandbox group or channel information |

## Chat Menu Callback

Incoming message represents information about a clicked button associated with a normal keypad menu.

| Field            | Type                          | Required | Description                                                                                              |
| ---------------- | ----------------------------- | -------- | -------------------------------------------------------------------------------------------------------- |
| method           | String                        | Yes      | "chatMenuCallback"                                                                                       |
| chatMenuCallback | [ChatMenuCallback](#_2dlolyb) | Yes      | object represents an incoming callback query from a callback button associated with a normal keypad menu |

## Inline Message Callback

Incoming message represents information about a clicked button within an inline keypad menu associated with a specific message

| Field                 | Type                              | Required | Description                                                                                                                         |
| --------------------- | --------------------------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| method                | String                            | Yes      | "inlineMessageCallback"                                                                                                             |
| inlineMessageCallback | [inlineMessageCallback](#_sqyw64) | Yes      | object represents an incoming callback query from a callback button within an inline keypad menu associated with a specific message |

## Chat Member

Incoming message represents information about group or channel member returned as a reply to [getChatMember](#_3mzq4wv) , [banChatMember](#_haapch), [unbanChatMember](#_319y80a), [removeChatMember](#_1gf8i83) and when user join or leaves the chat.

| Field      | Type                    | Required | Description                           |
| ---------- | ----------------------- | -------- | ------------------------------------- |
| method     | String                  | Yes      | "chatMember"                          |
| chatMember | [ChatMemebr](#_1rvwp1q) | Yes      | object represents a chat member user. |

## Chat Administrators

Incoming message represents information about group or channel administrators returned as a reply to [getChatAdministrators](#_2250f4o).

| Field              | Type                            | Required | Description                                             |
| ------------------ | ------------------------------- | -------- | ------------------------------------------------------- |
| method             | String                          | Yes      | "chatAdministrators"                                    |
| chatAdministrators | [ChatAdministrators](#_4bvk7pj) | Yes      | object represents channel or group administrator users. |

## My Profile

Incoming message represents Bot profile details , this will be come as a reply to [getMyProfiles](#_3ep43zb) outgoing message

| Field  | Type              | Required | Description                                |
| ------ | ----------------- | -------- | ------------------------------------------ |
| method | String            | Yes      | "myProfile"                                |
| user   | [User](#_3tbugp1) | Yes      | User object represents Bot profile details |

**JSON Example:**

```json
{

"method": "myProfile",

"user": {

"name": "Bot Title",

"photo": {

"thumbnail": {

"width": 120,

"id": "7e8bc6cddff924.jpg.thumb.jpg",

"height": 120

},

"width": 256,

"id": "7e8bc6cddff92487fbeb4074e.jpg",

"height": 256

},

"id": "4521191845180798",

"version": "0btm",

"status": "Bot Status",

}

}
```

## Message Ack

Incoming message represents outbound message acknowledge.

| Field  | Type   | Required | Description                                                 |
| ------ | ------ | -------- | ----------------------------------------------------------- |
| method | String | Yes      | "myProfilemessageAck"                                       |
| ack    | Ack    | Yes      | Object represents outbound messages acknowledgment details. |

**JSON Example:**

```json
{

"method": "messageAck",

"ack": {

"reference": 15459134560801,

"date": 1545913595858,

"message_id": "p1_Ua0ZWAyX13260293"

}

}
```
