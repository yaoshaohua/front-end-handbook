# NestJS

## Node.js Web 框架的三个层次

![Alt text](assets/web-framework.png)

Web 框架指的是开发 HTTP(S) API 服务的框架

### 第一层：Web 框架的基础，Node.js 提供了 HTTP(S) 模块用于处理协议数据

创建一个简单的 HTTP 服务器：

```js
const http = require('http')
const url = require('url')

const server = http.createServer((req, res) => {
  // 判断请求类型
  if (req.method === 'get') {
    //...
  } else if (req.method === 'post') {
    //...
  }
  // 获取请求参数
  const queryObject = url.parse(req.url, true).query

  // 响应返回
  res.writeHead(200, { 'Content-Type': 'text/plain' })
  res.end('Hello World\n')
})

server.listen(8080, '127.0.0.1', () => {
  console.log('server running on http://127.0.0.1:8080')
})
```

局限性：提供的 API 过于原始，直接使用很麻烦，比如：

1. 请求类型需要自己判断
2. 获取请求参数还需要 url 模块 parse一次
3. 响应的返回只能用 write 或 end 返回一段 buffer 或 string。

因此，一般使用 Express、Koa、Fastify 这类 Web 框架。

### 第二层：简约框架 Express、Koa、Fastify

1. 提供了路由机制，无需手动判断 method 和 path

    ```js
    app.get('/list', function (req, res) {
        //...
    })
    app.post('/save', function (req, res) {
        //...
    })
    ```

2. 提供更简捷的 request 和 response API

    ```js
    // req.params 获取请求参数
    app.get('/user/:id', function (req, res) {
        res.send('user ' + req.params.id)
    })

    // res.download 返回下载的响应
    res.download('/report-12345.pdf')

    // res.render 返回模版引擎渲染的 html
    app.render('xxx-template', { name: 'guang' }, function (err, html) {
        // ...
    })
    ```

3. 提供了中间件机制，用于逻辑复用

    ```js
    // Error-handling middleware
    app.use((err, req, res, next) => {
        console.error(err.stack)
        res.status(500).send('Something broke!')
    })
    ```

局限性：

没有规定代码应该怎么组织，怎么复用、怎么集成各种方案，代码可以写出各种样子，对于大型项目开发来说较难维护

因此，出现了更上层的框架，Nest、Egg、Midway，他们提供了额外的架构能力。

### 第三层：企业级开发框架，Nest、Egg、Midway

Nest 底层基于 Express，封装出了 IOC、AOP 等架构特性
