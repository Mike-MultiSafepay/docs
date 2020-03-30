---
weight: 304
meta_title: "API - Create Apple Pay transaction - Developers MultiSafepay"
meta_description: "In the MultiSafepay Documentation Center all relevant information regarding our Plugins and API. As well as Support pages for Payment Method, Tools and General Questions. You can also find the contact details of our Support Team and Integration Team."
---
{{< code-block >}}

> POST - /orders 

```shell 

{
    "type": "redirect",
    "order_id": "my-order-id-1",
    "gateway": "",
    "currency": "EUR",
    "amount": "9743",
    "description": "Test Order Description",
    "manual": "false",
    "payment_options": {
        "notification_url": "http://www.example.com/client/notification?type=notification",
        "redirect_url": "http://www.example.com/client/notification?type=redirect",
        "cancel_url": "http://www.example.com/client/notification?type=cancel",
        "close_window": ""
    },
```

> JSON Response 

```shell
{
  "success": true,
  "data": {
    "order_id": "my-order-id-1",
    "payment_url": "https://payv2.multisafepay.com/connect/13ztRF4ic5Kz23n2Lf5F3UzcVqMRxwjlfQw/?lang=nl_NL"
  }
}
```

> POST - /orders

```shell 

{
    "type": "redirect",
    "order_id": "my-order-id-1",
    "gateway": "APPLEPAY",
    "currency": "EUR",
    "amount": "9743",
    "description": "Test Order Description",
    "manual": "false",
    "payment_options": {
        "notification_url": "http://www.example.com/client/notification?type=notification",
        "redirect_url": "http://www.example.com/client/notification?type=redirect",
        "cancel_url": "http://www.example.com/client/notification?type=cancel",
        "close_window": ""
    },
```

> JSON Response 

```shell
{
  "success": true,
  "data": {
    "order_id": "my-order-id-1",
    "payment_url": "https://payv2.multisafepay.com/connect/13ztRF4ic5Kz23n2Lf5F3UzcVqMRxwjlfQw/?lang=nl_NL"
  }
}
```

{{< /code-block >}}

{{< description >}}

## Apple Pay

All parameters shown are required field(s) for a Apple Pay _Redirect_ transaction. 

__How to detect Apple Pay on a device__

```JavaScript
try {
    if (window.ApplePaySession && ApplePaySession.canMakePayments()) {
    console.log('ApplePay available');
    }
    } catch (error) {
    console.debug('An error occurred while verifying if Apple Pay is available:', error);
    }
```
If this code is not implemented in your back-end platform, consumers choosing Apple Pay on the payment page will be displayed an error if their device does not support Apple Pay, thus we highly reccomend using the abovementioned code to avoid any issues.

| Parameter                       | Type     | Description                                                                             |
|---------------------------------|----------|-----------------------------------------------------------------------------------------|
| type                            | string | Specifies the payment flow for the checkout process. Options: Redirect.                   |
| gateway                         | string | The payment gateway does not need to be specified.
| order_id                        | <nobr>string\|integer</nobr> | The unique identifier from your system for the order. If the values are only numbers the type will be integer, otherwise it will be string.                                   |
| currency                        | string | The currency [ISO-4217](https://www.iso.org/iso-4217-currency-codes.html) you want the customer to pay with. |
| amount                          | integer | The amount (in cents) that the customer has to pay.                                     |
| description                     | string | A text which will be shown with the order in MultiSafepay Control. If the customer's bank supports it this will also be shown on the bank statement. Max. 200 characters. HTML is no longer supported. Use the 'items' or 'shopping_cart' objects for this. |
| payment_options                 | object |   |
| notification_url                | string    | Endpoint where we will send the notifications to [notification_url](/faq/api/how-does-the-notification-url-work/)|
| redirect_url                    | string    | Customer will be redirected to this page after a successful payment. In the event that the transaction is marked with the status uncleared, the customer will also be redirected to the thank-you page of the webshop. The uncleared status will not be passed on to the customer who will experience the payment as successful at all times.|
| cancel_url                      | string    | Customer will be redirected to this page after a failed payment.  | 


### Apple Pay Direct

All parameters shown are required field(s) for a Apple Pay _Direct_ transaction. Please note this is a  simply a _Redirect_ call with 'APPLEPAY' pre-selected.

It must be noted that the 'gateway' parameter for the Apple Pay direct transaction __must be set to 'APPLEPAY'__ in order for Apple Pay to be preselected on the payment page. The payment page will detect whether the device being used supports Apple Pay or not.

If the device supports Apple Pay, the user will be directed to the Apple Pay interface where a payment can be completed. If the device does not support Apple Pay, an error will be displayed. The following code will allow the detection of Apple Pay. This can be implemented to your platform:


__How to detect Apple Pay on a device__

```JavaScript
try {
    if (window.ApplePaySession && ApplePaySession.canMakePayments()) {
    console.log('ApplePay available');
    }
    } catch (error) {
    console.debug('An error occurred while verifying if Apple Pay is available:', error);
    }
```

| Parameter                       | Type     | Description                                                                             |
|---------------------------------|----------|-----------------------------------------------------------------------------------------|
| type                            | string | Specifies the payment flow for the checkout process. Options: Redirect.                   |
| gateway                         | string | Fixed value: [APPLEPAY](/payment-methods/wallet/applepay/)|
| order_id                        | <nobr>string\|integer</nobr> | The unique identifier from your system for the order. If the values are only numbers the type will be integer, otherwise it will be string.                                   |
| currency                        | string | The currency [ISO-4217](https://www.iso.org/iso-4217-currency-codes.html) you want the customer to pay with. |
| amount                          | integer | The amount (in cents) that the customer has to pay.                                     |
| description                     | string | A text which will be shown with the order in MultiSafepay Control. If the customer's bank supports it this will also be shown on the bank statement. Max. 200 characters. HTML is no longer supported. Use the 'items' or 'shopping_cart' objects for this. |
| payment_options                 | object |   |
| notification_url                | string    | Endpoint where we will send the notifications to [notification_url](/faq/api/how-does-the-notification-url-work/)|
| redirect_url                    | string    | Customer will be redirected to this page after a successful payment. In the event that the transaction is marked with the status uncleared, the customer will also be redirected to the thank-you page of the webshop. The uncleared status will not be passed on to the customer who will experience the payment as successful at all times.|
| cancel_url                      | string    | Customer will be redirected to this page after a failed payment.  | 


Read more about [Apple Pay](/payment-methods/wallet/applepay/) on our documentation page.

{{< /description >}}