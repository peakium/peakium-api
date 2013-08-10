Submission Form
===============

The submission form resource is not an actual data resource. It is a helper resource that returns submission forms so your customers can be transferred smoothly to the correct location when necessary.

For security, each form contains a field with a salted integrity hash to secure against modification of the `POST` values. For your convenience Peakium automatically build these forms through the API with this resource handle.

Form for new subscriptions
--------------------------
This call will build a form so customers can create new subscriptions through any gateway you have registered at Peakium.

### Arguments

Name | Required | Description
--:|:-:|:--
**customer** | required | The reference id for your customer object in your application.
**subscription** | required | The reference id for your customer-specific subscription object in your application.
**item_description** | required |
**item_id** | required |
**period_amount** | required |
**period_type** | required | day, month or year
**payment_amount** | required |
**payment_currency** | required |
**payment_discount** | required |
**return_url_ok** | required |
**return_url_error** | required |
**gateway** | optional | If not defined, the gateway parameter will be set automatically depending on default payment method for your customer, and your default gateway.
**submit_button_text** | optional | What text the submit button should contain. Default is "*Click here if you are not redirected within 10 seconds*".
**auto_submit_page** | optional | A boolean value representing if the returning HTML should include the full auto submit page. If `false`, or undefined, only the form element will be returned.
**auto_submit_page_title** | optional | A string for the title to display in the auto submit page. Default is "*Redirecting to payment method...*"

### Example request

	curl https://secure.peakium.com/api/v1/submission_form/create-subscription/ \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9: \
		-p customer="cu4321" \
		-p subscription="50aaeccb73dd310010" \
		-p item_description="Plus Plan" \
		-p item_id=101 \
		-p period_amount=1 \
		-p period_type="month" \
		-p payment_amount=7200 \
		-p payment_currency="USD" \
		-p payment_discount=0.0 \
		-p return_url_ok="http://example.org/payment/success/" \
		-p return_url_error="http://example.org/payment/error/" \
		-p auto_submit_page=true

### Example response

```json
{
	"html": "<!DOCTYPE html PUBLIC \"-\/\/W3C\/\/DTD XHTML 1.0 Transitional\/\/EN\" \"http:\/\/www.w3.org\/TR\/xhtml1\/DTD\/xhtml1-transitional.dtd\"><html xmlns=\"http:\/\/www.w3.org\/1999\/xhtml\"><head><title>Redirecting to payment method...<\/title><\/head><body><h3>Redirecting to payment method...<\/h3><body onload=\"document.p.submit();\"><form action=\"http:\/\/secure.peakium.com\/update-subscription\/\" method=\"post\" name=\"p\"><input type=\"hidden\" name=\"action\" value=\"create\" \/><input type=\"hidden\" name=\"customer\" value=\"cu4321\" \/><input type=\"hidden\" name=\"subscription\" value=\"50aaeccb73dd310010\" \/><input type=\"hidden\" name=\"item_description\" value=\"Plus Plan\" \/><input type=\"hidden\" name=\"item_id\" value=\"101\" \/><input type=\"hidden\" name=\"period_amount\" value=\"1\" \/><input type=\"hidden\" name=\"period_type\" value=\"month\" \/><input type=\"hidden\" name=\"payment_amount\" value=\"7200\" \/><input type=\"hidden\" name=\"payment_currency\" value=\"USD\" \/><input type=\"hidden\" name=\"payment_discount\" value=\"0\" \/><input type=\"hidden\" name=\"return_url_ok\" value=\"http:\/\/example.org\/payment\/success\/\" \/><input type=\"hidden\" name=\"return_url_error\" value=\"http:\/\/example.org\/payment\/error\/\" \/><input type=\"hidden\" name=\"publishable_key\" value=\"pk_QTBkCKdRworbXYZens4V4LZZs1X00FeM\" \/><input type=\"hidden\" name=\"gateway\" value=\"gw_TlTNIsHSf5lh85\" \/><input type=\"hidden\" name=\"integrity_value\" value=\"8cc1e258bfb0e8d7371ef068433b79b9ae910a48\" \/><input type=\"submit\" value=\"0\" \/><\/form><\/body><\/html>"
}
```

Form for upgrading existing subscriptions
-----------------------------------------
This call will build a form so customers can upgrade or downgrade existing subscriptions through any gateway you have registered at Peakium.

### Arguments

Name | Required | Description
--:|:-:|:--
**customer** | required | The reference id for your customer object in your application.
**subscription** | required | The reference id for your customer-specific subscription object in your application.
**item_description** | required |
**item_id** | required |
**period_amount** | required |
**period_type** | required | day, month or year
**payment_amount** | required |
**payment_currency** | required |
**payment_discount** | required |
**return_url_ok** | required |
**return_url_error** | required |
**gateway** | optional | If not defined, the gateway parameter will be set automatically depending on default payment method for your customer, and your default gateway.
**submit_button_text** | optional | What text the submit button should contain. Default is "*Click here if you are not redirected within 10 seconds*".
**auto_submit_page** | optional | A boolean value representing if the returning HTML should include the full auto submit page. If `false`, or undefined, only the form element will be returned.
**auto_submit_page_title** | optional | A string for the title to display in the auto submit page. Default is "*Redirecting to payment method...*"

### Example request

	curl https://secure.peakium.com/api/v1/submission_form/update-subscription/ \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9: \
		-p customer="cu4321" \
		-p subscription="50aaeccb73dd310010" \
		-p item_description="Plus Plan" \
		-p item_id=101 \
		-p period_amount=1 \
		-p period_type="month" \
		-p payment_amount=7200 \
		-p payment_currency="USD" \
		-p payment_discount=0.0 \
		-p return_url_ok="http://example.org/payment/success/" \
		-p return_url_error="http://example.org/payment/error/" \
		-p auto_submit_page=true

### Example response

```json
{
	"html": "<!DOCTYPE html PUBLIC \"-\/\/W3C\/\/DTD XHTML 1.0 Transitional\/\/EN\" \"http:\/\/www.w3.org\/TR\/xhtml1\/DTD\/xhtml1-transitional.dtd\"><html xmlns=\"http:\/\/www.w3.org\/1999\/xhtml\"><head><title>Redirecting to payment method...<\/title><\/head><body><h3>Redirecting to payment method...<\/h3><body onload=\"document.p.submit();\"><form action=\"http:\/\/secure.peakium.com\/update-subscription\/\" method=\"post\" name=\"p\"><input type=\"hidden\" name=\"action\" value=\"update\" \/><input type=\"hidden\" name=\"customer\" value=\"cu4321\" \/><input type=\"hidden\" name=\"subscription\" value=\"50aaeccb73dd310010\" \/><input type=\"hidden\" name=\"item_description\" value=\"Plus Plan\" \/><input type=\"hidden\" name=\"item_id\" value=\"101\" \/><input type=\"hidden\" name=\"period_amount\" value=\"1\" \/><input type=\"hidden\" name=\"period_type\" value=\"month\" \/><input type=\"hidden\" name=\"payment_amount\" value=\"7200\" \/><input type=\"hidden\" name=\"payment_currency\" value=\"USD\" \/><input type=\"hidden\" name=\"payment_discount\" value=\"0\" \/><input type=\"hidden\" name=\"return_url_ok\" value=\"http:\/\/example.org\/payment\/success\/\" \/><input type=\"hidden\" name=\"return_url_error\" value=\"http:\/\/example.org\/payment\/error\/\" \/><input type=\"hidden\" name=\"publishable_key\" value=\"pk_QTBkCKdRworbXYZens4V4LZZs1X00FeM\" \/><input type=\"hidden\" name=\"gateway\" value=\"gw_TlTNIsHSf5lh85\" \/><input type=\"hidden\" name=\"integrity_value\" value=\"8cc1e258bfb0e8d7371ef068433b79b9ae910a48\" \/><input type=\"submit\" value=\"0\" \/><\/form><\/body><\/html>"
}
```

Form for paying existing invoices
---------------------------------
This call will build a form so customers can pay invoices through any gateway you have registered at Peakium. It is useful for invoices that cannot be charged automatically (e.g. overdue invoices).

### Arguments

Name | Required | Description
--:|:-:|:--
**customer** | required | The reference id for your customer object in your application.
**invoice** | required | The id for the invoice object at Peakium.
**return_url_ok** | required |
**return_url_error** | required |
**gateway** | optional | If not defined, the gateway parameter will be set automatically depending on default payment method for your customer, and your default gateway.
**submit_button_text** | optional | What text the submit button should contain. Default is "*Click here if you are not redirected within 10 seconds*".
**auto_submit_page** | optional | A boolean value representing if the returning HTML should include the full auto submit page. If `false`, or undefined, only the form element will be returned.
**auto_submit_page_title** | optional | A string for the title to display in the auto submit page. Default is "*Redirecting to payment method...*"

### Example request

	curl https://secure.peakium.com/api/v1/submission_form/pay-invoice/ \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9: \
		-p customer="cu4321" \
		-p invoice="in_TlQFJ1ZvXfuX2g" \
		-p return_url_ok="http://example.org/payment/success/" \
		-p return_url_error="http://example.org/payment/error/"

### Example response

```json
{
	"html": "<form action=\"http:\/\/secure.peakium.com\/pay-invoice\/in_TlQFJ1ZvXfuX2g\/\" method=\"post\" name=\"p\"><input type=\"hidden\" name=\"customer\" value=\"cu4321\" \/><input type=\"hidden\" name=\"invoice\" value=\"in_TlQFJ1ZvXfuX2g\" \/><input type=\"hidden\" name=\"return_url_ok\" value=\"http:\/\/example.org\/payment\/success\/\" \/><input type=\"hidden\" name=\"return_url_error\" value=\"http:\/\/example.org\/payment\/error\/\" \/><input type=\"hidden\" name=\"publishable_key\" value=\"pk_QTBkCKdRworbXYZens4V4LZZs1X00FeM\" \/><input type=\"hidden\" name=\"gateway\" value=\"gw_TlTNIsHSf5lh85\" \/><input type=\"hidden\" name=\"integrity_value\" value=\"b860f950df56104a9328e44f6b3ce6e30f6db55a\" \/><input type=\"submit\" value=\"0\" \/><\/form>"
}
```

Form for single payments
------------------------
At times you might want customers to just pay a one-time fee. This call will build a form for paying one or more items.

### Arguments

Name | Required | Description
--:|:-:|:--
**customer** | required | The reference id for your customer object in your application.
**items** | required | A list of items to pay
**items**>**item_id** | required |
**items**>**item_description** | required |
**items**>**unit_amount** | required |
**items**>**currency** | required |
**items**>**quantity** | required |
**items**>**discount** | required |
**return_url_ok** | required |
**return_url_error** | required |
**gateway** | optional | If not defined, the gateway parameter will be set automatically depending on default payment method for your customer, and your default gateway.
**submit_button_text** | optional | What text the submit button should contain. Default is "*Click here if you are not redirected within 10 seconds*".
**auto_submit_page** | optional | A boolean value representing if the returning HTML should include the full auto submit page. If `false`, or undefined, only the form element will be returned.
**auto_submit_page_title** | optional | A string for the title to display in the auto submit page. Default is "*Redirecting to payment method...*"

### Example request

	curl https://secure.peakium.com/api/v1/submission_form/pay-invoice/ \
		-u pk_gEVUPX6FwObZSgg3v0BjkVxmdzatPyV9: \
		-p customer="cu4321" \
		-p items[0][item_id]=1 \
		-p items[0][item_description]="Setup fee" \
		-p items[0][unit_amount]=599 \
		-p items[0][currency]="USD" \
		-p items[0][quantity]=1" \
		-p items[0][discount]=0.0 \
		-p items[1][item_id]=2 \
		-p items[1][item_description]="1 hour support" \
		-p items[1][unit_amount]=999 \
		-p items[1][currency]="USD" \
		-p items[1][quantity]=1" \
		-p items[1][discount]=0.0 \
		-p invoice="in_TlQFJ1ZvXfuX2g" \
		-p return_url_ok="http://example.org/payment/success/" \
		-p return_url_error="http://example.org/payment/error/"

### Example response

```json
{
	"html": "<form action=\"http:\/\/secure.peakium.com\/single-payment\/\" method=\"post\" name=\"p\"><input type=\"hidden\" name=\"customer\" value=\"cu4321\" \/><input type=\"hidden\" name=\"items[0][item_id]\" value=\"1\" \/><input type=\"hidden\" name=\"items[0][item_description]\" value=\"Setup fee\" \/><input type=\"hidden\" name=\"items[0][unit_amount]\" value=\"599\" \/><input type=\"hidden\" name=\"items[0][currency]\" value=\"USD\" \/><input type=\"hidden\" name=\"items[0][quantity]\" value=\"1\" \/><input type=\"hidden\" name=\"items[0][discount]\" value=\"0.0\" \/><input type=\"hidden\" name=\"items[1][item_id]\" value=\"2\" \/><input type=\"hidden\" name=\"items[1][item_description]\" value=\"1 hour support\" \/><input type=\"hidden\" name=\"items[1][unit_amount]\" value=\"999\" \/><input type=\"hidden\" name=\"items[1][currency]\" value=\"USD\" \/><input type=\"hidden\" name=\"items[1][quantity]\" value=\"1\" \/><input type=\"hidden\" name=\"items[1][discount]\" value=\"0.0\" \/><input type=\"hidden\" name=\"return_url_ok\" value=\"http:\/\/example.org\/payment\/success\/\" \/><input type=\"hidden\" name=\"return_url_error\" value=\"http:\/\/example.org\/payment\/error\/\" \/><input type=\"hidden\" name=\"publishable_key\" value=\"pk_QTBkCKdRworbXYZens4V4LZZs1X00FeM\" \/><input type=\"hidden\" name=\"gateway\" value=\"gw_TlTNIsHSf5lh85\" \/><input type=\"hidden\" name=\"integrity_value\" value=\"b860f950df56104a9328e44f6b3ce6e30f6db55a\" \/><input type=\"submit\" value=\"0\" \/><\/form>"
}
```