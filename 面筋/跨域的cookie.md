[CORS 跨域 Cookie 的设置与获取 - 简书 (jianshu.com)](https://www.jianshu.com/p/13d53acc124f)

1. 跨域的请求 `XMLHttpRequest` 中  把  withCredentials 设置为 true
2. 服务器配合 Access-Control-Allow-Credentials: true 
3. 要想设置和获取跨域 Cookie，上面提到的两点缺一不可。**另外有一点需要注意的是**：规范中提到，如果 `XMLHttpRequest` 请求设置了`withCredentials` 属性，那么服务器不得设置 `Access-Control-Allow-Origin`的值为`*` ，否则浏览器将会抛出`The value of the 'Access-Control-Allow-Origin' header in the response must not be the wildcard '*'` 错误。

  