# Command-line switches

In order to control some features of desktop app, you can use the following command-line switches:  
`--disable-updater` totally disable updater and hide Update option in app settings  
`--proxy-server=1.2.3.4:80` use proxy 1.2.3.4:80 instead of system-wide setting  
`--html-path=path` path to content files (useful for development)  

You can also specify the file which you would like to open as the last argument:  
`KeeWeb my.kdbx`

# JSON app config

The webapp can load settings from JSON config located on your server. To load it, add `config` url parameter:  
```
https://your-keeweb-deployment-url/?config=your-config.json
```
Contents of this config must be a valid JSON file with keys from [app settings](https://github.com/keeweb/keeweb/blob/master/app/scripts/models/app-settings-model.js#L7).  
Once loaded, settings are saved to local storage, so the users will not have to add `config` url parameter every time they use the app.

# App settings js API

There's an interface for accessing app settings from [this list](https://github.com/keeweb/keeweb/blob/master/app/scripts/models/app-settings-model.js#L8):
```javascript
var value = kw.settings.get('setting');
var allSettings = kw.settings.get();
kw.settings.set('setting', value);
kw.settings.set({ setting: value });
```
Values you set here are saved and applied immediately. Please be careful.  
You can call these methods from dev console.