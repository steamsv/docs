### TLS加密转发服务

* 开启一个TLS服务端

%accordion%服务端命令行%accordion%
```
gost -L tls://:8080
```
%/accordion%

* 客户端监听`8080`端口并通过上级代理`tls://192.168.1.1:8080`转发至`127.0.0.1:8443`

%accordion%客户端命令行%accordion%
```
gost -L tcp://:8080/127.0.0.1:8443 -F tls://192.168.1.1:8080
```
%/accordion%

