# 客户端读取cookie

```javascript
 alert(document.cookie);
```



# 客户端设置cookie

```javascript
document.cookie="username=wuya"; 
```



# 修改

 新建一个同名的cookie，**覆盖**原来的cookie（属性必需一致） 

# 删除 

把**过期时间**设置为比当前时间早的时间 

```javascript
setcookie("username",'',time()-1)
```

