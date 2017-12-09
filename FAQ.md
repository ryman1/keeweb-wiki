### General
Q: Password manager in a browser?  
A: If you prefer desktop version, there are [desktop clients](https://github.com/keeweb/keeweb/releases/latest) for all major OS: Mac, Windows, and Linux. It's called Kee*Web* because it's created with web technologies.  

Q: Yet another KeePass client app? Why? What is the motivation?  
A: Because there's no cross-platform app with good UI and no browser version.  

Q: What is the geography of KeeWeb?  
A: KeeWeb is made in Amsterdam, the Netherlands. Websites and source code are hosted in the U.S. on GitHub servers, the content is delivered through CloudFlare, Akamai and Amazon CDNs. Domain names are registered in the U.S.  

### Compatibility
Q: Is it compatible with KeePass? What about KeePassX or other clients?  
A: File format is compatible and all features important to users are supported. If something is not working, please open an issue, and it will be investigated. Only kdbx (KeePass v2), not kdb (KeePass v1) is supported. You can use KeePass to convert between them.  

Q: What will happen if KeeWeb gets abandoned?  
A: You can switch to any other KeePass-compatible client. We don't lock you in.  

Q: WebDAV is not working  
A: Most probably CORS is not enabled on your server. Please check out this [page](WebDAV-Config).  

### Security
Q: Does it send my data anywhere?  
A: The app never sends your data over network, unless you ask for it explicitly, it's completely offline, all your data is stored locally and never sent by network. It doesn't contain and will never contain any statistics collection scripts, analytics, ads and other slow, disturbing and insecure stuff like that.  

Q: Can other pages in my browser or insecure plugins access my passwords?  
A: Other pages must have no access to it. If you have some strange plugins in your browser installed, they might have access to data on pages, depending on plugin permissions.  

Q: Does it have full protection from trojans or keyloggers?  
A: No. As any password manager. No app can have protection against targeted malware running with superuser privileges. Don't believe in bullshit and don't use password managers if it's common for you to clean out trojans from your computer during an antivirus check. You can read more in [KeePass FAQ](http://keepass.info/help/base/security.html#secspecattacks).  

Q: I have forgot my password or lost a keyfile.  
A: There's no way to unlock your file. All your data is encrypted with your password and stored inside kdbx on your computer.  

### Sync
Q: What is offline?  
A: A web page cannot open files from your filesystem, so they are cached. When you open an offline file, a cached state will be used.  

Q: What will happen if I change a file saved to cloud on another computer?  
A: Changes will be loaded by all peers once you save them or auto-save happens.  

Q: I've changed WebDAV password and cannot sync my db anymore.  
A: Remove it and add again. Don't forget to download it if there are any changes.  

Q: Is WebDAV password stored in cleartext?  
A: No. It's not possible to decrypt it without access to kdbx.  

### Update
Q: How to use a proxy server with this app?  
A: The app will use proxy settings from system-wide config. If you want to use custom setting for this app, start it with `--proxy-server` command-line switch.  

Q: Are desktop updates secure?  
A: Yes, updates are delivered only via HTTPS and checked for a valid signature before unpacking.  

### Plugins
Q: Will KeePass plugins be ever supported?  
A: No. They are not cross-platform and depend on KeePass libs.  

Q: Are plugins secure?  
A: Yes. KeeWeb checks plugins signatures and doesn't allow to install unverified plugins. 3rdparty plugins can be enabled only if you configure KeeWeb to allow them.  

### Self-hosting
Q: Which server should I use?  
A: Any static server (nginx, apache, IIS, ...). The app is single HTML file loaded in a browser. [Here](https://github.com/keeweb/keeweb#self-hosting) you will find some useful tips about self-hosting.  

Q: Is it possible to use Dropbox in self-hosted version?  
A: Yes but you will have to [create](https://github.com/keeweb/keeweb/wiki/Dropbox-and-GDrive) your own Dropbox app.  

### Features
Q: When will my issue be fixed?  
A: Please check the Milestone field for this issue. Possible values:
- vN.M.x: in the upcoming hotfix for currently published version
- vN.M: in vN.M release, according to the [roadmap](TODO)
- vN.x: in some release after current release
- Future: I don't know, maybe never

If the issue is assigned, this means that it's already implemented and you can test it on [beta.keeweb.info](https://beta.keeweb.info)  

Q: I want a feature.  
A: You can [either open a feature request](https://github.com/keeweb/keeweb/issues/new?title=[Feature%20request]%20) or submit a pull request with it.  

Q: The feature I want is very strange, or useful for me only, or conflicts with author's product vision or roadmap, and I'm ready to pay for it.  
A: Please, [contact](http://antelle.net/) the author (please note, the price will be high; expected requests are corporate features, enterprise customization, private installations an so on, and not _plz make this feature faster for a cup of coffee_).  

Q: And if I donate?  
A: Donation is a way to say "thank you", it does not imply any type of service contract.  