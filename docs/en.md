[简体中文](../README.md) | English  

Please help me improve this document.  

This script is used to deploy vless-ws proxy to Cloudflare pages.

#### Deploy
 1. Download `cfxhttp.zip` from [releases](https://github.com/vrnobody/cfxhttp/releases), and upload to pages
 2. Add `UUID` and `WS_PATH` enviroment variables

If every thing goes right, you would see a `Hello World!` when accessing `https://your-project-name.pages.dev`.  
Visit `https://your-project-name.pages.dev/(WS_PATH)/?fragment=true&uuid=(UUID)` to get a client `config.json` with WebSocket transport.  
Set `fragment` to `false` to get a config without fragment settings.  

#### Settings detail
 * `UUID` Need no explains.
 * `PROXY` (optional) Reverse proxies for websites using Cloudflare CDN. Randomly pick one for every connection. Format: `a.com, b.com, ...`
 * `WS_PATH` URL path for ws transport. e.g. `/ws`. Leave it empty to disable this feature.
 * `DOH_QUERY_PATH` URL path for DNS over HTTP(S) feature. e.g. `/doh-query`. Leave it empty to disable this feature.
 * `UPSTREAM_DOH` e.g. `https://dns.google/dns-query`. Do not use Cloudflare DNS.
 * `IP_QUERY_PATH` URL path for querying client IP information feature. e.g. `/ip-query/?key=123456`. Leave it empty to disable this feature. The `key` parameter is used for authentication.
 * `LOG_LEVEL` debug, info, error, none
 * `TIME_ZONE` Timestamp time zone of logs. e.g. Argentina is `-3`
 * `BUFFER_SIZE` Upload/Download buffer size in KiB. Set to `0` to disable buffering. I don't know what the optimal value is. XD
 * `RELAY_SCHEDULER` Experimental feature. Available values are `pipe` or `yield`. Please read the comment in source code.

#### Notice
 * `src/index.js` is under developing, could have bugs, please download `Source code (zip)` from [releases](https://github.com/vrnobody/cfxhttp/releases).
 * This script is slow, do not expect too much.
 * Workers and pages do not support UDP. Applications require UDP feature will not work. Such as DNS.
 * Workers and pages have CPU executing-time limit. Applications require long-term connection would disconnect randomly. Such as downloading a big file.
 * DoH feature is not for xray-core, use DNS over TCP in `config.json` instead. e.g. `tcp://8.8.8.8:53`  
 * WebSocket transport does not and would not support early data feature.
 * The more people knows of this script, the sooner this script got banned.

#### Credits
[tina-hello/doh-cf-workers](https://github.com/tina-hello/doh-cf-workers/) DoH feature  
[6Kmfi6HP/EDtunnel](https://github.com/6Kmfi6HP/EDtunnel/) WebSocket transport feature  
[clsn blog](https://clsn.io/post/2024-07-11-%E5%80%9F%E5%8A%A9cloudflare%E8%8E%B7%E5%8F%96%E5%85%AC%E7%BD%91ip) Get IP information feature  
