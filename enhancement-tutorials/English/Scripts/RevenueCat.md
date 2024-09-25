# Cracking RevenueCat Apps :cat:


[Revenue Cat API](https://www.revenuecat.com/)


## Perparing to use the templates

> To use the template you'll first need two things:
- The app's `Product ID`
- The app's `Entitlements`

### Grabbing `Revenue Cat` `Product IDs` & `Entitlements`

> Follow the steps provided after setting up WebProxyTool:  

> Turn on WebProxyTool, re-open the app, look for `api.revenuecat.com` & tap on it, open any request, in the `Request` tab scroll down and look for the header: `Authorization`, copy that and paste on [this](https://n9dev-dev.github.io/ScriptGenerator/ReqSend/index.html) website.

[Here](https://docs.google.com/spreadsheets/d/1qw_gQDLB42vREe8OE2_JBQXvbidmJI20/edit?usp=sharing&ouid=105008758580906401700&rtpof=true&sd=true) is a list of RevenueCat apps' Entitlements & Product IDs

#### Example: `(Clipboard Pro)`

```
{
	"product_entitlement_mapping": {
		"it.beatcode.clipboardpro.annualSubscription": {
			"entitlements": [
				"pro" <-- <!!--Entitlement--!!>
			],
			"product_identifier": "it.beatcode.clipboardpro.annualSubscription" <-- <!!--Product ID--!!> 
		}
```

## Revenue Cat Script Generator

> Add the Product ID & Entitlment to [this](https://n9dev-dev.github.io/ScriptGenerator/RevenueCat/index.html) page to generate your revenuecat script.



# The God Trick (only for super lazy ones😉)


## Auto-Crack All Apps (Module)

```
#!name=Unlock Any Revenuecat
#!desc=Auto All Revenuecat
[MITM]
hostname = %APPEND% api.revenuecat.com, isi.csan.goodnotes.com

[Header Rewrite]
#Anticache
.+ header-del if-modified-since
.+ header-del if-none-match
.+ header-del X-RevenueCat-ETag
.+ header-del x-revenuecat-etag

[URL Rewrite]
^https:\/\/(api\.revenuecat|isi.csan.goodnotes)\.com\/.+\/(receipts$|subscribers\/[^/]+$|offers$) https://api.langkhach89.workers.dev header
```

### Using Surge
> First Step:
> On `Surge` --> `Modify` --> `Module`

> Second Step:
> `New Local Module...` --> Paste the above script --> `Done` --> Input `Unlock Any Revenuecat` --> `OK` --> Tap on `Unlock Any Revenuecat` --> `Done`

> Third Step:
> Run Vpn and boom every RevenueCat App Cracked automatically 🤣

### 💡Credits:
> Thanks to [Lang](https://t.me/LKTEAM23)