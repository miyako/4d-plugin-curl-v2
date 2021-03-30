compile for Apple Silicon

```sh
export CC="gcc"
export CXX="g++"
export CCFLAGS="-arch arm64"
export CXXFLAGS="-arch arm64 -isysroot /Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX.sdk"
export CFLAGS="-arch arm64 -isysroot /Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX.sdk"
export LDFLAGS="-arch arm64 -isysroot /Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX.sdk"

./configure --host=aarch64-apple-darwin --enable-static --with-nghttp2 --with-libssh2 --without-librtmp
```

```
curl version:     7.75.0
  SSL:              enabled (OpenSSL)
  SSH:              enabled (libSSH2)
  zlib:             enabled
  brotli:           enabled (libbrotlidec)
  zstd:             enabled (libzstd)
  GSS-API:          no      (--with-gssapi)
  TLS-SRP:          enabled
  resolver:         POSIX threaded
  IPv6:             enabled
  Unix sockets:     enabled
  IDN:              enabled (libidn2)
  Build libcurl:    Shared=yes, Static=yes
  Built-in manual:  enabled
  --libcurl option: enabled (--disable-libcurl-option)
  Verbose errors:   enabled (--disable-verbose)
  Code coverage:    disabled
  SSPI:             no      (--enable-sspi)
  ca cert bundle:   no
  ca cert path:     no
  ca fallback:      no
  LDAP:             enabled (OpenLDAP)
  LDAPS:            enabled
  RTSP:             enabled
  RTMP:             no      (--with-librtmp)
  Metalink:         no      (--with-libmetalink)
  PSL:              no      (libpsl not found)
  Alt-svc:          enabled
  HTTP1:            enabled (--with-hyper)
  HTTP2:            enabled (nghttp2)
  HTTP3:            no      (--with-ngtcp2, --with-quiche)
  ECH:              no      (--enable-ech)
  Protocols:        DICT FILE FTP FTPS GOPHER GOPHERS HTTP HTTPS IMAP IMAPS LDAP LDAPS MQTT POP3 POP3S RTSP SCP SFTP SMB SMBS SMTP SMTPS TELNET TFTP
  Features:         AsynchDNS HTTP2 HTTPS-proxy IDN IPv6 NTLM NTLM_WB SSL TLS-SRP UnixSockets alt-svc brotli libz zstd
```
