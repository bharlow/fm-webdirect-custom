# Claris FileMaker WebDirect Custom Homepage #

This repository has been provided by [Harlow Technologies Inc.](http://www.harlowtech.com) as a service to the FileMaker community in making Claris FileMaker WebDirect logins for our customers easier.

Below are the instructions for how to install and configure the HTML pages for custom FileMaker WebDirect login, logoff and form pages.

![FileMaker WebDirect Basic Login Example Page](images/fm-example-5.png)
![FileMaker WebDirect Form Login Example Page](images/fm-example-6.png)

## Installation ##

* Install Instructions
* Web Directory Root Folder
* How to Download these Files

### Install Instructions ###

1. After downloading the files, look inside the folder titled "html"
2. Select the folder for the version you need then open the index.html and logoff.html in a text editor for that Version.
    * FileMaker 13 = mysolution13
    * FileMaker 14 = mysolution14
    * FileMaker 15 = mysolution15
    * FileMaker 16 = mysolution16-basic or mysolution16-form
    * FileMaker 17 = mysolution17-basic or mysolution17-form
    * FileMaker 18 = mysolution18-basic or mysolution18-form
    * FileMaker 19 = mysolution19-basic or mysolution19-form
3. On both files, make the following adjustments:
    1. If you are using https, update the url protocol to https from http on both the URL and URL parameter “homeurl”.
    2. Update the web host (example: fms.example.com) to the host name or IP you wish to use for the FileMaker Server.
    3. Update the web host (example: web.example.com) to the host name or IP you wish to use for URL parameter "homeurl"
    4. Update the folder name to the folder name you wish to use on the web server in the URL parameter "homeurl" for the logoff page.
    5. Update the database name in the URL
        * For FileMaker 15 or earlier, update the database name after the # sign in the URL parameter "homeurl"
        * For FileMaker 16 or later, update the database name after "fmi/webd/" in the URL "homeurl"
4. Place the folder on the web server root folder and provide the user with the URL to the index.html file.
5. Give the user your adjusted URL to start using FileMaker WebDirect with a custom home page Example: http://web.example.com/mysolution/index.html

### Web Directory Root Folder ###

The typical web server root folders for FileMaker Server can be found at:

__For IIS (Windows) through HTTP or HTTPS__

* [drive]:\Program Files\FileMaker\FileMaker Server\HTTPServer\conf
* Where [drive] is the drive on which the Web Publishing Engine component of your FileMaker Server deployment resides.

__For Apache (OS X) through HTTP__

* /Library/FileMaker Server/HTTPServer/htdocs

__For Apache (OS X) through HTTPS__

* /Library/FileMaker Server/HTTPServer/htdocs/httpsRoot

### How to Download these Files ###

Want to download and try these files out with your solution. Look for the "Clone or download" button at the on the top of the [GitHub](https://github.com/bharlow/fm-webdirect-custom) page.

### FileMaker 19.4.x Custom Homepage Redirect Configuration ###

As of FileMaker Server 19.4.1, the introduction of an Allow-List for greater control of URL's which can be used as a HomeURL in WebDirect was made, however this causes additional configuration. Below is a link from Claris Support on how to configure the new settings for FileMaker 19.4.x.

[Claris Support: HomeURL parameters in FileMaker Server 19.4.1](https://support.claris.com/s/article/HomeURL-parameters-in-FileMaker-Server-19-4-1)

## Bugs ##

### Naming of CSS File ###

As of FileMaker Server 19.4.x, it has been reported that the web file break any CSS file that **contains** the name _style_ as part of the filename. This appears to be part of a redirection on the FileMaker Server. The temporary fix is to rename the CSS file style.css and update the approprate HTML files with the new filename.

### HTTP Form Post Bug ###

On the HTTP Form Post method, there appears to be a bug in FileMaker Server (versions prior to 19) when a user logins with the incorrect credentials. The FileMaker Server appears to append the server URL before the full request URL, which results in an invalid domain name. **This appears to be resolved in FileMaker 19, but remains in FileMaker 16 - 18.**

#### Example Request URL for HTTP Post to FileMaker ####

https://fms.example.com/fmi/webd/webd-example?homeurl=https://web.example.com/webd-custom/index.html

#### Example Response URL for HTTP Post from FileMaker ####

https://fms.example.comhttps://web.example.com/webd-custom/index.html?homeurl=https://web.example.com/webd-custom/index.html&db=webd-example&loginerr=212&guesten=0

## Tips and Hints ##

* When you update the web host or folder name the index.html needs to have it updated in two locations while the logoff.html only has one location.
* The URL Host Name or IP for the FileMaker Server can be different than the homeurl URL Host Name or IP. You must be sure to link the pages up appropriately.
* All of the files listed in the folder inside the *html* folder are designed to be used at either the root of the web server or in a folder name of your choosing.
* As of FileMaker 16, the url fragment character "#" is no longer supported. See [Miscellaneous behavior changes in FileMaker 16 Platform](http://help.filemaker.com/app/answers/detail/a_id/16316).
* Microsoft Edge has two versions numbers that must be factored in, the Version of the Browser "38" and the Version of EdgeHTML "14.14342". Browser detection must check against EdgeHTML. See [Wikipedia - Microsoft Edge Release History](https://en.wikipedia.org/wiki/Microsoft_Edge#Release_history) to translate the version FileMaker requires to the version the browser detection requires.
* For FileMaker version 18 and prior, Microsoft Internet Explorer has a mode where Intranet sites are placed in compatibility mode. This by default sets the browser to behave as if it is IE 7 rather than IE 10 or 11. Notes with how to turn this mode off have been added to the HTML pages.
* For FileMaker version 19 or later, Microsoft Internet Explorer is no longer supported.
* Some web servers allow both HTTP and HTTPS access to the same pages. If this is the case, it is best if you can force the user to use HTTPS at the web server level. If this cannot be done, you can leverage an optional JavaScript to check and force a user to HTTPS.

## Examples ##

For examples of how the [basic login screens appear](EXAMPLES.md) visit our example markdown file.

## Official Documentation ##

Official documentation on using the WebDirect custom homepage that can be found at:
* [FileMaker 13 WebDirect PDF - Starting at Page 26](https://fmhelp.filemaker.com/docs/13/en/fm13_webdirect_guide.pdf#page=26) 
* [FileMaker 14 WebDirect PDF - Starting at Page 28](https://fmhelp.filemaker.com/docs/14/en/fm14_webdirect_guide.pdf#page=28) 
* [FileMaker 15 WebDirect PDF - Starting at Page 27](https://fmhelp.filemaker.com/docs/15/en/fm15_webdirect_guide.pdf#page=27) 
* [FileMaker 16 WebDirect Website](https://fmhelp.filemaker.com/docs/16/en/fmwd/)
* [FileMaker 17 WebDirect Website](https://fmhelp.filemaker.com/docs/17/en/fmwd/)
* [FileMaker 18 WebDirect Website](https://fmhelp.filemaker.com/docs/18/en/fmwd/)
* [FileMaker 19 WebDirect Website](https://help.claris.com/en/webdirect-guide/)

## Change Notes ##

See [CHANGELOG.md](CHANGELOG.md) for all changes.

## Copyright ##

The Harlow Technologies logo design is the exclusive property of Harlow Technologies Inc. and is Copyright (c) 2018 Harlow Technologies Inc. All rights reserved.

Copyright (c) 2016-2020 Harlow Technologies Inc.

* Released under the MIT license
* https://github.com/bharlow/fm-webdirect-custom/blob/master/LICENSE.txt

FileMaker is a trademark of FileMaker, Inc., registered in the U.S. and other countries. FileMaker WebDirect is a trademark of FileMaker, Inc.

Detect.js: User-Agent Parser (https://github.com/darcyclarke/Detect.js) is Dual licensed under the MIT and GPL licenses.

* Added v1.3
* Removed v2.0

Bowser: User-Agent Parser (https://github.com/lancedikson/bowser) is licensed under the MIT license.

* Added v2.0
* Updated v2.6
