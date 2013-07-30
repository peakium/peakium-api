Subscription
===========

The subscription object is read-only.

The subscription object
-----------------

### Attributes

Name | Type | Description
--:|:-:|:--
**id** | string |
**object** | string | Will be "subscription"
**display_name** | string |
**plan** | array | 
**plan**->**period_amount** | integer | 
**plan**->**period_type** | string | 
**plan**->**amount** | integer | 
**plan**->**currency** | string | 
**plan**->**discount** | float | 
**plan**->**item_id** | integer | 
**cycle_number** | integer |
**period_start** | integer |
**period_end** | integer |
**next_charge** | integer |
**customer** | object |

### Example

```json
{
	"id": "50aaeccb73dd310010",
	"object": "subscription",
	"display_name": "Plus Plan",
	"plan": {
		"period_amount": 1,
		"period_type": "M",
		"amount": 7200,
		"currency": "USD",
		"discount": 0.0,
		"item_id": 101
	},
	"cycle_number": 1,
	"period_start": 1375217068,
	"period_end": 1375217068,
	"next_charge": 1375217068,
	"customer": {
		"id": "cu4321",
		"object": "customer",
	}
}
```

List all subscriptions
-----------------
Returns a list of all subscriptions.

### Arguments

Name | Required | Description
--:|:-:|:--
**count** | optional |
**offset** | optional |
**customer** | optional |

### Example request

	$ curl https://secure.peakium.com/api/v1/subscriptions/?count=2 \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9:

### Example response

```json
{
	"object": "list",
	"count": 2,
	"data": [
		{
			"id": "50aaeccb73dd310010",
			"object": "subscription",
			"display_name": "Plus Plan",
			"plan": {
				"period_amount": 1,
				"period_type": "M",
				"amount": 7200,
				"currency": "USD",
				"discount": 0.0,
				"item_id": 101
			},
			"cycle_number": 1,
			"period_start": 1375217068,
			"period_end": 1375217068,
			"next_charge": 1375217068,
			"customer": {
				"id": "cu4321",
				"object": "customer",
			}
		},
		{...}
	]
}
```