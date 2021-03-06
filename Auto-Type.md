## Supported

### Modifiers

`+` &rarr; shift  
`%` &rarr; alt  
`^` &rarr; cmd on Mac, ctrl on Windows and Linux  
`^^` &rarr; ctrl on all OS  

### Keys

`{TAB}` `{ENTER}`=`~` `{SPACE}`   
`{UP}` `{DOWN}` `{LEFT}` `{RIGHT}` `{HOME}` `{END}` `{PGUP}` `{PGDN}`  
`{INSERT}`=`{INS}` `{DELETE}`=`{DEL}` `{BACKSPACE}`=`{BS}`=`{BKSP}` `{ESC}`  
`{WIN}`=`{LWIN}` `{RWIN}` `{F1}`..`{F16}`  
`{ADD}` `{SUBTRACT}` `{MULTIPLY}` `{DIVIDE}` `{NUMPAD0}`..`{NUMPAD9}`  
`{+}` `{%}` `{^}` `{~}` `{(}` `{)}` `{[}` `{]}` `{{}` `{}}`  

### Substitutions

`{TITLE}` `{USERNAME}` `{URL}` `{PASSWORD}` `{NOTES}` `{GROUP}`  
`{TOTP}` `{S:Custom Field Name}`  
`{DT_SIMPLE}` `{DT_YEAR}` `{DT_MONTH}` `{DT_DAY}` `{DT_HOUR}` `{DT_MINUTE}` `{DT_SECOND}`  
`{DT_UTC_SIMPLE}` `{DT_UTC_YEAR}` `{DT_UTC_MONTH}` `{DT_UTC_DAY}` `{DT_UTC_HOUR}` `{DT_UTC_MINUTE}` `{DT_UTC_SECOND}`  

### Commands

`{DELAY X}` `{CLEARFIELD}` `{VKEY X}`

### Combinations

`+(abc)` &rarr; ABC (abc with shift)  
`{a 3}` &rarr; aaa  
`^^({TAB} +{TAB})` &rarr; ctrl-tab ctrl-shift-tab  

## Not supported

`{CAPSLOCK}` `{NUMLOCK}` `{SCROLLLOCK}` `{APPS}` `{HELP}` `{PRTSC}` `{BREAK}`  
`{DELAY=X}`  
`{VKEY-NX *}` `{VKEY-EX *}`  
`{REF:*}` `{T-REPLACE-RX:*}` `{T-CONV:*}`  
`{BASE}` `{BASE:*}` `{URL:*}`  
`{%ENVVAR%}` `{ENV_DIRSEP}` `{ENV_PROGRAMFILES_X86}` `{APPDIR}`  
`{INTERNETEXPLORER}` `{FIREFOX}` `{OPERA}` `{GOOGLECHROME}` `{SAFARI}`  
`{PICKCHARS}` `{PICKCHARS:*}` `{NEWPASSWORD}` `{NEWPASSWORD:*}` `{PASSWORD_ENC}` `{BEEP *}`  
`{HMACOTP}`  
`{APPACTIVATE WindowTitle}`  
`{GROUP_PATH}` `{GROUP_NOTES}` `{DB_PATH}` `{DB_DIR}` `{DB_NAME}` `{DB_BASENAME}` `{DB_EXT}`  

## macOS

Auto Type module has been re-written in KeeWeb v1.17, this unfortunately means we'll have a bit more issues with it in this version. Please forgive us this inconvenience, it should become even more stable in future releases. Additionally, it's extracted to [its own library](https://github.com/antelle/keyboard-auto-type), which should help developers building auto-type in their apps too.

Auto-type requires Accessibility and Input Monitoring permissions to be able to work on macOS. Normally it asks you to give access, however some updates make macOS forget about it. In this case, go to `System Settings` ??? `Security & Privacy` ??? `Privacy` -> `Accessibility`, remove KeeWeb from there and add it again. If this doesn't help, you can try the same on the `Input Monitoring` tab.

What else you can try to debug it:

- restart KeeWeb;
- open a simple text editor, then launch KeeWeb and press <kbd>???</kbd><kbd>T</kbd>;
- restart the app where you try to do auto typing;
- check KeeWeb logs, they can be found in Settings / General / Advanced
- try switching to legacy auto-type in Settings / General / Advanced (this will be removed in future releases)

Nothing worked? Please [open an issue](https://github.com/keeweb/keeweb/issues/new?labels=bug,auto-type,desktop,mac&template=bug_report.md)!