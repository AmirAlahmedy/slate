# ![](../images/ic_outcoming.svg) API Manual: Outgoing Messages

## Send Message

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

Use this method to send photos. On success, the sent Message is returned. Bots can currently send phot files of up to 20 MB in size, this limit may be changed in the future.

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
    "method":"inlineSearchAnswer",
    "results":
      [
        {
          "title":"ص (50)",
          "caption":"﴿جَنَّاتِ عَدْنٍ مُفَتَّحَةً لَهُمُ الْأ َبْوَابُ﴾\nص (50)\nShared via @qurany_nb",
          "height":10,
          "width":40,
          "description":"جَنَّاتِ عَدْنٍ مُفَتَّحَةً لَهُمُ الْأَبْوَابُ"
        }
      ],
    "next_offset":"",
    "chat":{"id":"90089668723575679","type":"Mobile"},
    "to_user_id":"90089668723575679","search_id":1589060
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
