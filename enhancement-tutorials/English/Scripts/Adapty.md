# Cracking Adapty Apps Using Templates :tree:

> ⚠️This is not working 100% `(might work, might not)` ⚠️

## Perparing to use the template

> To use the template you'll first need two things:
- The app's `Product ID`
- The app's `Premium Access Level`


### Getting Product ID






### Template - `HTTP-Response`

```
var body = $response.body;
var obj = JSON.parse(body);
var header = $request.headers;

obj = {
"data": {
 "type": "adapty_analytics_profile",
  "id": $request.headers["adapty-sdk-profile-id"],
 "attributes": {
  "app_id": "20ed8826-ed31-44ad-a0b3-43c8d360d393",
  "profile_id" : $request.headers["adapty-sdk-profile-id"],
  "customer_user_id": "6FCDBCBC-E369-4A1F-AE94-C898475A813C",
  "total_revenue_usd": 0.0,
  "segment_hash": "f29021fa71267408",
  "paid_access_levels": {
   "premium": {
    "id": "premium",
    "is_active": true,
    "is_lifetime": false,
    "expires_at": "9692-12-26T16:30:25.000000+0000",
    "starts_at": null,
    "will_renew": true,
    "vendor_product_id": "xremover.instants.oneYear",
    "store": "app_store",
    "activated_at": "2023-12-23T16:30:26.000000+0000",
    "renewed_at": "2023-12-23T16:30:25.000000+0000",
    "unsubscribed_at": null,
    "billing_issue_detected_at": null,
    "is_in_grace_period": false,
    "active_introductory_offer_type": "free_trial",
    "offer_id": null,
    "active_promotional_offer_type": null,
    "active_promotional_offer_id": null,
    "cancellation_reason": null,
    "is_refund": false
   }
  },
  "subscriptions": {
   "xremover.instants.oneYear": {
    "is_active": true,
    "is_lifetime": false,
    "expires_at": "9692-12-26T16:30:25.000000+0000",
    "starts_at": null,
    "will_renew": true,
    "vendor_product_id": "xremover.instants.oneYear",
    "vendor_transaction_id": "420001719421278",
    "vendor_original_transaction_id": "420001719421278",
    "store": "app_store",
    "activated_at": "2023-12-23T16:30:26.000000+0000",
    "renewed_at": "2023-12-23T16:30:25.000000+0000",
    "unsubscribed_at": null,
    "billing_issue_detected_at": null,
    "is_in_grace_period": false,
    "active_introductory_offer_type": "free_trial",
    "offer_id": null,
    "active_promotional_offer_type": null,
    "active_promotional_offer_id": null,
    "cancellation_reason": null,
    "is_sandbox": false,
    "is_refund": false
   }
  },
  "non_subscriptions": null,
  "custom_attributes": {},
  "promotional_offer_eligibility": false,
  "introductory_offer_eligibility": false
    }
}
};
body = JSON.stringify(obj);
$done({body:body});
```