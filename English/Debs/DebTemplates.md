# Script To Deb Templates

Templates for the `Tweak.x` file!

First you'll need to know the mechanism your app uses, here is how: (You'll need `Flexing` Injected)

Hold three fingers on the center of the screen to open flexing menu --> Tap on `menu` --> `Network History` --> `Turn on` --> Re-open the app --> open the URL your trying to modify the response of --> The mechanism will be under `Mechanism:`



## RevenueCat Template

- Change `<!--Product-ID--!>` to your Product ID
- Change `<!--Entitlement--!>` to your Entitlement

```
#import <Foundation/Foundation.h>

%hook NSURLSession
- (id)dataTaskWithRequest:(NSMutableURLRequest *)request completionHandler:(void (^)(NSData *data, NSURLResponse *response, NSError *error))completionHandler {
void (^customCompletion)(NSData *data, NSURLResponse *response, NSError *error) = ^(NSData *data, NSURLResponse *response, NSError *error) {

if (([request.URL.absoluteString containsString:@"subscribers"] || [request.URL.absoluteString containsString:@"receipt"]) && (![request.URL.absoluteString containsString:@"offerings"])) {
            NSDictionary *dict = @{
    @"request_date": @"2023-08-02T02:21:57Z",
    @"request_date_ms": @1690942917283,
    @"subscriber": @{
        @"entitlements": @{
            @"<!--Entitlement--!>": @{
                @"expires_date": @"2099-02-18T07:52:54Z",
                @"original_purchase_date": @"2020-02-11T07:52:55Z",
                @"purchase_date": @"2020-02-11T07:52:54Z",
                @"product_identifier": @"<!--Product-ID--!>"
            }
        },
        @"first_seen": @"2023-07-27T12:47:03Z",
        @"last_seen": @"2023-08-02T01:57:17Z",
        @"management_url": NSNull.null,
        @"non_subscriptions": @{
        },
        @"original_app_user_id": @"70B24288-83C4-4035-B001-573285B21AE2",
        @"original_application_version": @"3",
        @"original_purchase_date": @"2023-07-26T17:04:14Z",
        @"other_purchases": @{
        },
        @"subscriptions": @{
            @"<!--Product-ID--!>": @{
                @"expires_date": @"2099-02-18T07:52:54Z",
                @"original_purchase_date": @"2020-02-11T07:52:55Z",
                @"purchase_date": @"2020-02-11T07:52:54Z"
            }
        },
        @"entitlement": @{
        }
    }
};
            data = [NSJSONSerialization dataWithJSONObject:dict options:0 error:nil];
        }
        completionHandler(data, response, error);
    };

    return %orig(request, customCompletion);
}
%end

```


## Boilerplate Template

> For apps that use `NSURLSessionDataTask (Delegate: AFHttpsSessionManager)` Mechanism

- Change `<!--URL--!>` to your URL Expression

E.G. RevenueCat: `https://api.revenuecat.com/api/v1/subscribers/Rc$ID`

```
#import <Foundation/Foundation.h>

%hook AFURLSessionManager

-(void)URLSession:(NSURLSession *)session dataTask:(NSURLSessionDataTask *)task didReceiveData:(NSData *)data {
 if ([task.currentRequest.URL.absoluteString containsString:@"<!--URL--!>"]) {
   NSDictionary *dict = @{
  

};

  data = [NSJSONSerialization dataWithJSONObject:dict options:0 error:0];
 }
 %orig(session, task, data);
}
%end
```

## [Alamofire](https://github.com/Alamofire/Alamofire) Apps Template

> For apps that use `NSURLSessionDataTask (Delegate: Alamofire.SessionDelegate)` Mechanism

- Change `<!--URL--!>` to your URL Expression

E.G. RevenueCat: `https://api.revenuecat.com/api/v1/subscribers/Rc$ID`

```
#import <Foundation/Foundation.h>

%hook SessionDelegate
-(void)URLSession:(NSURLSession *)session dataTask:(NSURLSessionDataTask *)task didReceiveData:(NSData *)data {
 if ([task.currentRequest.URL.absoluteString containsString:@"<!--URL--!>"]) {
   NSDictionary *dict = @{
  

};

  data = [NSJSONSerialization dataWithJSONObject:dict options:0 error:0];
 }
 %orig(session, task, data);
}
%end

%ctor {
 %init(SessionDelegate = objc_getClass("Alamofire.SessionDelegate"));
 }
```


## HttpAsynConnection Apps Template


> For apps that use `NSURLConnection (delegate: HttpAsynConnection)` Mechanism

- Change `<!--URL--!>` to your URL Expression

E.G. RevenueCat: `https://api.revenuecat.com/api/v1/subscribers/Rc$ID`

```
#import  <Foundation/Foundation.h>

%hook HttpAsynConnection

- (void)connection:(NSURLConnection *)connection didReceiveData:(NSData *)data {
    NSURLRequest *originalRequest = [connection originalRequest];
    NSString *urlString = [[originalRequest URL] absoluteString];
    
    if ([urlString containsString:@"<!--URL--!>"]) {
        NSDictionary *dict = @{
          
        };

        NSError *error = nil;
        NSData *modifiedData = [NSJSONSerialization dataWithJSONObject:dict options:0 error:&error];
        if (!error) {
            %orig(connection, modifiedData);
        } else {
            %orig(connection, data);
        }
    } else {
        %orig(connection, data);
    }
}

%end
```