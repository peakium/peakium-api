Peakium API
===========

The Peakium API is build on REST principles with resource-oriented URL's. The API is using HTTP status codes for errors. All responses will be returned in JSON format.

API Endpoints
-------------
* [Customer](/sections/customer.md)
* [Event](/sections/event.md)
* [Event Webhook](/sections/event_webhook.md)
* [Gateway](/sections/gateway.md)
* [Invoice](/sections/invoice.md)
* [Subscription](/sections/subscription.md)
* [Submission Form](/sections/submission_form.md)
* [Webhook](/sections/webhook.md)


Authentication
-------------
Authentication to the API is granted by using the test or live API key in your Peakium account. The API will request authentication via [HTTP Basic Auth](http://en.wikipedia.org/wiki/Basic_access_authentication). For the username, you will use the API key, and for the password you do not need to enter anything.

API keys can be found and rolled, when logged into your Peakium account. Please keep your API keys secure as they allow for many irreversible actions.

Authentication are mandatory for all requests to the API.

Example on authenticating an API request through curl:

	$ curl https://secure.peakium.com/api/v1/customers \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9:

SSL
---
All requests are required to be done through HTTPS. Requests over plain HTTP will be rejected.

Errors
-------------
Peakium uses HTTP status codes to indicate errors (or success). Codes in range 2xx indicates success, codes in 4xx range indicates a client side error (e.g. a missing or invalid parameter), and codes in 5xx range indicates an error in Peakium's system.

### HTTP status code errors

Error | Description
---|---
200 OK | The request was handled and returned correctly
400 Bad Request | Missing a required parameter, or using an invalid parameter
401 Unauthorized | No valid API key used
404 Not Found | A resource was not found
500 Internal Server Error | Something went wrong in Peakium's system

### Error return
The returning JSON on errors will often include the following attributes:

Name | Description
--:|:--
message | A human-readable message giving information about the error.

Versioning
-------------
Currently there is no versioning of the API. All users will be notified when backwards-incompatible changes are to be introduced.

Expanding objects
-------------
If an object contains the ID of another object, you can expand this object by using the `expand` attribute. As an example, you might want to view the customer for a subscription, thus the API call will be:

	$ curl https://secure.peakium.com/api/v1/subscription/50aaeccb73dd310010 \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9: \
		-d "expand[]=customer"

Identify your app
-------------
The Peakium API app will record logs of your requests. If you wish to more easily identify your apps, you can add a `User-Agent` header to the request. Example:

	User-Agent: Dan's Integration (dan@example.com)

Help us
-------

We always love to hear from you if you have any ideas of how to make the API better. You can contact us directly at <beta@peakium.com> with your suggestions. Also, feel free to fork these docs and send a pull request with improvements!	