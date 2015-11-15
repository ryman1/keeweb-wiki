### Compatibility
Q: Is it compatible to KeePass? What about KeePassX or other clients?  
A: File format should be 100% compatible but I test integration with KeePass only. Other clients should be ok, if not, please, open an issue and it will be fixed.  

### Security
Q: Is it secure?  
A: The app makes no external requests, it's completely offline. It doesn't contain and will never contain any statistics collection scripts, analytics, ads and other slow and disturbing stuff like that. The only request this app performs is version check which can be disabled in app settings.  

### Sync
Q: Why does the app overwrite my files in Dropbox?  
A: Because 2-way sync is [not implemented](https://github.com/antelle/keeweb#known-issues) for now, I'm working on it.  

Q: What is offline?  
A: A web page cannot open files from your filesystem, so they are cached. When you open an offline file, cached state will be used.  

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

Q: The feature I want is very strange or useful for me only and I'm ready to pay for it.  
A: Please, [contact](http://antelle.net/) the author.  