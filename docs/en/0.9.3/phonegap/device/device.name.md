---
license: Licensed to the Apache Software Foundation (ASF) under one
         or more contributor license agreements.  See the NOTICE file
         distributed with this work for additional information
         regarding copyright ownership.  The ASF licenses this file
         to you under the Apache License, Version 2.0 (the
         "License"); you may not use this file except in compliance
         with the License.  You may obtain a copy of the License at

           http://www.apache.org/licenses/LICENSE-2.0

         Unless required by applicable law or agreed to in writing,
         software distributed under the License is distributed on an
         "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
         KIND, either express or implied.  See the License for the
         specific language governing permissions and limitations
         under the License.
---

device.name
===========

Get the device's model name.

    var string = device.name;
    
Description
-----------

`device.name` returns the name of the device's model or product. This value is set by the device manufacturer and may be different across versions of the same product.

Supported Platforms
-------------------

- Android
- BlackBerry
- BlackBerry Widgets (OS 5.0 and higher)
- iPhone

Quick Example
-------------

    // Android:    Nexus One       returns "Passion" (Nexus One code name)
    //             Motorola Droid  returns "voles"
    // BlackBerry: Bold 8900       returns "8900"
    // iPhone:     All devices     returns a name set by iTunes e.g. "Joe's iPhone"
    //
    var name = device.name;

Full Example
------------

    <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
                          "http://www.w3.org/TR/html4/strict.dtd">
    <html>
      <head>
        <title>Device Properties Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // Wait for PhoneGap to load
        //
        function onLoad() {
            document.addEventListener("deviceready", onDeviceReady, false);
        }

        // PhoneGap is ready
        //
        function onDeviceReady() {
            var element = document.getElementById('deviceProperties');
    
            element.innerHTML = 'Device Name: '     + device.name     + '<br />' + 
                                'Device PhoneGap: ' + device.phonegap + '<br />' + 
                                'Device Platform: ' + device.platform + '<br />' + 
                                'Device UUID: '     + device.uuid     + '<br />' + 
                                'Device Version: '  + device.version  + '<br />';
        }

        </script>
      </head>
      <body onload="onLoad()">
        <p id="deviceProperties">Loading device properties...</p>
      </body>
    </html>


Android Quirks
--------------

- Gets the [product name](http://developer.android.com/reference/android/os/Build.html#PRODUCT) instead of the [model name](http://developer.android.com/reference/android/os/Build.html#MODEL).
    - The product name is often the code name given during production.
    - e.g. Nexus One returns "Passion", Motorola Droid returns "voles"

iPhone Quirks
-------------

- Gets the [device's custom name](http://developer.apple.com/iphone/library/documentation/uikit/reference/UIDevice_Class/Reference/UIDevice.html#//apple_ref/doc/uid/TP40006902-CH3-SW13) instead of the [device model name](http://developer.apple.com/iphone/library/documentation/uikit/reference/UIDevice_Class/Reference/UIDevice.html#//apple_ref/doc/uid/TP40006902-CH3-SW1).
    - The custom name is set by the owner in iTunes.
    - e.g. "Joe's iPhone"