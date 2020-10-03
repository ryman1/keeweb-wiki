Electron is known to be less memory-efficient, so here's a comparison between Electron, WebView, and Qt. This evaluation was made in October 2020.

### About memory in macOS

[Mac OS X Memory Jargon](https://apple.stackexchange.com/questions/284464/how-is-the-memory-column-calculated-in-activity-monitor)  
[Mac OS X Process Memory Statistics](https://www.mikeash.com/pyblog/friday-qa-2009-06-19-mac-os-x-process-memory-statistics.html)  

Here we're using "Memory" value because it's the most realistic expectation of memory that would become available if you terminate the app.

### Electron
Our current electron app, production version, with the demo database open.

<img width="615" alt="KeeWeb" src="https://user-images.githubusercontent.com/633557/94986318-2a51ca00-055e-11eb-8aff-cf4506279b9c.png">

Total: ≈215 MB

### WebView
WebKit web view with app.keeweb.info, that's the theoretical minimum that we can get with this approach. Additionally there would be more memory consumed in the main process, a rough approximation is around 25 MB.

What is actually a “WebView”? For this evaluation we selected the [minimal possible embedding](https://github.com/webview/webview) of a built-in WKWebView, it doesn’t have any node.js or other framework. Other options like Neutralino, Tauri, etc... would just use more memory compared to it.

<img width="615" alt="WebView" src="https://user-images.githubusercontent.com/633557/94986319-30e04180-055e-11eb-9a76-70117af26148.png">

Total: ≈112 MB  
What it would be if missing parts are implemented: ≈140 MB

### Qt

KeePassXC with the same demo database open. They have a minimalistic user interface without animations, transitions, transparency, rich icons, and other resource-consuming elements of graphic design that we have in KeeWeb. A rough approximation is that implementing them with Qt would require extra 20 MB.  

<img width="834" alt="KeePassXC" src="https://user-images.githubusercontent.com/633557/94986320-35a4f580-055e-11eb-91d1-c052bebd76ac.png">

Total: ≈160 MB  
Approximated UI implementation: ≈180 MB  

### Environment

All testing was done on macOS Catalina without memory pressure, with a demo database that you can find in KeeWeb.

### Conclusion

Quick comparison gives us the following results:

|          | Observed | Calculated |
|----------|----------|------------|
| Electron | 215 MB   | -          |
| WebView  | 112 MB   | 140 MB     |
| Qt       | 160 MB   | 180 MB     |

If we compare the file size:

|          | Size   |
|----------|--------|
| Electron | 180 MB |
| WebView  | 20 MB  |
| Qt       | 80 MB  |

So, replacing Electron with either WebView or Qt would reduce memory consumption by 50..70 MB and save ≈100 MB of disk space. The difference between WebView or Qt in terms of performance is negligible.

We're not concerned much about disk space since extra 100 MB doesn't matter nowadays (which is arguable but that's our opinion), while reducing memory requirements would be nice.

In terms of development effort, rewriting the app in Qt is equal to full re-creation from scratch, this doesn’t sound realistic. Switching to a WebView-based solution would need some work on app stability and implementation of missing features, but it has big wins in filesystem space and consumes less memory.

### Decision

Right now the decision is not to migrate.