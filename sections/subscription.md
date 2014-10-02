Subscription
============

A subscription object is always tied to a [Customer](/sections/customer.md). The subscription token is only unique within the customer scope, thus it is possible to reuse the same subscription token for different customers. For this reason, when you are handling individual subscriptions, you are always required to use the [Customer](/sections/customer.md) resource.

A subscription can be created by a customer through the submission form. The subscription object can be cancelled through the API.

The subscription object
-----------------------

### Attributes

Name | Type | Description
--:|:-:|:--
**token** | string | The token is under the scope of a customer
**object** | string | Will be "subscription"
**created** | integer |
**plan** | array | 
**plan**->**period_amount** | integer | 
**plan**->**period_type** | string | day, month or year
**plan**->**items** | object | A list of items the subscription has
**plan**->**items**>**item_id** | required |
**plan**->**items**>**item_description** | required |
**plan**->**items**>**unit_amount** | required |
**plan**->**items**>**currency** | optional |
**plan**->**items**>**quantity** | optional |
**plan**->**items**>**discount** | optional |
**plan**->**currency** | string | 
**cycle_number** | integer |
**period_start** | integer |
**period_end** | integer |
**next_charge** | integer |
**status** | string |
**customer** | object |
**metadata** | object |

### Example

```json
{
	"token": "50aaeccb73dd310010",
	"object": "subscription",
	"created": 1375217068,
	"display_name": "Plus Plan",
	"plan": {
		"period_amount": 1,
		"period_type": "month",
		"amount": 7200,
		"currency": "USD",
		"discount": 0.0,
		"item_id": 101
	},
	"cycle_number": 1,
	"period_start": 1375217068,
	"period_end": 1375217068,
	"next_charge": 1375217068,
	"status": "active",
	"customer": "cu4321"
}
```

List all subscriptions
----------------------
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
			"token": "50aaeccb73dd310010",
			"object": "subscription",
			"created": 1375217068,
			"display_name": "Plus Plan",
			"plan": {
				"period_amount": 1,
				"period_type": "month",
				"amount": 7200,
				"currency": "USD",
				"discount": 0.0,
				"item_id": 101
			},
			"cycle_number": 1,
			"period_start": 1375217068,
			"period_end": 1375217068,
			"next_charge": 1375217068,
			"status": "active",
			"customer": "cu4321"
		},
		{...}
	]
}
```

List all subscriptions for a specific customer
----------------------------------------------
Returns a list of all subscriptions for a specific customer.

### Arguments

Name | Required | Description
--:|:-:|:--
**count** | optional |
**offset** | optional |

### Example request

	$ curl https://secure.peakium.com/api/v1/customers/cu4321/subscriptions/?count=2 \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9:

### Example response

```json
{
	"object": "list",
	"count": 2,
	"data": [
		{
			"token": "50aaeccb73dd310010",
			"object": "subscription",
			"created": 1375217068,
			"display_name": "Plus Plan",
			"plan": {
				"period_amount": 1,
				"period_type": "month",
				"amount": 7200,
				"currency": "USD",
				"discount": 0.0,
				"item_id": 101
			},
			"cycle_number": 1,
			"period_start": 1375217068,
			"period_end": 1375217068,
			"next_charge": 1375217068,
			"status": "active",
			"customer": "cu4321"
		},
		{...}
	]
}
```

Retrieve a specific subscription
--------------------------------
To retrieve a specific subscription resource, you need to use the [Customer](/sections/customer.md) resource for the subscription in the URI.

### Example request

	$ curl https://secure.peakium.com/api/v1/customers/cu4321/subscriptions/50aaeccb73dd310010/ \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9:

### Example response

```json
{
	"token": "50aaeccb73dd310010",
	"object": "subscription",
	"display_name": "Plus Plan",
	"plan": {
		"period_amount": 1,
		"period_type": "month",
		"amount": 7200,
		"currency": "USD",
		"discount": 0.0,
		"item_id": 101
	},
	"cycle_number": 1,
	"period_start": 1375217068,
	"period_end": 1375217068,
	"next_charge": 1375217068,
	"status": "active",
	"customer": "cu4321"
}
```

Cancel a subscription
---------------------
This will cancel an active subscription, and stop any future charges. A cancelled subscription cannot be reactivated.

You need to use the [Customer](/sections/customer.md) resource for the subscription in the URI to cancel a subscription.

### Example request

	$ curl https://secure.peakium.com/api/v1/customers/cu4321/subscriptions/50aaeccb73dd310010/ \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9: \
		-X DELETE

### Example response

```json
{
	"token": "50aaeccb73dd310010",
	"object": "subscription",
	"created": 1375217068,
	"display_name": "Plus Plan",
	"plan": {
		"period_amount": 1,
		"period_type": "month",
		"amount": 7200,
		"currency": "USD",
		"discount": 0.0,
		"item_id": 101
	},
	"cycle_number": 1,
	"period_start": 1375217068,
	"period_end": 1375217068,
	"next_charge": 1375217068,
	"status": "cancelled",
	"customer": "cu4321"
}
```