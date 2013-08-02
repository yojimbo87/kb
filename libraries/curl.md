## cURL

 - [Installation](#installation)
 - [Send POST with data](#send-post-with-data)
 
### Installation

 - [Download](http://curl.haxx.se/download.html)
 - node.js [jsontool](https://github.com/trentm/json) library for pretty print
 
### Send POST with data

```
c:\cURL>curl --data "{'request':{'serverTimestamp':'2008-12-20T02:12:02Z','service':'events','search':null}}" http://api.lionexpo.com/mobile/v1/endpoint | json -i
```
