## YubiKey modes

YubiKey can be used in several modes with KeeWeb:
- [Challenge-response](#Challenge-response): to provide a hardware-backed component of master key
- [OATH](#OATH): for generating one-time codes

## Challenge-response

This mode is used to store a component of master key on a YubiKey. The implementation is compatible with [KeeChallenge](https://github.com/brush701/keechallenge) plugin for KeePass, [KeePassXC](https://keepassxc.org/docs/#faq-yubikey-2fa), and many other apps.

## Usage

Yubico: https://www.yubico.com/products/services-software/personalization-tools/challenge-response/  
KeePass: https://keepass.info/help/kb/yubikey.html  

To select a YubiKey, click the YubiKey icon on the open screen. Once selected, YubiKey choice is saved in settings, next time it will be used automatically. If the YubiKey is not plugged in, you will be prompted about it.

It's possible to save YubiKey codes in memory while the app is open. Depending on your threat model it may be unexpected or not desired, so it's disabled by default. To enable it, check the corresponding option in settings.

After changing YubiKey settings of a file it's recommended to delete it on other devices and re-add again, to avoid syncing issues.

### Caveats

There are some caveats:

1. YubiKey must be plugged in and you have to press the key every time a file is saved or synced. This means that if you have automatic save enabled, you will be asked to press the button on your YubiKey. If you fail to do so in a timely manner or reject the request, syncing or saving will result in an error.
2. If a file is changed remotely and these changes arrived during sync, you will see the same question again. In case you won't be able to touch the YubiKey in a timely manner, sync will fail.
3. The implementation is compatible to KeePassXC and not KeePass/KeeChallenge (see the list below), which means, you will be able to use it with clients implementing YubiKey integration this way.

### Compatibility

- ✅ [KeePassXC](https://keepassxc.org/docs/#faq-yubikey-incompatible)
- ✅ [Strongbox](https://strongboxsafe.com/faq/#hrf-entry-400)
- ✅ [KeePassium](https://keepassium.com/blog/keepassium-1.10-yubikey/)
- ✅ [Keepass2Android](https://github.com/PhilippC/keepass2android/blob/master/docs/How-to-use-Keepass2Android-with-YubiKey-NEO.md), the file must be in KDBX4 format
- 🚫 [KeePass/KeeChallenge](https://keepass.info/plugins.html#keechl)

### Warning

⚠️ It's strongly recommended to save the file manually after making changes to avoid issues mentioned above.

## OATH

YubiKey can be used to generate one-time codes for 2FA. Compared to 2FA implemented in KeeWeb, this is a much better option because secrets cannot be exported from a YubiKey.

## Usage

Yubico: https://www.yubico.com/products/services-software/personalization-tools/oath/  

KeeWeb is using [ykman](https://github.com/Yubico/yubikey-manager#yubikey-manager-cli), YubiKey Manager CLI, a tool developed by Yubico to access the YubiKey OATH application. If you don't have it installed, KeeWeb will show the installation instructions.

YubiKey OATH is usually protected with a password, which is managed by `ykman`. If you don't have it saved there, KeeWeb will show an error.

New OATH codes can be added in other tools, such as YubiKey Authenticator. After modifying codes on the YubiKey reopen it in KeeWeb to load new codes.

### Entry matching

When you open YubiKey from the open screen, the app shows codes saved there as read-only entries. If there's an open file, KeeWeb tries to match entries from files with entries on the YubiKey, so that both are displayed on the same details page. Entries are considered matching when:

- they have the same title
- the username is exactly the same, or username on the YubiKey is empty

If it's not possible to change title and username (for example, PayPal has strange usernames in 2FA), you can add a custom property called `YubiKey` with the following contents: `title:username`. For example, if you have 2FA on Dropbox, it will be `Dropbox:user@mail.com`. It's exactly the same format as printed by `ykman oath list`.

## Issues

Sometimes YubiKeys can be stuck, in this case `ykman list` doesn't show the serial number. For example, this happens if you're actively using actively using other YubiKey features, such as gpg or ssh integration. It can be easily fixed if you re-enable the OATH interface (`ykman config usb -e oath -f`), however it's a potentially invasive operation, so KeeWeb doesn't do it by default. If you would like to run this command automatically when a YubiKey is stuck, you can enable this option in Settings / Devices.

## Platform support

All features described here are supported only in desktop apps.