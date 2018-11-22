# 4d-plugin-curl-v2
Generic network client based on libcurl-7.62.0

### Platform

| carbon | cocoa | win32 | win64 |
|:------:|:-----:|:---------:|:---------:|
|<img src="https://cloud.githubusercontent.com/assets/1725068/22371562/1b091f0a-e4db-11e6-8458-8653954a7cce.png" width="24" height="24" />|<img src="https://cloud.githubusercontent.com/assets/1725068/22371562/1b091f0a-e4db-11e6-8458-8653954a7cce.png" width="24" height="24" />|<img src="https://cloud.githubusercontent.com/assets/1725068/22371562/1b091f0a-e4db-11e6-8458-8653954a7cce.png" width="24" height="24" />|<img src="https://cloud.githubusercontent.com/assets/1725068/22371562/1b091f0a-e4db-11e6-8458-8653954a7cce.png" width="24" height="24" />|

### Version

<img src="https://cloud.githubusercontent.com/assets/1725068/18940649/21945000-8645-11e6-86ed-4a0f800e5a73.png" width="32" height="32" /> <img src="https://cloud.githubusercontent.com/assets/1725068/18940648/2192ddba-8645-11e6-864d-6d5692d55717.png" width="32" height="32" /> <img src="https://user-images.githubusercontent.com/1725068/41266195-ddf767b2-6e30-11e8-9d6b-2adf6a9f57a5.png" width="32" height="32" />

![preemption xx](https://user-images.githubusercontent.com/1725068/41327179-4e839948-6efd-11e8-982b-a670d511e04f.png)

### Releases

~~[1.0]~~

## Syntax

```
error:=cURL(options;request;response{;callbackMethod{;transferInfo}})
```

Parameter|Type|Description
------------|------------|----
options|TEXT|``JSON`` object
request|BLOB|
response|BLOB|
callbackMethod|TEXT|optional
transferInfo|TEXT|out, ``JSON`` ``curl_easy_getinfo``
error|LONGINT|[Error code](https://curl.haxx.se/libcurl/c/libcurl-errors.html)

---

Signature of ``callbackMethod``

```
abort:=method(transferInfo;userInfo)
```

Parameter|Type|Description
------------|------------|----
transferInfo|TEXT|out, ``JSON`` ``curl_easy_getinfo``
userInfo|TEXT|out, the text passed as the ``PRIVATE`` property of ``option``
abort|BOOLEAN|

[``CURLcode``](https://curl.haxx.se/libcurl/c/libcurl-errors.html) is returned in ``error``. when ``True`` is returned from the callback method, ``CURLE_ABORTED_BY_CALLBACK (42)`` is returned. Same if the process has been aborted via the runtime explorer. aborting the debugger will not kill the process immediately.

---

Properties of ``curlInfo``

```
conditionUnmet
contentLengthUpload
rtspClientCseq
rtspServerCseq
rtspCseqRecv
lastSocket
primaryPort
localPort
contentLengthDownload
connectCode
fileTime
totalTime
requestSize
headerSize
speedUpload
speedDownload
sizeDownload
sizeUpload
httpAuthAvail
proxyAuthAvail
osErrNo
numConnects
responseCode
nameLookupTime
connectTime
appConnectTime
preTransferTime
startTransferTime
redirectTime
sslVerifyResult
redirectCount
effectiveUrl
localIp
contentType
primaryIp
redirectUrl
ftpEntryPath
rtspSessionId
```

---

Special ``options``

Value|Type|Description
------------|------------|----
[PRIVATE](https://curl.haxx.se/libcurl/c/CURLOPT_PRIVATE.html) |TEXT|context info passed to ``callbackMethod``
[WRITEDATA](https://curl.haxx.se/libcurl/c/CURLOPT_WRITEDATA.html) |TEXT|use file path instead of ``request``
[READDATA](https://curl.haxx.se/libcurl/c/CURLOPT_READDATA.html) |TEXT|use file path instead of ``response``

Standard  ``options``

Value|Type|Description
------------|------------|----
[TIMEVALUE_LARGE](https://curl.haxx.se/libcurl/c/CURLOPT_TIMEVALUE_LARGE.html) |TEXT|text, to support 64-bit integer
[HAPPY_EYEBALLS_TIMEOUT_MS](https://curl.haxx.se/libcurl/c/CURLOPT_HAPPY_EYEBALLS_TIMEOUT_MS.html) |LONGINT|
[HAPROXYPROTOCOL](https://curl.haxx.se/libcurl/c/CURLOPT_HAPROXYPROTOCOL.html) |LONGINT|
[DNS_SHUFFLE_ADDRESSES](https://curl.haxx.se/libcurl/c/CURLOPT_DNS_SHUFFLE_ADDRESSES.html) |LONGINT|
[TLS13_CIPHERS](https://curl.haxx.se/libcurl/c/CURLOPT_TLS13_CIPHERS.html) |TEXT|
[PROXY_TLS13_CIPHERS](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_TLS13_CIPHERS.html) |TEXT|
[DISALLOW_USERNAME_IN_URL](https://curl.haxx.se/libcurl/c/CURLOPT_DISALLOW_USERNAME_IN_URL.html) |LONGINT|
[DOH_URL](https://curl.haxx.se/libcurl/c/CURLOPT_DOH_URL.html) |TEXT|
[UPLOAD_BUFFERSIZE](https://curl.haxx.se/libcurl/c/CURLOPT_UPLOAD_BUFFERSIZE.html) |LONGINT|
[UPKEEP_INTERVAL_MS](https://curl.haxx.se/libcurl/c/CURLOPT_UPKEEP_INTERVAL_MS.html) |LONGINT|

