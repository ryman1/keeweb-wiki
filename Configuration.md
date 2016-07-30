# Command-line switches

In order to control some features of desktop app, you can use the following command-line switches:  
`--disable-updater` totally disable updater and hide Update option in app settings  
`--proxy-server=1.2.3.4:80` use proxy 1.2.3.4:80 instead of system-wide setting  
`--html-path=path` path to content files (useful for development)  

You can also specify the file which you would like to open as the last argument:  
`KeeWeb my.kdbx`

# JSON app config

⚠️ some configuration options are new and will work only in v1.3 release, or beta version  

The webapp can load settings from JSON config ([here's an example config](https://github.com/keeweb/keeweb/blob/develop/util/config-example.json)) located on your server. There are two options to specify config location, whichever you like more:
- add `config` url parameter: `https://your-keeweb-deployment-url/?config=your-config.json`
- set `kw-config` meta-tag value: replace `(no-config)` string in app index.html with your config url

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