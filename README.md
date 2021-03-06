Snowdog_Freshmail v2.8.1
=====================

It provides an integration with the FreshMail email marketing service.


Requirements
-----------
* Mage_Newsletter


Compatibility
-----------
Magento CE >= 1.8.0.0 / Magento EE >= 1.12.0.0


Basic setup
-----------

Please login to your Magento admin panel and go to the module configuration tab at **FreshMail -> Configuration**.
Next, you need to provide FreshMail API credentials, set up a secure key for the webhooks controller and save the configuration.

When the configuration page is reloaded you will be able to set a subscription list for every store view.
If your subscription lists have been updated you should refresh them by clicking at the refresh button.

> **Note:** To run this module you need to have configured the Magento cron properly. Some of the API communication is done using cron jobs, so it is required.


Webhooks
-----------
To support unsubscribing directly from emails you will need to configure a gateway url for webhooks at your FreshMail account settings (Settings -> Plugins and API -> Web Hooks).
The gateway url can be found in the module configuration (System -> Configuration -> FreshMail Configuration -> Webhooks).


Shell scripts
-----------

The module includes some shell scripts (**shell/** directory) to cover some synchronization tasks.

#### Synchronize subscribers in a batch mode

To synchronize a remaining batch please run this command once.
A single batch contains max 100 subscribers. The limit is set by the FreshMail API, so it can not be increased.

```
$ php freshmail.php -- sync
```

#### Synchronize all subscribers at once

Executing this command once will synchronize all batches.

```
$ php freshmail.php -- syncAll
```

Troubleshooting
-----------

If you noticed some issues while using the module the best way to debug is to review logs in **FreshMail -> Request logs**
or read plain api communication logs in **var/log/snowfreshmail.log** if api logs are enabled (disabled by default).
The request logs are automatically removed after 14 days (by default, but you are able to change it).
Be sure your Magento cron is working correctly too.


License
-----------
[OSL - Open Software Licence 3.0](http://opensource.org/licenses/osl-3.0.php)
