### 开启一个WSS服务端

```
gost -L wss://:8443
```

### 参数

`path` 请求URI(示例`path=/abc` 默认`/ws`)

`backlog` 请求队列大小(示例`backlog=256` 默认`128`)

`header` 自定义HTTP响应头(示例`host=baidu.com` 只能在配置文件内设定)

`handshakeTimeout` 设置握手超时时长(示例`handshakeTimeout=5s`)

`readHeaderTimeout` 设置请求头读取超时时长(示例`readHeaderTimeout=5s`)

`readBufferSize` 读缓冲区大小(示例`readBufferSize=2048`)

`writeBufferSize` 写缓冲区大小(示例`writeBufferSize=2048`)

`enableCompression` 开启压缩(示例`enableCompression=true` 默认`false`)
