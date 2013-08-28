Event webhook
=============

An event webhook object will be created whenever an event is created. The event webhook is making sure that a specific webhook endpoint receives the event.

The event webhook object is read-only.

The event webhook object
------------------------

### Attributes

Name | Type | Description
--:|:-:|:--
**object** | string | Is "event_webhook"
**created** | integer |
**number_of_attempted_deliveries** | integer |
**last_delivery_attempt** | integer | The timestamp for the last delivery attempt
**delivered** | boolean |
**timestamp_delivered** | integer |
**webhook** | object | The webhook object.
**event** | object | The event object.

### Example

```json
{
	"object": "event_webhook",
	"number_of_attempted_deliveries": 1,
	"last_delivery_attempt": 1375217068,
	"delivered": true,
	"delivered_timestamp": 1375217068,
	"webhook": {
		"object": "webhook",
		"url": "http://example.com/webhook_endpoint/"
	},
	"event": {
		"id": "ev_TlSEvdkrRAg4aD",
		"object": "event",
		"event": "subscription.created",
		"created": 1375217068,
		"subscription": {
			"id": "50aaeccb73dd310010",
			"object": "subscription"
		},
	},
}
```

List all event webhooks
-----------------------
Returns a list of all event webhooks.

### Arguments

Name | Required | Description
--:|:-:|:--
**count** | optional |
**offset** | optional |
**event** | optional |
**url** | optional |

### Example request

	$ curl https://secure.peakium.com/api/v1/event_webhooks/?count=2 \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9:

### Example response

```json
{
	"object": "list",
	"count": 2,
	"data": [
		{
			"object": "event_webhook",
			"number_of_attempted_deliveries": 1,
			"last_delivery_attempt": 1375217068,
			"delivered": true,
			"delivered_timestamp": 1375217068,
			"webhook": {
				"object": "webhook",
				"url": "http://example.com/webhook_endpoint/"
			},
			"event": {
				"id": "ev_TlSEvdkrRAg4aD",
				"object": "event",
				"event": "subscription.created",
				"created": 1375217068,
				"subscription": {
					"id": "50aaeccb73dd310010",
					"object": "subscription"
				},
			},
		},
		{...}
	]
}
```