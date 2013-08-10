Invoice
=======

The invoice object presents invoices that has been created in relation to a subscription or customer in your account.

The invoice object
------------------

### Attributes

Name | Type | Description
--:|:-:|:--
**id** | string |
**object** | string | Is "invoice".
**created** | integer |
**due** | integer | When the invoice is to be paid the latest.
**locked** | boolean |
**timestamp_locked** | integer |
**paid** | boolean |
**timestamp_paid** | integer |
**retracted** | boolean |
**timestamp_retracted** | integer |
**type** | string | Describes if the invoice is a recurring event, or is a user based action.
**calculated_total** | array | An array containing the currency and amount calculated to be paid in the invoice. The invoice might change during it's lifetime, so it is a current view of the total for the invoice.
**calculated_total**->**currency**  | string |
**calculated_total**->**amount**  | integer |
**attempt_automatic_charge** | boolean | If an invoice will be automatically charged, or requires action from the customer.
**items** | array | An array containing a list of invoice item objects.
**customer** | object |
**charge** | object |

### Example

```json
{
	"id": "in_TlQFJ1ZvXfuX2g",
	"object": "invoice",
	"created": 1375217068,
	"due_date": 1375217068,
	"locked": true,
	"timestamp_locked": 1375217068,
	"paid": true,
	"timestamp_paid": 1375217068,
	"retracted": false,
	"timestamp_retracted": null,
	"type": "single",
	"calculated_total": {
		"currency": "USD",
		"amount": 7200
	},
	"attempt_automatic_charge": true,
	"items": [
		{
			"object": "invoice_item",
			"type": "debit",
			"description": "Plus Plan",
			"item_id": 101,
			"unit_amount": 7200,
			"currency": "USD",
			"quantity": 1,
			"date_range_start": 1375217068,
			"date_range_end": 1375217068,
			"discount": 0.0,
			"total_amount": 7200,
			"reference": {
				"id": "50aaeccb73dd310010"
				"object": "subscription"
			}
		}
	],
	"customer": {
		"id": "cu4321",
		"object": "customer",
	},
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

List all invoices
-----------------
Returns a list of all invoices.

### Arguments

Name | Required | Description
--:|:-:|:--
**count** | optional |
**offset** | optional |
**customer** | optional |
**overdue** | optional | Boolean presenting if only overdue invoices should be returned

### Example request

	$ curl https://secure.peakium.com/api/v1/invoices/?count=2 \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9:

### Example response

```json
{
	"object": "list",
	"count": 2,
	"data": [
		{
			"id": "in_TlQFJ1ZvXfuX2g",
			"object": "invoice",
			"created": 1375217068,
			"due_date": 1375217068,
			"locked": true,
			"timestamp_locked": 1375217068,
			"paid": true,
			"timestamp_paid": 1375217068,
			"retracted": false,
			"timestamp_retracted": null,
			"type": "single",
			"calculated_total": {
				"currency": "USD",
				"amount": 7200
			},
			"attempt_automatic_charge": true,
			"items": [
				{
					"object": "invoice_item",
					"type": "debit",
					"description": "Plus Plan",
					"item_id": 101,
					"unit_amount": 7200,
					"currency": "USD",
					"quantity": 1,
					"date_range_start": 1375217068,
					"date_range_end": 1375217068,
					"discount": 0.0,
					"total_amount": 7200,
					"reference": {
						"id": "50aaeccb73dd310010"
						"object": "subscription"
					}
				}
			],
			"customer": {
				"id": "cu4321",
				"object": "customer",
			},
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

Attempt payment of an invoice
-----------------------------
It is possible with certain invoices to attempt a payment at the present time. You can request an invoice to be paid through the API. Payments are only possible for API type gateways, and not external type gateways.

### Example request

	$ curl https://secure.peakium.com/api/v1/invoices/in_TlQFJ1ZvXfuX2g/pay/ \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9: \
		-x POST

### Example response

Will respond with `200 OK` status, and the full invoice object if payment could go through, or fail with HTTP status codes.