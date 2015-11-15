### Compatibility
Q: Is it compatible to KeePass? What about KeePassX or other clients?  
A: File format should be 100% compatible but I test integration with KeePass. Other clients should be ok, if not, please, open an issue and it will be fixed.  

### Sync
Q: Why does the app overwrite my files in Dropbox?  
A: Because 2-way sync is [not implemented](https://github.com/antelle/keeweb#known-issues) for now, I'm working on it.  

Q: What is offline?  
A: A web page cannot open files from your filesystem, so they are cached. When you open an offline file, cached state will be used.  

### Self-hosting
Q: Which server should I use?  
A: Any static server (nginx, Apache, IIS, ...). The app is single HTML file which is executed in browser. Please, read [here](https://github.com/antelle/keeweb#self-hosting) about self-hosting  

Q: Is it possible to use Dropbox in self-hosted version?  
A: [Yes](https://github.com/antelle/keeweb/issues/19#issuecomment-154710697)  

### Extensions
Q: Will KeePass plugins be ever supported?  
A: No. They are not cross-platform and depends on KeePass libs. But I'm planning to support javascript plugins and CSS themes.  

Q: I want a feature.  
A: You can [either open a feature request](https://github.com/antelle/keeweb/issues/new?title=[Feature%20request]%20), or sumbit a pullreq with it (but please, contact the author first, because I have strong opinion against some features, e.g. entry background color).  

Q: I want a very strange custom feature and I'm ready to pay for it.  
A: Please, [contact](http://antelle.net/) the author.  