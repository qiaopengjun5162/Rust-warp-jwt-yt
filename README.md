# Rust-warp-jwt-yt

## Explain main.rs code

这段代码是一个简单的Web服务器，用于处理用户登录和用户角色验证的请求。以下是代码的步骤解释：

1. 导入所需的库和模块。
2. 定义一些类型别名，用于简化代码中的类型声明。
3. 定义了一个 `User` 结构体，表示用户的信息。
4. 定义了一个 `LoginRequest` 结构体，表示登录请求的信息。
5. 定义了一个 `LoginResponse` 结构体，表示登录响应的信息。
6. 定义了一个 `main` 函数，作为程序的入口点。
7. 在 `main` 函数中，首先初始化用户信息，并将其存储在一个全局的 `HashMap` 中。
8. 定义了几个路由处理函数，用于处理不同的请求。其中包括登录请求、普通用户请求和管理员请求。
9. 将这些路由处理函数组合成一个路由，并启动服务器监听指定的端口。
10. 定义了一个 `with_users` 函数，用于将用户信息注入到请求处理函数中。
11. 定义了 `login_handler` 函数，用于处理登录请求。它首先在用户信息中查找匹配的用户，如果找到则生成一个JWT令牌，并返回登录响应。如果未找到匹配的用户，则返回错误。
12. 定义了 `user_handler` 函数和 `admin_handler` 函数，分别用于处理普通用户请求和管理员请求。这两个函数简单地返回一个包含用户ID的欢迎消息。
13. 定义了一个 `init_users` 函数，用于初始化用户信息。

总结：这段代码实现了一个简单的Web服务器，用于处理用户登录和用户角色验证的请求。它使用了Warp框架来构建路由和处理请求，并使用了JWT来生成令牌进行身份验证。

## Usage

See src/test.http

```shell
➜ curl http://localhost:8000/login -d '{"email": "user@userland.com", "pw": "1234"}' -H 'Content-Type:application/json'
{"token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJzdWIiOiIxIiwicm9sZSI6IlVzZXIiLCJleHAiOjE2OTYwNjM1OTd9.aVMRjmRFk6L-_ZzzZ7xrMcs8p81nTVk2FoPQ3LAJOLsax15GOOAkH6VizfGgxYJ9cl-LqmK5SRmN1txIXx9HMA"}%
