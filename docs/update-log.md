### 发布记录 update log

#### v1.0.7 (2025-01-20)
 * 删除 xhttp 协议相关说明，这个脚本已经不能在 workers 中部署
 * remove xhttp transport, workers have banned this script

#### v1.0.6 (2025-01-15)
 * 把 BUFFER_SIZE 设置为 `0` 可以禁用缓存功能
 * 添加关闭 ws 和远程链接的善后代码
 * 添加一个 yield 中继器（实验功能）
 * buffering feature can be disabled by setting `BUFFER_SIZE` to `0`
 * add code for closing ws server and remote connection
 * add an "yield" relay (experimental)

#### v1.0.5 (2025-01-12)
 * 添加上传、下载缓存大小设置项
 * add upload/download buffer size setting

#### v1.0.4 (2025-01-10)
 * 重构代码

#### v1.0.3 (2025-01-08)
 * ws 添加写缓存
 * xhttp 添加读缓存

#### v1.0.2 (2025-01-06)
 * 重构代码

#### v1.0.1 (2025-01-02)
 * 支持指定多个 Cloudflare 反向代理
 * 生成的配置添加分片（fragment）选项
 * 当 UUID 为空时，显示随机配置示例

#### v1.0.0 (2024-12)
 * WebSocket 协议
 * XHTTP 协议
 * DNS over HTTPS
 * 查询客户 IP 信息
