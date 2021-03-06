---
title : "MultiSafepay Magento 2 installation & configuration manual"
meta_title: "Magento 2 plugin manual - MultiSafepay Documentation Center"
meta_description: "The MultiSafepay Documentation Center presents all relevant information about our Plugins and API. You can also find support pages for Payment Methods, Tools and General Questions as well as the contact details of our Support and Integration Teams."
aliases:
    - /support-tab/magento2/manual
---

### Introduction

This manual helps merchants to process MultiSafepay payments as quickly as possible from a Magento 2 webshop. For some steps in this manual, assistance from your technical partner may be required.

The installation can be carried out in three ways:

+ SFTP
+ Composer
+ Magento Marketplace.

In this manual we describe the installation via Composer.

{{% introduction_plugin "Magento 2" %}}

### 1. Requirements
- Magento Open Source version 2.2.x & 2.3.x
- PHP 7.0 and higher
- Tested with PHP 7.0 (Magento 2.3.x adds support for 7.2)

### 2. Installation
Run the following commands via the CLI:

```
composer require multisafepay/magento2msp
php bin/magento setup:upgrade
php bin/magento setup:static-content:deploy
```

After running these commands, the latest stable release is downloaded and installed within your
Magento 2 webshop.

Depending on your webserver/webshop configuration you also need to check:

- Set rights on files correctly. Our files can be found at vendor/multisafepay/magento2msp
- Empty static files when running in production mode
- Flush cache.

### 3. Configuration
1. Login on the backend of your webshop and navigate to _Stores_ -> _Configuration_ -> _MultiSafepay x.x.x_ -> _MultiSafepay Settings_.  
This page contains all main settings and is used for all gateways and gift cards.
{{% account_info %}}
Your Account ID is shown in the dashboard of your MultiSafepay Control in the top right corner

2. Navigate to _Stores_ -> _Configuration_ -> _MultiSafepay x.x.x_-> _MultiSafepay Gateways_.  
This page contains the configuration options for all payment methods supported by MultiSafepay.  
Be sure that you have the selected payment methods active in your [MultiSafepay Control](https://merchant.multisafepay.com)

3. MultiSafepay Gift cards  
This page contains the configuration options for all gift cards supported by MultiSafepay.  
Gift cards need to be activated, more information can be found on our [gift card page](/payment-methods/prepaid-cards/gift-cards/)

4. Fastcheckout  
This page contains the Fastcheckout specific settings.  
More information about the Fastcheckout can be found on https://www.multisafepay.com/fastcheckout-payments

### 4. Congratulations
You have installed and configured the plugin successfully. If you have any questions regarding the plugin, feel free to contact our Integration Team at <integration@multisafepay.com> or start a discussion in our [Magento Slack channel](https://magentocommeng.slack.com) _#multisafepay-payments_
