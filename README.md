hoodie_plugin_email_verifier sample app

This application illustrates how to use the hoodie_plugin_email_verifier Hoodie plugin to verify a newly signed up user's email.  The intention is to provide a sample use of the hoodie-plugin-email-verifier plugin, *not* a comprehensive security solution for your app/company!

## Installation

* First, this sample is *REALLY* intended for people familiar with Hoodie.  But if you are not, please start with the intro Hoodie docs to install Hoodie and its dependencies: [install guides for OS X, Linux and Windows](http://hood.ie/#installation).
* Clone this repository to your computer
* Install the hoodie-plugin-email plugin:  
  * hoodie install hoodie-plugin-email
* npm install
* Run:
  * hoodie start
* Configure the application's email settings (for sending out verification emails) in the app's Admin Dashboard.  

## Programming notes

This app has three blocks of code that have been added to the Hoodie default application.  You can see these blocks in context by looking at commit XXX (insert link here).  
Below is a brief overview of the additions:
* Added [hoodie-plugin-email-verifier plugin](https://github.com/mikehedman/hoodie-plugin-email-verifier).  This plugin adds server side functionality to mark a newly signed up user as unconfirmed, sends the user an email with a verification link, and switches the user to confirmed when the link is clicked.
* www/assets/vendor/hoodie.accountbar.bootstrap.js: Added a 'progress' callback to close the signup modal dialog once the user account has been created (but not yet confirmed).  This block of code is really just a workaround, because prior to the release of Hoodie 1.0, the user confirmation process is somewhat poorly defined and there is not a "proper" way for Hoodie to signal client code that the new user still needs to be confirmed. 
* www/assets/js/main.js: Added a jQuery doc ready function to open up the login dialog modal when the app has been opened by clicking on the link that is sent in the verification email.  That link includes a "confirmed" hash as a marker to the app.

