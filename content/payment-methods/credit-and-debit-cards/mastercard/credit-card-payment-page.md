---
title: "Mastercard credit card payment page"
weight: 26
meta_title: "Mastercard credit card payment page - MultiSafepay Support"
meta_description: "In the MultiSafepay Documentation Center all relevant information regarding our Plugins and API. As well as Support pages for Payment Method, Tools and General Questions. You can also find the contact details of our Support Team and Integration Team."
read_more: '.'
--- 
## Integrating Mastercard

It is possible to either redirect to our credit card payment page where Mastercard will be readily available, thus allowing MultiSafepay to handle Mastercard as well as other credit card payment methods for you __or__ redirecting specifically to Mastercard.

### Redirect for all credit cards including Mastercard
Choose this method if you would like for MultiSafepay to handle all credit cards for you. By bundling all the credit cards in the checkout, you will save space and collapse all the different credit card providers. Mastercard is included this bundle.

The customer will be redirected to our credit card payment page. The customer fills in his/her credentials and we will detect the credit card provider based on the first four digits.

The [credit card API page](/api/#credit-cards) illustrates the API implementation.

### Redirect specifically to Mastercard
Choose this way if you wish to only accept Mastercard. Your customer will be redirected to Mastercard. After the credentials are filled in, MultiSafepay will ensure the payment is completed.

For implementation, see the API calls for [Mastercard](/api/#mastercard)