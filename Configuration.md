# Command-line switches

In order to control some features of desktop app, you can use the following command-line switches:  
`--disable-updater` totally disable updater and hide Update option in app settings  
`--proxy-server=1.2.3.4:80` use proxy 1.2.3.4:80 instead of system-wide setting  
`--html-path=path` path to content files (useful for development)  

You can also specify the file which you would like to open as the last argument:  
`KeeWeb my.kdbx`

# Advanced app settings

There's an interface for accessing app settings from [this list](https://github.com/antelle/keeweb/blob/master/app/scripts/models/app-settings-model.js#L8):
```javascript
var value = kwSettings.get('setting');
kwSettings.set('setting', value);
// which is equal to 
kwSettings.set({ setting: value });
```
You can call these methods from dev console.