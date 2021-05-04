🚧  This page is going to change! Next version of KeeWeb will provide a better way of browser integration.

Browser AutoFill is possible with extensions compatible with KeePassHTTP.  

But first, we would like to warn you about the [criticism of KeePassHTTP security](https://github.com/pfn/keepasshttp/issues/258), that's why this extension not enabled by default in KeeWeb. [Auto-Type](https://github.com/keeweb/keeweb/wiki/Auto-Type) can be a solid alternative, moreover, it works with other apps, not only browsers. It's recommended to try auto-type approach first.

## KeeWebHttp

AutoFill is available only in Desktop apps.
1. Go to Settings &rarr; Plugins and load the plugin gallery:
![plugins](https://user-images.githubusercontent.com/633557/34461926-b0ba929c-ee38-11e7-9d71-3c47fa0cd3c7.png)
2. Find KeeWebHttp plugin and install it:
![http](https://user-images.githubusercontent.com/633557/34461924-b069df50-ee38-11e7-851a-548cc648c9fd.png)
3. It's recommended to activate automatic update check to get updates and security fixes:
![installed](https://user-images.githubusercontent.com/633557/34461947-f50025e8-ee38-11e7-9b05-3631eb331bdd.png)

## Chrome

1. Install [KeePassHttp-Connector extension](https://chrome.google.com/webstore/detail/keepasshttp-connector/dafgdjggglmmknipkhngniifhplpcldb).
2. Go to its settings and click Connect:
![settings](https://user-images.githubusercontent.com/633557/34462051-49750146-ee3b-11e7-8fc7-1785e9b8b3ec.png)
3. Approve the request in KeeWeb:
![keeweb](https://user-images.githubusercontent.com/633557/34462026-ada43584-ee3a-11e7-9fc6-1bb240696512.png)
4. Make sure it's connected:
![connected](https://user-images.githubusercontent.com/633557/34462027-adcc24d6-ee3a-11e7-9324-2501f75c01e0.png)

## Safari

There's no extension at the moment. You can use auto-type to autofill passwords.

## Firefox

### KeePassHttp-Connector 

1. Install [KeePassHttp-Connector](https://addons.mozilla.org/en-US/firefox/addon/keepasshttp-connector/).
2. Click Connect button inside the extension popup:
![firefox](https://user-images.githubusercontent.com/633557/34462254-f500e40e-ee3f-11e7-8717-6f359a5ad51f.png)
3. Approve the request in KeeWeb:
![keeweb](https://user-images.githubusercontent.com/633557/34462026-ada43584-ee3a-11e7-9fc6-1bb240696512.png)
4. Check it on any website:
![check](https://user-images.githubusercontent.com/633557/34462271-3c931008-ee40-11e7-9ddd-35aa1fe2db89.png)

### KeePassHelper Password Manager

1. Install [KeePassHelper Password Manager](https://addons.mozilla.org/en-US/firefox/addon/keepasshelper/).
2. Click Lock button:
![firefox](https://user-images.githubusercontent.com/633557/34462319-3dd07360-ee41-11e7-9f60-2a08d8b4f93f.png)
3. Approve the request in KeeWeb:
![keeweb](https://user-images.githubusercontent.com/633557/34462026-ada43584-ee3a-11e7-9fc6-1bb240696512.png)
4. Check it:
![check](https://user-images.githubusercontent.com/633557/34462318-3da81f0a-ee41-11e7-82d7-27047a1f5abe.png)

## Other browsers

To use KeeWeb Connect in other browsers, first, you need the extension itself. Depending on your browser type, you can install it either from the [Google Chrome Web Store](https://chrome.google.com/webstore/detail/keeweb-connect/pikpfmjfkekaeinceagbebpfkmkdlcjk), or from the [Mozilla Firefox extension gallery](https://addons.mozilla.org/firefox/addon/keeweb-connect/). It's not possible to install from stores? You can also download the extension from [GitHub releases](https://github.com/keeweb/keeweb-connect/releases/latest).

Next thing you need to do is configuring connection with KeeWeb.

KeeWeb Connect exchanges data with KeeWeb using a secure communication technology called [Native Messaging](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/Native_messaging). While KeeWeb can automatically set up native messaging for popular browsers, it requires a bit of manual effort for others.

1. Create a file called `net.antelle.keeweb.keeweb_connect.json` (where? check in the guide below):

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

Note the `path` property. Make sure the file exists there and is executable. On windows add `.exe` and don't forget about double slashes, for example, it can be something like:
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

Native messaging manifest setup guides:
- [Google Chrome](https://developer.chrome.com/docs/apps/nativeMessaging/#native-messaging-host-location)
- [Mozilla Firefox](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/Native_messaging#setup)
- [Microsoft Edge](https://docs.microsoft.com/en-us/microsoft-edge/extensions-chromium/developer-guide/native-messaging?tabs=windows#step-3---copy-the-native-messaging-host-manifest-file-to-your-system)