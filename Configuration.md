## Command-line switches

In order to control some features of desktop app, you can use the following command-line switches:  
`--proxy-server=1.2.3.4:80` use proxy 1.2.3.4:80 instead of system-wide setting  
`--minimized` start the app minimized to tray or menubar  
`--devtools` show devtools on start  
`--startup-logging` print startup debugging messages to stdout  

You can also specify a file you would like to open as the last argument:  
```bash
KeeWeb my.kdbx
```

Or with a keyfile:
```bash
KeeWeb --keyfile=keyfile.key my.kdbx
```

## JSON app config

The webapp can load settings from JSON config located on your server. There are two options to specify config location, whichever you like more:
- add `config` url parameter: `https://your-keeweb-deployment-url/?config=your-config.json`
- set `kw-config` meta-tag value: replace `(no-config)` string in app index.html with your config url (please remember to clear browser cache to make sure changes are applied)

Config fields description (all fields are optional; please don't copy exactly this config; add only necessary fields and remove all comments):
```javascript
{
  "settings": {
    ...
  },
  "files": [{ // pre-defined files that will appear on Open page
    "storage": "webdav", // dropbox, webdav, other cloud storage providers
    "name": "My file", // file name, as it will be displayed in UI
    "path": "webdav-url", // full path to file, including file name, e.g. WebDAV url
    "options": { "user": "", "password": "" } // only for WebDAV, server auth details
  }],
  "showOnlyFilesFromConfig": false, // allow to open only files from config, remove previously opened files
  "plugins": [{ // if you want to auto-install some plugins
    "url": "" // plugin url (you can also add "manifest" to enforce publicKey validation)
  }]
}
```

Settings configuration options can be found [here](https://github.com/keeweb/keeweb/blob/master/app/scripts/const/default-app-settings.js#L1).

To get currently applied settings, run this in browser console:
```javascript
kw.settings.get();
```

If it doesn't start with your config:
- open DevTools in browser and inspect the error
- validate your config, e.g. here: https://jsonlint.com/

## App settings js API

There's an interface for accessing app settings from [this list](https://github.com/keeweb/keeweb/blob/master/app/scripts/models/app-settings-model.js#L8):
```javascript
var value = kw.settings.get('setting');
var allSettings = kw.settings.get();
kw.settings.set('setting', value);
kw.settings.set({ setting: value });
kw.settings.del('setting');
```
Values you set here are saved and applied immediately. Please be careful.  
You can call these methods from dev console.

## Portable

By default KeeWeb saves temporary files and configs into the default user's data directory. To create a completely portable installation:

1. put KeeWeb to the desired location, for example a USB drive
2. create a file called `keeweb-portable.json` with the following content:
    ```json
    {
        "userDataDir": "relative/path/to/data/dir"
    }
    ```
    (if you're on Windows, don't forget to escape slashes in JSON, like `"C:\\program files\\..."`).  
    The config should be located:
    - on windows: next to `KeeWeb.exe`
    - on Linux: next to `KeeWeb` (executable)
    - on macOS: next to `KeeWeb.app`
3. launch KeeWeb and make sure it creates the directory you specified in the config
