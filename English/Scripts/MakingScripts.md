# How to make your own scripts (Intermediate) :newspaper:

> If you are an absolute beginner I don't recommend you start with this page. Head over to the [Revenue Cat API Tutorial](/Scripts/RevenueCat.md) first.

Keep in mind this page is still under development.

> And if you have any questions, we're glad to help in our telegram channel. `t.me/crackhub_69`
## Make your own script

> Keep in mind, I can't teach you how to make a script for all apps, but I can. Just not the way I taught you how to make `RevenueCat` scripts, this is totally different.

If you want to learn how to make scripts, you'll have to learn other things first:

- How to analyze the HTTP traffic
- What are expressions and how are they used when making scripts
- Basic JS
- JSON Structures
- MitM

And this guide will cover most of that.




## Analyzing Traffic

By now you should know how to capture traffic, but analyzing will be the next step. Just like when your cracking RevenueCat apps. You looked for the Entitlements & Product IDs. The difference is you were told where to look `api.revenuecat.com`. But when your cracking apps on your own, no one will guide you where to look or find. This is why you should look everywhere & try everything.

Here is `when` you should be capturing HTTP:

- First opening the app after installing (Usually when data about purchases are sent. [Prices, Discounts, etc])
- Opening the subscription page on the app (Usually checks for subscription & prices)
- Restoring Purchases (Checks if you have subscription)
- Re-opening the app (Also checks if you have subscription)

After capturing traffic during these points ⬆ analyze the traffic, look for requests with the apps' name, `"api.whatever.com"` & words like `"subscriptions", "receipt", "purchases", "pro", "validate", "premium", etc`. Check the request & response bodies for them. Anything intresting? Any `{ "pro": false }`? probably not but thats just an example.

## Expressions

> To modify request & response bodies you'll need to know what are expressions & how to use them.

BASICALLY, an expression is the URL you want to modify. For example.

`https://amIbest.com/check/user` gave me this response body:

```
{
    "username": "DaddyDev",
    "isCool": true,
    "isStinky": true,
    "isBest": false
}
```

My expression will be `https://amIbest.com/check/user` because I want to modify its response & make my self the best & not stink. Make sure to use the COMPLETE path, not just `https://amIbest.com` or else youll modify all responses. 

Although you'll learn how to make scripts later on... but for this example the script to make me the best & not stinky will be the following:

```
const objc = {
    "isStinky": false,
    "isBest": true
}

$done({body : JSON.stringify(objc)});
```

I made `isStinky` false & `isBest` true. (Obviously)



## Making the actual script

Now that you know the reponse body & the expression.

Next step is to write the actual script.

### Example 1 (Not real)

The expression: `https://mylife/info/`
The response:
```
{
    "name": "Dev The 2nd",
    "age": 69,
    "isStudent": false,
    "hasSkills": true,
    "Skills": {"Cooking", "Taking Notes"},
    "address": {
        "city": "Dubai",
        "zipcode": "69420"
    },
    "Social": {
        "hasFriends": false,
        "Friends": "null",
        "hasFamily": false
    }
}
```

First know your target. In this case I want to modify 2 things:

- `isStudent` to true, to get student benifets.
- `hasFriends` to true, to spoof friends.

First of all I will use the modify response boilerplate

```
const objc = {
    
}

$done({body : JSON.stringify(objc)});
```

Anything you add to between the `{ }` will replace whatever is in the response.

First thing before modifying the target value, you will need to know how to reach for it.

Indents are just like boxes, to reach for whats inside the box you'll have to open it. EVERYTHING in the response body is by defualt in the first box without a name. And you already opened it by defualt in the script. Since you opened the first box you can edit whatever value you want in that box. In this example, the following values are in the first box:

```
"name",
"age",
"isStudent",
"Skills",
```
However you can't change the values of  `"City"` or `"hasFriends"` because they're inside their own boxes named `"Address"` & `"Social"`.

To make a script that access those values you'll have to declare the name of the box like this:
```
const objc = {
    "Address" {
        "City" = "China"
    },
    "Social" {
        "hasFriends" = true
    }
}

$done({body : JSON.stringify(objc)});

```

So a script that makes `isStudent` true & `hasFriends` true will be this:

```
var objc = JSON.parse($response.body);

objc.isStudent = true,
objc.hasFriends = true

$done({ body: JSON.stringify(objc) });
```

You will only add the values you want to change, not the whole response body.

### Example 2 ([AdGuard](https://apps.apple.com/us/app/adguard-adblock-privacy/id1047223162))

As soon as I open the app while recording HTTP Traffic, I see the `https://mobile-api.adguard.org/api/2.0/ios_validate_reciept/ADG_EXT` request. So I check the reponse and I get this:

```
{
    "products": []
}
```

"But Dev, its not a true or false scenario... What do I do?" We can never guess what that would be. Check if there is a trial for the app, if there is take it.

Once you take the trial, re-open the app to look for that same request & check the response. After the trial this is the response.

```
{
    "products": [
        {
            "product_id" = "com.adguard.monthly",
            "premium_status" = "ACTIVE",
            "expiration_date" = 1707605690000
        }
    ]
}
```

Now once you know what your response should be, start making your script.


The expression is `https://mobile-api.adguard.org/api/2.0/ios_validate_reciept/ADG_EXT`

The script:

```
const objc = {
    "products": [
        {
            "product_id" = "com.adguard.monthly", // I took the monthly trial thats why its monthly, but it wont matter because I can change the expiration date
            "premium_status" = "ACTIVE",
            "expiration_date" = 4073650693 // This is in unix time, I will change the value of it for the subscription to last more
        }
    ]
}

$done({body : JSON.stringify(objc)});
```

To know about unix time check [this](/English/Etc/unixTime.md) Unix Time guide. 

Thats it, you just cracked your first app that has its own API.