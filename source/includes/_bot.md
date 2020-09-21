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
{"method":"TOKEN_AUTH","rem":true,"token":"90091784056528980:0:odIgBOQZ4lVpqSIuxpQlGzmse3hwsS"}
``` 

If bot is successfully authenticated, you should receive a response like the following:

```json
{"method": "TOKEN_AUTH_OK", "name":"Hello World”, Bot","ID":"90091784056528980","reference":15269906159119, "date":1533216558322}
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
