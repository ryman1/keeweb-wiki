### General
Q: Password manager in browser?  
A: If you prefer desktop version, there are [desktop clients](https://github.com/keeweb/keeweb/releases/latest) for all major OS: Mac, Windows and Linux. It's called Kee*Web* because it's created with web technologies.  

Q: Yet another KeePass client app? Why? What is the motivation?  
A: Because there's no cross-platform app with good ui and no browser version.  

### Compatibility
Q: Is it compatible with KeePass? What about KeePassX or other clients?  
A: File format is compatible and all features important to users are supported. If something is not working, please open an issue, and it will be investigated. Only kdbx (KeePass v2), not kdb (KeePass v1) is supported. You can use KeePass to convert between them.  

Q: What will happen, if KeeWeb gets abandoned?  
A: You can switch to any other KeePass-compatible client. We don't lock you in.  

Q: WebDAV is not working  
A: Most probably CORS is not enabled on your server. Please check out this [page](WebDAV-Config).  

### Security
Q: Is it secure?  
A: The app makes no external requests unless you ask for it explicitly, it's completely offline, all your data is stored locally and never sent by network. It doesn't contain and will never contain any statistics collection scripts, analytics, ads and other slow, disturbing and insecure stuff like that. The only request this app performs is version check which can be disabled in app settings, and it's done via HTTPS. The other behaviour is not different from usual desktop or web apps.  

Q: Can other pages in browser or insecure plugins access my passwords?  
A: Other pages must have no access to it. If you have some strange plugins in your browser installed, they might have access to data on pages, depending on plugin permissions.  

Q: Does it have any protection from trojans or key loggers?  
A: No. As any password manager. No app can have protection against targeted malware running with superuser privileges (which is typical for malware). Don't believe in bullshit and don't use password managers if it's common for you to clean out trojans from your computer during an antivirus check. You can read more in [KeePass FAQ](http://keepass.info/help/base/security.html#secspecattacks).  

Q: I have forgot my password or lost a keyfile.  
A: There's no way to restore. All your data is encrypted with your password and stored inside kdbx on your computer.  

### Sync
Q: What is offline?  
A: A web page cannot open files from your filesystem, so they are cached. When you open an offline file, cached state will be used.  

Q: What will happen if I change a file saved to cloud on another computer?  
A: Changes will be loaded by all peers once you save them or auto-save happens.  

Q: I've changed WebDAV password and cannot sync my db anymore.  
A: Remove it and add again. Don't forget to download it if there are any changes.  

Q: Is WebDAV password stored in cleartext?  
A: No. It's not possible to decrypt it without access to kdbx.  

### Update
Q: How to use proxy server for this app?  
A: The app will use proxy settings from system-wide config. If you want to use custom setting for this app, start it with `--proxy-server` command-line switch.  

Q: Are desktop updates secure?  
A: Yes, updates are delivered only via HTTPS and checked for a valid signature before unpacking.  

### Plugins

Q: Are plugins secure?  
A: It depends. Some plugins are developed by KeeWeb authors, they are 100% secure and marked with a special sign. We don't give any guarantee about other plugins. Install them at your own risk. However, KeeWeb guarantees secure plugin delivery: if you trust plugin author, the installation is safe.  

Q: Can I load plugin code by its url to inspect it before installing?  
A: No. It's possible to distinguish between you and KeeWeb loading plugin and give you two different versions.  

### Self-hosting
Q: Which server should I use?  
A: Any static server (nginx, apache, IIS, ...). The app is single HTML file which is executed in browser. [Here](https://github.com/keeweb/keeweb#self-hosting) you will find some useful tips about self-hosting.  

Q: Is it possible to use Dropbox in self-hosted version?  
A: Yes but you have to create your own Dropbox app.  

### Features
Q: Will KeePass plugins be ever supported?  
A: No. They are not cross-platform and depend on KeePass libs.  

Q: When will my issue be fixed?  
A: Please check the Milestone field for this issue. Possible values:
- vN.M.x: in the upcoming hotfix for currently published version
- vN.M: in vN.M release, according to the [roadmap](TODO)
- vN.x: in some release after current release
- Future: I don't know, maybe never

If the issue is assigned, this means that it's already implemented and you can test it on [beta.keeweb.info](https://beta.keeweb.info)  

Q: I want a feature.  
A: You can [either open a feature request](https://github.com/keeweb/keeweb/issues/new?title=[Feature%20request]%20), or submit a pull request with it.  

Q: The feature I want is very strange, or useful for me only, or conflicts with author's product vision or roadmap, and I'm ready to pay for it.  
A: Please, [contact](http://antelle.net/) the author (please note, the price will be high; expected requests are corporate features, enterprise customisation, private installations an so on, and not _plz make this feature faster for a cup of coffee_).  

Q: And if I donate?  
A: Donation is a way to say "thank you", it does not imply any type of service contract.  