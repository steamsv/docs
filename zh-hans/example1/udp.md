### 开启一个UDP转发服务

* 监听端口 `8080` 并转发到 `192.168.1.1:8080`

%accordion%命令行%accordion%
```
gost -L udp://:8080/192.168.1.1:8080
```
%/accordion%


%accordion%yaml%accordion%
```
services:
- name: service-0
  addr: :8080
  handler:
    type: udp
  listener:
    type: udp
  forwarder:
    targets:
    - 192.168.1.1:8080
```
%/accordion%

%accordion%json%accordion%
```
{
    "services": [
        {
            "name": "service-0",
            "addr": ":8080",
            "handler": {
                "type": "udp"
            },
            "listener": {
                "type": "udp"
            },
            "forwarder": {
                "targets": [
                    "192.168.1.1:8080"
                ]
            }
        }
    ]
}
```
%/accordion%

### 开启多个UDP转发服务

* 监听端口 `8080` 并转发到 `192.168.1.1:8080`
* 监听端口 `8090` 并转发到 `192.168.1.1:8090`

%accordion%命令行%accordion%
```
gost -L udp://:8080/192.168.1.1:8080 -L udp://:8090/192.168.1.1:8090
```
%/accordion%

%accordion%yaml%accordion%
```
services:
- name: service-0
  addr: :8080
  handler:
    type: udp
  listener:
    type: udp
  forwarder:
    targets:
    - 192.168.1.1:8080
- name: service-1
  addr: :8090
  handler:
    type: udp
  listener:
    type: udp
  forwarder:
    targets:
    - 192.168.1.1:8090
```
%/accordion%

%accordion%json%accordion%
```
{
    "services": [
        {
            "name": "service-0",
            "addr": ":8080",
            "handler": {
                "type": "udp"
            },
            "listener": {
                "type": "udp"
            },
            "forwarder": {
                "targets": [
                    "192.168.1.1:8080"
                ]
            }
        },
        {
            "name": "service-1",
            "addr": ":8090",
            "handler": {
                "type": "udp"
            },
            "listener": {
                "type": "udp"
            },
            "forwarder": {
                "targets": [
                    "192.168.1.1:8090"
                ]
            }
        }
    ]
}
```
%/accordion%

### 参数

`backlog` UDP连接队列大小(示例`backlog=256` 默认`128`)

`keepAlive` 是否保持连接，默认当返回响应数据给客户端后立即断开连接(示例`keepAlive=true` 默认`false`)

`ttl` UDP连接超时时长，当`keepAlive`为`true`时有效(示例`ttl=10s` 默认`5s`)

`readBufferSize` UDP读数据缓冲区字节大小(示例`readBufferSize=2000` 默认`1500`)

`readQueueSize` UDP连接读数据队列大小(示例`readQueueSize=256` 默认`128`)
