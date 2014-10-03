Gateway Module
==============

The gateway gateway module is the type of gateway payment that a gateway is connecting to.

The gateway object
------------------

### Attributes

Name | Type | Description
--:|:-:|:--
**object** | string | Is "gateway_module".
**name** | string |
**required_fields** | array |
**necessary_gateway_settings** | array |
**required_field_parameters** | array |

### Example

```json
{
	"object": "gateway_module",
	"name": "Paypal_Payments_Standard",
	"required_fields": [
		"paypal_email"
	],
	"necessary_gateway_settings": [
		"instant_payment_notification_url"
	],
	"required_field_parameters": {
		"paypal_email": {
			"description": "The e-mail of the Paypal account."
		}
	}
}
```

List all gateway modules
------------------------
Returns a list of all available gateway modules.

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
			"object": "gateway_module",
			"name": "Paypal_Payments_Standard",
			"required_fields": [
				"paypal_email"
			],
			"necessary_gateway_settings": [
				"instant_payment_notification_url"
			],
			"required_field_parameters": {
				"paypal_email": {
					"description": "The e-mail of the Paypal account."
				}
			}
		},
		{...}
	]
}
```