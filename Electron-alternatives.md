Electron is known to be less memory-efficient, so here's a comparison between Electron, WebView, and Qt, applied to KeeWeb. This evaluation was made in October 2020.

### About memory in macOS

[Mac OS X Memory Jargon](https://apple.stackexchange.com/questions/284464/how-is-the-memory-column-calculated-in-activity-monitor)  
[Mac OS X Process Memory Statistics](https://www.mikeash.com/pyblog/friday-qa-2009-06-19-mac-os-x-process-memory-statistics.html)  

Here we're using "Memory" value because it's the most realistic expectation of memory that would become available if you terminate the app.

### Electron
Our current electron app, production version, with the demo database open.

<img width="615" alt="KeeWeb" src="https://user-images.githubusercontent.com/633557/94986318-2a51ca00-055e-11eb-8aff-cf4506279b9c.png">

Total: ≈215 MB

### WebView
WebKit web view with app.keeweb.info, that's the theoretical minimum that we can get with this approach. Additionally there would be more memory consumed in the main process, what we can expect here is something around 25 MB.

What is actually a “WebView”? For this evaluation we selected the [minimal possible embedding](https://github.com/webview/webview) of a built-in WKWebView, it doesn’t have any node.js or other framework. Other options like Neutralino, Tauri, etc... would just use more memory compared to it.

<img width="615" alt="WebView" src="https://user-images.githubusercontent.com/633557/94986319-30e04180-055e-11eb-9a76-70117af26148.png">

Total: ≈112 MB  
What it would be if missing parts are implemented: ≈140 MB

### Qt

KeePassXC with the same demo database open. They have a minimalistic user interface without animations, transitions, transparency, rich icons, and other resource-consuming elements of graphic design that we have in KeeWeb. A rough approximation is that implementing them with Qt would require extra 20 MB.  

<img width="834" alt="KeePassXC" src="https://user-images.githubusercontent.com/633557/94986320-35a4f580-055e-11eb-91d1-c052bebd76ac.png">

Total: ≈118 MB  
With approximated UI implementation: ≈140 MB  

There are additional processes on the screenshot above, they're not included in this metric because they're also present in other apps.

### Environment

All testing was done on macOS Catalina without memory pressure, with a demo database that you can find in KeeWeb.

### Conclusion

Quick comparison gives us the following results:

<img width="527" alt="KeeWeb Memory" src="https://user-images.githubusercontent.com/633557/94991497-d2c65500-0583-11eb-91d8-5f2c1d0abde1.png">

If we compare the filesystem space:

<img width="527" alt="KeeWeb Filesystem" src="https://user-images.githubusercontent.com/633557/94990520-19fd1780-057d-11eb-8ab5-70f62a794dcc.png">

Download size impact:

<img width="527" alt="KeeWeb download size" src="https://user-images.githubusercontent.com/633557/94990553-5cbeef80-057d-11eb-8655-2604f8df199d.png">


So, replacing Electron with either WebView or Qt would reduce memory consumption by ≈70 MB and save ≈100 MB of disk space. The difference between all of them (Electron, WebView, Qt) in terms of performance is negligible.

We're not concerned much about disk space since extra 100 MB doesn't matter nowadays (which is arguable but that's our opinion), while reducing memory requirements would be nice.

In terms of development effort, rewriting the app in Qt is equal to full re-creation from scratch, this doesn’t sound realistic.

Switching to a WebView-based solution would need some work on app stability and implementation of missing features, but it has big wins in filesystem space and consumes 35% less memory. WebView feature support is however not great and it will also add limitations on our operating system coverage because we're using latest web technologies, such as WebAssembly and WebCrypto.

Apart from this, there's some stigma around Electron. People are complaining about memory-hungry apps while attributing their high resource usage to the framework. Sometimes they don't know that a certain app is built on Electron even they're happily using it (for example, VSCode).

### Related

[Why Slack switched to Electron](https://slack.engineering/building-hybrid-applications-with-electron/)

### Decision

Right now the decision is not to migrate, KeeWeb continues using Electron. Having a stable app built on a mature framework and better support of older operating systems is more important compared to extra 70 MB of memory and 100 MB of disk space.