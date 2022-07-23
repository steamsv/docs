# 代理服务

## 开启一个代理服务

%accordion%命令行%accordion%
```
gost -L http://:8080
```
%/accordion%

%accordion%yaml%accordion%
```
services:
- name: service-0
  addr: ":8080"
  handler:
    type: http
  listener:
    type: tcp
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
                "type": "http"
            },
            "listener": {
                "type": "tcp"
            }
        }
    ]
}
```
%/accordion%

## 开启多个代理服务

%accordion%命令行%accordion%
```
gost -L http://:8080 -L socks5://:1080 
```
%/accordion%

%accordion%yaml%accordion%
```
services:
- name: service-0
  addr: :8080
  handler:
    type: http
  listener:
    type: tcp
- name: service-1
  addr: :1080
  handler:
    type: socks5
  listener:
    type: tcp
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
                "type": "http"
            },
            "listener": {
                "type": "tcp"
            }
        },
        {
            "name": "service-1",
            "addr": ":1080",
            "handler": {
                "type": "socks5"
            },
            "listener": {
                "type": "tcp"
            }
        }
    ]
}
```
%/accordion%
