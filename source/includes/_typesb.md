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
