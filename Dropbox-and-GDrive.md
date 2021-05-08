How to make Dropbox and Google Drive work on your server?
## Dropbox

1. Go to Dropbox Developers: https://www.dropbox.com/developers  
   <img src="https://habrastorage.org/files/476/46a/e60/47646ae607ac48188fecb5ac3fc842c7.png"/>
2. Create your app  
   <img src="https://habrastorage.org/files/d33/233/587/d33233587d134e0bb130ad08e66a4405.png"/>
3. Choose Dropbox API, not business API, and the desired Dropbox access  
   <img src="https://habrastorage.org/files/100/dbb/0af/100dbb0afdf84635b834366a8b558ef9.png"/>
4. Setup URLs (the redirect uri is `https://<your host>/oauth-result/dropbox.html`)  
   <img src="https://habrastorage.org/files/6c3/1de/8e3/6c31de8e307545eb99d4a938bb65362c.png"/>
5. Add Dropbox app key to KeeWeb, either as `dropboxAppKey` [config](Configuration#json-app-config) field, or in the UI
6. Click Show secret and add it to KeeWeb in the same way, the config field is called `dropboxSecret`
7. If it doesn't work, make sure that PKCE is enabled and custom scopes are configured on the Permissions tab
8. To add a file from Dropbox folder using config.json, use the following snippet:
   ```
   {
       "settings": {
           "dropboxAppKey": "APP_KEY_FROM_DROPBOX",
           "dropboxSecret": "APP_SECRET_FROM_DROPBOX"
       },
       "files": [{
           "storage": "dropbox",
           "name": "Your file name",
           "path": "/your_file.kdbx"
       }]
   }
   ```

## Google Drive

1. Go to Google Developer Console: https://console.developers.google.com/
2. Add a project  
   <img src="https://habrastorage.org/files/f25/825/dd0/f25825dd0beb4f6ebe0e20a083406363.png"/>
3. Create OAuth Client ID  
   <img src="https://habrastorage.org/files/4b4/8e8/fbb/4b48e8fbb1e04c95910bcdb4e993861d.png"/>
4. Choose Web application  
5. Setup URLs (the redirect uri is `https://<your host>/oauth-result/gdrive.html`)  
   <img src="https://habrastorage.org/files/8fb/e84/e08/8fbe84e08cfd4fdc987cd3b430d030ee.png"/>  
   <img src="https://habrastorage.org/files/df5/26a/064/df526a0649c9493aa1dffd3e0454f96c.png"/>

   URL here is the exact URL where you load KeeWeb: if it has index.html, add index.html there too.
6. Set Client ID and Secret in KeeWeb, in `gdriveClientId` and `gdriveClientSecret` fields of your [config](Configuration#json-app-config)
7. You will need to either verify your domain, or add yourself to [Risky Access Permissions By Unreviewed Apps](https://groups.google.com/forum/#!forum/risky-access-by-unreviewed-apps) Google Group (more about Google Drive in [this issue](https://github.com/keeweb/keeweb/issues/667)).
8. [Enable](https://console.developers.google.com/apis/library) Drive API for your project.

## OneDrive

1. Create an app in [Azure Portal](https://portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade):  
  <img width="923" alt="Azure Portal" src="https://user-images.githubusercontent.com/633557/117539118-7049a180-b009-11eb-8a82-763d0c713d94.png" />

2. Choose the desired audience and name, and click Register:  
  <img width="923" alt="App name" src="https://user-images.githubusercontent.com/633557/117539144-9a9b5f00-b009-11eb-848c-1999c0d66f30.png" />

3. Select Authentication and click Add Platform:  
  <img width="923" alt="Platform" src="https://user-images.githubusercontent.com/633557/117539221-f960d880-b009-11eb-9602-e7c8132901ca.png" />

4. Choose "Single-page application"   

5. Enter a redirect URI as `https://your-domain/oauth-result/onedrive.html`:  
  <img width="579" alt="Domain" src="https://user-images.githubusercontent.com/633557/117539311-58265200-b00a-11eb-800e-8cf559ca5054.png" />

6. Click Configure   

7. Add the following API permissions: `Files.Read.All`, `Files.ReadWrite.All`, `Directory.Read.All` from `Microsoft Graph` section:  
  <img width="1017" alt="Permissions" src="https://user-images.githubusercontent.com/633557/117539562-88babb80-b00b-11eb-9b75-b4f38b8ccc68.png" />

8. Make sure the permission screen looks like this:  
  <img width="925" alt="API permissions" src="https://user-images.githubusercontent.com/633557/117539622-ca4b6680-b00b-11eb-9a64-5b32ecb7a217.png" />

9. Copy the `Application (client) ID` value from the Overview screen and put it in KeeWeb's `config.json` under `onedriveClientId` key  

10. If desired, your can also set up the secret in "Certificates and secrets" section and save it as `onedriveClientSecret`, but it doesn't seem to change anything