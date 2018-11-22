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
[MAIL_AUTH](https://curl.haxx.se/libcurl/c/CURLOPT_MAIL_AUTH.html) |TEXT|
[SASL_IR](https://curl.haxx.se/libcurl/c/CURLOPT_SASL_IR.html) |LONGINT|
[XOAUTH2_BEARER](https://curl.haxx.se/libcurl/c/CURLOPT_XOAUTH2_BEARER.html) |TEXT|
[DNS_INTERFACE](https://curl.haxx.se/libcurl/c/CURLOPT_DNS_INTERFACE.html) |TEXT|
[DNS_LOCAL_IP4](https://curl.haxx.se/libcurl/c/CURLOPT_DNS_LOCAL_IP4.html) |TEXT|
[DNS_LOCAL_IP6](https://curl.haxx.se/libcurl/c/CURLOPT_DNS_LOCAL_IP6.html) |TEXT|
[LOGIN_OPTIONS](https://curl.haxx.se/libcurl/c/CURLOPT_LOGIN_OPTIONS.html) |TEXT|
[SSL_ENABLE_NPN](https://curl.haxx.se/libcurl/c/CURLOPT_SSL_ENABLE_NPN.html) |LONGINT|
[SSL_ENABLE_ALPN](https://curl.haxx.se/libcurl/c/CURLOPT_SSL_ENABLE_ALPN.html) |LONGINT|
[EXPECT_100_TIMEOUT_MS](https://curl.haxx.se/libcurl/c/CURLOPT_EXPECT_100_TIMEOUT_MS.html) |LONGINT|
[HEADEROPT](https://curl.haxx.se/libcurl/c/CURLOPT_HEADEROPT.html) |LONGINT|
[PINNEDPUBLICKEY](https://curl.haxx.se/libcurl/c/CURLOPT_PINNEDPUBLICKEY.html) |TEXT|path or string
[SSL_VERIFYSTATUS](https://curl.haxx.se/libcurl/c/CURLOPT_SSL_VERIFYSTATUS.html) |LONGINT|
[SSL_FALSESTART](https://curl.haxx.se/libcurl/c/CURLOPT_SSL_FALSESTART.html) |LONGINT|
[PATH_AS_IS](https://curl.haxx.se/libcurl/c/CURLOPT_PATH_AS_IS.html) |LONGINT|
[PROXY_SERVICE_NAME](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_SERVICE_NAME.html) |TEXT|
[SERVICE_NAME](https://curl.haxx.se/libcurl/c/CURLOPT_SERVICE_NAME.html) |TEXT|
[PIPEWAIT](https://curl.haxx.se/libcurl/c/CURLOPT_PIPEWAIT.html) |LONGINT|
[DEFAULT_PROTOCOL](https://curl.haxx.se/libcurl/c/CURLOPT_DEFAULT_PROTOCOL.html) |TEXT|
[STREAM_WEIGHT](https://curl.haxx.se/libcurl/c/CURLOPT_STREAM_WEIGHT.html) |LONGINT|
[TFTP_NO_OPTIONS](https://curl.haxx.se/libcurl/c/CURLOPT_TFTP_NO_OPTIONS.html) |LONGINT|
[TCP_FASTOPEN](https://curl.haxx.se/libcurl/c/CURLOPT_TCP_FASTOPEN.html) |LONGINT|
[KEEP_SENDING_ON_ERROR](https://curl.haxx.se/libcurl/c/CURLOPT_KEEP_SENDING_ON_ERROR.html) |LONGINT|
[PROXY_CAINFO](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_CAINFO.html) |TEXT|path
[PROXY_CAPATH](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_CAPATH.html) |TEXT|path
[PROXY_SSL_VERIFYPEER](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_SSL_VERIFYPEER.html) |LONGINT|
[PROXY_SSL_VERIFYHOST](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_SSL_VERIFYHOST.html) |LONGINT|
[PROXY_TLSAUTH_USERNAME](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_TLSAUTH_USERNAME.html) |TEXT|
[PROXY_TLSAUTH_PASSWORD](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_TLSAUTH_PASSWORD.html) |TEXT|
[PROXY_TLSAUTH_TYPE](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_TLSAUTH_TYPE.html) |TEXT|
[PROXY_SSLCERT](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_SSLCERT.html) |TEXT|path
[PROXY_SSLCERTTYPE](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_SSLCERTTYPE.html) |TEXT|
[PROXY_SSLKEY](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_SSLKEY.html) |TEXT|path
[PROXY_SSLKEYTYPE](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_SSLKEYTYPE.html) |TEXT|
[PROXY_KEYPASSWD](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_KEYPASSWD.html) |TEXT|
[PROXY_SSL_CIPHER_LIST](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_SSL_CIPHER_LIST.html) |TEXT|
[PROXY_CRLFILE](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_CRLFILE.html) |TEXT|path
[PROXY_SSL_OPTIONS](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_SSL_OPTIONS.html) |LONGINT|
[PRE_PROXY](https://curl.haxx.se/libcurl/c/CURLOPT_PRE_PROXY.html) |TEXT|
[PROXY_PINNEDPUBLICKEY](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_PINNEDPUBLICKEY.html) |TEXT|
[SUPPRESS_CONNECT_HEADERS](https://curl.haxx.se/libcurl/c/CURLOPT_SUPPRESS_CONNECT_HEADERS.html) |LONGINT|
[REQUEST_TARGET](https://curl.haxx.se/libcurl/c/CURLOPT_REQUEST_TARGET.html) |TEXT|
[SOCKS5_AUTH](https://curl.haxx.se/libcurl/c/CURLOPT_SOCKS5_AUTH.html) |LONGINT|
[SSH_COMPRESSION](https://curl.haxx.se/libcurl/c/CURLOPT_SSH_COMPRESSION.html) |LONGINT|
[TIMEVALUE_LARGE](https://curl.haxx.se/libcurl/c/CURLOPT_TIMEVALUE_LARGE.html) |TEXT|64-bit integer
[HAPPY_EYEBALLS_TIMEOUT_MS](https://curl.haxx.se/libcurl/c/CURLOPT_HAPPY_EYEBALLS_TIMEOUT_MS.html) |LONGINT|
[HAPROXYPROTOCOL](https://curl.haxx.se/libcurl/c/CURLOPT_HAPROXYPROTOCOL.html) |LONGINT|
[DNS_SHUFFLE_ADDRESSES](https://curl.haxx.se/libcurl/c/CURLOPT_DNS_SHUFFLE_ADDRESSES.html) |LONGINT|
[TLS13_CIPHERS](https://curl.haxx.se/libcurl/c/CURLOPT_TLS13_CIPHERS.html) |TEXT|
[PROXY_TLS13_CIPHERS](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_TLS13_CIPHERS.html) |TEXT|
[DISALLOW_USERNAME_IN_URL](https://curl.haxx.se/libcurl/c/CURLOPT_DISALLOW_USERNAME_IN_URL.html) |LONGINT|
[DOH_URL](https://curl.haxx.se/libcurl/c/CURLOPT_DOH_URL.html) |TEXT|
[UPLOAD_BUFFERSIZE](https://curl.haxx.se/libcurl/c/CURLOPT_UPLOAD_BUFFERSIZE.html) |LONGINT|
[UPKEEP_INTERVAL_MS](https://curl.haxx.se/libcurl/c/CURLOPT_UPKEEP_INTERVAL_MS.html) |LONGINT|

Not implemented

``GSSAPI_DELEGATION``  
``SOCKS5_GSSAPI_NEC``  
``SOCKS5_GSSAPI_SERVICE``  
``CLOSESOCKETDATA``  
``CLOSESOCKETFUNCTION``  
``FNMATCH_DATA``  
``CHUNK_DATA``  
``FNMATCH_FUNCTION``  
``CHUNK_END_FUNCTION``  
``CHUNK_BGN_FUNCTION``  
``INTERLEAVEFUNCTION``  
``INTERLEAVEDATA``  
``SSH_KEYDATA``  
``SSH_KEYFUNCTION``  
``STREAM_DEPENDS_E``  
``STREAM_DEPENDS``  
``UNIX_SOCKET_PATH``  
``XFERINFOFUNCTION``  
``SSL_OPTIONS``  
``ABSTRACT_UNIX_SOCKET``  
``MIMEPOST``  
``RESOLVER_START_FUNCTION``  
``RESOLVER_START_DATA``  
