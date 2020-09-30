---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - java
  - javascript
  - json

toc_footers:
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:

search: true
code_clipboard: true
---

# ![](../images/ic_home.svg) Introduction

The API/Bot allows you to easily create programs that interface with nandbox App ecosystem platform. nandbox API/Bots are special accounts created without a phone number, or email that run as third party applications to provide extra functionality by interfacing to nandbox App ecosystem platform. Users can interact with API/Bots by sending them messages, commands and inline requests. You control your API/Bots using WebSocket messages to nandbox API server.

# ![](../images/ic_setting.svg) How API/Bot works?

Users can interact with API/bots in two ways:

1. Send messages and commands to API/bots through a direct chat, by adding them to groups/channels, or associate them to your nandbox Apps. This is useful for example in automated chat bots, news bots, and/or integrating your nandbox&#39;s App to your backend systems.

1. Send requests directly from the input field by typing the bot&#39;s @handle and a query. This allows sending content from inline API/bots directly into any chat, group or channel within nandbox Apps.

Messages, commands and requests sent by users are passed to the software running on your servers where API/Bot is hosted. Our intermediary server handles all encryption and communication with the nandbox API/Bot for you. You communicate with this server via a WebSocket interface that offers a simplified version of the nandbox API/Bot.

## How do I create an API access or bot?

Creating API access or bot within nandbox is easy. In few steps, you can configure and publish your new bots using an interactive menu.

### Create API/Bot within your nandbox App

Login to your administrative portal of your nandbox App. Go to Bot Manager section and follow the instruction to create your first API/Bot as illustrated in the following screen.
![](../images/image002.png)
![](../images/image003.png)

There are some API/Bot are already implemented by third party vendors offered in the Bot marketplace, where you can add them to your nandbox App and determine their access level to the information within your App.
![](../images/image004.png)

### Create API/Bot within nandbox Messenger

Use nandbox Android App version 2.1.0 or later.
From Settings menu open "Bot Manager".
![](../images/image005.jpg)

Tap "+" to create a new bot.
![](../images/image006.png)

Enter your Bot title (Limited to 32 characters).
![](../images/image007.jpg)

1. Choose your bot type

- Choose "Business", if your bot is associated or will be for use by organization, or business.

- Choose "Individual" if bot will be for use by individual.
  ![](../images/image008.jpg)

Enter Bot Description: a short text of up to 120 characters, describing your bot. Users will see this text on the bot&#39;s profile page and when they share your bot with someone, this text is sent together with the link.

1. when they are about to join your bot.

1. Update your Bot Image

1. Enter "About" section:
   a short text of up to 512 characters, describing your bot. Users will see this text at the beginning of the conversation with the bot.

1. Give your bot a unique handle by providing your business email.
   ![](../images/image009.jpg)

Unlike others, we protect your business name from being reserved by others bots. Your bot unique handle will be matching your web domain name. For example, if your business domain name is XYZ.com your bot handle will be "xyz".

After you reserve and book your bot handle, you can configure the following options:

1. Inline: toggle [inline mode](https://core.telegram.org/bots/inline) for your bot.

1. Private: Private Bot will not appear in Bot index search. Admin must send the Bot link to the user to invite him/her to join the bot.

1. Filter: select which messages your bot will receive when added to a group. Choose from "none", "when mentioned", "posts" or "All".

![](../images/image010.jpg)

# ![](../images/ic_info.svg) Authorization Token

Once you&#39;ve created an API/bot, you can obtain the API/bot&#39;s token by opening the bot for edit/chat and click "Get token" from top right overflow menu. The authorization token and API Server URL link will be sent within the bot chat window. The information will be used to connect your API/bot to API Server.

![](../images/image011.png)
As the owner (creator) of the API/bot, you will have a chance to test the bot before publishing. As soon as the bot is tested successfully, you can publish the bot by pressing "publish" button. Within 24 hours, the bot will be published and available for bot public search index within your App only.

It is important to know that any change in the bot information will result the bot being unpublished, and the owner must publish his/her bot again to make it available for public search index.

```javascript
const TOKEN = "90091903321704167:0:pVB3qS7H3JBDVvxA9pRh4EQl8ObLVJ";
const config = {
  URI: "wss://w1.nandbox.net:5020/nandbox/api/",
  DownloadServer: "https://w1.nandbox.net:5020/nandbox/download/",
  UploadServer: "https://w1.nandbox.net:5020/nandbox/upload/",
};
```

<aside class="notice">
You must replace <code>TOKEN</code> in your bot code with the token you got earlier.
</aside>

# ![](../images/ic_search.svg) Bot Search Index

Your app users will be able to search bots title, description and username and join them. It is recommended for owners to use keywords within the title, description and handle to better represent their bot functionality for better exposure.
![](../images/image012.png)

# ![](../images/ic_favourite.svg) API Bot Features

## Keypad Menu Types

### Normal Keypad Menu

Whenever your bot sends a message, it can pass along a special keypad with predefined reply options. nandbox apps that receive the message will display your keypad to the user. Tapping any of the buttons will send the respective command. This way you can drastically simplify user interaction with your bot.
nandbox currently supports text and emoji for the buttons. Here are some custom keyboard examples:
![](../images/image013.png)

### Inline Keypad Menu

There are times when you would prefer to do things directly within the chat, such as when the user is changing settings, is choosing from a selection (e.g. voting) or flipping through search results. In such cases you can use Inline Keypads that are integrated directly into the messages they belong to.
When callback buttons are used, your bot can update its existing messages (or just the keyboard) so that the chat remains tidy.

![](../images/image014.png)

## Message Edit

Since Inline Keypad Menus do not send additional messages to the chat, it makes sense to give bots a way of manipulating existing messages, so that they don’t have to send a new message each time they need to update something. This helps reduce clutter and build more fluid interfaces. All updated and edited messages will be marked with a small edit icon.
![](../images/image015.png)

## API/Bot Types

### Chat API/Bot

Users can interact with chat bots directly by opening the API/bot chat, or indirectly by communicating with a bot within a group, channel, or App.

### Inline API/Bot

Users can interact with your bot via inline queries straight from the text input field in any chat, by typing the bot's handle and then a query.
Having received the query, your bot can return some results. As soon as the user taps one of them, it is sent to the user's currently opened chat. This way, users can request content from your bot in any of their chats, groups or channels.
![](../images/image016.jpg)

## API/Bot Filter

Bots are frequently added to groups and/or channels in order to augment communication between human users, e.g. by providing news, notifications from external services or additional search functionality. In order to insure that the bot is not receiving messages not intended for it, you can configure a bot filter.

A bot running with a filter will not receive all messages that people send to the group. Instead, it will only receive:

- Messages that are posted by admins (for Channels/App only)
- Replies to the bot&#39;s own messages.
- Service messages (people added or removed from the Group, etc.)
- All or none.

This allows the bot developer to save a on resources, since they won&#39;t need to process irrelevant messages.

API/Bots added as admins to groups, channels or your App have disabled filters by default (i.e. bot admins always receive all messages unless they have a filter).

## Deep link

nandbox API/bots have a deep linking mechanism that allows for passing additional parameters to a menu button to start a chat. The API/bot menu button has an optional chat field that, when pressed, will automatically open the chat and initialize the bot.

## Location and Mobile Number

Some API/bots need extra data from the user to work properly. For example, knowing the user&#39;s location helps provide more relevant geo-specific results. The user&#39;s phone number can be very useful for integrations with other services, like banks, etc.

API/Bots can ask a user for their **location** and **phone number** using special buttons. Note that both phone number and location request buttons will only work after the user accepts and grants permission for such service.

# ![](../images/ic_Api.svg) API/Bot

## Authentication

Each bot is given a unique authentication token. You can obtain the token through the "Get token" overflow menu from the API/bot chat. Obtaining a new token will cause any existing token to immediately expire.

<aside class="success">
Remember — a happy bot is an authenticated bot!
</aside>

## Sending Requests

Requests to nandbox Bot API are sent as JSON objects over a WebSocket session. In order to connect to the server, you need to obtain an authentication token first.

The Bot Server WebSocket URL format is:

`wss://<nandboxBotServer>:<port>/nandbox/api/`

The first request over the WebSocket method must be an authentication request. An example of an authentication request is as follows:

```json
{
  "method": "TOKEN_AUTH",
  "rem": true,
  "token": "90091784056528980:0:odIgBOQZ4lVpqSIuxpQlGzmse3hwsS"
}
```

If bot is successfully authenticated, you should receive a response like the following:

```json
{
  "method": "TOKEN_AUTH_OK",
  "name": "Hello World”, Bot",
  "ID": "90091784056528980",
  "reference": 15269906159119,
  "date": 1533216558322
}
```

After the bot is successfully authenticated it can send further requests.

## Uploading Media

Media files are uploaded using HTTP PUT. You must set the following HTTP headers in the upload request:

- " Content-type" = `"<File content type>"`
- "Authorization" = `"Bearer <Bot Token>"`

Example: Authorization = "Bearer 90091783861271726:0:4ydsafdsInS5VIl3R4psQpsad"

The Bot Server upload URL format is:
`https://<nandboxBotServer>:<port>/nandbox/upload/<filename>`

## Downloading Media

Media files are downloaded using HTTP GET. You must set the following HTTP headers in the download request.

- "Content-type" = application/json
- "Authorization" = `"Bearer <Bot Token>"`

Example: Authorization = "Bearer 90091783861271726:0:4ydsafdsInS5VIl3R4psQpsad"

The Bot Server download URL format is:

`**https://<nandboxBotServer>:<port>/nandbox/download/<file id>`

## Keypad Menu

### Sending Menu to Chat

For both Normal and Inline Keypad menus, the menu structure definition can be sent to chat in two ways:

1. separately with specific JSON, or
2. associated with specific message to the chat. The app will define the structure and associate the reference menu to that specific message.

### Using Menu

Every menu has a reference identifier. Menus can be called and used in many ways:

1. Associate menu reference with a specific message to chat. When you associate a menu reference to a message, the message will reference this menu. If the menu is already defined, it will be displayed as inline keypad menu.

2. Associate menu reference with "start menu button." When the user presses the start menu button, the menu will be displayed as normal menu.

3. Menus can also be referenced from any other menu button by defining the menu reference in "next_menu" field.

All keypad menus can be used online or offline. If the app is offline, the menu can still be used offline, since the definition for the menu structure is stored in the app. In that case, the menu can be used for browsing and deep linking to other chats.

### Menu Button Properties

Each menu is composed from a set of buttons with a set of properties. When the user provides formal input or click a button the app will send the respective command.

#### Button Call Back

Callback command is sent into "[Callback](#_2szc72q)" field when a button is pressed by the user. For example, the bot can use callback command as an identifier for this button action. It is the responsibility of the bot developer to keep unique callback commands for all defined buttons.

#### Button Inquiry

A button can query some information from the app with the permission of the user. Examples of supported button queries:

- Location: Ask user permission to inquire about geo-location and and if permission granted provide bot with geo-location coordinates of the device.
- Contact: Ask user permission to inquire about the mobile number and if permission granted provide bot with mobile number of the device.

#### Buttons URL

Bots can define Button URL. When the button is pressed, the URL link will be opened.

All buttons with a defined URL will have a small arrow icon to indicate that pressing this button will open an external link.

#### Button next menu

When the button is pressed, the app will display next menu referenced within that button. This function is a great help for designing browsing menus and offline menus.

# ![](../images/ic_incoming.svg) IncomingMessages

Your bot must be connected and authenticated over the WebSocket session to receive incoming messages. The Bot Server does not store any messages for bots for later retrieval.

The following table lists the different incoming JSON messages for the bot.

## Incoming Messages

## Message

```json
{
  "method": "message",
  "message": {
    "date": 1600168078602,
    "reference": 2097,
    "chat": {
      "name": "Amir Salah",
      "id": "90089668723575679",
      "terminal": "Mobile",
      "type": "Contact",
      "version": "('0HNt','1QBk','2c2H','31RN')"
    },
    "sent_to": { "id": "90091903321704167" },
    "message_id": "i1_CD11KwDr126551",
    "style": 0,
    "from": {
      "name": "Amir Salah",
      "id": "90089668723575679",
      "terminal": "Mobile",
      "type": "Contact",
      "version": "('0HNt','1QBk','2c2H','31RN')"
    },
    "text": "Hello",
    "type": "text"
  }
}
```

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

```json
{
  "method": "chatMenuCallback",
  "chatMenuCallback": {
    "date": 1600588639278,
    "button_callback": "VCB0",
    "next_menu": null,
    "button_query_result": null,
    "chat": { "id": "90089668723575679", "type": "Mobile" },
    "from": { "id": "90089668723575679", "type": "Mobile" },
    "menu_ref": "ThirdMenu",
    "button_label": "الفاتحة"
  }
}
```

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

    "status": "Bot Status"
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

# ![](../images/ic_Types.svg) Types

Capitalized types are data structures represented as JSON objects. The different types in incoming messages are listed below.

File identifiers in the Photo, Sticker, GIF, Video, Audio, Voice, Document and Text_File document can be used to download the actual file, see Section 4.4

It is safe to use 32-bit signed integers for storing all **Integer** fields unless otherwise noted.

**Long** fields are sent as Strings to avoid problems with JavaScript based clients.

**Optional** fields may be not returned when not relevant.

## User

This object represents a nandbox user or bot account.

| Field    | Type    | Required | Description                                                                                                                                            |
| -------- | ------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| id       | String  | Yes      | Unique identifier for this user or bot                                                                                                                 |
| name     | String  | Yes      | User or bot name.                                                                                                                                      |
| version  | String  | Yes      | Last updated user profile version.                                                                                                                     |
| terminal | String  | Optional | Mobile if it is sent from mobile, API if it is sent from API. It will returned only if the user object come inside incoming [message](#_32hioqz)       |
| type     | String  | Optional | Contact if it is sent from normal user, Bot if it is sent from Bot. It will returned only if the user object come inside incoming [message](#_32hioqz) |
| is_bot   | Boolean | Optional | True if this user is a bot. Returned only in GetUser                                                                                                   |
| status   | String  | Optional | User status. Returned only in GetUser ,                                                                                                                |
| photo    | Photo   | Optional | Public user&#39;s Photo. Returned only in GetUser                                                                                                      |
| profile  | String  | Optional | Profile type "Other" , "Friend" , "Work" or "Family"                                                                                                   |

## Chat

This object represents a nandbox group or channel information

| Field          | Type                                       | Required    | Description                                                                                                               |
| -------------- | ------------------------------------------ | ----------- | ------------------------------------------------------------------------------------------------------------------------- |
| id             | String                                     | Yes         | Unique identifier for Group or Channel.                                                                                   |
| title          | String                                     | Yes         | Optional. title for Group or Channel                                                                                      |
| type           | String                                     | Yes         | "Group" , "Channel" "Contact" Or "Bot"                                                                                    |
| version        | String                                     | Yes         | Last updated Group or Channel profile version.                                                                            |
| language_code  | Integer                                    | Optional    | [IETF language tag](https://en.wikipedia.org/wiki/IETF_language_tag) of the main Chat language. Returned only in getChat. |
| Regions        | String                                     | Optional    | Allowed region, if it is null means "All". Returned only in getChat.                                                      |
| description    | String                                     | Optional    | Chat Description. Returned only in getChat.                                                                               |
| photo          | Photo                                      | Optional    | Chat Photo. Returned only in getChat.                                                                                     |
| category       | String                                     | Optional    | Chat category. Returned only in getChat.                                                                                  |
| member_count   | Integer                                    | Optional    | Total Chat members count. Response only in getChat.                                                                       |
| invite_link    | String                                     | Optional    | Chat invite link. Returned only in getChat.                                                                               |
| tagsDefinition | Array of [TagDefinition](#_Tag_Defination) | Conditional | List of "tag definition"                                                                                                  |

## Message

The main message method defines all parameters for all incoming messages to the bot.

| Field               | Type                         | Required    | Description                                                                                                                                                                                                                                                                                                                                                                                                     |
| ------------------- | ---------------------------- | ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| message_id          | String                       | Yes         | Unique identifier for this message.                                                                                                                                                                                                                                                                                                                                                                             |
| Referencereference  | StringLong                   | yes         | Unique local identifier                                                                                                                                                                                                                                                                                                                                                                                         |
| Chatchat            | [Chat](#_Chat)               | Yes         | Conversation the message belongs to.                                                                                                                                                                                                                                                                                                                                                                            |
| Fromfrom            | User                         | Yes         | Sender User of this message                                                                                                                                                                                                                                                                                                                                                                                     |
| sent_to             | User                         | Yes         | Receiver user, most of the case it is the bot ID except if channel has multiple administrators, it will be the specific admin who should receive the message.                                                                                                                                                                                                                                                   |
| type                | String                       | Yes         | "text": For text messages "text_file": Message is a text tile. Any message exceeds 1800 characters will be converted to text file. "photo":Message is a photo."gif": Message is a GIF"sticker": Message is a sticker."video": Message is a video"audio": Message is an audio"voice": Message is a voice note "location": Message is a location"contact": Message is a contact "document": Message is a document |
|                     |
| Date                | Long                         | Yes         | Date the message was sent in Unix Epoch timestamp in milliseconds.                                                                                                                                                                                                                                                                                                                                              |
| reply_to_message_id | String                       | Optional    | Parent message Unique identifier.                                                                                                                                                                                                                                                                                                                                                                               |
| from_admin          | Integer                      | Optional    | 1 if from user is admin, otherwise it is 0                                                                                                                                                                                                                                                                                                                                                                      |
| Text                | String                       | Conditional | Only available when type is text                                                                                                                                                                                                                                                                                                                                                                                |
| text_file           | Text_File                    | Conditional | Only available when type is text_file                                                                                                                                                                                                                                                                                                                                                                           |
| Photo               | Photo                        | Conditional | Only available when type is photo                                                                                                                                                                                                                                                                                                                                                                               |
| Gif                 | GIF                          | Conditional | Only available when type is gif                                                                                                                                                                                                                                                                                                                                                                                 |
| Sticker             | Sticker                      | Conditional | Only available when type is sticker                                                                                                                                                                                                                                                                                                                                                                             |
| Video               | Video                        | Conditional | Only available when type is video                                                                                                                                                                                                                                                                                                                                                                               |
| Audio               | Audio                        | Conditional | Only available when type is audio                                                                                                                                                                                                                                                                                                                                                                               |
| Voice               | Voice                        | Conditional | Only available when type is voice                                                                                                                                                                                                                                                                                                                                                                               |
| Document            | Document                     | Conditional | Only available when type is document                                                                                                                                                                                                                                                                                                                                                                            |
| Location            | Location                     | Conditional | Only available when type is location                                                                                                                                                                                                                                                                                                                                                                            |
| Contact             | Contact                      | Conditional | Only available when type is contact                                                                                                                                                                                                                                                                                                                                                                             |
| Status              | String                       | Optional    | "deleted" if messages is recalled and "updated" if it is updated.                                                                                                                                                                                                                                                                                                                                               |
| chat_settings       | Integer                      | Optional    | 1 if from chat settings bot, otherwise it is 0                                                                                                                                                                                                                                                                                                                                                                  |
| caption             | String                       |
|                     |
|                     |
| bg_color            | String                       |
|                     |
|                     |
| article             | Article                      |
|                     |
|                     |
| url                 | String                       |
|                     |
|                     |
| White_list_user     | [WhiteListUser](#_Whitelist) |
|                     |
|                     |
| tag                 | TagDefinition                |
|                     |
|                     |
| schedule_date       | Long                         | Optional    | Long time format like this example 1579102262                                                                                                                                                                                                                                                                                                                                                                   |

**JSON Example:**

```json
{
  "method": "message",

  "message": {
    "date": 1512445910180,

    "gif": {
      "thumbnail": {
        "width": 256,

        "id": "cfdb3cc5.gif.thumb.jpg",

        "height": 191
      },

      "size": 4136640,

      "width": 443,

      "id": "02505e8f5e01aff254904853.gif",

      "height": 332
    },

    "chat": {
      "name": "chat 1",

      "id": "4522291356145774",

      "type": 0
    },

    "message_id": "d2_QhlW1MAH12617138",

    "from": {
      "name": "John Smith",

      "id": "4521191845180798",

      "type": 0,

      "version": "(&#39;0hn0&#39;,&#39;1YDA&#39;,&#39;2ViB&#39;,&#39;32Fg&#39;)"
    },

    "type": "gif"
  }
}
```

## Text

This object represents Text entry.

| Field                                                | Type   | Required | Description                                                                                                       |
| ---------------------------------------------------- | ------ | -------- | ----------------------------------------------------------------------------------------------------------------- |
| Text                                                 | String | Yes      | The actual UTF-8 text of the message, 0-1800 characters.                                                          |
|                                                      |
| bg_color                                             | String | Optional | Text message Background color name in hexadecimal format (Hex triplet ) or according to its common English name . |
| Example : Red color can be set as "RED" or "#FF0000" |

## Photo

This object represents one size of a photo and/or thumbnail.

| Field     | Type    | Required | Description                     |
| --------- | ------- | -------- | ------------------------------- |
| id        | String  | Yes      | Unique identifier for this file |
| width     | Integer | Yes      | Photo width                     |
| height    | Integer | Yes      | Photo height                    |
| size      | Integer | Optional | Photo size                      |
| thumbnail | Photo   | Optional | Thumbnail of the photo          |

## GIF

This object represents GIF image.

| Field     | Type    | Required | Description                     |
| --------- | ------- | -------- | ------------------------------- |
| id        | String  | Yes      | Unique identifier for this file |
| width     | Integer | Yes      | GIF width                       |
| height    | Integer | Yes      | GIF height                      |
| size      | Integer | Optional | GIF size                        |
| thumbnail | Photo   | Optional | Thumbnail of the photo          |

## Sticker

This object represents Sticker Photo.

| Field     | Type    | Required | Description                        |
| --------- | ------- | -------- | ---------------------------------- |
| id        | String  | Yes      | Unique identifier for this sticker |
| width     | Integer | Optional | Sticker width                      |
| height    | Integer | Optional | Sticker height                     |
| size      | Integer | Optional | Sticker size                       |
| thumbnail | Photo   | Optional | Thumbnail of the photo             |

## Video

This object represents a video file.

| Field     | Type    | Required | Description                       |
| --------- | ------- | -------- | --------------------------------- |
| id        | String  | Yes      | Unique identifier for this file   |
| width     | Integer | Yes      | Video width                       |
| height    | Integer | Yes      | Video height                      |
| duration  | Integer | Yes      | Duration of the video in seconds. |
| size      | Integer | Yes      | Video size                        |
| thumbnail | Photo   | Optional | Video thumbnail                   |

## Audio

This object represents a audio file.

| Field     | Type    | Required | Description                                                           |
| --------- | ------- | -------- | --------------------------------------------------------------------- |
| id        | String  | Yes      | Unique identifier for this file                                       |
| duration  | Integer | Yes      | Duration of the audio file                                            |
| performer | String  | Optional | Performer of the audio as defined by sender or by audio tags.         |
| title     | String  | Optional | Title of the audio of the audio as defined by sender or by audio tags |
| size      | Integer | Yes      | Audio file size                                                       |

## Voice

This object represents a voice note.

| Field    | Type    | Required | Description                     |
| -------- | ------- | -------- | ------------------------------- |
| id       | String  | Yes      | Unique identifier for this file |
| duration | Integer | Yes      | Duration of the voice note.     |
| size     | Integer | Yes      | Voice file size.                |

## Document

This object represents a general file (as opposed to photos, voice messages and audio files).

| Field | Type    | Required | Description                         |
| ----- | ------- | -------- | ----------------------------------- |
| id    | String  | Yes      | Unique identifier for this file     |
| name  | Integer | Optional | Document name as defined by Sender. |
| size  | Integer | Yes      | Document file size.                 |

## Text_File

This object represents a text file.

| Field |
| Type | Required | Description |
| --- | --- | --- | --- | --- |
| Id |
| String | Yes | Unique identifier for this file |
| size |
| Integer | Yes | File size. |

## Location

This object represents a point on the map.

| Field     | Type   | Required | Description      |
| --------- | ------ | -------- | ---------------- |
| longitude | String | Yes      | longitude        |
| Latitude  | String | Yes      | latitude         |
| name      | String | Optional | Location name    |
| details   | String | Optional | Location details |

## Contact

This object represents a phone contact.

| Field        | Type   | Required | Description                |
| ------------ | ------ | -------- | -------------------------- |
| phone_number | String | Yes      | Contact&#39;s phone number |
| Name         | String | Yes      | Contact full name          |

## ChatMenuCallback

This object represents an incoming callback query from a callback button associated with a normal keypad menu.

| Field               | Type              | Required | Description                                                                                                                                                                                  |
| ------------------- | ----------------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| button_callback     | String            | Yes      | Unique identifier for button as defined by bot.                                                                                                                                              |
| menu_ref            | String            | Yes      | Menu Unique identifier defined by bot where button belongs to.                                                                                                                               |
| from                | User              | Yes      | Sender User who pressed the button.                                                                                                                                                          |
| chat                | Chat              | Yes      | Conversation the message belongs to.                                                                                                                                                         |
| date                | Long              | Yes      | Long date format in milliseconds                                                                                                                                                             |
| next_menu           | IntegerString     | Optional | The menu to navigate to it when the button pressed.                                                                                                                                          |
| button_query_result | ButtonQueryResult | Optional | Returned inquiry information from app. The field either will return "Location" in form of longitude and latitude respectively as comma separated. "Phone number" depends on the buttonQuery. |

## InlineMessageCallback

This object represents an incoming callback query from a callback button within an inline keypad menu associated with a specific message. If the button that originated the query was attached to a message sent by the bot, the field message_id will be present.

| Field               | Type              | Required | Description                                                                                                                                                                                  |
| ------------------- | ----------------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| button_callback     | String            | Yes      | Callback Unique identifier as defined by bot.                                                                                                                                                |
| menu_ref            | String            | Yes      | Menu reference                                                                                                                                                                               |
| from                | User              | Yes      | Sender User of the message                                                                                                                                                                   |
| chat                | Chat              | Yes      | Conversation the message belongs to.                                                                                                                                                         |
| message_id          | String            | Yes      | Associated message Global Unique identifier where the menu belong to.                                                                                                                        |
| reference           | long              | Yes      | Associated message Unique local identifier as defined by the bot.                                                                                                                            |
| date                | Long              | Yes      | Long date format in milliseconds                                                                                                                                                             |
| next_menu           | Integer           | Optional | The menu to navigate to it when the button pressed.                                                                                                                                          |
| button_query_result | ButtonQueryResult | Optional | Returned inquiry information from app. The field either will return "Location" in form of longitude and latitude respectively as comma separated. "Phone number" depends on the buttonQuery. |
| button_label        | String            | Optional | Button label                                                                                                                                                                                 |

## InlineSearch

```json
{
  "method": "inlineSearch",
  "inlineSearch": {
    "date": 1600589339535,
    "keywords": "فتح",
    "chat": { "id": "90089668723575679", "type": "Mobile" },
    "from": { "id": "90089668723575679", "type": "Mobile" },
    "search_id": 1589060
  }
}
```

This object represents InlineSearch

| Field     | Type    | Required | Description                          |
| --------- | ------- | -------- | ------------------------------------ |
| date      | Long    | Yes      | Long date format in milliseconds     |
| keywords  | String  | yes      | Search keyword                       |
| chat      | Chat    | Yes      | Conversation the message belongs to. |
| from      | User    | Yes      | Sender User of the message           |
| search_id | Integer | Yes      | Unique search id for this message    |
| offset    | String  | Optional | Offset of the results to be returned |

## Results

| Field       | Type   | Required | Description                                                             |
| ----------- | ------ | -------- | ----------------------------------------------------------------------- |
| thumb_url   | String | Optional | URL of Thumbnail of the media                                           |
| caption     | String | Optional | Caption of the media                                                    |
| description | String | Optional | Description of the media .                                              |
| title       | String | Optional | Title of the media                                                      |
| type        | String | Yes      | Type of media file like text, image , video , gif_image, gif_video etc. |
| url         | String | yes      | Download URL of media file                                              |
| width       | Long   | Optional | Width of thumbnail image                                                |
| height      | Long   | Optional | Height if thumbnail image                                               |

## Tag Defination

| Field       | Type    | Required | Description              |
| ----------- | ------- | -------- | ------------------------ |
| name        | String  | yes      | The name of tag          |
| description | String  | yes      | Description of tag       |
| id          | String  | yes      | Id of tag                |
| isPrivate   | Integer | yes      | 1= private 0= no private |

## Users

| Field       | Type            | Required | Description      |
| ----------- | --------------- | -------- | ---------------- |
| signup_user | String          | yes      | Add signup user  |
| tags        | Array of String | Optional | Add list of tags |

## Data

| Field   | Type   | Required | Description                         |
| ------- | ------ | -------- | ----------------------------------- |
| pattern | String | yes      | Add pattern for black or white list |
| example | String | yes      | Add example of pattern              |

## Signup User

| Field       | Type            | Required | Description                          |
| ----------- | --------------- | -------- | ------------------------------------ |
| id          | String          | yes      | Id of signup user                    |
| signup_user | String          | yes      | Signup user (mobile number or email) |
| tags        | Array of String | Optional | Only when you have tags in whitelist |

## ButtonQueryResult

This object represents an incoming button query results from a callback button

| Field     | Type   | Required | Description                                       |
| --------- | ------ | -------- | ------------------------------------------------- |
| latitude  | String | Optional | Only sent in case of buttonQuery is location      |
| longitude | String | Optional | Only sent in case of buttonQuery is location      |
| contact   | String | Option   | Only sent in case of buttonQuery is phone_number. |

## Chat Member

This object represents a chat member user returned in getChatMember banChatMember, unbanChatMember, removeChatMember and when user join or leaves the chat.

| Field                                      | Type            | Required                                                          | Description                                                                                                                                                                           |
| ------------------------------------------ | --------------- | ----------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| user                                       | User            | Yes                                                               | Member User Unique identifier                                                                                                                                                         |
| chat                                       | Chat            | Yes                                                               | Chat Unique identifier where member belongs or used to belongs to.                                                                                                                    |
| type                                       | String          | Yes                                                               | "member" if user is a member, "admin" if user is an admin.                                                                                                                            |
| member_since                               | Timestamp       | Optional                                                          | Unix Epoch timestamp.                                                                                                                                                                 |
| status                                     | String          | Yes                                                               | "active": where user is an active member in the Chat"deleted" : where user has been deleted from Chat."banned": when user has been banned from Chat."left" : when user left the Chat. |
| tags                                       | Array of String | Optional                                                          | List of tags id if user have tags                                                                                                                                                     |
| account_type                               | String          | OptionalMust have specific privilege from Web (Get User Login ID) |
| Type for which user signup(email , msisdn) |
| msisdn                                     | String          | Optional                                                          | Get email or msisdn                                                                                                                                                                   |

**JSON Example:**

```json
"chatMember": {

"view": 0,

"chat": {

"id": "90090684265189649",

"type": "Channel"

},

"tester": 0,

"type": "Member",

"user": {

"id": "90089585281071029"

},

"tags": ["1",

"2"],

"status": "Active"

},

"method": "chatMember"

}

{

"chatMember":{

"user":{

"id":"4521191845180798"

},

"chat":{

"id":"4522291356145774"

},

"type":"Admin",

"status":"Active",

"member_since":1512440093000

},

"method":"chatMember"

}
```

## Chat Administrators

This object represents channel or group administrator users. Returned as a reply to [getChatAdministrators](#_2250f4o)

| Field          | Type                       | Required | Description                                                                |
| -------------- | -------------------------- | -------- | -------------------------------------------------------------------------- |
| chat           | [Chat](#_28h4qwu)          | Yes      | channel or group Unique identifier object where administrators belongs to. |
| administrators | Array of [User](#_3tbugp1) | Yes      | List of All administrator users of this channel or group.                  |

**JSON Example:**

```json
{
  "chatAdministrators": {
    "chat": {
      "id": "90090684268836495"
    },

    "administrators": [
      {
        "id": "90089584770196915"
      },

      {
        "id": "90091783798510047"
      },

      {
        "id": "90091783950702380"
      },

      {
        "id": "90091783958740938"
      }
    ]
  },

  "method": "chatAdministrators"
}
```

## Blacklist

This object represents blacklist. Returned as a reply to [getBlacklist](#_Get_Blacklist)

| Field | Type                     | Required | Description                                                                |
| ----- | ------------------------ | -------- | -------------------------------------------------------------------------- |
| chat  | [Chat](#_28h4qwu)        | Yes      | channel or group Unique identifier object where administrators belongs to. |
| eop   | String                   | Yes      | Number of page                                                             |
| users | Array of UsersSignupUser | Yes      | Array of users                                                             |

**JSON Example:**

```json
{
  "method": "blacklist",

  "blacklist": {
    "chat": {
      "id": "90090684293612221"
    },

    "eop": "19",

    "users": [
      {
        "id": "2",

        "signup_user": "201116601107"
      },

      {
        "id": "4",

        "signup_user": "201116601109"
      },

      {
        "id": "5",

        "signup_user": "201116601111"
      },

      {
        "id": "14",

        "signup_user": "1111111"
      },

      {
        "id": "15",

        "signup_user": "222222"
      },

      {
        "id": "19",

        "signup_user": "222223"
      }
    ]
  }
}
```

## Whitelist

This object represents whitelist. Returned as a reply to [getWhitelist](#_Get_Blacklist)

| Field | Type                 | Required | Description                                                                |
| ----- | -------------------- | -------- | -------------------------------------------------------------------------- |
| chat  | [Chat](#_28h4qwu)    | Yes      | channel or group Unique identifier object where administrators belongs to. |
| eop   | String               | Yes      | Number of page                                                             |
| users | Array of SignupUsers | Yes      | Array of users                                                             |

**JSON Example:**

```json
{
  "method": "whitelist",

  "whitelist": {
    "chat": {
      "id": "90090684293612221"
    },

    "eop": "13",

    "users": [
      {
        "id": "1",

        "signup_user": "11111",

        "tags": ["1", "2"]
      },

      {
        "id": "2",

        "signup_user": "22222",

        "tags": ["1", "2", "4"]
      },

      {
        "id": "8",

        "signup_user": "222223"
      },

      {
        "id": "9",

        "signup_user": "9999999"
      },

      {
        "id": "11",

        "signup_user": "6666666"
      },

      {
        "id": "13",

        "signup_user": "3636526",

        "tags": ["1", "2"]
      }
    ]
  }
}
```

## Message Acknowledge

Object represents outbound messages acknowledgment details.

| Field      | Type   | Required | Description                                                       |
| ---------- | ------ | -------- | ----------------------------------------------------------------- |
| reference  | Long   | Yes      | Unique local identifier for the original message.                 |
| message_id | String | Yes      | Global Unique identifier for the original message.                |
| date       | Long   | Yes      | Date the message was sent in Unix Epoch timestamp in milliseconds |

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

## Started Bot

This object represents a user, Returned when user started bot

| Field | Type | Required | Description                   |
| ----- | ---- | -------- | ----------------------------- |
| user  | User | Yes      | Member User Unique identifier |

**JSON Example:**

```json
{
  "method": "userStartedBot",

  "user": {
    "id": "4521191845180798"
  }
}
```

## User Joined Bot

This object represents a user, Returned when user joined bot

| Field | Type | Required | Description                   |
| ----- | ---- | -------- | ----------------------------- |
| user  | User | Yes      | Member User Unique identifier |

**JSON Example:**

```json
{
  "method": "userJoinedBot",

  "user": {
    "id": "4521191845180798"
  }
}
```

## User Stopped Bot

This object represents a user, Returned when user stopped bot

| Field | Type | Required | Description                   |
| ----- | ---- | -------- | ----------------------------- |
| user  | User | Yes      | Member User Unique identifier |

**JSON Example:**

```json
{
  "method": "userStoppedBot",

  "user": {
    "id": "90089584801498185"
  }
}
```

## User Left Bot

This object represents a user, Returned when user left bot

| Field | Type | Required | Description                   |
| ----- | ---- | -------- | ----------------------------- |
| user  | User | Yes      | Member User Unique identifier |

**JSON Example:**

```json
{
  "method": "userLeftBot",

  "user": {
    "id": "90089584801498185"
  }
}
```

## Inline Search

This object represents an inline search, Returned when user write search keyword in inline bot

| Field       | Type                           | Required | Description                   |
| ----------- | ------------------------------ | -------- | ----------------------------- |
| method      | String                         | yes      | "inlineSearch"                |
| inineSearch | [InlineSearch](#_InlineSearch) | Yes      | Member User Unique identifier |

**JSON Example:**

```json
{
  "method": "inlineSearch",

  "inlineSearch": {
    "date": 1559491192232,

    "keywords": "hi",

    "chat": {
      "id": "90089585282313728",

      "type": "Mobile"
    },

    "from": {
      "id": "90089585282313728",

      "type": "Mobile"
    },

    "search_id": 3329
  }
}
```

## User

| Field | Type | Required | Description                   |
| ----- | ---- | -------- | ----------------------------- |
| user  | User | Yes      | Member User Unique identifier |

**JSON Example:**

```json
{

"method": "user",

"user": {

"image": "\/9j\/4AAQSkZJRgABAQAAAQABAAD\/2wBDABsSFBcUERsXFhceHBsgKEIrKCUlKFE6PTBCYFVlZF9V\nXVtqeJmBanGQc1tdhbWGkJ6jq62rZ4C8ybqmx5moq6T\/2wBDARweHigjKE4rK06kbl1upKSkpKSk\npKSkpKSkpKSkpKSkpKSkpKSkpKSkpKSkpKSkpKSkpKSkpKSkpKSkpKSkpKT\/wAARCABpAGkDASIA\nAhEBAxEB\/8QAGQAAAwEBAQAAAAAAAAAAAAAAAgMEBQEA\/8QANBAAAgIBAwIEAwYFBQAAAAAAAQIA\nAxEEITESQSJRYXETFIEFMjNSkaEjJDRysTVCYpLR\/8QAGAEBAQEBAQAAAAAAAAAAAAAAAgEAAwT\/\nxAAdEQEBAQEAAgMBAAAAAAAAAAAAARECEjEDIUFR\/9oADAMBAAIRAxEAPwCnuYi2+tNhuYWqYrUc\ncnaZh6snbM48z9dqpa+wnYDE91ty3HrJlsIGCM+kMEN6enadBUqosGFYZ8oLK42KmK8SnIl9bGyo\nE8jvFOqliF1PkYvBzxLjAMWhieDKSBEWDxfWc7DlPTvKK+JPX3lNfEc9BfZWt\/A+omdtNHUrZYOh\nVyvnJvlLPy\/vOk6kTxtWarHwxmQ7SzW\/hD3kgX0+s83Pp2rgUeUalWCDDrqxuYWQp3MrKNPpksHi\ng69Pk9IGrO\/Vg5jNPdWD0538sRP2zaraPpDZPUJY1Z665icOB7iPVw4yrAiZTbTqWsh6lMTm1cmK\nsBzmcou+KmcbjmO+E7jKiaxpaKvvKK+IpanHIjkBAwZYlEFJ4BPtPdJ8jHVjwrkDmHkeQ\/SbWxDq\n16qGx23kqkNhwRtyJoYzJKqDVbZ3U8ThzXamg7T1dCWthp3IgLb0sW5AjZ41JRql6ePKSfaKCu7o\nBJGOrc95RWBfaXLkb5kGuuFuodgcrnAPoIoNTsIPTCG5Al2mpU0MWUHeUYn0Jw7L5iaI6yB0nG0S\nlSV\/dUCUJz9Jak9p7NRbW\/SRv7wPm38v3nbgTqWxjjvPCtz+X9JMbWppmJorJ7rmNyYuoYrQeSiM\nmUsCJPJlIRsZ3GfOC1RYcKwg5+P9K95We1pUnuJxXDHY7HmVNpVJ3Vl\/cT1mmGn01jICWxsRF42J\n5SotVctNHQhw7nB37TMYzZ1f2dZqFS1ehLCPECefWQP9l6oDIQN\/awlwbU9JzYAZqacH4BwM53mZ\nTWwswQR2M19M9agL1jPkZKUKzGqf8QdSFFmV4InU4HtLRzKi1R\/mG+kWCSRC1RxqGg1DqsUeZE0Z\nvLtt5ACFAB8RhZlY7rY+UWwUnqCjPfbeHBLYYH9Y4ALKrlwarMg\/7X3\/AHhI9qKPiBR4sHHaGXDd\nJHEF8MXU8ESo4KmQkDLKTkf8T\/5PWIUrLA8HM7VZlME5I2PrGHDoV8xiZkL0pazEDx4zt3Ekt03i\nVg2MS+vCHqOxCkRep07Ei1e43ENhSpNQ2Co9IyvdQfSIZC5xyRKaqQ1akkjbicz9\/aDVIxvJCkic\n0qP8zXlTjqE0\/l1\/MZ1KArg5OxmY5RyfWHODidiQefSJssGM9vPiMsOQF7E7yUOtjFuR29orcSTT\nK7BsM8RnX\/FT1k7V+UFSyuCcnEk7W8fw8nosz5bH2jwcbiSvYrHIjFfw88RaGO34VHftOUXCzYmJ\ne8FSB0nfcGJNyjxJsfKTyLxN1FHQ5deDz6TivlfC2MQ67www0VqakC5DBQfOGxoLrf8AOP0hVOzW\nYJB+kzQy1ucP1Z2lehI6ue0Br14E7BGw84UYkam8DTNYp5Xw+5mbp9QawFbcdo0\/6VX7j\/MjMWSw\ndxopqeoZ3xGrcp7iZ1X3RCE53l0nWtDKGASC3Qm7YzzxJRxD039Sf7JJFteOnOfGWHtGfKZ4fH0l\nBnRxHPoKmGnur32YehnEsF3Uj4CkdzKbPvp7GZVf4495dRQdHpc5wP8AsYwLUg8JH6z0B+JMjSjp\n1I8Sk7A7GO+MPzCZlPDe8bMr\/9k=\n",

"name": "Shawmi dev",

"photo": {

"thumbnail": {

"width": 120,

"id": "V_0rbN_90089584980037358_0_Fcs3Z4qxaq.jpg.thumb.jpg",

"height": 120

},

"width": 256,

"id": "V_0rbN_90089584980037358_0_Fcs3Z4qxaq.jpg",

"height": 256

},

"id": "90089584980037358",

"is_bot": false,

"version": "0rbN",

"status": "

}

}
```

## SetChatMenu_ack

This object represents acknowledgement of receipt new or updated normal keypad menu in returned for setChatMenu.

| Field | Type | Required | Description                           |
| ----- | ---- | -------- | ------------------------------------- |
| chat  | Chat | Yes      | Conversation Chat which menu send to. |

**JSON Example:**

```json
{
  "method": "setChatMenu_ack",

  "chat": {
    "id": "4522291356145774"
  }
}
```

# ![](../images/ic_outcoming.svg) Outgoing Messages

## Send Message

```javascript
// below is an example that sends a button on receiving a message
nCallBack.onReceive = (incomingMsg) => {
  // send a button on receiving a message

  // construct the outgoing message
  let outmsg = new TextOutMessage();
  const reference = Id();
  outmsg.chat_id = incomingMsg.chat.id;
  outmsg.reference = reference;
  outmsg.text = "https://edition.cnn.com/";
  outmsg.web_page_preview = OutMessage.WEB_PREVIEW_INSTANCE_VIEW;
  outmsg.echo = 1;

  let menuRef = MAIN_MENU_001;
  let oneBtn = createButton(
    "",
    "oneBtnCBInWebView",
    1,
    "RED",
    "White",
    null,
    null
  );
  oneBtn.button_icon = "ic_ball_ic_24dp";
  oneBtn.button_icon_bgcolor = "#FFFF44";

  let buttons = [];
  buttons.push(oneBtn);

  // a row is an array of buttons
  let rowOrder = 1;
  let firstRow = new Row(buttons, rowOrder);
  let rows = [];
  rows.push(firstRow);

  // a menu is an array of rows
  let inlineMenu = [];
  let firstInlineMenu = new Menu(rows, menuRef);
  inlineMenu.push(firstInlineMenu);

  // the outgoing message in this case contains an inline menu
  outmsg.menu_ref = menuRef;
  outmsg.inline_menu = inlineMenu;

  // send the outgoing message to the server
  api.send(JSON.stringify(outmsg));
};

// use the following function to create your buttons
let createButton = (
  label,
  callback,
  order,
  bgColor,
  txtColor,
  buttonQuery,
  nextMenuRef
) => {
  let btn = new Button();

  btn.button_label = label;
  btn.button_order = order;
  btn.button_callback = callback;
  btn.button_bgcolor = bgColor;
  btn.button_textcolor = txtColor;
  btn.button_query = buttonQuery;
  btn.next_menu = nextMenuRef;

  return btn;
};
```

```json
{
  "method": "sendMessage",
  "chat_id": "90089668723575679",
  "reference": 6096600070010,
  "text": "https://edition.cnn.com/",
  "echo": 1,
  "menu_ref": "MAIN_MENU_001",
  "inline_menu": [
    {
      "menu_ref": "MAIN_MENU_001",
      "rows": [
        {
          "row_order": 1,
          "buttons": [
            {
              "button_label": "",
              "button_order": 1,
              "button_callback": "oneBtnCBInWebView",
              "button_bgcolor": "RED",
              "button_textcolor": "White",
              "button_query": null,
              "next_menu": null,
              "button_icon": "ic_ball_ic_24dp",
              "button_icon_bgcolor": "#FFFF44"
            }
          ]
        }
      ]
    }
  ]
}
```

| Field                    | Type          | Required | Description                                                                                                       |
| ------------------------ | ------------- | -------- | ----------------------------------------------------------------------------------------------------------------- |
| method                   | String        | Yes      | "SendMessage"                                                                                                     |
| chat_id                  | String        | Yes      | Unique identifier for the target chat or User_id                                                                  |
| text                     | String        | Yes      | Text to send                                                                                                      |
| disable_web_page_preview | Boolean       | Optional | Disables link previews for links in this message                                                                  |
| disable_notification     | Boolean       | Optional | Sends the message silently. Users will receive a notification with no sound.                                      |
| reply_to_message_id      | String        | Optional | If the message is a reply, unique identification for the original (parent) message.                               |
| reference                | long          | Yes      | Unique local identifier for the message.                                                                          |
| to_user_id               | String        | Optional | if reply or send message to target user within a group chat or channel, unique identifier of the target user.     |
| echo                     | Integer       | Optional | 1= of sent message                                                                                                |
|                          |
| menu_ref                 | String        | Optional | Menu reference for existing predefined Menu. The menu will be displayed as inline menu associated to the message. |
| inline_menu              | Array of Menu | Optional | Inline menu object to hold menus.If both inline_menu and menu_ref are defined. Priority for inline_menu.          |
|                          |
| chat_settings            | Integer       | Optional | 1= if you want to send to bot chat settings                                                                       |

## Send Photo

```javascript
/* use the MediaTansfer in src/util/MediaTransfer class to upload the photo to the server
 then send it */
MediaTransfer.uploadFile(TOKEN, "./your_photo.jpg", config.UploadServer)
  .then((uploadedPhotoId) => {
    let photoMsg = new PhotoOutMessage();
    photoMsg.chat_id = incomingMsg.chat.id;
    photoMsg.reference = Id();
    photoMsg.photo = uploadedPhotoId;
    photoMsg.caption = "Photo From Bot";
    photoMsg.echo = 1;

    api.send(JSON.stringify(photoMsg));
  })
  .catch((e) => console.log("Upload failed", e));
```

```json
{
  "method": "sendPhoto",
  "chat_id": "90091903321704167",
  "reference": 36006160866836,
  "photo": "f3b0f1e475e5eebf9c320c1231767f3476210a24c04285132cae083494a65468.jpg",
  "caption": "Photo From Bot",
  "echo": 1
}
```

Use this method to send photos. On success, the sent Message is returned. Bots can currently send photo files of up to 20 MB in size, this limit may be changed in the future.

| Field                    | Type          | Required | Description                                                                                                       |
| ------------------------ | ------------- | -------- | ----------------------------------------------------------------------------------------------------------------- |
| method                   | String        | Yes      | "SendPhoto"                                                                                                       |
| chat_id                  | String        | Yes      | Unique identifier for the target chat or User_id                                                                  |
| photo                    | String        | Yes      | Photo to send. Pass a file_id as String to send a photo that exists on the nandbox servers.                       |
| caption                  | String        | Optional | "Photo caption 0-256 characters                                                                                   |
| disable_web_page_preview | Boolean       | Optional | Disables link previews for links in this message                                                                  |
| disable_notification     | Boolean       | Optional | Sends the message silently. Users will receive a notification with no sound.                                      |
| reply_to_message_id      | String        | Optional | If the message is a reply, unique identification for the original (parent) message.                               |
| reference                | long          | Yes      | Unique local identifier for the target chat/user                                                                  |
| to_user_id               | String        | Optional | if reply or send message to target user within a group chat or channel, unique identifier of the target user.     |
| echo                     | Integer       | Optional | 1= repeat message 0= no echo                                                                                      |
| menu_ref                 | String        | Optional | Menu reference for existing predefined Menu. The menu will be displayed as inline menu associated to the message. |
| inline_menu              | Array of Menu | Optional | Inline menu object to hold menus.If both inline_menu and menu_ref are defined. Priority for inline_menu.          |
| chat_settings            | Integer       | Optional | 1= if you want to send to bot chat settings                                                                       |

## Send Video

```javascript
MediaTransfer.uploadFile(TOKEN, "./your_video.mp4", config.UploadServer)
  .then((uploadedVideoId) => {
    let vidoMsg = new VideoOutMessage();
    vidoMsg.chat_id = incomingMsg.chat.id;
    vidoMsg.reference = Id();
    vidoMsg.video = uploadedVideoId;
    vidoMsg.caption = "Video From Bot";
    vidoMsg.echo = 0;

    api.send(JSON.stringify(vidoMsg));
  })
  .catch((e) => console.log("Upload failed", e));
```

```json
{
  "method": "sendVideo",
  "chat_id": "90091903321704167",
  "reference": 26646740171012,
  "video": "190717a3076b1eeac6ba555a2924179e9046bf2ceb28389f39d22dc697c54219.mp4",
  "caption": "Video From Bot",
  "echo": 0
}
```

Use this method to send videos. nandbox clients support mp4 videos (other formats mybe sent as Document). On success, the sent Message is returned. Bots can currently send phot files of up to 50 MB in size, this limit may be changed in the future.

| Field                    | Type          | Required | Description                                                                                                                                                                          |
| ------------------------ | ------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| method                   | String        | Yes      | "SendVideo"                                                                                                                                                                          |
| chat_id                  | String        | Yes      | Unique identifier for the target chat or User_id                                                                                                                                     |
| video                    | String        | Yes      | video to send. Pass a file_id as String to send a video that exists on the nandbox servers (recommended), pass an HTTP URL as a String for nandbox to get a video from the Internet. |
| caption                  | String        | Optional | "Video caption 0-256 characters                                                                                                                                                      |
| disable_web_page_preview | Boolean       | Optional | Disables link previews for links in this message                                                                                                                                     |
| disable_notification     | Boolean       | Optional | Sends the message silently. Users will receive a notification with no sound.                                                                                                         |
| reply_to_message_id      | String        | Optional | If the message is a reply, ID of the original message                                                                                                                                |
| reference                | long          | Yes      | Unique local identifier for the target chat/user                                                                                                                                     |
| to_user_id               | String        | Optional | if reply or send message to target user within a group chat or channel, unique identifier of the target user.                                                                        |
| echo                     | Integer       | Optional | 1= repeat message 0= no echo                                                                                                                                                         |
| menu_ref                 | String        | Optional | Menu reference for existing predefined Menu. The menu will be displayed as inline menu associated to the message.                                                                    |
| inline_menu              | Array of Menu | Optional | Inline menu object to hold menus.If both inline_menu and menu_ref are defined. Priority for inline_menu.                                                                             |
|                          |
| chat_settings            | Integer       | Optional | 1= if you want to send to bot chat settings                                                                                                                                          |

## Send Audio

```javascript
MediaTransfer.uploadFile(TOKEN, "./your_audio.mp3", config.UploadServer).then(
  (uploadedAudioId) => {
    let audioOutMsg = new AudioOutMessage();
    audioOutMsg.chat_id = incomingMsg.chat.id;
    audioOutMsg.reference = Id();
    audioOutMsg.audio = uploadedAudioId;
    audioOutMsg.performer = "Perfomer Man";
    audioOutMsg.title = " Song";
    audioOutMsg.caption = "Audio From Bot";

    api.send(JSON.stringify(audioOutMsg));
  }
);
```

```json
{
  "method": "sendAudio",
  "chat_id": "90089668723575679",
  "reference": 64818504566661,
  "audio": "a2517a187f5c78f3b3b5b6e535e7ab6be54e524e7f94b718b079b82a9c008ee6.mp3",
  "performer": "Perfomer Man",
  "title": " Song",
  "caption": "Audio From Bot"
}
```

Use this method to send audio files, if you want nandbox clients to display them in the music player. Your audio must be in the .mp3 format. On success, sent Message is returned. Bots can currently send audio files of up to 50 MB in size, this limit may be changed in the future.

| Field                    | Type          | Required | Description                                                                                                       |
| ------------------------ | ------------- | -------- | ----------------------------------------------------------------------------------------------------------------- |
| method                   | String        | Yes      | "SendAudio"                                                                                                       |
| chat_id                  | String        | Yes      | Unique identifier for the target chat or User_id                                                                  |
| audio                    | String        | Yes      | Audio to send. Pass a file_id as String to send an audio that exists on the nandbox server.                       |
| performer                | String        | Optional | Audio file performer                                                                                              |
| title                    | String        | Optional | Audio file title                                                                                                  |
| caption                  | String        | Optional | "Audio caption 0-256 characters                                                                                   |
| disable_web_page_preview | Boolean       | Optional | Disables link previews for links in this message.                                                                 |
| disable_notification     | Boolean       | Optional | Sends the message silently. Users will receive a notification with no sound.                                      |
| reply_to_message_id      | String        | Optional | If the message is a reply, unique identification for the original (parent) message.                               |
| reference                | long          | Yes      | Unique local identifier for this message as defined by bot.                                                       |
| to_user_id               | String        | Optional | if reply or send message to target user within a group chat or channel, unique identifier of the target user.     |
| echo                     | Integer       | Optional | 1= repeat message 0= no echo                                                                                      |
| menu_ref                 | String        | Optional | Menu reference for existing predefined Menu. The menu will be displayed as inline menu associated to the message. |
| inline_menu              | Array of Menu | Optional | Inline menu object to hold menus.If both inline_menu and menu_ref are defined. Priority for inline_menu.          |
|                          |
| chat_settings            | Integer       | Optional | 1= if you want to send to bot chat settings                                                                       |

## Send Voice

Use this method to send voice note. If you want nandbox clients to display the file as a playable voice message, your voice audio must be in an .ogg file encoded with OPUS (other format may be sent as Audio or Document). On success, the sent Message is returned. Bots can currently send voice note files of up to 50 MB in size, this limit may be changed in the future.

| Field                    | Type          | Required | Description                                                                                                       |
| ------------------------ | ------------- | -------- | ----------------------------------------------------------------------------------------------------------------- |
| method                   | String        | Yes      | "SendVoice"                                                                                                       |
| chat_id                  | String        | Yes      | Unique identifier for the target chat or User_id                                                                  |
| size                     | String        | Optional | Size of document                                                                                                  |
| voice                    | String        | Yes      | Voice note to send. Pass a file_id as String to send a voice note that exists on the nandbox servers .            |
| caption                  | String        | Optional | "Voice note caption 0-256 characters                                                                              |
| disable_web_page_preview | Boolean       | Optional | Disables link previews for links in this message                                                                  |
| disable_notification     | Boolean       | Optional | Sends the message silently. Users will receive a notification with no sound.                                      |
| reply_to_message_id      | String        | Optional | If the message is a reply, unique identification for the original (parent) message.                               |
| reference                | long          | Yes      | Unique local identifier for the target chat/user                                                                  |
| to_user_id               | String        | Optional | if reply or send message to target user within a group chat or channel, unique identifier of the target user.     |
| echo                     | Integer       | Optional | 1= repeat message 0= no echo                                                                                      |
| menu_ref                 | String        | Optional | Menu reference for existing predefined Menu. The menu will be displayed as inline menu associated to the message. |
| inline_menu              | Array of Menu | Optional | Inline menu object to hold menus.If both inline_menu and menu_ref are defined. Priority for inline_menu.          |
|                          |
| chat_settings            | Integer       | Optional | 1= if you want to send to bot chat settings                                                                       |

## Send Document

```javascript
MediaTransfer.uploadFile(
  TOKEN,
  "./your_document.pdf",
  config.UploadServer
).then((uploadedDocumentId) => {
  let documentOutMsg = new DocumentOutMessage();
  documentOutMsg.chat_id = incomingMsg.chat.id;
  documentOutMsg.reference = Id();
  documentOutMsg.document = uploadedDocumentId;
  documentOutMsg.name = "Document renamed inside Bot";
  documentOutMsg.caption = "Document From Bot";

  api.send(JSON.stringify(documentOutMsg));
});
```

```javascript
https://github.com/nandbox/nandboxbotsapi-js/blob/master/src/data/Document.js
```

```json
{
  "method": "sendDocument",
  "chat_id": "90091903321704167",
  "reference": 96181774767671,
  "caption": "from all option send",
  "name": null,
  "size": null
}
```

Use this method to send general files. On success, the sent Message is returned. Bots can currently send files of any type of up to 50 MB in size, this limit may be changed in the future.

| Field                    | Type          | Required | Description                                                                                                       |
| ------------------------ | ------------- | -------- | ----------------------------------------------------------------------------------------------------------------- |
| method                   | String        | Yes      | "SendDocument"                                                                                                    |
| chat_id                  | String        | Yes      | Unique identifier for the target chat or User_id                                                                  |
| name                     | String        | Optional | Name of document                                                                                                  |
| size                     | String        | Optional | Size of document                                                                                                  |
| document                 | String        | Yes      | Document to send. Pass a file_id as String to a file that exists on the nandbox servers (recommended)             |
| caption                  | String        | Optional | "Photo caption 0-256 characters                                                                                   |
| disable_web_page_preview | Boolean       | Optional | Disables link previews for links in this message                                                                  |
| disable_notification     | Boolean       | Optional | Sends the message silently. Users will receive a notification with no sound.                                      |
| reply_to_message_id      | String        | Optional | If the message is a reply, unique identification for the original (parent) message.                               |
| reference                | long          | Yes      | Unique local identifier for the target chat/user                                                                  |
| to_user_id               | String        | Optional | if reply or send message to target user within a group chat or channel, unique identifier of the target user.     |
| echo                     | Integer       | Optional | 1= repeat message 0= no echo                                                                                      |
| menu_ref                 | String        | Optional | Menu reference for existing predefined Menu. The menu will be displayed as inline menu associated to the message. |
| inline_menu              | Array of Menu | Optional | Inline menu object to hold menus.If both inline_menu and menu_ref are defined. Priority for inline_menu.          |
|                          |
| chat_settings            | Integer       | Optional | 1= if you want to send to bot chat settings                                                                       |

## Send Location

```javascript
let locationOutMsg = new LocationOutMessage();
locationOutMsg.chat_id = incomingMsg.chat.id;
locationOutMsg.reference = Id();
locationOutMsg.name = incomingMsg.location.name;
locationOutMsg.details = incomingMsg.location.details;
locationOutMsg.latitude = incomingMsg.location.latitude;
locationOutMsg.longitude = incomingMsg.location.longitude;
locationOutMsg.caption = "Location From Bot";

api.send(JSON.stringify(locationOutMsg));
```

```json
{
  "method": "sendLocation",
  "chat_id": "90089668723575679",
  "reference": 80613906787070,
  "latitude": "29.9740559",
  "longitude": "31.482059",
  "caption": "Location From Bot"
}
```

Use this method to send location and point of map. On success, the sent Message is returned.

| Field                    | Type          | Required | Description                                                                                                       |
| ------------------------ | ------------- | -------- | ----------------------------------------------------------------------------------------------------------------- |
| method                   | String        | Yes      | "SendLocation"                                                                                                    |
| chat_id                  | String        | Yes      | Unique identifier for the target chat or User_id                                                                  |
| longitude                | String        | Yes      | longitude                                                                                                         |
| latitude                 | String        | Yes      | latitude                                                                                                          |
| name                     | String        | Optional | Location name                                                                                                     |
| details                  | String        | Optional | Location details                                                                                                  |
| caption                  | String        | Optional | "Location caption 0-256 characters                                                                                |
| disable_web_page_preview | Boolean       | Optional | Disables link previews for links in this message                                                                  |
| disable_notification     | Boolean       | Optional | Sends the message silently. Users will receive a notification with no sound.                                      |
| reply_to_message_id      | String        | Optional | If the message is a reply, unique identification for the original (parent) message.                               |
| reference                | long          | Yes      | Unique local identifier for the target chat/user                                                                  |
| to_user_id               | String        | Optional | if reply or send message to target user within a group chat or channel, unique identifier of the target user.     |
| echo                     | Integer       | Optional | 1= repeat message 0= no echo                                                                                      |
| menu_ref                 | String        | Optional | Menu reference for existing predefined Menu. The menu will be displayed as inline menu associated to the message. |
| inline_menu              | Array of Menu | Optional | Inline menu object to hold menus.If both inline_menu and menu_ref are defined. Priority for inline_menu.          |
|                          |
| chat_settings            | Integer       | Optional | 1= if you want to send to bot chat settings                                                                       |

## Send Contact

```javascript
// this example echoes the received contact
let contactOutMsg = new ContactOutMessage();
contactOutMsg.chat_id = incomingMsg.chat.id;
contactOutMsg.reference = Id;
contactOutMsg.name = incomingMsg.contact.name;
contactOutMsg.phoneNumber = incomingMsg.contact.phoneNumber;

api.send(JSON.stringify(contactOutMsg));
```

```json
{
  "method": "sendContact",
  "chat_id": "90089668723575679",
  "reference": 16350635381030,
  "name": "Youssef Sayed"
}
```

Use this method to send phone contact. On success, the sent Message is returned.

| Field                    | Type          | Required | Description                                                                                                       |
| ------------------------ | ------------- | -------- | ----------------------------------------------------------------------------------------------------------------- |
| method                   | String        | Yes      | "SendContact"                                                                                                     |
| chat_id                  | String        | Yes      | Unique identifier for the target chat or User_id                                                                  |
| phone_number             | String        | Yes      | phone number                                                                                                      |
| name                     | String        | Yes      | Contact name                                                                                                      |
| disable_web_page_preview | Boolean       | Optional | Disables link previews for links in this message                                                                  |
| disable_notification     | Boolean       | Optional | Sends the message silently. Users will receive a notification with no sound.                                      |
| reply_to_message_id      | String        | Optional | If the message is a reply, unique identification for the original (parent) message.                               |
| reference                | long          | Yes      | Unique local identifier for the target chat/user                                                                  |
| to_user_id               | String        | Optional | if reply or send message to target user within a group chat or channel, unique identifier of the target user.     |
| echo                     | Integer       | Optional | 1= repeat message 0= no echo                                                                                      |
| menu_ref                 | String        | Optional | Menu reference for existing predefined Menu. The menu will be displayed as inline menu associated to the message. |
| inline_menu              | Array of Menu | Optional | Inline menu object to hold menus.If both inline_menu and menu_ref are defined. Priority for inline_menu.          |
|                          |
| chat_settings            | Integer       | Optional | 1= if you want to send to bot chat settings                                                                       |

## Update Message

```javascript
const newPage = new UpdateOutMessage();
newPage.message_id = inlineMsgCallback.message_id;
newPage.text = data.msgText;
newPage.reference = inlineMsgCallback.reference;
newPage.to_user_id = inlineMsgCallback.from.id;
newPage.chat_id = inlineMsgCallback.chat.id;
newPage.inline_menu = data.menus;
newPage.menu_ref = data.menuRef;
api.send(JSON.stringify(newPage));
```

Use this message to update existing Message sent. On success, the sent Message is returned with status "updated"

| Field       | Type          | Required    | Description                                                                                                                                                                                                    |
| ----------- | ------------- | ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| method      | String        | Yes         | "updateMessage"                                                                                                                                                                                                |
| message_id  | String        | Yes         | Old message ID that you want to edit it                                                                                                                                                                        |
| reference   | StringLong    | Yes         | Unique local identifier for the target chat/user                                                                                                                                                               |
| text        | String        | Conditional | Only use if you want to update Message has type of "text"                                                                                                                                                      |
| caption     | String        | Conditional | Only use if you want to update Message has type of other than "text" e.g. photo, video, audio,..etc.                                                                                                           |
| chat_id     | String        | Yes         | Unique identifier for the target chat or User_id                                                                                                                                                               |
| to_user_id  | String        | Optional    | if reply or send message to target user within a group chat or channel, unique identifier of the target user.                                                                                                  |
| menu_ref    | String        | Optional    | Menu reference for existing predefined Menu. The menu will be displayed as inline menu associated to the message. To hide the inline menu from message set menu_ref to empty String .                          |
| inline_menu | Array of Menu | Optional    | Inline menu object to hold menus. Previous menu will be dropped and replaced by the updated one.If both inline_menu and menu_ref is defined. Priority for inline_menu unless menu_ref is set to empty String . |

## Set Chat Menu

Use this message to set normal keypad menus "Chat Menu". This message will overwrite the existing Chat Menus. If bot wants to update specific item in the Chat Menus, bot must send the entire menus again to the target chat. On success, setChatMenu_ack will be returned.

| Field      | Type   | Required | Description                                                                                                   |
| ---------- | ------ | -------- | ------------------------------------------------------------------------------------------------------------- |
| method     | String | Yes      | "setChatMenu"                                                                                                 |
| menus      | Menu   | Yes      | New or updated Menus                                                                                          |
| chat_id    | String | Yes      | Unique identifier for the target chat or User_id                                                              |
| to_user_id | String | Optional | if reply or send message to target user within a group chat or channel, unique identifier of the target user. |

```json
{
  "method": "setChatMenu",

  "chat_id": "4522291356145774",

  "menus": [
    {
      "menu_ref": "KEY1",

      "rows": [
        {
          "buttons": [
            {
              "next_menu": null,

              "button_span": "1",

              "button_order": "1",

              "button_textcolor": "white",

              "button_callback": "B1",

              "button_bgcolor": "black",

              "button_label": "B1",

              "button_url": "abc",

              "button_query": "abc"
            }
          ],

          "row_order": "1"
        }
      ]
    }
  ]
}
```

## Inline Search Answer

```json
{
  "method": "inlineSearchAnswer",
  "results": [
    {
      "title": "ص (50)",
      "caption": "﴿جَنَّاتِ عَدْنٍ مُفَتَّحَةً لَهُمُ الْأ َبْوَابُ﴾\nص (50)\nShared via @qurany_nb",
      "height": 10,
      "width": 40,
      "description": "جَنَّاتِ عَدْنٍ مُفَتَّحَةً لَهُمُ الْأَبْوَابُ"
    }
  ],
  "next_offset": "",
  "chat": { "id": "90089668723575679", "type": "Mobile" },
  "to_user_id": "90089668723575679",
  "search_id": 1589060
}
```

| Field       | Type                 | Required | Description                                                                                                                                                                                       |
| ----------- | -------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| method      | String               | Yes      | "inlineSearchAnswer"                                                                                                                                                                              |
| to_user_id  | String               | Yes      | The user id you want to sent to him                                                                                                                                                               |
| results     | [Results](#_Results) | Yes      | Array of media information                                                                                                                                                                        |
| next_offset | String               | yes      | Pass the offset that a client should send in the next search with the same text to receive more results. Pass an empty string if there are no more results or if you don&#39;t support pagination |
| chat_id     | String               | yes      | Chat id                                                                                                                                                                                           |
| search_id   | String               | yes      | Unique id of this message                                                                                                                                                                         |

# ![](../images/ic_Types.svg) More Types

The following data structures represents custom keypad menus with reply options

## Menu

Each Menu composes of set of rows. At least one row should be defined.

| Field    | Type         | Required | Description                                                |
| -------- | ------------ | -------- | ---------------------------------------------------------- |
| menu_ref | String       | Yes      | Unique identifier of this Menu as defined by bot.          |
| rows     | Array of Row | Yes      | Rows belong to this menu. Row which is an Array of buttons |

## Row

Each row belongs to one keypad menu that composes of set of buttons. At least one button should be defined.

| Field     | Type            | Required | Description                |
| --------- | --------------- | -------- | -------------------------- |
| buttons   | Array of Button | Yes      | Button belongs to the row. |
| row_order | Integer         | Yes      | Row order in the menu.     |

## Button

This object represents button of reply. Button must have a button_callback which is the unique identifier defined by bot.

| Field                                                | Type    | Required | Description                                                                                                                                                                                             |
| ---------------------------------------------------- | ------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| button_callback                                      | String  | Yes      | This is unique identifier as defined by bot. The button_callback returned in inlineMessageCallback and ChatMenuCallbakc when button pressed.                                                            |
| next_menu                                            | Menu    | Optional | Menu unique identifier that reference the next menu to navigate to it when the button pressed.                                                                                                          |
| button_span                                          | Integer | Optional | Button Span                                                                                                                                                                                             |
| button_order                                         | Integer | Optional | The number of button order by ascending                                                                                                                                                                 |
| button_text_color                                    | String  | Optional | Text color of the button Title The color should be in hexadecimal format (Hex triplet ) or according to its common English name .                                                                       |
| Example : Red color can be set as "RED" or "#FF0000" |
| button_bg_color                                      | String  | Optional | Button background color .The color should be in hexadecimal format (Hex triplet ) or according to its common English name .                                                                             |
| Example : Red color can be set as "RED" or "#FF0000" |
| button_label                                         | String  | Optional | Button label or title.                                                                                                                                                                                  |
| button_url                                           | String  | Optional | Button URL. When button pressed, an external URL link will be opened.                                                                                                                                   |
| button_query                                         | String  | Optional | Field used to query information from app, this can take one of two values as follows Location: to ask user to get location or point of map information.Contact : to ask user to get his contact number. |
| button_chat                                          | Chat    | Optional | Chat unique identifier that reference the specific chat to be opened when button is pressed. if button_url and button_chat are both defined, button_chat priority to button_chat.                       |
| nav_type                                             | String  | Optional | -Null is default to show navigation button for channel, group or contact-Type "admin" for show admin navigation button in chat setting                                                                  |

## Set Navigation Button

Use this method to set the navigation button with the menu reference. When navigation button is pressed the referenced menu will be displayed as normal keypad menu "Chat Menu".

| Field                      | Type                              | Required | Description                                                                                                               |
| -------------------------- | --------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------- |
| method                     | String                            | Yes      | "setNavigationButton"                                                                                                     |
| navigation_buttonsmenu_ref | StringArray of [Button](#_Button) | Yes      | Array of Button.Menu unique identifier that reference the next menu to navigate to it when the navigation button pressed. |
| chat_id                    | String                            | Yes      | Unique identifier for the target chat or User_id                                                                          |
| to_user_id                 | String                            | Optional | if reply or send message to target user within a group chat or channel, unique identifier of the target user.             |

## Get User

Use this method to get profile for a user. On success, User is returned.

| Field   | Type   | Required | Description                             |
| ------- | ------ | -------- | --------------------------------------- |
| method  | String | Yes      | "getUser"                               |
| user_id | String | Yes      | Unique identifier for this user or bot. |

**JSON Example:**

```json
{
  "method": "getUser",

  "user_id": "4521191845180798"
}
```

## Get Chat

Use this method to get Group or Channel information. On success, Chat is returned.

| Field   | Type   | Required | Description                             |
| ------- | ------ | -------- | --------------------------------------- |
| method  | String | Yes      | "getChat"                               |
| chat_id | String | Yes      | Unique identifier for Group or Channel. |

**JSON Example:**

```json
{
  "method": "getChat",

  "chat_id": "4522291356145774"
}
```

## Get Chat Member

Use this method to get Chat Member user public profile. On success, ChatMember is returned.

| Field   | Type   | Required | Description                                                     |
| ------- | ------ | -------- | --------------------------------------------------------------- |
| method  | String | Yes      | "getChatMember"                                                 |
| chat_id | String | Yes      | Unique identifier for Group or Channel where member belongs to. |
| user_id | String | Yes      | Unique identifier for this user member.                         |

**JSON Example:**

```json
{
  "method": "getChatMember",

  "chat_id": "4522291356145774",

  "user_id": "4521191845180798"
}
```

## Get Chat Administrators

Use this method to get Chat Administrators. On success, [ChatAdministrators](#_1v1yuxt) message will received .

| Field   | Type   | Required | Description                             |
| ------- | ------ | -------- | --------------------------------------- |
| method  | String | Yes      | "getChatAdministrators"                 |
| chat_id | String | Yes      | Unique identifier for Group or Channel. |

**JSON Example:**

```json
{
  "method": "getChatAdministrators",

  "chat_id": "4522291356145774"
}
```

## Ban Chat Member

Use this method to ban a Chat Member from accessing Chat. On success, ChatMember is returned with status "banned". Ban is a black list, user will not be able to join Chat again.

| Field   | Type   | Required | Description                                                     |
| ------- | ------ | -------- | --------------------------------------------------------------- |
| method  | String | Yes      | "banChatMember"                                                 |
| chat_id | String | Yes      | Unique identifier for Group or Channel where member belongs to. |
| user_id | String | Yes      | Unique identifier for this user member.                         |

**JSON Example:**

```json
{
  "method": "banChatMember",

  "chat_id": "4522291356145774",

  "user_id": "90089584758972053"
}
```

## Unban Chat Member

Use this method to unban a Chat Member from accessing Chat. On success, ChatMember is returned with status "Active". unBan is remove from black list, user will be able to join Chat once again.

| Field   | Type   | Required | Description                                                            |
| ------- | ------ | -------- | ---------------------------------------------------------------------- |
| method  | String | Yes      | "unbanChatMember"                                                      |
| chat_id | String | Yes      | Unique identifier for Group or Channel where member used to belong to. |
| user_id | String | Yes      | Unique identifier for the banned user.                                 |

**JSON Example:**

```json
{
  "method": "unbanChatMember",

  "chat_id": "4522291356145774",

  "user_id": "90089584758972053"
}
```

## Remove Chat Member

Use this method to remove a Chat Member from Chat. On success, ChatMember is returned with status "removed". Remove user is a temprorary kicking the user out from the Group or Channel. User will be able to join Chat once again.

| Field   | Type   | Required | Description                                                            |
| ------- | ------ | -------- | ---------------------------------------------------------------------- |
| method  | String | Yes      | "removeChatMember"                                                     |
| chat_id | String | Yes      | Unique identifier for Group or Channel where member used to belong to. |
| user_id | String | Yes      | Unique identifier for the banned user.                                 |

**JSON Example:**

```json
{
  "method": "removeChatMember",

  "chat_id": "4522291356145774",

  "user_id": "90089584758972053"
}
```

## Set Chat

Use this method to set Chat Group or Channel information. On success, chat is returned.

| Field  | Type   | Required | Description                             |
| ------ | ------ | -------- | --------------------------------------- |
| method | String | Yes      | "setChat"                               |
| chat   | Chat   | Yes      | Unique identifier for Group or Channel. |

**JSON Example:**

```json
{
  "method": "setChat",
  "chat": {
    "id": "4522291356145774",

    "name": "CHANGE 3",

    "photo": {
      "id": "8d7773be38db78.jpg"
    }
  }
}
```

## Add Blacklist

Use this method to add black list.

| Field  | Type            | Required | Description                                       |
| ------ | --------------- | -------- | ------------------------------------------------- |
| method | String          | Yes      | "addBlacklist"                                    |
| chat   | Chat            | Yes      | Unique identifier for Group or Channel.           |
| users  | Array of String | yes      | Add list of users (mobile or Email) to black list |

**JSON Example:**

```json
{
  "method": "addBlacklist",

  "users": ["111133", "222223"],

  "chat_id": "90090684293612221"
}
```

## Add Whitelist

Use this method to add white list.

| Field  | Type                                   | Required | Description                             |
| ------ | -------------------------------------- | -------- | --------------------------------------- |
| method | String                                 | Yes      | "addWhitelist"                          |
| chat   | Chat                                   | Yes      | Unique identifier for Group or Channel. |
| users  | Array of [UsersWhiteListUser](#_Users) | yes      | Add Array of Users                      |

**JSON Example:**

```json
{
  "method": "addWhitelist",

  "users": [
    {
      "signup_user": "3636526",

      "tags": ["1", "2"]
    }
  ],

  "chat_id": "90090684293612221"
}
```

## Add Blacklist Patterns

Use this method to add black list patterns:

| Field  | Type                    | Required | Description                             |
| ------ | ----------------------- | -------- | --------------------------------------- |
| method | String                  | Yes      | "addBlacklistPatterns"                  |
| chat   | Chat                    | Yes      | Unique identifier for Group or Channel. |
| data   | Array of [Data](#_Data) | yes      | Add Array of Data                       |

**JSON Example:**

```JSON
{

"method": "addBlacklistPatterns",

"data": [{

"pattern": "44444\*",

"example": "44444444"

},

{

"pattern": "222\*",

"example": "222222222"

}],

"chat_id": "90090684293612221"

}
```

## AddWhitelistPatterns

Use this method to add white list.patterns:

| Field  | Type                    | Required | Description                             |
| ------ | ----------------------- | -------- | --------------------------------------- |
| method | String                  | Yes      | "addWhitelistPatterns"                  |
| chat   | Chat                    | Yes      | Unique identifier for Group or Channel. |
| data   | Array of [Data](#_Data) | yes      | Add Array of Data                       |

**JSON Example:**

```json
{
  "method": "addWhitelistPatterns",

  "data": [
    {
      "pattern": "44444*",

      "example": "44444444"
    },

    {
      "pattern": "222*",

      "example": "222222222"
    }
  ],

  "chat_id": "90090684293612221"
}
```

## Delete Blacklist

Use this method to delete black list:

| Field  | Type            | Required | Description                                       |
| ------ | --------------- | -------- | ------------------------------------------------- |
| method | String          | Yes      | "deleteBlacklist"                                 |
| chat   | Chat            | Yes      | Unique identifier for Group or Channel.           |
| users  | Array of String | yes      | Add list of users (mobile or Email) to black list |

**JSON Example:**

```JSON
{

"method": "deleteBlacklist",

"users": ["111133"],

"chat_id": "90090684293612221"

}

```

## Delete Whitelist

Use this method to delete white list:

| Field  | Type            | Required | Description                                       |
| ------ | --------------- | -------- | ------------------------------------------------- |
| method | String          | Yes      | "deleteWhitelist"                                 |
| chat   | Chat            | Yes      | Unique identifier for Group or Channel.           |
| users  | Array of String | yes      | Add list of users (mobile or Email) to black list |

**JSON Example:**

```JSON
{

"method": "deleteWhitelist",

"users": ["111133"],

"chat_id": "90090684293612221"

}
```

## Delete Blacklist Pattern

Use this method to delete black list pattern:

| Field   | Type            | Required | Description                             |
| ------- | --------------- | -------- | --------------------------------------- |
| method  | String          | Yes      | "deleteBlacklistPatterns"               |
| chat    | Chat            | Yes      | Unique identifier for Group or Channel. |
| pattern | Array of String | yes      | Add list of pattern                     |

**JSON Example:**

```JSON
{

"method": "deleteBlacklistPatterns",

"pattern": ["222\*"],

"chat_id": "90090684293612221"

}
```

## Delete Whitelist Pattern

Use this method to delete white list pattern:

| Field   | Type            | Required | Description                             |
| ------- | --------------- | -------- | --------------------------------------- |
| method  | String          | Yes      | "deleteWhitelistPatterns"               |
| chat    | Chat            | Yes      | Unique identifier for Group or Channel. |
| pattern | Array of String | yes      | Add list of pattern                     |

**JSON Example:**

```JSON
{

"method": "deleteWhitelistPatterns",

"pattern": ["5555\*"],

"chat_id": "90090684293612221"

}
```

## Recall Message

Use this message to recall existing Message sent .

| Field        | Type       | Required | Description                                                           |
| ------------ | ---------- | -------- | --------------------------------------------------------------------- |
| method       | String     | Yes      | "recallMessage"                                                       |
| chat_id      | String     | Yes      | Unique identifier of chat id                                          |
| message_id   | String     | Yes      | Global Unique identifier for message requested to be recalled.        |
| reference    | StringLong | Yes      | Unique local identifier for the target chat/user                      |
| from_user_id | String     | Optional | Original sender id Mandatory in case the bot is the admin of the Chat |

**JSON Example:**

```JSON
{

"method": "recallMessage",

"chat_id": "4522291356145774",

"message_id": "d2_F4k48l1t12617132"

}
```

## Get Blacklist

Use this method to get black list. On success, blacklist is returned.

| Field     | Type   | Required | Description                                                     |
| --------- | ------ | -------- | --------------------------------------------------------------- |
| method    | String | Yes      | "getBlacklist"                                                  |
| chat_id   | String | Yes      | Unique identifier for Group or Channel where member belongs to. |
| page_size | String |

**JSON Example:**

```JSON
{

"method": "getBlacklist",

"chat_id": "90090684293612221"

}
```

## Get Whitelist

Use this method to get white list. On success, whitelist is returned.

| Field     | Type   | Required | Description                                                     |
| --------- | ------ | -------- | --------------------------------------------------------------- |
| method    | String | Yes      | "getWhitelist"                                                  |
| chat_id   | String | Yes      | Unique identifier for Group or Channel where member belongs to. |
| page_size | String |

**JSON Example:**

```JSON
{

"method": "getWhitelist",

"chat_id": "90090684293612221"

}
```

## Set My Profile

Use this method to set Bot Profile. On success, myProfile is returned.

| Field     | Type   | Required | Description             |
| --------- | ------ | -------- | ----------------------- |
| method    | String | Yes      | "setMyProfile"          |
| user      | User   | Yes      | Bot profile user object |
| page_size | String |
|           |
|           |

**JSON Example:**

```json
{
  "method": "setMyProfile",

  "user": {
    "profile": "Other",

    "status": "OTHER PROFILE",

    "photo": {
      "id": "95d4438d7773be38db78.jpg"
    }
  }
}
```

## Get My Profiles

Use this method to get Bot Profile. On success, myProfile is returned.

| Field  | Type   | Required | Description     |
| ------ | ------ | -------- | --------------- |
| method | String | Yes      | "getMyProfiles" |

**JSON Example:**

```json
{
  "method": "getMyProfiles"
}
```
