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
[SSLCERT](https://curl.haxx.se/libcurl/c/CURLOPT_SSLCERT.html) |TEXT|path
[KEYPASSWD](https://curl.haxx.se/libcurl/c/CURLOPT_KEYPASSWD.html) |TEXT|
[CRLF](https://curl.haxx.se/libcurl/c/CURLOPT_CRLF.html) |LONGINT|
[COOKIEFILE](https://curl.haxx.se/libcurl/c/CURLOPT_COOKIEFILE.html) |TEXT|path
[TIMEVALUE](https://curl.haxx.se/libcurl/c/CURLOPT_TIMEVALUE.html) |LONGINT|
[CUSTOMREQUEST](https://curl.haxx.se/libcurl/c/CURLOPT_CUSTOMREQUEST.html) |TEXT|
[HEADER](https://curl.haxx.se/libcurl/c/CURLOPT_HEADER.html) |LONGINT|
[NOBODY](https://curl.haxx.se/libcurl/c/CURLOPT_NOBODY.html) |LONGINT|
[FAILONERROR](https://curl.haxx.se/libcurl/c/CURLOPT_FAILONERROR.html) |LONGINT|
[UPLOAD](https://curl.haxx.se/libcurl/c/CURLOPT_UPLOAD.html) |LONGINT|
[POST](https://curl.haxx.se/libcurl/c/CURLOPT_POST.html) |LONGINT|
[DIRLISTONLY](https://curl.haxx.se/libcurl/c/CURLOPT_DIRLISTONLY.html) |LONGINT|
[APPEND](https://curl.haxx.se/libcurl/c/CURLOPT_APPEND.html) |LONGINT|
[NETRC](https://curl.haxx.se/libcurl/c/CURLOPT_NETRC.html) |LONGINT|
[FOLLOWLOCATION](https://curl.haxx.se/libcurl/c/CURLOPT_FOLLOWLOCATION.html) |LONGINT|
[PUT](https://curl.haxx.se/libcurl/c/CURLOPT_PUT.html) |LONGINT|
[AUTOREFERER](https://curl.haxx.se/libcurl/c/CURLOPT_AUTOREFERER.html) |LONGINT|
[PROXYPORT](https://curl.haxx.se/libcurl/c/CURLOPT_PROXYPORT.html) |LONGINT|
[HTTPPROXYTUNNEL](https://curl.haxx.se/libcurl/c/CURLOPT_HTTPPROXYTUNNEL.html) |LONGINT|
[INTERFACE](https://curl.haxx.se/libcurl/c/CURLOPT_INTERFACE.html) |TEXT|
[KRBLEVEL](https://curl.haxx.se/libcurl/c/CURLOPT_KRBLEVEL.html) |TEXT|
[SSL_VERIFYPEER](https://curl.haxx.se/libcurl/c/CURLOPT_SSL_VERIFYPEER.html) |LONGINT|
[CAINFO](https://curl.haxx.se/libcurl/c/CURLOPT_CAINFO.html) |TEXT|path
[MAXREDIRS](https://curl.haxx.se/libcurl/c/CURLOPT_MAXREDIRS.html) |LONGINT|
[FILETIME](https://curl.haxx.se/libcurl/c/CURLOPT_FILETIME.html) |LONGINT|
[MAXCONNECTS](https://curl.haxx.se/libcurl/c/CURLOPT_MAXCONNECTS.html) |LONGINT|
[FRESH_CONNECT](https://curl.haxx.se/libcurl/c/CURLOPT_FRESH_CONNECT.html) |LONGINT|
[FORBID_REUSE](https://curl.haxx.se/libcurl/c/CURLOPT_FORBID_REUSE.html) |LONGINT|
[RANDOM_FILE](https://curl.haxx.se/libcurl/c/CURLOPT_RANDOM_FILE.html) |TEXT|
[EGDSOCKET](https://curl.haxx.se/libcurl/c/CURLOPT_EGDSOCKET.html) |TEXT|
[CONNECTTIMEOUT](https://curl.haxx.se/libcurl/c/CURLOPT_CONNECTTIMEOUT.html) |LONGINT|
[HTTPGET](https://curl.haxx.se/libcurl/c/CURLOPT_HTTPGET.html) |LONGINT|
[SSL_VERIFYHOST](https://curl.haxx.se/libcurl/c/CURLOPT_SSL_VERIFYHOST.html) |LONGINT|
[COOKIEJAR](https://curl.haxx.se/libcurl/c/CURLOPT_COOKIEJAR.html) |TEXT|path
[SSL_CIPHER_LIST](https://curl.haxx.se/libcurl/c/CURLOPT_SSL_CIPHER_LIST.html) |TEXT|
[FTP_USE_EPSV](https://curl.haxx.se/libcurl/c/CURLOPT_FTP_USE_EPSV.html) |LONGINT|
[SSLCERTTYPE](https://curl.haxx.se/libcurl/c/CURLOPT_SSLCERTTYPE.html) |TEXT|
[SSLKEY](https://curl.haxx.se/libcurl/c/CURLOPT_SSLKEY.html) |TEXT|path
[SSLKEYTYPE](https://curl.haxx.se/libcurl/c/CURLOPT_SSLKEYTYPE.html) |TEXT|
[DNS_CACHE_TIMEOUT](https://curl.haxx.se/libcurl/c/CURLOPT_DNS_CACHE_TIMEOUT.html) |LONGINT|
[COOKIESESSION](https://curl.haxx.se/libcurl/c/CURLOPT_COOKIESESSION.html) |LONGINT|
[CAPATH](https://curl.haxx.se/libcurl/c/CURLOPT_CAPATH.html) |TEXT|path
[BUFFERSIZE](https://curl.haxx.se/libcurl/c/CURLOPT_BUFFERSIZE.html) |LONGINT|
[ACCEPT_ENCODING](https://curl.haxx.se/libcurl/c/CURLOPT_ACCEPT_ENCODING.html) |TEXT|
[UNRESTRICTED_AUTH](https://curl.haxx.se/libcurl/c/CURLOPT_UNRESTRICTED_AUTH.html) |LONGINT|
[FTP_USE_EPRT](https://curl.haxx.se/libcurl/c/CURLOPT_FTP_USE_EPRT.html) |LONGINT|
[HTTPAUTH](https://curl.haxx.se/libcurl/c/CURLOPT_HTTPAUTH.html) |LONGINT|
[FTP_CREATE_MISSING_DIRS](https://curl.haxx.se/libcurl/c/CURLOPT_FTP_CREATE_MISSING_DIRS.html) |LONGINT|
[PROXYAUTH](https://curl.haxx.se/libcurl/c/CURLOPT_PROXYAUTH.html) |LONGINT|
[FTP_RESPONSE_TIMEOUT](https://curl.haxx.se/libcurl/c/CURLOPT_FTP_RESPONSE_TIMEOUT.html) |LONGINT|
[IPRESOLVE](https://curl.haxx.se/libcurl/c/CURLOPT_IPRESOLVE.html) |LONGINT|
[MAXFILESIZE](https://curl.haxx.se/libcurl/c/CURLOPT_MAXFILESIZE.html) |LONGINT|
[RESUME_FROM_LARGE](https://curl.haxx.se/libcurl/c/CURLOPT_RESUME_FROM_LARGE.html) |TEXT|text, to support 64-bit integer
[MAXFILESIZE_LARGE](https://curl.haxx.se/libcurl/c/CURLOPT_MAXFILESIZE_LARGE.html) |TEXT|text, to support 64-bit integer
[NETRC_FILE](https://curl.haxx.se/libcurl/c/CURLOPT_NETRC_FILE.html) |TEXT|path
[FTP_ACCOUNT](https://curl.haxx.se/libcurl/c/CURLOPT_FTP_ACCOUNT.html) |TEXT|
[COOKIELIST](https://curl.haxx.se/libcurl/c/CURLOPT_COOKIELIST.html) |TEXT|
[IGNORE_CONTENT_LENGTH](https://curl.haxx.se/libcurl/c/CURLOPT_IGNORE_CONTENT_LENGTH.html) |LONGINT|
[FTP_SKIP_PASV_IP](https://curl.haxx.se/libcurl/c/CURLOPT_FTP_SKIP_PASV_IP.html) |LONGINT|
[FTP_FILEMETHOD](https://curl.haxx.se/libcurl/c/CURLOPT_FTP_FILEMETHOD.html) |LONGINT|
[LOCALPORT](https://curl.haxx.se/libcurl/c/CURLOPT_LOCALPORT.html) |LONGINT|
[LOCALPORTRANGE](https://curl.haxx.se/libcurl/c/CURLOPT_LOCALPORTRANGE.html) |LONGINT|
[CONNECT_ONLY](https://curl.haxx.se/libcurl/c/CURLOPT_CONNECT_ONLY.html) |LONGINT|
[MAX_SEND_SPEED_LARGE](https://curl.haxx.se/libcurl/c/CURLOPT_MAX_SEND_SPEED_LARGE.html) |TEXT|text, to support 64-bit integer
[MAX_RECV_SPEED_LARGE](https://curl.haxx.se/libcurl/c/CURLOPT_MAX_RECV_SPEED_LARGE.html) |TEXT|text, to support 64-bit integer
[FTP_ALTERNATIVE_TO_USER](https://curl.haxx.se/libcurl/c/CURLOPT_FTP_ALTERNATIVE_TO_USER.html) |TEXT|
[SSL_SESSIONID_CACHE](https://curl.haxx.se/libcurl/c/CURLOPT_SSL_SESSIONID_CACHE.html) |LONGINT|
[SSH_AUTH_TYPES](https://curl.haxx.se/libcurl/c/CURLOPT_SSH_AUTH_TYPES.html) |LONGINT|
[SSH_PUBLIC_KEYFILE](https://curl.haxx.se/libcurl/c/CURLOPT_SSH_PUBLIC_KEYFILE.html) |TEXT|path
[SSH_PRIVATE_KEYFILE](https://curl.haxx.se/libcurl/c/CURLOPT_SSH_PRIVATE_KEYFILE.html) |TEXT|path
[FTP_SSL_CCC](https://curl.haxx.se/libcurl/c/CURLOPT_FTP_SSL_CCC.html) |LONGINT|
[TIMEOUT_MS](https://curl.haxx.se/libcurl/c/CURLOPT_TIMEOUT_MS.html) |LONGINT|
[CONNECTTIMEOUT_MS](https://curl.haxx.se/libcurl/c/CURLOPT_CONNECTTIMEOUT_MS.html) |LONGINT|
[HTTP_TRANSFER_DECODING](https://curl.haxx.se/libcurl/c/CURLOPT_HTTP_TRANSFER_DECODING.html) |LONGINT|
[HTTP_CONTENT_DECODING](https://curl.haxx.se/libcurl/c/CURLOPT_HTTP_CONTENT_DECODING.html) |LONGINT|
[NEW_FILE_PERMS](https://curl.haxx.se/libcurl/c/CURLOPT_NEW_FILE_PERMS.html) |LONGINT|
[NEW_DIRECTORY_PERMS](https://curl.haxx.se/libcurl/c/CURLOPT_NEW_DIRECTORY_PERMS.html) |LONGINT|
[POSTREDIR](https://curl.haxx.se/libcurl/c/CURLOPT_POSTREDIR.html) |LONGINT|
[SSH_HOST_PUBLIC_KEY_MD5](https://curl.haxx.se/libcurl/c/CURLOPT_SSH_HOST_PUBLIC_KEY_MD5.html) |TEXT|
[PROXY_TRANSFER_MODE](https://curl.haxx.se/libcurl/c/CURLOPT_PROXY_TRANSFER_MODE.html) |LONGINT|
[CRLFILE](https://curl.haxx.se/libcurl/c/CURLOPT_CRLFILE.html) |TEXT|path
[ISSUERCERT](https://curl.haxx.se/libcurl/c/CURLOPT_ISSUERCERT.html) |TEXT|path
[ADDRESS_SCOPE](https://curl.haxx.se/libcurl/c/CURLOPT_ADDRESS_SCOPE.html) |LONGINT|
[CERTINFO](https://curl.haxx.se/libcurl/c/CURLOPT_CERTINFO.html) |LONGINT|
[USERNAME](https://curl.haxx.se/libcurl/c/CURLOPT_USERNAME.html) |TEXT|
[PASSWORD](https://curl.haxx.se/libcurl/c/CURLOPT_PASSWORD.html) |TEXT|
[PROXYUSERNAME](https://curl.haxx.se/libcurl/c/CURLOPT_PROXYUSERNAME.html) |TEXT|
[PROXYPASSWORD](https://curl.haxx.se/libcurl/c/CURLOPT_PROXYPASSWORD.html) |TEXT|
[NOPROXY](https://curl.haxx.se/libcurl/c/CURLOPT_NOPROXY.html) |TEXT|
[TFTP_BLKSIZE](https://curl.haxx.se/libcurl/c/CURLOPT_TFTP_BLKSIZE.html) |LONGINT|
[PROTOCOLS](https://curl.haxx.se/libcurl/c/CURLOPT_PROTOCOLS.html) |LONGINT|
[REDIR_PROTOCOLS](https://curl.haxx.se/libcurl/c/CURLOPT_REDIR_PROTOCOLS.html) |LONGINT|
[SSH_KNOWNHOSTS](https://curl.haxx.se/libcurl/c/CURLOPT_SSH_KNOWNHOSTS.html) |TEXT|
[FTP_USE_PRET](https://curl.haxx.se/libcurl/c/CURLOPT_FTP_USE_PRET.html) |LONGINT|
[RTSP_REQUEST](https://curl.haxx.se/libcurl/c/CURLOPT_RTSP_REQUEST.html) |LONGINT|
[RTSP_SESSION_ID](https://curl.haxx.se/libcurl/c/CURLOPT_RTSP_SESSION_ID.html) |TEXT|
[RTSP_STREAM_URI](https://curl.haxx.se/libcurl/c/CURLOPT_RTSP_STREAM_URI.html) |TEXT|
[RTSP_TRANSPORT](https://curl.haxx.se/libcurl/c/CURLOPT_RTSP_TRANSPORT.html) |TEXT|
[RTSP_CLIENT_CSEQ](https://curl.haxx.se/libcurl/c/CURLOPT_RTSP_CLIENT_CSEQ.html) |LONGINT|
[RTSP_SERVER_CSEQ](https://curl.haxx.se/libcurl/c/CURLOPT_RTSP_SERVER_CSEQ.html) |LONGINT|
[WILDCARDMATCH](https://curl.haxx.se/libcurl/c/CURLOPT_WILDCARDMATCH.html) |LONGINT|
[TLSAUTH_USERNAME](https://curl.haxx.se/libcurl/c/CURLOPT_TLSAUTH_USERNAME.html) |TEXT|
[TLSAUTH_PASSWORD](https://curl.haxx.se/libcurl/c/CURLOPT_TLSAUTH_PASSWORD.html) |TEXT|
[TLSAUTH_TYPE](https://curl.haxx.se/libcurl/c/CURLOPT_TLSAUTH_TYPE.html) |TEXT|
[TRANSFER_ENCODING](https://curl.haxx.se/libcurl/c/CURLOPT_TRANSFER_ENCODING.html) |LONGINT|
[DNS_SERVERS](https://curl.haxx.se/libcurl/c/CURLOPT_DNS_SERVERS.html) |TEXT|
[ACCEPTTIMEOUT_MS](https://curl.haxx.se/libcurl/c/CURLOPT_ACCEPTTIMEOUT_MS.html) |LONGINT|
[TCP_KEEPALIVE](https://curl.haxx.se/libcurl/c/CURLOPT_TCP_KEEPALIVE.html) |LONGINT|
[TCP_KEEPIDLE](https://curl.haxx.se/libcurl/c/CURLOPT_TCP_KEEPIDLE.html) |LONGINT|
[TCP_KEEPINTVL](https://curl.haxx.se/libcurl/c/CURLOPT_TCP_KEEPINTVL.html) |LONGINT|
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

``OBSOLETE72``  
``PROGRESSDATA``  
``PROGRESSFUNCTION``  
``TRANSFERTEXT``  
``OBSOLETE40``  
``STDERR``  
``HEADERDATA``  
``HTTPPOST``  
``IOCTLDATA``  
``IOCTLFUNCTION``  
``TCP_NODELAY``  
``SSL_CTX_DATA``  
``SSL_CTX_FUNCTION``  
``SHARE``  
``NOSIGNAL``  
``DEBUGDATA``  
``DEBUGFUNCTION``  
``DNS_USE_GLOBAL_CACHE``  
``SSLENGINE_DEFAULT``  
``SSLENGINE``  
``HEADERFUNCTION``  
``SEEKDATA``  
``SEEKFUNCTION``  
``COPYPOSTFIELDS``  
``OPENSOCKETDATA``  
``OPENSOCKETFUNCTION``  
``SOCKOPTDATA``  
``SOCKOPTFUNCTION``  
``CONV_FROM_UTF8_FUNCTION``  
``CONV_TO_NETWORK_FUNCTION``  
``CONV_FROM_NETWORK_FUNCTION``  
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
