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
json
```
%/accordion%

## 开启多个代理服务

%accordion%json%accordion%
```
gost -L http://:8080 -L socks5://:1080 
```
%/accordion%
