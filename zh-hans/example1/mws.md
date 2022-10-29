### 开启一个MWS服务

* 监听端口 `8080` 并转发到 `192.168.1.1:8080`

```
gost -L http+mws://:8080?path=/ws
```

### 开启一个MWS+TLS服务

```
gost -L http+mwss://:8443?path=/ws
```

`path` 请求URI(示例`/abc` 默认`/ws`)

`backlog` 请求队列大小(示例`backlog=256` 默认`128`)

`header ` 自定义HTTP响应头(示例`host=baidu.com` 只能在配置文件内设定)

`handshakeTimeout ` 设置握手超时时长(示例`handshakeTimeout=20s` 默认`5s`)

`readHeaderTimeout` 设置请求头读取超时时长(示例`readHeaderTimeout=60s`)

`readBufferSize` 读缓冲区大小(字节)(示例`readBufferSize=65536`)

`writeBufferSize ` 写缓冲区大小(字节)(示例`writeBufferSize =8388603`)

`enableCompression ` 开启压缩(示例`enableCompression=true` 默认`false`)

`muxKeepAliveDisabled` 多路复用会话设置。禁用心跳保活(示例`muxKeepAliveDisabled=true` 默认`false`)

`muxKeepAliveInterval` 多路复用会话设置。心跳间隔(示例`muxKeepAliveInterval=20s` 默认`10s`)

`muxKeepAliveTimeout` 多路复用会话设置。心跳超时(示例`muxKeepAliveTimeout=60s` 默认`30s`)

`muxMaxFrameSize` 多路复用会话设置。最大数据帧大小(字节)(示例`muxMaxFrameSize=65536` 默认`32768`)

`muxMaxReceiveBuffer` 多路复用会话设置。最大接收缓冲大小(字节)(示例`muxMaxReceiveBuffer=8388603` 默认`4194304`)

`muxMaxStreamBuffer` 多路复用会话设置。最大流缓冲大小(字节)(示例`muxMaxStreamBuffer=30000` 默认 `65536`)
