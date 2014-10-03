Payment Session
===============

Payment sessions are created when customers initiate a payment process that requires an external gateway (such as Paypal Payments Standard).

The payment session object
--------------------------

### Attributes

Name | Type | Description
--:|:-:|:--
**id** | string |
**object** | string | Will be "webhook"
**created** | integer |
**handled** | boolean |
**timestamp_handled** | integer |
**payment_amount**  | string |
**payment_currency**  | integer |
**action**  | string | Type of action the user has requested
**ip**  | string |
**user_agent**  | string |
**parameters**  | array |
**gateway**  | object | The gateway object used for the payment session.
**customer**  | object | Will be populated if a customer is identified.
**charge**  | object |

### Example

```json
{
	"id": "payment_session",
	"object": "payment_session",
	"created": 1375217068,
	"handled": true,
	"timestamp_handled": 1375217068,
	"payment_amount": 7200,
	"payment_currency": "USD",
	"action": "subscription-update",
	"ip": "172.16.254.1",
	"user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_8_3) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/27.0.1453.93 Safari/537.36",
	"posted_values": {
		"customer": "cu4321",
		"subscription": "50aaeccb73dd310010",
		"item_description": "Plus Plan",
		"item_id": 101,
		"period_amount": 1,
		"period_type": "month",
		"payment_amount": 7200,
		"payment_currency": "USD",
		"payment_discount": 0.00,
		"return_url_ok": "http://example.org/payment/success/",
		"return_url_error: "http://example.org/payment/error/",
		"publishable_key": "pk_QTBkCKdRworbXYZens4V4LZZs1X00FeM",
		"gateway": "gw_TlTNIsHSf5lh85",
		"integrity_value": "b860f950df56104a9328e44f6b3ce6e30f6db55a"
	},
	"gateway": "gw_TlTNIsHSf5lh85",
	"customer": "cu4321",
	"charge": {
		"object": "charge",
		"amount": 7200,
		"currency": "USD",
		"paid": true,
		"timestamp_paid": 1375217068,
		"status": "completed"
	}
}
```

List all payment sessions
-------------------------
Returns a list of all payment sessions.

### Arguments

Name | Required | Description
--:|:-:|:--
**count** | optional |
**offset** | optional |

### Example request

	$ curl https://secure.peakium.com/api/v1/payment_session/?count=2 \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9:

### Example response

```json
{
	"object": "list",
	"count": 2,
	"data": [
		{
			"id": "payment_session",
			"object": "payment_session",
			"created": 1375217068,
			"handled": true,
			"timestamp_handled": 1375217068,
			"payment_amount": 7200,
			"payment_currency": "USD",
			"action": "subscription-update",
			"ip": "172.16.254.1",
			"user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_8_3) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/27.0.1453.93 Safari/537.36",
			"posted_values": {
				"customer": "cu4321",
				"subscription": "50aaeccb73dd310010",
				"item_description": "Plus Plan",
				"item_id": 101,
				"period_amount": 1,
				"period_type": "month",
				"payment_amount": 7200,
				"payment_currency": "USD",
				"payment_discount": 0.00,
				"return_url_ok": "http://example.org/payment/success/",
				"return_url_error: "http://example.org/payment/error/",
				"publishable_key": "pk_QTBkCKdRworbXYZens4V4LZZs1X00FeM",
				"gateway": "gw_TlTNIsHSf5lh85",
				"integrity_value": "b860f950df56104a9328e44f6b3ce6e30f6db55a"
			},
			"gateway": "gw_TlTNIsHSf5lh85",
			"customer": "cu4321",
			"charge": {
				"object": "charge",
				"amount": 7200,
				"currency": "USD",
				"paid": true,
				"timestamp_paid": 1375217068,
				"status": "completed"
			}
		},
		{...}
	]
}
```