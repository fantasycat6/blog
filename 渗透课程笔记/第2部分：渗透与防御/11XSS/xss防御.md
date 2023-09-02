# 测试payload

```javascript
<script>alert('XSS')</script>
<script>alert(document.cookie)</script>
><script>alert(document.cookie)</script>
='><script>alert(document.cookie)</script>
"><script>alert(document.cookie)</script>
%3Cscript%3Ealert('XSS')%3C/script%3E
<img src="javascript:alert('XSS')">
onerror="alert('XSS')">
```

#  输入

识别：正则<script>

处理：<scr_ipt>

## WAF过滤

WAF——web application firewall

web应用防火墙



### **modsecurity** 

https://github.com/SpiderLabs/ModSecurity

# 输出

htmlspecialchars()转义