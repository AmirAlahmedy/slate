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
```javascript
const Chat = require("../data/Chat");

module.exports = class ChatDetails {

    constructor(obj) {
        this.chat = new Chat(obj.chat);
    }

    toJsonObject(){
        let obj;

        if (this.chat) obj.chat = chat.toJsonObject();

        return obj;
    }
}
```
```java
public class ChatDetails {
	private static final String KEY_CHAT = "chat";

	private Chat chat;

	public ChatDetails(JSONObject obj) {

		this.chat = new Chat((JSONObject) obj.get(KEY_CHAT));

	}

	public JSONObject toJsonObject() {

		JSONObject obj = new JSONObject();

		if (chat != null) {
			obj.put(KEY_CHAT, chat.toJsonObject());
		}

		return obj;

	}
}
```
Incoming message represent new or updated Group or Channel profile This inbound message returned as a reply to [GetChat](#_1302m92)

| Field  | Type              | Required | Description                                                   |
| ------ | ----------------- | -------- | ------------------------------------------------------------- |
| method | String            | Yes      | "chatDetails"                                                 |
| chat   | [Chat](#_28h4qwu) | Yes      | This object represents a nandbox group or channel information |

## Chat Menu Callback
```javascript
const ButtonQueryResult = require("../data/ButtonQueryResult");
const User =  require("../data/User");
const Chat = require("../data/Chat");

module.exports = class ChatMenuCallback {

    constructor(jsonObj) {
       console.log("json " + JSON.stringify(jsonObj));
        let obj = jsonObj.chatMenuCallback;

        let fromUser = new User(obj.from);
        this.chat = obj.chat == null ? null : new Chat( obj.chat);
        let btnqueryResults = obj.button_query_result == null ? null
            : new ButtonQueryResult( obj.button_query_result);
        this.method = obj.method;
        this.menu_ref = obj.menu_ref;
        this.from = fromUser;
        this.button_query_result = btnqueryResults;
        this.button_callback = obj.button_callback;
        this.next_menu = obj.next_menu;
        this.date = obj.date;
    }

     toJsonObject(){

        let obj;

        if (this.date) obj.date = this.date;
        if (this.from) obj.from = this.from.toJsonObject();
        if (this.chat) obj.chat = this.chat.toJsonObject();
        if (this.method) obj.method = this.method;
        if (this.menuRef) obj.menu_ref = this.menu_ref;
        if (this.buttonCallback) obj.button_callback = this.button_callback;
        if (this.buttonQueryResult) obj.button_query_result = this.button_query_result;
        if (this.nextMenu) obj.next_menu = this.next_menu;

        console.log("to " + JSON.stringify(obj));
        return obj;

    }
}
```
Incoming message represents information about a clicked button associated with a normal keypad menu.

| Field            | Type                          | Required | Description                                                                                              |
| ---------------- | ----------------------------- | -------- | -------------------------------------------------------------------------------------------------------- |
| method           | String                        | Yes      | "chatMenuCallback"                                                                                       |
| chatMenuCallback | [ChatMenuCallback](#_2dlolyb) | Yes      | object represents an incoming callback query from a callback button associated with a normal keypad menu |

## Inline Message Callback
```javascript
const User = require("../data/User");
const Chat = require("../data/Chat");

module.exports = class InlineMessageCallback {


    constructor(jsonObj) {
        let obj = jsonObj.inlineMessageCallback;

        let fromUser = new User(obj.from);
        this.chat = obj.chat == null ? null : new Chat(obj.chat);
        let btnqueryResults = obj.button_query_result == null ? null
            : new ButtonQueryResult(obj.button_query_result);
        this.message_id = obj.message_id;
        this.menu_ref = obj.menu_ref;
        this.reference = obj.reference;
        this.from = fromUser;
        this.button_query_result = btnqueryResults;
        this.button_callback = obj.button_callback;
        this.date = obj.date;
    }

    toJsonObject(){
        let obj;

        if (this.date) obj.date = this.date;
        if (this.from) obj.from = this.from.toJsonObject();
        if (this.chat) obj.chat = this.chat.toJsonObject();
        if (this.message_id) obj.message_id = this.message_id;
        if (this.menu_ref) obj.menu_ref = this.menu_ref;
        if (this.reference) obj.reference = this.reference;
        if (this.button_callback) obj.button_callback =  this.button_callback;
        if (this.button_query_result) obj.button_query_result = this.button_query_result;

        return obj;

    }
}
```
Incoming message represents information about a clicked button within an inline keypad menu associated with a specific message

| Field                 | Type                              | Required | Description                                                                                                                         |
| --------------------- | --------------------------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| method                | String                            | Yes      | "inlineMessageCallback"                                                                                                             |
| inlineMessageCallback | [inlineMessageCallback](#_sqyw64) | Yes      | object represents an incoming callback query from a callback button within an inline keypad menu associated with a specific message |

## Chat Member
```javascript
module.exports = class ChatMember {

    constructor(jsonObj) {
        let obj = jsonObj.chatMember;
    
        this.user = obj.user == null ? null : new User(obj.user);
        this.chat = obj.chat == null ? null : new Chat(obj.chat);

        this.type = obj.type;
        this.member_since = obj.member_since;
        this.status = obj.status;
        this.tags = obj.tags;
        this.account_type = obj.account_type;
        this.msisdn = obj.msisdn;
    }
    
    toJsonObject(){
        let obj;

        if (this.user) obj.user = this.user.toJsonObject();
        if (this.chat) obj.chat = this.chat.toJsonObject();
        if (this.type) obj.type = this.type;
        if (this.member_since) obj.member_since = this.member_since;
        if (this.status) obj.status = this.status;
        if (this.tags) obj.tags =  this.tags;
        if ( this.account_type) obj.account_type = this.account_type;
        if (this.msisdn) obj.msisdn = this.msisdn;
        return obj;
    }

}
```

Incoming message represents information about group or channel member returned as a reply to [getChatMember](#_3mzq4wv) , [banChatMember](#_haapch), [unbanChatMember](#_319y80a), [removeChatMember](#_1gf8i83) and when user join or leaves the chat.

| Field      | Type                    | Required | Description                           |
| ---------- | ----------------------- | -------- | ------------------------------------- |
| method     | String                  | Yes      | "chatMember"                          |
| chatMember | [ChatMemebr](#_1rvwp1q) | Yes      | object represents a chat member user. |

## Chat Administrators
```javascript
const Chat = require("../data/Chat");
const User =  require("../data/User");

module.exports = class ChatAdministrators {
    
    constructor(jsonObj) {
        let obj = jsonObj.chatAdministrators;
        this.administrators = [];
        this.chat = obj.chat == null ? null : new Chat( obj.chat);

         let adminArrayObj = obj.administrators;
        if (adminArrayObj != null) {

            let admin = [];
            for (let i = 0; i < adminArrayObj.length; i++)
                admin[i] = new User(adminArrayObj[i]);

            this.administrators = admin; 
            
        }
        
    }

    toJsonObject(){
        let obj;
        if (this.administrators) {
            let adminsArrayObjnew = [];
            for (let i = 0; i < administrators.length; i++)
                adminsArrayObjnew.push(administrators[i].toJsonObject());
            obj.administrators = adminsArrayObjnew;
        }

        if (this.chat) {
            obj.chat =  chat.toJsonObject();
        }

        return obj;
    }
}
```
Incoming message represents information about group or channel administrators returned as a reply to [getChatAdministrators](#_2250f4o).

| Field              | Type                            | Required | Description                                             |
| ------------------ | ------------------------------- | -------- | ------------------------------------------------------- |
| method             | String                          | Yes      | "chatAdministrators"                                    |
| chatAdministrators | [ChatAdministrators](#_4bvk7pj) | Yes      | object represents channel or group administrator users. |

## My Profile

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
Incoming message represents Bot profile details , this will be come as a reply to [getMyProfiles](#_3ep43zb) outgoing message

| Field  | Type              | Required | Description                                |
| ------ | ----------------- | -------- | ------------------------------------------ |
| method | String            | Yes      | "myProfile"                                |
| user   | [User](#_3tbugp1) | Yes      | User object represents Bot profile details |


## Message Ack
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
Incoming message represents outbound message acknowledge.

| Field  | Type   | Required | Description                                                 |
| ------ | ------ | -------- | ----------------------------------------------------------- |
| method | String | Yes      | "myProfilemessageAck"                                       |
| ack    | Ack    | Yes      | Object represents outbound messages acknowledgment details. |



