## Repositories

* [keeweb](https://github.com/keeweb/keeweb)
  * the main repository containing the application code, desktop installers, and other support files
  * [app.keeweb.info](https://app.keeweb.info)
* [kdbxweb](https://github.com/keeweb/kdbxweb)
  * core library used to read and write the KDBX file format
* [keeweb-plugins](https://github.com/keeweb/keeweb-plugins)
  * plugin repository for KeeWeb
  * contains plugins, themes, and translations
  * [plugins.keeweb.info](https://plugins.keeweb.info)
* [keeweb-site](https://github.com/keeweb/keeweb-site)
  * our promotional website
  * [keeweb.info](https://keeweb.info)
* [favicon-proxy](https://github.com/keeweb/favicon-proxy)
  * CORS-enabled proxy used to load favicons from websites
  * [favicon.keeweb.info](https://favicon.keeweb.info)
* [keeweb-tools](https://github.com/keeweb/keeweb-tools)
  * tools for low-level working with kdbx files
  * [tools.keeweb.info](https://tools.keeweb.info)
* [keeweb-native-modules](https://github.com/keeweb/keeweb-native-modules)
  * pre-built native modules used in KeeWeb
* ...forks of some repositories that can be found in [keeweb](https://github.com/keeweb) organization

## KeeWeb repository layout

Let's take a closer look at [keeweb](https://github.com/keeweb/keeweb) repository.  
It consists of the following parts:

* `app`: application source code, both web and desktop
* `build`: build system tasks and the webpack config
* `desktop`: source code of the desktop part, entry point of the Electron app
* `graphics`: icons and images
* `img`: screenshots for the README on GitHub
* `package`: support files for packagers, docker images, and installers
* `plugins`: infrastructure for developing plugins and plugin examples
* `test`: tests
* `util`: utility scripts for performing different tasks on the repository
* `grunt*.js`: build system configuration files and task definitions

## Application

Now let's dive deeper into the structure of the application code located in [keeweb/app](https://github.com/keeweb/keeweb/tree/master/app) folder.

* `icons`: website favicons
* `lib`: 3rd-party code that doesn't exist in npm
* `manifest`: manifests for different browsers
  * `browserconfig.xml`: Microsoft Edge favicons definition
  * `manifest.json`: SPA manifest for other browsers
* `resources`: resources embedded in the application
  * `Demo.kdbx`: demo database
  * `public-key.pem`: public key used to verify plugin and update signatures
  * `public-key-new.pem`: rotated public key
* `scripts`: JS source code root
  * `app.js`: entry point
  * `auto-type`: auto-type engine used in desktop apps
  * `collections`: collection models with their methods, such as list of open files
  * `comp`: complex components with business logic using utilities, views, events, and so on
  * `const`: constant definitions
  * `framework`: micro-framework used in the app: models, collections, views, and events
  * `hbs-helpers`: helpers for Handlebars used in templates
  * `locales`: translations distributed with the app
  * `models`: models, such as file, entry, group, and so on
  * `plugins`: plugin engine
  * `presenters`: presentation-layer model extensions
  * `storage`: implementation of storage, such as Dropbox, Google Drive, WebDAV, and others
  * `util`: utility classes, they are similar co components, but they don't have dependencies and business logic
  * `views`: view controllers
* `styles`: SCSS styles root
  * `main.scss`: entry point
  * `areas`: styles divided by parts of the app, such as footer or header
  * `base`: common styles, such as global font stack
  * `common`: SCSS components used on different areas of the application
  * `themes`: theme definitions
  * `utils`: SCSS utilities and mixins
* `templates`: Handlebars templates root
* `favicon.png`: favicon for the website
* `index.html`: HTML page template where all scripts and styles are imported
* `manifest.appcache`: not used for caching anymore, contains only update information for desktop apps
* `service-worker.js`: service worker used for caching and update management

## Frameworks

The app is built on our own [micro-framework](https://github.com/keeweb/keeweb/tree/master/app/scripts/framework) that is similar to Backbone. Originally it was on Backbone, but we were not using much of it and the number of limitations became more than problems solved. The current framework consists of these building blocks:

* [events](https://github.com/keeweb/keeweb/blob/master/app/scripts/framework/events.js) (the `EventEmitter` module from node.js)
* [model](https://github.com/keeweb/keeweb/blob/master/app/scripts/framework/model.js)
* [collection](https://github.com/keeweb/keeweb/blob/master/app/scripts/framework/collection.js)
* [view](https://github.com/keeweb/keeweb/blob/master/app/scripts/framework/views/view.js)

Views are built on [Handlebars.js](https://handlebarsjs.com) and rendered with [morphdom](https://github.com/patrick-steele-idem/morphdom), which gives us a possibility to re-render them without losing input state. New code should be written in reactive style, however there are some direct DOM modifications in different places, ideally they should be replaced.

SCSS styles are using [Bourbon](https://www.bourbon.io) as a framework. We have our own [theme engine](https://github.com/keeweb/keeweb/tree/master/app/styles/themes) that supports switching themes with CSS custom properties.

Desktop apps are created with Electron.

## Building

The app is bundled with WebPack and built with Grunt. While it's so 2010s to use Grunt nowadays, it's still far ahead of using npm scripts and perfectly does the job of running different actions with JS. However it's not used for any of web bundle building tasks, this part is completely moved to WebPack.

Desktop apps are packaged with [electron-packager](https://github.com/electron/electron-packager) and then built into distributables with Grunt. We're not using [electron-builder](https://www.electron.build) for major installers (Windows MSI, macOS app, .deb, .zip) because the setup process is heavily customized and patching electron-builder would be way harder than implementing builders on our own. However electron-builder is used for various Linux packages, such as Snap or AppImage.

## Native modules

KeeWeb uses native modules ([node.js C++ addons](https://nodejs.org/api/addons.html#addons_context_aware_addons)) in desktop apps. All modules used in KeeWeb are built in [keeweb-native-modules](https://github.com/keeweb/keeweb-native-modules) repository. Native modules are created:
- if the functionality is not available in Electron, for example, YubiKey API
- when implementing it in JavaScript would be significantly slower, for example, Argon2

In other cases it's better to implement everything in JavaScript. For example, a native module for reading QR codes would not be an acceptable solution.

List of used native modules:

- [`node-keyboard-auto-type`](https://github.com/antelle/node-keyboard-auto-type): auto-type implemented using [`keyboard-auto-type`](https://github.com/antelle/keyboard-auto-type)
- [`node-argon2`](https://github.com/ranisalt/node-argon2): faster Argon2 for desktop apps
- [`node-keytar`](https://github.com/atom/node-keytar): secret management, used for settings encryption
- [`node-yubikey-chalresp`](https://github.com/antelle/node-yubikey-chalresp): YubiKey interaction
- [`node-usb-detection`](https://github.com/MadLittleMods/node-usb-detection): for watching USB devices and displaying the YubiKey icon
- [`node-secure-enclave`](https://github.com/antelle/node-secure-enclave): Touch ID support on macOS