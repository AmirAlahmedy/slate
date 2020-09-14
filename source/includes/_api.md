# How API/Bot works?

Users can interact with API/bots in two ways:

  1. Send messages and commands to API/bots through a direct chat, by adding them to groups/channels, or associate them to your nandbox Apps. This is useful for example in automated chat bots, news bots, and/or integrating your nandbox&#39;s App to your backend systems.

  1. Send requests directly from the input field by typing the bot&#39;s @handle and a query. This allows sending content from inline API/bots directly into any chat, group or channel within nandbox Apps.

Messages, commands and requests sent by users are passed to the software running on your servers where API/Bot is hosted. Our intermediary server handles all encryption and communication with the nandbox API/Bot for you. You communicate with this server via a WebSocket interface that offers a simplified version of the nandbox API/Bot.

## How do I create an API access or bot?

Creating API access or bot within nandbox is easy. In few steps, you can configure and publish your new bots using an interactive menu.

### Create API/Bot within your nandbox App

Login to your administrative portal of your nandbox App. Go to Bot Manager section and follow the instruction to create your first API/Bot as illustrated in the following screen.


There are some API/Bot are already implemented by third party vendors offered in the Bot marketplace, where you can add them to your nandbox App and determine their access level to the information within your App.


### Create API/Bot within nandbox Messenger

1. Use nandbox Android App version 2.1.0 or later

1. From Settings menu open "Bot Manager"




1. Tap "+" to create a new bot



1. Enter your Bot title
   (Limited to 32 characters)

1. Choose your bot type

- Choose "Business", if your bot is associated or will be for use by organization, or business.

- Choose "Individual" if bot will be for use by individual.


Enter Bot Description: a short text of up to 120 characters, describing your bot. Users will see this text on the bot&#39;s profile page and when they share your bot with someone, this text is sent together with the link.

1. when they are about to join your bot.

1. Update your Bot Image

1. Enter "About" section:
   a short text of up to 512 characters, describing your bot. Users will see this text at the beginning of the conversation with the bot.

1. Give your bot a unique handle by providing your business email.


Unlike others, we protect your business name from being reserved by others bots. Your bot unique handle will be matching your web domain name. For example, if your business domain name is XYZ.com your bot handle will be "xyz".

After you reserve and book your bot handle, you can configure the following options:

1. Inline: toggle [inline mode](https://core.telegram.org/bots/inline) for your bot.

1. Private: Private Bot will not appear in Bot index search. Admin must send the Bot link to the user to invite him/her to join the bot.

1. Filter: select which messages your bot will receive when added to a group. Choose from "none", "when mentioned", "posts" or "All".

