### 开启一个TLS服务端

%accordion%命令行%accordion%
```
gost -L tls://:8080
```
%/accordion%

%accordion%yaml%accordion%
```
services:
- name: service-0
  addr: :8080
  handler:
    type: auto
  listener:
    type: tls
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
        "type": "auto"
      },
      "listener": {
        "type": "tls"
      }
    }
  ]
}
```
%/accordion%
