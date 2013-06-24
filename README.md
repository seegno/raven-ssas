Raven-SSAS
==========

Server Side ActionScript client for Sentry.

Limitations
-----------

Raven-SSAS uses the [LoadVars](http://help.adobe.com/en_US/flashmediaserver/ssaslr/WS5b3ccc516d4fbf351e63e3d11a11afc95e-7ff7SSASLR.html) class to communicate with the Sentry API. Unfortunately, this API does not support SSL, which Sentry requires. 

This means that you must provide a non-secure DSN such as http://<your_dsn> and not https://<your_dsn>.

Installation
------------

Place Raven.asc in your Flash Media Server/Adobe Media Server application directory and then load it with:

	load("Raven.asc");

Configuration
-------------

First you need to make sure that your server host is listed under the "Allowed Domains" section of your Project Details in Sentry.

![Allowed Domains](http://i.imgur.com/S09MeSM.png)

Next, simply initialize Raven with your Sentry DSN:

	Raven.config('https://public@getsentry.com/1').install()

Congratulations. Any unhandled exception will now be automatically logged to your Sentry account.

Usage
-----

As with most Sentry clients, you may use `Raven.captureException()` and `Raven.captureMessage` to explicitly capture and report any exceptions.

If you have any user data to go along with the exception, you may provide it using the `Raven.setUser()` function.