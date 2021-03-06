---
title : "Klarna, How it works"
weight: 21
meta_title: "Klarna, How it works - MultiSafepay Support"
meta_description: "The MultiSafepay Documentation Center presents all relevant information about our Plugins and API. You can also find support pages for Payment Methods, Tools and General Questions as well as the contact details of our Support and Integration Teams."
read_more: '.'
---
# How it works
## Integration
Before integration can start, every merchant needs to sign an additional independent agreement with Klarna, where pricing is agreed upon and where the merchant is given a Klarna Merchant Number (EID) and a Shared Secret (Password). These credentials should be sent to MultiSafepay in order for us to be able to configure the Klarna Gateway within your MultiSafepay Control account. MultiSafepay will give all the necessary support during this process and when it is possible, facilitates the contract.

Once the Klarna Gateway is configured, you can start your integration using our plugins or by creating your own implementation with our [API](/api/)

## Activate an order
When a customer chooses to pay with Klarna, MultiSafepay will create a Klarna transaction marked "Not Shipped". After the order is shipped by the merchant to the customer, the order needs to be activated to start the communication process to the customer. After 14 business days, MultiSafepay will receive the funds from Klarna and will add the amount to your MultiSafepay Control balance.

To activate a Klarna order you need to log into [MultiSafepay Control](https://merchant.multisafepay.com) and go to the transaction details of the Klarna order. In the Order Details section there is a _Change Order Status_ button. Here you can change the status to _Shipped_ and provide Track & Trace details if desired.

Klarna does not support an Auto-Ship function, thus all orders have to be manually activated.

## Reservation Number & Invoice Number
For every transaction, a reservation number and an invoice number will be generated by Klarna. In case a created order is not yet activated, you can find the reservation number in MultiSafepay Control under the specific Klarna order and in the transaction details. This information can serve for merchants when getting into contact with Klarna about any questions at this stage of the process.

Similarly, once a Klarna order has been shipped (_shipped_ status), you can view the Klarna invoice number in MultiSafepay Control under the specific Klarna order in the transaction details.

All questions related to Klarna orders and transactions should be communicated directly to Klarna via <merchant@klarna.com>

## Transaction flow
The transaction flow shows the different ways a transaction can be processed. This differs per payment method.

* Order status      
The order status indicates the status of the order, such as _completed_, _pending_ or _rejected_. The order status is independent of the incoming or outgoing payment of the transaction.

* Transaction status       
The transaction status indicates the payment status of the transaction, such as _completed_, _pending_ or _rejected_. Once the transaction status is _completed_, the amount of the transaction is added to your MultiSafepay balance.

{{< alert-notice >}} From May 11th onwards, a Klarna transaction will no longer have the status _Initialized_ after acceptance of an order. This will be replaced by the status _Uncleared_ and will be changed to _Completed_ after shipment of the order and payment settlement from Klarna. Following this, the funds will be added to your account. If you have any questions regarding this change please contact <support@multisafepay.com> {{< /alert-notice >}} 


| Order Status                      | Transaction Status      | Description |
|--------------------------------|-----------|-----------------------------------------------------------------------------------------|
| Initialized   | Initialized  | A Klarna transaction has been initiated by the consumer.   |
| Completed  | Uncleared  | A successful Klarna transaction has been placed. The order is awaiting shipment. A payment has not yet been received by Klarna.   |
| Shipped    | Uncleared  | A capture has been sent to Klarna, the transaction has been confirmed. An invoice will be sent to the customer and your payout is guaranteed. |
| Shipped    | Completed  | Payout of a Klarna transaction has been received and added to your MultiSafepay Control balance.|
| Declined   | Declined   | Transaction has been rejected by Klarna. Behind the declined status in your [MultiSafepay Control](https://merchant.multisafepay.com/), the reason of rejection is shown.     |
| Void       | Cancelled   | Transaction has been cancelled.  | 
| Expired    | Expired    | When no action is being taken when receiving a transaction with the payment method Klarna, the transaction will automatically expire. | 

### Refund flow 

| Order Status                      | Transaction Status      | Description |
|--------------------------------|-----------|-----------------------------------------------------------------------------------------|
| Initialized    | Completed   | A refund has been requested. | 
| Completed      | Completed   | Refund has been successfully processed.  | 


The full API reference for Klarna can be found [here](/api/#klarna)


## Reconciliation & Reporting
MultiSafepay supports a fully reconciled implementation of Klarna. This means that all Klarna payments are received by MultiSafepay and forwarded to the specific merchant accounts. By having a fully reconciled implementation of Klarna we are able to add Klarna to all existing reports like the financial report and an MT940 report.

After 14 business days, MultiSafepay will receive funds from Klarna and make them available to all merchants. After 18-19 days, funds are made available in your merchant account balance.

## Customisation of invoices
Klarna enables all merchants to customise all invoices sent to your customers. In order to make changes to their styling and layout, you need to log in to your Klarna Merchant Account. All questions related to this topic should be referred directly to Klarna.

## Product rules
Some rules may apply to certain payment methods. For Klarna, the following rules apply:

* Refunding more than the stated amount of the original transaction is not possible with Klarna. More information is available on our [refund more than original amount](/faq/finance/refund-more-than-original-amount/) page.

* Successful Klarna transactions have no expiring date regarding refunding, as long as the receiving bank is able to process the refund.

* As a post-payment method, Klarna has a different payment flow and therefore the setting of days or seconds active will have no influence. Full documentation can be found on our [lifetime of a payment link](/faq/api/lifetime-of-a-payment-link/) FAQ page

* Payments done through Klarna are processed in [Euros (EUR)](/faq/general/which-currencies-are-supported-by-multisafepay/)

*  Klarna is currently offered in offered in Austria, Germany and the Netherlands

* As a rule of thumb, post-payment methods do not allow the use of a [gift card](/payment-methods/gift-cards/) by a customer when filling in the payment details (after the order has already been placed). This has to do with the accuracy of the order specifications, needed by the collecting party (i.e. Klarna). Our platform would otherwise interpret the gift card as a discount (which is not present in the shopping cart specification) and would not reflect the right order information needed, for example, for taxation purposes. However, using gift cards for post-payment can be implemented as an option before placing the order (i.e. on your checkout page, before calling our API). It is the merchant's sole responsibility to enable this feature. Failing to comply with this product rule might result in unexpected errors and unwanted complications.

* When multiple order rules are supplied with the same _merchant-item-id_, it will result in a conflict if a partial refund is requested. Thus, to be able to do the partial refund for the same product with different specifications (e.g. size, color) via the shopping cart successfully, each merchant-item-id should be unique. For example, for products with different sizes the _merchant-item-id_ can be distinguished with ‘-size’: 1001311-xxl, 1001311-m, 1001311-s.
