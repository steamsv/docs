### 开启一个MTLS服务端

%accordion%命令行%accordion%
```
gost -L mtls://:8443
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
    type: mtls
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
                "type": "mtls"
            }
        }
    ]
}
```
%/accordion%

### 参数

### 参数

`backlog` UDP连接队列大小(示例`backlog=256` 默认`128`) 
`muxKeepAliveDisabled` 多路复用会话设置。禁用心跳保活(示例`muxKeepAliveDisabled=true` 默认`false`)
`muxKeepAliveInterval` 多路复用会话设置。心跳间隔(示例`muxKeepAliveInterval=20s` 默认`10s`)
`muxKeepAliveTimeout` 多路复用会话设置。心跳超时(示例`muxKeepAliveTimeout=60s` 默认`30s`)
`muxMaxFrameSize` 多路复用会话设置。最大数据帧大小(字节)(示例`muxMaxFrameSize=65536` 默认`32768`)
`muxMaxReceiveBuffer` 多路复用会话设置。最大接收缓冲大小(字节)(示例`muxMaxReceiveBuffer=8388603` 默认`4194304`)
`muxMaxStreamBuffer` 多路复用会话设置。最大流缓冲大小(字节)(示例`muxMaxStreamBuffer=30000` 默认 `65536`)