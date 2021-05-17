Browser auto-fill is more convenient with extensions. Compared to auto-type, they provide deeper and more convenient integration.

KeeWeb Connect is developed here: https://github.com/keeweb/keeweb-connect  

The extension can be installed from the official stores, depending on your browser:

- [Chrome](https://chrome.google.com/webstore/detail/keeweb-connect/pikpfmjfkekaeinceagbebpfkmkdlcjk)
- [Firefox](https://addons.mozilla.org/firefox/addon/keeweb-connect/)
- [Edge](https://microsoftedge.microsoft.com/addons/detail/keeweb-connect/nmggpehkjmeaeocmaijenpejbepckinm)
- [Safari](https://apps.apple.com/app/keeweb-connect/id1565748094)
- Other browsers: [how to set up](#other-browsers)

The main components of the extension are:

Extension button, provides one-click auto-fill and submit:

<img width="312" alt="KeeWeb Connect button" src="https://user-images.githubusercontent.com/633557/117531307-31ecbc00-afe2-11eb-902b-23fa16c9d6f1.png" />

Extension menu, gives an option to choose the desired action:

<img width="756" alt="KeeWeb Connect menu" src="https://user-images.githubusercontent.com/633557/117531275-0a95ef00-afe2-11eb-9ffa-0ca0b6a84762.png" />

Extension settings page:

<img width="922" alt="KeeWeb Connect Settings" src="https://user-images.githubusercontent.com/633557/117531461-df5fcf80-afe2-11eb-9ed4-87ee9acfa339.png" />


## How it works

In one picture:

<img width="776" alt="KeeWeb Connect communication" src="https://user-images.githubusercontent.com/633557/117531084-1503b900-afe1-11eb-9c80-97894433ce38.png" />

To be able to use the extension, enable the integration in KeeWeb settings:

<img width="1136" alt="KeeWeb Settings" src="https://user-images.githubusercontent.com/633557/117531536-26e65b80-afe3-11eb-8326-1a2be6a0ea1f.png">

## Other browsers

To use KeeWeb Connect in other browsers, first, you need the extension itself. Depending on your browser type, you can install it either from the [Google Chrome Web Store](https://chrome.google.com/webstore/detail/keeweb-connect/pikpfmjfkekaeinceagbebpfkmkdlcjk), or from the [Mozilla Firefox extension gallery](https://addons.mozilla.org/firefox/addon/keeweb-connect/). It's not possible to install from stores? You can also download the extension from [GitHub releases](https://github.com/keeweb/keeweb-connect/releases/latest).

Next thing you need to do is configuring connection with KeeWeb.

KeeWeb Connect exchanges data with KeeWeb using a secure communication technology called [Native Messaging](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/Native_messaging). While KeeWeb can automatically set up native messaging for popular browsers, it requires a bit of manual effort for others.

1. Create a file called `net.antelle.keeweb.keeweb_connect.json` (where? check in the [manifest setup guides](#Native-messaging-manifest-setup-guides) below:

For Chromium-based browsers (such as Vivaldi, Opera, Brave, ...):
```json
{
    "allowed_origins": [
        "chrome-extension://pikpfmjfkekaeinceagbebpfkmkdlcjk/"
    ],
    "description": "KeeWeb native messaging host",
    "name": "net.antelle.keeweb.keeweb_connect",
    "type": "stdio",
    "path": "/path/to/keeweb/keeweb-native-messaging-host"
}
```

For browsers based on Firefox (you may also hear words "Mozilla" or "Gecko" about them):
```json
{
    "allowed_extensions": [
        "keeweb-connect@keeweb.info"
    ],
    "description": "KeeWeb native messaging host",
    "name": "net.antelle.keeweb.keeweb_connect",
    "type": "stdio",
    "path": "/path/to/keeweb/keeweb-native-messaging-host"
}
```

Note the `path` property. Make sure the file exists there and is executable. On Windows add `.exe` and don't forget about double slashes, for example, it can be something like:
```
    "path": "C:\\Program Files\\KeeWeb\\keeweb-native-messaging-host.exe"
```

On macOS it will be inside the app bundle, for example:
```
    "path": "/Applications/KeeWeb.app/Contents/MacOS/util/keeweb-native-messaging-host"
```

2. For Windows: add a registry key as described in the guide below

3. Some browsers may need a restart

4. Still doesn't work? Open the extensions page and inspect the "background page" of the extension, the Console tab there can give a clue

## Native messaging manifest setup guides:
- [Google Chrome](https://developer.chrome.com/docs/apps/nativeMessaging/#native-messaging-host-location)
- [Mozilla Firefox](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/Native_messaging#setup)
- [Microsoft Edge](https://docs.microsoft.com/en-us/microsoft-edge/extensions-chromium/developer-guide/native-messaging?tabs=windows#step-3---copy-the-native-messaging-host-manifest-file-to-your-system)
