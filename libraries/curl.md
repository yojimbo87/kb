## cURL

 - [Installation](#installation)
 - [Send POST with data](#send-post-with-data)
 
### Installation

 - [Download](http://curl.haxx.se/download.html)
 - node.js [jsontool](https://github.com/trentm/json) library for pretty print
 
### Send POST with data

```
curl -H "Content-Type:application/json" --data "{'request':{'serverTimestamp':'2008-12-20T02:12:02Z','service':'events','search':null}}" http://127.0.0.1:2480/mobile/v1/endpoint | json -i
```
