How to create KeeWeb plugin

⚠️ WARNING: this API is deep under construction

Plugin example: https://github.com/keeweb/keeweb/tree/develop/plugins/example
Plugin creation script: https://github.com/keeweb/keeweb/blob/develop/plugins/kw-plugin-control.js

## Plugin contents

All plugins must have `manifest.json`.

Plugin can contain other files, depending on plugin type:

- JS:
 - plugin.js
- JS+CSS:
 - plugin.js
 - plugin.css
- CSS:
 - plugin.js
 - plugin.css
- Locales:
 - <locale_name>.json