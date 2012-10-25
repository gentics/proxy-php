# proxy-php

A simple PHP proxy that makes it possible to work around CORS limiations between a frontend and a backend server.

## Overview

The request cycle is as follows
* the browser makes a request to "/$PROXYNAME/xx" on the frontend server
* the proxy script takes everything after "/$PROXYNAME/" and appends it to $CMS_SERVERHOST
* the proxy script makes a request to the resulting URL $CMS_SERVERHOST/xx on the backend server
* the response is directed back to the browser

## Usage

Copy this folder to the document root of your frontend server and preferrably call the folder 'proxy'.

Adapt the settings.con.php file and customize the following variables
```php
// The URL of the backend server that browser requests should be proxied to
$CMS_SERVERHOST = 'http://example.com/';
// The path to the proxy script on the frontend server
$PROXYNAME = '/proxy/';
// Max times to follow a HTTP redirection response to a new URL
$HTTP_MAX_REDIRECTS = 10;
```

Adapt the .htaccess and replace occurrences of /proxy/ with the value of $PROXYNAME.
