# User-Based Scripts Tools :gear:

|       |  |
| ----------- | ----------- |
| Surge      | most expensive & most powerful.       |
| Loon   | best beginner option.        |
| Egern   | cheapest option.        |

## Setting Up

After installing one of the apps you will be required to set it up.

> Please follow the instructions based on your tool: 

### Set up `Surge`

> Here is how to setup `Surge` & be ready to start using scripts:

> First Step:
> `Setup` on the top-right corner --> `OK` --> `Allow`

> Second Step:
> `Capture` Tab --> `Configure` under MitM --> `Generate A New CA Certificate` --> `Install CA Certificate` --> `Allow` --> `Close` --> Go to the `Settings` app --> `General` --> `VPN & Device Management` --> `Loon CA` --> `Install` --> `Install` --> `Done

> Finally:
> In the `Settings` app --> `General` --> `About` --> `Certificate Trust Settings` --> Turn on `Surge Generated CA` --> `Continue`

### Set up `Loon`

>Here is how to setup `Loon` & be ready to start using scripts:

> First Step:
> Go to `Profile` --> `Certificate Mangement` --> `Generate A New CA Certificate` --> `Install CA Certificate to System` --> `Allow` --> `Close` --> Go to the `Settings` app --> `General` --> `VPN & Device Management` --> `Loon CA` --> `Install` --> `Install` --> `Done` 

> Second Step:
> In the `Settings` app --> `General` --> `About` --> `Certificate Trust Settings` --> Turn on `Loon CA` --> `Continue`

### Set up `Egern`

>Here is how to setup `Egern` & be ready to start using scripts:

> First Step:
> Go to `Tools` --> `Certificate` --> `Generate Certificate` --> `Install Certificate` --> `Allow` --> `Close` --> Go to the `Settings` app --> `General` --> `VPN & Device Management` --> `Egern CA (Date)` --> `Install` --> `Install` --> `Done` 

> Second Step:
> In the `Settings` app --> `General` --> `About` --> `Certificate Trust Settings` --> Turn on `Egern CA (Date)` --> `Continue`

## How To Use Scripts

Before you start using you will need this information:
- Script Type E.g. `HTTP-Request/HTTP-Response` (Usually `HTTP-Request` unless stated)
- Expression URL E.g. `https://thisisanexpression.com/this/is/an/expression`
- `MITM` 
- The Script Itself

```
!--SCRIPT-EXAMPLE--!

var objc = JSON.parse($response.body);

objc = {

    // Contents of the script

};

$done({body: JSON.stringify(objc)})
```

### Using `Surge`

> Coming Soon

### Using `Loon`
> How to add & use a script with `Loon`

> First Step:
> Inside `Loon`, go to `Profile` --> `Local JavaScript Files` --> `+` --> `Create empty script` --> Input Any Name --> Paste The Script

> Second Step:
> Back out of the text editor and  `Local JavaScript Files` --> `Scripts` --> `+` --> Input The Info --> Set `Script Location` to Local and select the script you made

> Finally:
> Go to `Dashboard` and Toggle loon

### Using `Egern`
> How to add & use a script with `Egern`

> First Step:
> Inside `Egern`, go to `Tools` --> `Scripts` --> `+` --> Input the info

> Second Step:
> Go to `Analytics` --> `Start`

## Adding `MITM` URL

### `MITM` on `Surge`
> How to add `MITM` `Hostnames` on `Surge`

> Coming Soon

### `MITM` on `Loon`
> How to add `MITM` `Hostnames` on `Loon`

> Inside `Loon` --> `Profile` --> `Hosts` Under `MitM` --> Toggle `MitM over HTTP/2` --> `+` --> Input the `hostname` --> `Sure`

### `MITM` on `Egern`
> How to add `MITM` `Hostnames` on `Egern`

> Inside `Egern` --> `Tools` --> `MitM Hostnames` --> Input the `hostname` --> `+` --> `Save`