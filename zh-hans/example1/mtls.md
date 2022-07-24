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


