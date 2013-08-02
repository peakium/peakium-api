Webhook
=======

Webhook objects define the URL endpoints for webhooks.

The webhook object
------------------

### Attributes

Name | Type | Description
--:|:-:|:--
**object** | string | Will be "webhook"
**url** | string |

### Example

```json
{
	"object": "webhook",
	"url": "http://example.com/webhook_endpoint/"
}
```

List all webhooks
-----------------
Returns a list of all webhooks.

### Arguments

Name | Required | Description
--:|:-:|:--
**count** | optional |
**offset** | optional |

### Example request

	$ curl https://secure.peakium.com/api/v1/webhooks/?count=2 \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9:

### Example response

```json
{
	"object": "list",
	"count": 2,
	"data": [
		{
			"object": "webhook",
			"url": "http://example.com/webhook_endpoint/"
		},
		{...}
	]
}
```

Create a webhook
----------------
A webhook can be created over the API.

### Arguments

Name | Required | Description
--:|:-:|:--
**url** | required | The webhook URL endpoint

### Example request

	$ curl https://secure.peakium.com/api/v1/webhooks/ \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9: \
		-d url="http://example.com/webhook_endpoint/"

### Example response

Will respond with `200 OK` status, and the full webhook object if valid, or fail with failure HTTP status code.
