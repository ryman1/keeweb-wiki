### Compatibility
Q: Is it compatible to KeePass? What about KeePassX or other clients?  
A: File format should be 100% compatible but I test integration with KeePass only. Other clients should be ok, if not, please, open an issue and it will be fixed. Only kdbx (KeePass v2), not kdb (KeePass v1) is supported. You can use KeePass to convert between them.  

### Security
Q: Is it secure?  
A: The app makes no external requests, it's completely offline. It doesn't contain and will never contain any statistics collection scripts, analytics, ads and other slow and disturbing stuff like that. The only request this app performs is version check which can be disabled in app settings, and it's done via HTTPS. The other behaviour is not different from usual desktop or web apps.  

Q: Can other pages in browser or insecure plugins access my passwords?  
A: Other pages must have no access to it. If you have some strange plugins in your browser installed, they might have access to data on pages, depending on plugin permissions. If you think there are some plugins/extensions in your browser which you don't trust, it's better to use desktop version and never enter passwords in that browser on any website (or just remove such plugins).  

Q: Why is there a security warning on Windows? Why Mac might disallow opening the app? Why the publisher is Unknown?  
A: There's no malware inside. The code is not signed because it costs money (this is not one-time fee), and for now I'm not going to pay yearly for a free app.  

### Sync
Q: What is offline?  
A: A web page cannot open files from your filesystem, so they are cached. When you open an offline file, cached state will be used.  

Q: What will happen if I change password in offline?  
A: For now, you have to re-open this file on other KeeWeb instances, this will be fixed.  

### Self-hosting
Q: Which server should I use?  
A: Any static server (nginx, apache, IIS, ...). The app is single HTML file which is executed in browser. [Here](https://github.com/antelle/keeweb#self-hosting) you will find some useful tips about self-hosting.  

Q: Is it possible to use Dropbox in self-hosted version?  
A: [Yes](https://github.com/antelle/keeweb/issues/19#issuecomment-154710697) but you have to create your own Dropbox app.  

### Extensions
Q: Will KeePass plugins be ever supported?  
A: No. They are not cross-platform and depends on KeePass libs. But I'm planning to support javascript plugins and CSS themes.  

Q: I want a feature.  
A: You can [either open a feature request](https://github.com/antelle/keeweb/issues/new?title=[Feature%20request]%20), or sumbit a pullreq with it (but please, contact the author first, because I have strong opinion against some features, e.g. entry background color).  

Q: The feature I want is very strange, or useful for me only, or conflicts with author's product vision or roadmap, and I'm ready to pay for it.  
A: Please, [contact](http://antelle.net/) the author.  