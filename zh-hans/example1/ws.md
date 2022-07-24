### 开启一个WS服务端

%accordion%命令行%accordion%
```
gost -L ws://:8443
```
%/accordion%


%accordion%yaml%accordion%
```
services:
- name: service-0
  addr: :8443
  handler:
    type: auto
  listener:
    type: ws
```
%/accordion%

%accordion%json%accordion%
```
{
    "services": [
        {
            "name": "service-0",
            "addr": ":8443",
            "handler": {
                "type": "auto"
            },
            "listener": {
                "type": "ws"
            }
        }
    ]
}
```
%/accordion%

### 参数


`path` 请求URI(示例`path=/abc` 默认`/ws`)
`backlog` 请求队列大小(示例`backlog=256` 默认`128`)
`header` 自定义HTTP响应头(示例`host=baidu.com`)
`handshakeTimeout` 设置握手超时时长(示例`handshakeTimeout=5s`)
`readHeaderTimeout` 设置请求头读取超时时长(示例`readHeaderTimeout=5s`)
`readBufferSize` 读缓冲区大小(示例`readBufferSize=2048`)
`writeBufferSize` 写缓冲区大小(示例`writeBufferSize=2048`)
`enableCompression` 开启压缩(示例`enableCompression=true` 默认`false`)