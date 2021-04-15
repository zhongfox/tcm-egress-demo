
pod sleep-1:


```
/ $ curl -I www.baidu.com
HTTP/1.1 401 Unauthorized
content-length: 18
content-type: text/plain
date: Thu, 15 Apr 2021 15:04:15 GMT
server: envoy

/ $ curl -I www.qq.com
HTTP/1.1 301 Moved Permanently
server: envoy
content-length: 0
location: https://www.qq.com/
date: Thu, 15 Apr 2021 15:04:21 GMT
x-envoy-upstream-service-time: 7

/ $ curl -I httpbin:8000/headers
HTTP/1.1 200 OK
server: envoy
date: Thu, 15 Apr 2021 15:06:14 GMT
content-type: application/json
content-length: 563
access-control-allow-origin: *
access-control-allow-credentials: true
x-envoy-upstream-service-time: 1
```


pod sleep-2:

```
/ $ curl -I  www.baidu.com
HTTP/1.1 200 OK
accept-ranges: bytes
cache-control: private, no-cache, no-store, proxy-revalidate, no-transform
content-length: 277
content-type: text/html
date: Thu, 15 Apr 2021 15:04:36 GMT
etag: "575e1f6f-115"
last-modified: Mon, 13 Jun 2016 02:50:23 GMT
pragma: no-cache
server: envoy
x-envoy-upstream-service-time: 278

/ $ curl -I www.qq.com
HTTP/1.1 401 Unauthorized
content-length: 18
content-type: text/plain
date: Thu, 15 Apr 2021 15:04:46 GMT
server: envoy

/ $ curl -I httpbin:8000/headers
HTTP/1.1 200 OK
server: envoy
date: Thu, 15 Apr 2021 15:06:23 GMT
content-type: application/json
content-length: 563
access-control-allow-origin: *
access-control-allow-credentials: true
x-envoy-upstream-service-time: 1
```
