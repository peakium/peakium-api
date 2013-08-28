Gateway
=======

The gateway object(s) is the gateway(s) that you can use to do payments. The gateway(s) is listed in your Peakium account.

The gateway object
------------------

### Attributes

Name | Type | Description
--:|:-:|:--
**id** | string |
**object** | string | Is "gateway".
**created** | integer |
**name** | string | The reference name for your gateway.
**active** | boolean |
**default** | boolean |
**module** | object | The gateway module name.
**settings** | array |

### Example

```json
{
	"id": "gw_TlTNIsHSf5lh85",
	"object": "gateway",
	"created": 1375217068,
	"name": "Paypal",
	"display_name": "Paypal",
	"active": true,
	"default": false,
	"module": {
		"object": "gateway_module",
		"name": "Paypal_Website_Payments_Standard",
		"required_fields": [
			"paypal_email"
		]
	},
	"settings": {
		"paypal_email": "paypal@example.com"
	}
}
```

List all gateway
----------------
Returns a list of all available gateways.

### Arguments

Name | Required | Description
--:|:-:|:--
**count** | optional |
**offset** | optional |

### Example request

	$ curl https://secure.peakium.com/api/v1/gateways/?count=2 \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9:

### Example response

```json
{
	"object": "list",
	"count": 2,
	"data": [
		{
			"id": "gw_TlTNIsHSf5lh85",
			"object": "gateway",
			"created": 1375217068,
			"name": "Paypal",
			"display_name": "Paypal",
			"active": true,
			"default": false,
			"module": {
				"object": "gateway_module",
				"name": "Paypal_Website_Payments_Standard",
				"required_fields": [
					"paypal_email"
				]
			},
			"settings": {
				"paypal_email": "paypal@example.com"
			}
		},
		{...}
	]
}
```

Set a gateway as the default gateway
------------------------------------
A specific gateway can be set as the default gateway to use. Any previous default gateway will be unset as the default gateway.

### Example request

	$ curl https://secure.peakium.com/api/v1/gateways/gw_TlTNIsHSf5lh85/default/ \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9: \
		-X POST

### Example response

Will respond with `200 OK` status, and the full gateway object if valid, or fail with HTTP status codes.

Create or update a gateway
---------------------------
A gateway can be created and/or updated over the API.

### Arguments

Name | Required/Optional | Description
--:|:-:|:--
**name** | required | The gateway reference name.
**module** | required | The gateway module name.
**settings** | required | An array of settings for the gateway.

### Example request create

	$ curl https://secure.peakium.com/api/v1/gateways/ \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9: \
		-d name="Paypal" \
		-d display_name="Paypal" \
		-d module="Paypal_Website_Payments_Standard" \
		-d settings["paypal_email"]="paypal@example.com"

### Example request update

	$ curl https://secure.peakium.com/api/v1/gateways/gw_TlTNIsHSf5lh85/ \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9: \
		-d name="Paypal" \
		-d display_name="Paypal" \
		-d module="Paypal_Website_Payments_Standard" \
		-d settings["paypal_email"]="paypal@example.com"

### Example response

Will respond with `200 OK` status, and the full gateway object if valid, or fail with failure HTTP status code.