Customer
========

The ID of a customer object is the same as the ID you have given through your application.

The customer object is read only.

The customer object
-------------------

### Attributes

Name | Type | Description
--:|:-:|:--
**id** | string |
**object** | string | Is "customer".
**created** | integer |
**balances** | list | A list of the customer's balances separated into currencies.
**metadata** | object |


### Example

```json
{
	"id": "cu4321",
	"object": "customer",
	"created": 1375217068,
	"balances": {
		"USD": 5612
	},
	"metadata": {}
}
```

List all customers
------------------
Returns a list of all customers.

### Arguments

Name | Required | Description
--:|:-:|:--
**count** | optional |
**offset** | optional |

### Example request

	curl https://secure.peakium.com/api/v1/customers/?count=2 \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9:

### Example response

```json
{
	"object": "list",
	"count": 2,
	"data": [
		{
			"id": "cu4321",
			"object": "customer",
			"created": 1375217068,
			"balances": {
				"USD": 5612
			},
			"metadata": {}
		},
		{...}
	]
}
```

Create or update customer
-------------------------

### Arguments

Name | Required/Optional | Description
--:|:-:|:--
**id** | required | The unique customer ID.
**metadata** | optional | An array.

### Example request create

	$ curl https://secure.peakium.com/api/v1/customers/ \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9: \
		-d id="UNIQUE_ID"

### Example request update

	$ curl https://secure.peakium.com/api/v1/customers/UNIQUE_ID/ \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9: \
		-d metadata[name]="Customer Name"

### Example response

Will respond with `200 OK` status, and the full customer object if valid, or fail with failure HTTP status code.
