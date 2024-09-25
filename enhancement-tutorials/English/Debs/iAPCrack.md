# In-App Purchases Crack

## What are In-App Purchases

> In-app purchases are extra content or subscriptions that you buy inside an app. Not all apps offer in-app purchases. To check if an app offers in-app purchases before you buy or download it, find it in the App Store. Then look for "In-App Purchases" near the app's price or Get button.

## [SatellaJailed](https://github.com/Paisseon/SatellaJailed) - Paisseon

> Satella Jailed is an in-app purchase cracker similar to `LocalIAPStore` (For Jailbroken Devices). In `vulnerable` apps, Satella Jailed can obtain in app purchases for free by attempting to buy a product and then clicking cancel on the popup.

### Installing Satella Jailed

> You first need the following:

- [SatellaJailed.dylib](https://github.com/Paisseon/SatellaJailed/raw/emt/SatellaJailed.dylib)
- [Decrypted IPAs](https://decrypt.day)
- [Signing Tool](https://esign.yyyue.xyz/)


#### On-Device (E-Sign)

- Download  from this repo
- In Signature -> More Settings, import `SatellaJailed.dylib`
- Make sure to use `@executable_path` and `Frameworks`
- Sign and install the patched IPA

#### Azula (Mac or On-Device)

> If you use TrollStore, make sure that the URL scheme is enabled, and turn on code signature slicing. Or just jailbreak with Dopamine and use the tweak version

- Download `SatellaJailed.dylib` from this repo
- Move `SatellaJailed.dylib` and the target IPA to the Azula folder in files app
- Select them in Azula
- Tap the Patch button

#### Script (Computer Required)


- Run `git clone https://github.com/Paisseon/SatellaJailed.git` && `cd SatellaJailed` in terminal
- Move the IPA file to the resultant `SatellaJailed` folder
- `sh patch-mac.sh` for macOS or `sh patch-linux.sh` for Linux and WSL
- Sideload the patched IPA to your jailed device