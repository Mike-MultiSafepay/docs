---
title: "Bancontact QR, How it works"
weight: 21
meta_title: "Bancontact QR, How it works - MultiSafepay Support"
meta_description: "The MultiSafepay Documentation Center presents all relevant information about our Plugins and API. You can also find support pages for Payment Methods, Tools and General Questions as well as the contact details of our Support and Integration Teams."
---

## How it works
A customer chooses to pay with Bancontact QR, authenticates their account and confirms to pay. Once a payment is completed, the payout is guaranteed and can not be reversed by the customer.

The full API reference for Bancontact QR can be found [here](/api/#bancontact-qr)

### Transaction flow
The transaction flow shows the different ways a transaction can be processed. This differs per payment method.

* Order status      
The order status indicates the status of the order, such as _completed_, _pending_ or _rejected_. The order status is independent of the incoming or outgoing payment of the transaction.

* Transaction status       
The transaction status indicates the payment status of the transaction, such as _completed_, _pending_ or _rejected_. Once the transaction status is _completed_, the amount of the transaction is added to your MultiSafepay balance.


| Order Status                      | Transaction Status      | Description |
|--------------------------------|-----------|-----------------------------------------------------------------------------------------|
| Initialized | Initialized | A payment link has been generated, but no payment has been received yet.  | 
| Completed   | Completed   | A successful Bancontact transaction has been received and the funds will be added to your MultiSafepay Control balance.   | 
| Declined    | Declined    | Transaction has been rejected   | 
| Expired     | Expired     | An unfinished transaction will automatically expire after a predefined period.  | 
| Void        | Cancelled    | Transaction has been cancelled.   | 


#### Refund flow 

| Order Status                      | Transaction Status      | Description |
|--------------------------------|-----------|-----------------------------------------------------------------------------------------|
| Reserved       | Reserved    | A refund has been requested. | 
| Completed      | Completed   | Refund has been successfully processed.  | 

### Product rules
Some rules may apply to certain payment methods. For Bancontact QR, the following rules apply:

* Refunding more than the stated amount of the original transaction is possible with Bancontact QR (e.g. refunding the return costs incurred by the customer). More information is available on our [refund more than original amount](/faq/finance/refund-more-than-original-amount/) page. Please bear in mind that by default, MultiSafepay does not allow refunds larger than  the original transaction amount and that this needs to be changed in your MultiSafepay Control 

* Successful Bancontact QR transactions have no expiring date regarding refunding, as long as the receiving bank is able to process the refund

* The lifetime of a payment link can be adjusted. This might be beneficial for your inventory. The adjustment can be processed through the days or seconds active.   
Full documentation can be found on our [lifetime of a payment link](/faq/api/lifetime-of-a-payment-link/) FAQ page.


* Payments done through Bancontact QR are processed in [Euros (EUR)](/faq/general/which-currencies-are-supported-by-multisafepay/)


