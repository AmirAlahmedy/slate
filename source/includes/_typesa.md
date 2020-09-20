# Types

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
