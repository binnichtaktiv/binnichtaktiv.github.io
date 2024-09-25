# Script To Deb
> The tutorial is only for `RevenueCat` Apps (for now) ;)

> If you need help join [our telegram](https://t.me/crackhub_69) group

## Requirements

- Phone or Windows Computer


### WSL 2 (Windows)

> Here is how to install a `linux` distro on your `windows` computer

[Microsofts's Instructions](https://learn.microsoft.com/en-us/windows/wsl/install)
or [This Video Tutorial](https://youtu.be/Tlx7qZCPIsA?feature=shared)


### Google Cloud Shell (On-Device)


### Theos Installation

> Here is how to install `theos` on your `linux` subsystem

[Their Documentation](https://theos.dev/docs/installation-linux) or mine:

```
sudo apt install bash curl sudo
```

```
bash -c "$(curl -fsSL https://raw.githubusercontent.com/theos/theos/master/bin/install-theos)"
```

If asked this:

`Would you like your toolchain to support Swift (larger toolchain size) or not (smaller toolchain size)? [y/n]`

Input `n`


### Script to Deb (Revenue Cat)

Run this:
```
$THEOS/bin/nic.pl
```
Then:
```
Choose a Template (required): 17
Project Name (required): <!--App-Name--!> (Recommended)
Package Name [com.yourcompany.name]: com.<!--Your-Name--!>.<!--App-Name--!>
Author/Maintainer Name [unix username]: <!--Your-Name--!>
[iphone/tweak] MobileSubstrate Bundle filter [com.apple.springboard]: <!--App-Bundle-ID--!>
[iphone/tweak] List of applications to terminate upon installation (space-separated, '-' for none) [SpringBoard]: -
```
Next (On your windows computer):

- Open `File Explorer`
- Select `\Linux` on the sidebar
- Open `\Ubuntu`
- Go to `\home\name`
- Open the project's folder
- Then open `Tweak.x` with note pad & replace all whats in it with the script template you want from [here](../Debs/DebTemplates.md)


> Don't forget to save the `Tweak.x` file after editing!

After (On your ubuntu terminal):

```
cd <!--Project-Name--!>
```
&
```
make package
```

IF YOU RUN `make package` AND GET AN ERROR LIKE THIS:

![alt text](/Gifs/fatalerror.png)

RUN THE FOLLOWING COMMANDS:

```
rm -rf $THEOS/toolchain/*

curl -sL https://github.com/kabiroberai/swift-toolchain-linux/releases/download/v2.3.0/swift-5.8-ubuntu20.04.tar.xz | tar -xJvf - -C $THEOS/toolchain/
```

Then re-run the `make package` command

![](../Gifs/fatalerror.png)

>Your .deb file will be in the `/packages` directory.

> If you run in to any errors join [this](https://t.me/crackhub_69) telegram group.

