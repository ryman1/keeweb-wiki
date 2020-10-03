Electron is known to be less memory-efficient. Here's the comparison:

### KeeWeb
Current electron app, production version, with the demo database open.

<img width="615" alt="KeeWeb" src="https://user-images.githubusercontent.com/633557/94986318-2a51ca00-055e-11eb-8aff-cf4506279b9c.png">

Total: ≈215 MB

### WebView
WebKit web view with app.keeweb.info, that's the theoretical minimum that we can get with this approach. Additionally there would be more memory consumed in the main process, a rough approximation is around 25 MB.

<img width="615" alt="WebView" src="https://user-images.githubusercontent.com/633557/94986319-30e04180-055e-11eb-9a76-70117af26148.png">

Total: ≈112 MB  
What it would be if missing parts are implemented: ≈140 MB

### Native

KeePassXC with the same demo database open. They have a minimalistic interface which doesn't have animations, transitions, transparency, rich icons, and other resource-consuming elements of graphic design that we have in KeeWeb. Very rough approximation is that implementing them with QT would require extra 20 MB.  

<img width="834" alt="KeePassXC" src="https://user-images.githubusercontent.com/633557/94986320-35a4f580-055e-11eb-91d1-c052bebd76ac.png">

Total: ≈118 MB  
Approximated UI implementation: ≈140 MB  

### Environment

All testing was done on macOS Catalina without memory pressure, with a demo database that you can find in KeeWeb.

### Conclusion

Quick comparison gives us the following results:

|          | Observed | Calculated |
|----------|----------|------------|
| Electron | 215 MB   | -          |
| WebView  | 112 MB   | 140 MB     |
| Qt       | 118 MB   | 140 MB     |

If we compare the file size:

|          | Size   |
|----------|--------|
| Electron | 180 MB |
| WebView  | 50 MB  |
| Qt       | 80 MB  |

So, replacing Electron with either WebView or Qt would reduce memory consumption by ≈70 MB (≈35%) and save ≈100 MB (≈55%) of disk space. The difference between WebView or Qt in terms of performance is negligible.

While we're not concerned much about disk space since extra 100 MB doesn't matter much nowadays, while reducing memory requirements would be nice. In terms of development effort, rewriting the app in Qt is equal to full re-creation from scratch and switching to a WebView would require some work on app stability and implementation of missing features.

Right the decision is not to migrate.

This evaluation was made in October 2020.