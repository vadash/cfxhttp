简体中文 | [English](./docs/en.md)  

在 Cloudflare pages 中部署 vless.ws 协议的代理服务器。  

#### 部署
 1. 下载 [releases](https://github.com/vrnobody/cfxhttp/releases) 中的 cfxhttp.zip，上传到 pages
 2. 在设置面板中添加环境变量： `UUID` 和 `WS_PATH`

一切顺利的话，访问（可能要挂代理） `https://your-project-name.pages.dev` 会看到 `Hello World!`。  
访问 `https://your-project-name.pages.dev/(WS_PATH)/?fragment=true&uuid=(UUID)`  
获取 WebSocket 协议的客户端 `config.json`。把 `fragment` 设置为 `false` 获取关闭分片功能的配置。  

#### 各设置项说明
 * `UUID` 这个不用解释了吧
 * `PROXY` （可选）反代 CF 网页的服务器，逗号分隔，每次随机抽取一个，格式：`a.com, b.com, ...`
 * `WS_PATH` ws 协议的访问路径，例如：`/ws`，留空表示关闭这个功能
 * `DOH_QUERY_PATH` DNS over HTTPS 服务的访问路径，例如：`/doh-query`，留空表示关闭这个功能
 * `UPSTREAM_DOH` 上游 DoH 服务器，例如：`https://dns.google/dns-query`，注意不要填 Cloudflare 的 DNS
 * `IP_QUERY_PATH` 查询客户 IP 信息功能的访问路径，例如: `/ip-query/?key=123456`，留空表示关闭这个功能，后面那个 key 相当于密码
 * `LOG_LEVEL` 日志级别，可选值：`debug`, `info`, `error`, `none`
 * `TIME_ZONE` 日志时间戳的时区，中国填 `8`
 * `BUFFER_SIZE` 上传、下载缓存大小，单位 KiB，设置为 `0` 禁用缓存功能，我也不知道应该设为多大
 * `RELAY_SCHEDULER` （实验功能）中继调度器，可选值：`pipe`, `yield`，详见代码中的注释

#### 注意事项
 * src/index.js 是开发中的代码，会有 bug，请到 [releases](https://github.com/vrnobody/cfxhttp/releases) 里面下载 Source code (zip)
 * 网站测速结果是错的，这个脚本很慢，不要有太高的期望
 * pages / workers 不支持 UDP，需要 UDP 功能的应用无法使用，例如：DNS
 * pages / workers 有 CPU 时间限制，需要长时间链接的应用会随机断线，例如：下载大文件
 * DoH 功能不是给 xray-core 使用的，`config.json` 应使用 DNS over TCP，例如：`tcp://8.8.8.8:53`
 * ws 协议不支持，也不会支持 early data 功能
 * 使劲薅，免费的资源就会消失，且用且珍惜

#### 感谢（代码抄袭自以下项目）
[tina-hello/doh-cf-workers](https://github.com/tina-hello/doh-cf-workers/) DNS over HTTPS 功能  
[6Kmfi6HP/EDtunnel](https://github.com/6Kmfi6HP/EDtunnel/) WebSocket 传输协议功能  
[clsn blog](https://clsn.io/post/2024-07-11-%E5%80%9F%E5%8A%A9cloudflare%E8%8E%B7%E5%8F%96%E5%85%AC%E7%BD%91ip) 获取 IP 信息功能  
