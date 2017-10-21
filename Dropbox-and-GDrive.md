How to make Dropbox and Google Drive work on your server?
## Dropbox

1. Go to Dropbox Developers: https://www.dropbox.com/developers  
   <img src="https://habrastorage.org/files/476/46a/e60/47646ae607ac48188fecb5ac3fc842c7.png"/>
2. Create your app  
   <img src="https://habrastorage.org/files/d33/233/587/d33233587d134e0bb130ad08e66a4405.png"/>
3. Choose Dropbox API, not business API, and the desired Dropbox access  
   <img src="https://habrastorage.org/files/100/dbb/0af/100dbb0afdf84635b834366a8b558ef9.png"/>
4. Setup URLs  
   <img src="https://habrastorage.org/files/6c3/1de/8e3/6c31de8e307545eb99d4a938bb65362c.png"/>

   add `https://app.keeweb.info` to the list of OAuth URLs as well
5. Add Dropbox app key to KeeWeb, either as `dropboxAppKey` [config](Configuration#json-app-config) field, or in the UI

## Google Drive

1. Go to Google Developer Console: https://console.developers.google.com/
2. Add a project  
   <img src="https://habrastorage.org/files/f25/825/dd0/f25825dd0beb4f6ebe0e20a083406363.png"/>
3. Create OAuth Client ID  
   <img src="https://habrastorage.org/files/4b4/8e8/fbb/4b48e8fbb1e04c95910bcdb4e993861d.png"/>
4. Choose Web application  
5. Setup URLs  
   <img src="https://habrastorage.org/files/8fb/e84/e08/8fbe84e08cfd4fdc987cd3b430d030ee.png"/>  
   <img src="https://habrastorage.org/files/df5/26a/064/df526a0649c9493aa1dffd3e0454f96c.png"/>
6. Set Client ID in KeeWeb, in `gdriveClientId` field of your [config](Configuration#json-app-config)
7. You will need to either verify your domain, or add yourself to [Risky Access Permissions By Unreviewed Apps](https://groups.google.com/forum/#!forum/risky-access-by-unreviewed-apps) Google Group (more about Google Drive in [this issue](https://github.com/keeweb/keeweb/issues/667)).
8. [Enable](https://console.developers.google.com/apis/library) Drive API for your project.