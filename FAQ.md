## General
Q: Password manager in a browser?  
A: If you prefer desktop version, there are [desktop clients](https://github.com/keeweb/keeweb/releases/latest) for all major OS: Mac, Windows, and Linux. It's called Kee*Web* because it's created with web technologies.  

Q: Yet another KeePass client app? Why? What is the motivation?  
A: Because there's no cross-platform app with good UX and no browser version.  

Q: Are there plans to commercialize KeeWeb?  
A: KeeWeb will always remain free and ad-free, at least for personal use. If you're asked to pay for “full version” or “ad removal”, most probably it's a scam. The only official app is https://app.keeweb.info and desktop apps downloaded from https://keeweb.info or [GitHub releases](https://github.com/keeweb/keeweb/releases).  

Q: What is the geography of KeeWeb?  
A: KeeWeb is made in Amsterdam, the Netherlands. The source code is hosted on GitHub in the U.S. Website content is stored on Google Cloud in multiple locations in the EU (Finland, Belgium, Frankfurt, Netherlands) and delivered through CloudFlare content delivery network. Domain names are registered in the U.S.  

## Compatibility
Q: Is it compatible with KeePass? What about KeePassX or other clients?  
A: File format is compatible and all important features are supported. Only kdbx (KeePass v2), not kdb (KeePass v1) is supported. You can use KeePass to convert between them.  

Q: What will happen if KeeWeb gets abandoned?  
A: You can switch to any other KeePass-compatible client. We don't lock you in.  

Q: WebDAV is not working  
A: Most probably CORS is not enabled on your server. Please check out this [page](WebDAV-Config).  

Q: Is there an iOS app?  
A: Yes and no, please see different options described on [this page](iOS).  

## Security
Q: Does it send my data anywhere?  
A: The app never sends your data over network unless you ask for it explicitly, it's completely offline, all your data is stored locally and never sent by network. It doesn't contain and will never contain any statistics collection scripts, analytics, ads, and other slow, disturbing and insecure stuff like that.  

Q: Can other pages in my browser or untrusted plugins access my passwords?  
A: Other pages must have no access to it. If you have some strange plugins in your browser installed, they might have access to data on pages, depending on plugin permissions.  

Q: Does it have full protection from trojans or keyloggers?  
A: Although we have implemented some measures to prevent other apps from accessing KeeWeb, the protection is not full. There's no way to protect any app against targeted malware running with superuser privileges. You can read more in [KeePass FAQ](http://keepass.info/help/base/security.html#secspecattacks).  

Q: I have forgot my password or lost a keyfile.  
A: Unfortunately, there's no way to unlock your file. All your data is encrypted with your password and stored inside a kdbx file on your computer.  

Q: I've found a vulnerability.  
A: Please [contact the author](mailto:antelle.net@gmail.com).  

Q: Was there an audit of KeeWeb?  
A: Yes, in April-May 2020 [Hackmanit](https://www.hackmanit.de/) audited KeeWeb during their [Pro Bono](https://www.hackmanit.de/en/blog-en/80-pro-bono-penetration-test) penetration test program. All the vulnerabilities have been fixed in v1.4.2, the report will be published in June 2020.  

## Sync
Q: What will happen if I change a file saved to cloud storage on another computer?  
A: Changes will be loaded and merged by all peers once you save them or auto-save happens.  

Q: I've changed WebDAV password and cannot sync my db anymore.  
A: Remove and add it again. Don't forget to download it if there are any changes.  

Q: Is WebDAV password stored in cleartext?  
A: No. It's not possible to decrypt it without access to kdbx.  

## Update
Q: How to use a proxy server with this app?  
A: The app will use proxy settings from system-wide config. If you want to use custom setting for this app, start it with `--proxy-server` command-line switch.  

Q: Are desktop updates secure?  
A: Yes, updates are delivered only via HTTPS and checked for a valid signature before unpacking.  

## Plugins
Q: Will KeePass plugins be ever supported?  
A: No. They are not cross-platform and depend on KeePass libs.  

Q: Are plugins secure?  
A: Yes. KeeWeb checks plugins signatures and doesn't allow to install unverified plugins. 3rd-party plugins can be enabled only if you configure KeeWeb to allow them.  

## Self-hosting
Q: Which server should I use?  
A: Any static server (nginx, apache, IIS, ...). The app is a single HTML file loaded in a browser. [Here](https://github.com/keeweb/keeweb#self-hosting) you will find some useful tips about self-hosting.  

Q: Is it possible to use Dropbox in a self-hosted installation?  
A: Yes but you will have to [create](https://github.com/keeweb/keeweb/wiki/Dropbox-and-GDrive) your own Dropbox app.  

## Contribution

Q: I would like to participate in development, donate, or contribute in another way.  
A: Contribution guide can be found [here](https://github.com/keeweb/keeweb/blob/master/CONTRIBUTING.md).  

## Features
Q: When will my issue be fixed?  
A: Please check the Milestone field for this issue. Possible values:
- vN.M.x: in the upcoming hotfix for the currently published version
- vN.M: in vN.M release, according to the [roadmap](TODO)
- vN.x: in some release after the current release
- Future: I don't know, maybe never
- Future-Plugins: never, unless anyone contributes a plugin

If an issue is assigned, this means that it's already implemented and you can test it on [beta.keeweb.info](https://beta.keeweb.info)  

Q: I want a feature.  
A: You can [either open a feature request](https://github.com/keeweb/keeweb/issues/new?title=[Feature%20request]%20) or submit a pull request with it.  

Q: Will you implement it if I donate?  
A: Donation is a way to say “thank you”, it does not imply any type of service contract.  