## cURL

 - [Installation](#installation)
 - [Send POST with data](#send-post-with-data)
 
### Installation

 - [Download](http://curl.haxx.se/download.html)
 - node.js [jsontool](https://github.com/trentm/json) library for pretty print
 
### Send POST with data

```
curl --data "{'data':'foo'}" http://localhost:2480/mobile/v1/endpoint | json -i
```
