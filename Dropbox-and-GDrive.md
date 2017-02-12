How to make Dropbox and Google Drive work on your server?
## Dropbox

1. Go to Dropbox Developers  
<img src="https://habrastorage.org/files/476/46a/e60/47646ae607ac48188fecb5ac3fc842c7.png"/>
2. Create your app  
<img src="https://habrastorage.org/files/d33/233/587/d33233587d134e0bb130ad08e66a4405.png"/>
3. Choose Dropbox App, not for business, and the desired Dropbox access  
<img src="https://habrastorage.org/files/100/dbb/0af/100dbb0afdf84635b834366a8b558ef9.png"/>
4. Setup URLs  
<img src="https://habrastorage.org/files/6c3/1de/8e3/6c31de8e307545eb99d4a938bb65362c.png"/>
5. Add Dropbox app id to KeeWeb, either as `dropboxAppKey` [config](Configuration#json-app-config) field, or in the UI

## Google Drive

1. Go to Google Developer Console: https://console.developers.google.com/
2. Create OAuth Client ID  
<img src="https://habrastorage.org/files/4b4/8e8/fbb/4b48e8fbb1e04c95910bcdb4e993861d.png"/>
3. Choose Web application  
4. Setup URLs  
<img src="https://habrastorage.org/files/8fb/e84/e08/8fbe84e08cfd4fdc987cd3b430d030ee.png"/>
5. Find your Google Drive Client ID
<img src="https://habrastorage.org/files/df5/26a/064/df526a0649c9493aa1dffd3e0454f96c.png"/>
6. Set Client ID in KeeWeb, either in config, in `gdriveClientId` field of your [config](Configuration#json-app-config)