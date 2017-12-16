# Command-line switches

In order to control some features of desktop app, you can use the following command-line switches:  
`--disable-updater` totally disable updater and hide Update option in app settings  
`--proxy-server=1.2.3.4:80` use proxy 1.2.3.4:80 instead of system-wide setting  
`--html-path=path` path to content files (useful for development)  
`--devtools` show devtools on start  

You can also specify a file you would like to open as the last argument:  
`KeeWeb my.kdbx`

Or, with keyfile:
`KeeWeb --keyfile=keyfile.key my.kdbx`

# JSON app config

The webapp can load settings from JSON config located on your server. There are two options to specify config location, whichever you like more:
- add `config` url parameter: `https://your-keeweb-deployment-url/?config=your-config.json`
- set `kw-config` meta-tag value: replace `(no-config)` string in app index.html with your config url

Config fields description (all fields are optional; please don't copy exactly this config; add only necessary fields and remove all comments):
```javascript
{
  "settings": {
    "theme": "fb", // UI theme, possible values: fb (flat blue), wh (white), hc (high contrast) and other
    "locale": "en", // language
    "expandGroups": true, // show entries from all subgroups
    "listViewWidth": null, // list view width
    "menuViewWidth": null, // left menu width
    "tagsViewHeight": null, // tags menu section height
    "autoUpdate": "install", // auto-update options: "install", "check", ""
    "autoSave": true, // auto-save open files
    "rememberKeyFiles": false, // remember keyfiles selected on Open page
    "idleMinutes": 15, // app lock timeout after inactivity
    "tableView": false, // view entries as table, instead of list
    "colorfulIcons": false, // use colorful custom icons, instead of grayscale
    "lockOnCopy": false, // lock app on password copy
    "skipOpenLocalWarn": false, // don't show warning for local files
    "hideEmptyFields": false, // hide empty entry fields
    "skipHttpsWarning": false, // don't show insecure http connection warning
    "demoOpened": false, // think that demo has already been opened, hide Demo button inside More
    "fontSize": 0, // global font size, possible options: 0, 1, 2
    "tableViewColumns": null, // columns inside table view (complex option, use with care)
    "generatorPresets": null, // user-defined generator presets (complex option, use with care)
    "cacheConfigSettings": false, // allow to start the app if the config is not available

    "canOpen": true, // show Open button
    "canOpenDemo": true, // show Demo button
    "canOpenSettings": true, // show Settings button
    "canCreate": true, // show Create button
    "canImportXml": true, // show Import XML button

    "dropbox": true, // enable Dropbox
    "dropboxFolder": null, // default folder path
    "dropboxAppKey": null, // custom app key

    "webdav": true, // enable WebDAV
    "webdavSaveMethod": "move", // how to save files with WebDAV ("move" or "put")

    "gdrive": true, // enable Google Drive
    "gdriveClientId": null, // custom client id

    "onedrive": true, // enable OneDrive
    "onedriveClientId": null // custom client id
  },
  "files": [{ // pre-defined files that will appear on Open page
    "storage": "webdav", // dropbox, webdav, etc...
    "name": "My file", // file name, as it will be displayed in UI
    "path": "webdav-url", // full path to file, including file name, e.g. WebDAV url
    "options": { "user": "", "password": "" } // only for WebDAV, server auth details
  }],
  "showOnlyFilesFromConfig": false, // allow to open only files from config, remove previously opened files
  "plugins": [{ // if you want to auto-install some plugins
    "url": "" // plugin url (you can also add "manifest", if to enforce publicKey validation)
  }]
}
```

To get currently applied settings, run this in browser console:
```javascript
kw.settings.get();
```

If it doesn't start with your config:
- open DevTools in browser and inspect the error
- validate your config, e.g. here: https://jsonlint.com/

# App settings js API

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