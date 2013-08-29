Event
=====

When an event object is created, subsequent event webhooks are created based on the webhook endpoints registered at the moment of the creation.

The event object has a method to be validated for added security.

An event webhook will be tried to be delivered each hour until delivered, or until 24 tries. The event webhook(s) can, at any time, be requested through the API to be resend to webhook endpoints.

The event object
----------------

### Attributes

Name | Type | Description
--:|:-:|:--
**id** | string |
**object** | string | Is "event".
**event** | string | The event type.
**created** | integer |
**data** | object | Referencing data. E.g. customer, invoice or subscription.

### Example

```json
{
	"id": "ev_TlSEvdkrRAg4aD",
	"object": "event",
	"event": "subscription.created",
	"created": 1375217068,
	"data": {
		"object": {
			"token": "50aaeccb73dd310010",
			"object": "subscription",
			"created": 1375217068,
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
			"status": "active",
			"customer": {
				"id": "cu4321",
				"object": "customer",
			}
		}
	}
}
```

Event types
-----------

Event | Description
--:|:--
**customer.created** | 
**invoice.locked** | 
**invoice.paid** | 
**invoice.payment_failed** | 
**payment_session.started** | 
**subscription.cancelled** | 
**subscription.created** | 
**subscription.updated** | 


List all events
---------------
Returns a list of all events.

### Arguments

Name | Required | Description
--:|:-:|:--
**count** | optional |
**offset** | optional |
**customer** | optional |
**invoice** | optional |
**subscription** | optional | Requires the customer argument to be defined also.

### Example request

	$ curl https://secure.peakium.com/api/v1/events/?count=2 \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9:

### Example response

```json
{
	"object": "list",
	"count": 2,
	"data": [
		{
			"id": "ev_TlSEvdkrRAg4aD",
			"object": "event",
			"event": "subscription.created",
			"created": 1375217068,
			"data": {
				"object": {
					"token": "50aaeccb73dd310010",
					"object": "subscription",
					"created": 1375217068,
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
					"status": "active",
					"customer": {
						"id": "cu4321",
						"object": "customer"
					}
				}
			}
		},
		{...}
	]
}
```

Validate an event
-----------------
To make sure that a request is not forged, you can validate the authenticity of an incoming event webhook. Send the full retrieved JSON event in the body as a POST request.

### Example request

	$ curl https://secure.peakium.com/api/v1/events/ev_TlSEvdkrRAg4aD/validate/ \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9: \
		-d '{"id":"ev_TlSEvdkrRAg4aD","object":"event","event":"subscription.created","created":1375217068,"data":{"token":"50aaeccb73dd310010","object":"subscription","created":1375217068,"display_name":"PlusPlan","plan":{"period_amount":1,"period_type":"M","amount":7200,"currency":"USD","discount":0.0,"item_id":101},"cycle_number":1,"period_start":1375217068,"period_end":1375217068,"next_charge":1375217068,"status":"active","customer":{"id":"cu4321","object":"customer"}}}'

### Example response

Will respond with `200 OK` status, and the full event object if valid, or fail with failure HTTP status code..

Resending an event
------------------
In certain cases you might want to resend events right away. The resend request can be directed to a specific event webhook endpoint, or to all the event webhooks existing for the event at once.

### Arguments

Name | Required | Description
--:|:-:|:--
**force** | optional | Boolean representing if the delivery should be forced or not. A forced delivery results in the event being send even if the event webhook is in a time lock.
**url** | optional | The URL for a specific webhook endpoint. If the webhook endpoint doesn't exist, the API will return `400 Bad Request`.

### Example request

	$ curl https://secure.peakium.com/api/v1/events/ev_TlSEvdkrRAg4aD/send/ \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9: \
		-d force=true \
		-d url="http://example.com/webhook_endpoint/"

### Example response

Will respond with `200 OK` status, and the full event object if valid, or fail with failure HTTP status code.