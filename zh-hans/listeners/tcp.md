# 开启一个TCP转发服务

* 监听端口 `8080` 并转发到 `192.168.1.1:8080`

%accordion%命令行%accordion%
```
gost -L tcp://:8080/192.168.1.1:8080
```
%/accordion%


%accordion%yaml%accordion%
```
services:
- name: service-0
  addr: :8080
  handler:
    type: tcp
  listener:
    type: tcp
  forwarder:
    targets:
    - 192.168.1.1:8080
```
%/accordion%