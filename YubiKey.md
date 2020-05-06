## 🚧 UNDER CONSTRUCTION 🚧

YubiKey integration is under construction, it's expected to appear in v1.15.

## YubiKey modes

YubiKey can be used in several modes with KeeWeb:
- [Challenge-response](#Challenge-response): to provide a hardware-backed component of master key
- [OATH](#OATH): for generating one-time codes

## Tools

KeeWeb is using [ykman](https://github.com/Yubico/yubikey-manager#yubikey-manager-cli), YubiKey Manager CLI, a tool developed by Yubico to access YubiKey from terminal. If you don't have it installed, KeeWeb will show the installation instructions.

## Challenge-response

This mode is used to store a component of master key on a YubiKey. The implementation is compatible with [KeeChallenge](https://github.com/brush701/keechallenge) plugin, [KeePassXC](https://keepassxc.org/docs/#faq-yubikey-2fa), and many other apps.

Yubico: https://www.yubico.com/products/services-software/personalization-tools/challenge-response/  
KeePass: https://keepass.info/help/kb/yubikey.html  

To select a YubiKey slot, click the YubiKey icon on the open screen. Clicking it several times switches between available slots and YubiKeys. Once selected, YubiKey choice is saved in settings, next time it will be used automatically.

There's a caveat: YubiKey must be plugged in and you have to press the key every time a file is saved or synced. This means that if you have automatic save enabled, you will be asked to press a button on your YubiKey. If you fail to do so in a timely manner or reject the request, KeeWeb will use the same challenge-response pair as the one used when opening the file.

## OATH

YubiKey can be used to generate one-time codes for 2FA. Compared to 2FA implemented in KeeWeb, this is a much better option because secrets cannot be exported from a YubiKey.

Yubico: https://www.yubico.com/products/services-software/personalization-tools/oath/  

YubiKey OATH is usually protected with a password, which is managed by `ykman`. If you don't have it saved there, KeeWeb will show an error.

When you open YubiKey from the open screen, the app shows codes saved there as read-only entries. If there's an open file, KeeWeb tries to match entries from files with entries on the YubiKey, so that both are displayed on the same details page. Entries are considered matching when:

- they have the same title
- the username is exactly the same, or username on the YubiKey is empty

If it's not possible to change title and username (for example, PayPal has strange usernames in 2FA), you can add a custom property called `YubiKey` with the following contents: `title:username`. For example, if you have 2FA on Dropbox, it will be `Dropbox:user@mail.com`. It's exactly the same format as printed by `ykman oath list`.

Sometimes YubiKey can be stuck, in this case `ykman oath` command times out without giving any codes. For example, this happens if you're actively using actively using other YubiKey features, such as gpg or ssh integration. It can be easily fixed if you re-enable the OATH interface (`ykman config usb -e oath -f`), however it's a potentially invasive operation, so KeeWeb doesn't do it by default. If you would like to run this command automatically when a YubiKey is stuck, you can enable this option in Settings / Devices.

## Platform support

All features described here are supported only in 64-bit desktop apps.