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

### 开启一个WSS服务端

%accordion%命令行%accordion%
```
gost -L wss://:8443
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
    type: wss
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
                "type": "wss"
            }
        }
    ]
}
```
%/accordion%


