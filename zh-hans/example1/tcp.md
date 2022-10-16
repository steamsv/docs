### 开启一个TCP转发服务

* 监听端口 `8080` 并转发到 `192.168.1.1:8080`

<details><summary>命令行</summary><blockquote>
gost -L tcp://:8080/192.168.1.1:8080
</blockquote></details>


<details><summary>yaml</summary><blockquote>
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
</blockquote></details>

<details><summary>json</summary><blockquote>
{
    "services": [
        {
            "name": "service-0",
            "addr": ":8080",
            "handler": {
                "type": "tcp"
            },
            "listener": {
                "type": "tcp"
            },
            "forwarder": {
                "targets": [
                    "192.168.1.1:8080"
                ]
            }
        }
    ]
}
</blockquote></details>

### 开启多个TCP转发服务

* 监听端口 `8080` 并转发到 `192.168.1.1:8080`
* 监听端口 `8090` 并转发到 `192.168.1.1:8090`

<details><summary>命令行</summary><blockquote>
gost -L tcp://:8080/192.168.1.1:8080 -L tcp://:8090/192.168.1.1:8090
</blockquote></details>


<details><summary>yaml</summary><blockquote>
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
- name: service-1
  addr: :8090
  handler:
    type: tcp
  listener:
    type: tcp
  forwarder:
    targets:
    - 192.168.1.1:8090
</blockquote></details>

<details><summary>json</summary><blockquote>
{
    "services": [
        {
            "name": "service-0",
            "addr": ":8080",
            "handler": {
                "type": "tcp"
            },
            "listener": {
                "type": "tcp"
            },
            "forwarder": {
                "targets": [
                    "192.168.1.1:8080"
                ]
            }
        }，
        {
            "name": "service-1",
            "addr": ":8090",
            "handler": {
                "type": "tcp"
            },
            "listener": {
                "type": "tcp"
            },
            "forwarder": {
                "targets": [
                    "192.168.1.1:8090"
                ]
            }
        }
    ]
}
</blockquote></details>

### 使用代理转发服务

* 监听端口 `8080` 通过`tls://192.168.1.2:8090`转发到 `192.168.1.1:8080`

<details><summary>命令行</summary><blockquote>
gost -L tcp://:8080/192.168.1.1:8080 -F tls://192.168.1.2:8090
</blockquote></details>

<details><summary>yaml</summary><blockquote>
services:
- name: service-0
  addr: :8080
  handler:
    type: tcp
    chain: chain-0
  listener:
    type: tcp
  forwarder:
    nodes:
    - name: target-0
      addr: 192.168.1.1:8080
chains:
- name: chain-0
  hops:
  - name: hop-0
    nodes:
    - name: node-0
      addr: 192.168.1.2:8090
      connector:
        type: http
      dialer:
        type: tls
</blockquote></details>

<details><summary>json</summary><blockquote>
{
    "services": [
        {
            "name": "service-0",
            "addr": ":8080",
            "handler": {
                "type": "tcp",
                "chain": "chain-0"
            },
            "listener": {
                "type": "tcp"
            },
            "forwarder": {
                "nodes": [
                    {
                        "name": "target-0",
                        "addr": "192.168.1.1:8080"
                    }
                ]
            }
        }
    ],
    "chains": [
        {
            "name": "chain-0",
            "hops": [
                {
                    "name": "hop-0",
                    "nodes": [
                        {
                            "name": "node-0",
                            "addr": "192.168.1.2:8090",
                            "connector": {
                                "type": "http"
                            },
                            "dialer": {
                                "type": "tls"
                            }
                        }
                    ]
                }
            ]
        }
    ]
}
</blockquote></details>

### 使用多个代理转发服务

* 监听端口 `8080` 通过`tls://192.168.1.2:8090`转发到 `192.168.1.1:8080`
* 监听端口 `8082` 通过`tls://192.168.1.3:8091`转发到 `192.168.1.4:8080`

<details><summary>命令行</summary><blockquote>
gost -L tcp://:8082/192.168.1.4:8080 -F tls://192.168.1.3:8091 -L tcp://:8080/192.168.1.1:8080 -F tls://192.168.1.2:8090
</blockquote></details>

<details><summary>yaml</summary><blockquote>
services:
- name: service-0
  addr: :8082
  handler:
    type: tcp
    chain: chain-0
  listener:
    type: tcp
  forwarder:
    nodes:
    - name: target-0
      addr: 192.168.1.4:8080
- name: service-1
  addr: :8080
  handler:
    type: tcp
    chain: chain-0
  listener:
    type: tcp
  forwarder:
    nodes:
    - name: target-0
      addr: 192.168.1.1:8080
chains:
- name: chain-0
  hops:
  - name: hop-0
    nodes:
    - name: node-0
      addr: 192.168.1.3:8091
      connector:
        type: http
      dialer:
        type: tls
  - name: hop-1
    nodes:
    - name: node-0
      addr: 192.168.1.2:8090
      connector:
        type: http
      dialer:
        type: tls
</blockquote></details>

<details><summary>json</summary><blockquote>
{
    "services": [
        {
            "name": "service-0",
            "addr": ":8082",
            "handler": {
                "type": "tcp",
                "chain": "chain-0"
            },
            "listener": {
                "type": "tcp"
            },
            "forwarder": {
                "nodes": [
                    {
                        "name": "target-0",
                        "addr": "192.168.1.4:8080"
                    }
                ]
            }
        },
        {
            "name": "service-1",
            "addr": ":8080",
            "handler": {
                "type": "tcp",
                "chain": "chain-0"
            },
            "listener": {
                "type": "tcp"
            },
            "forwarder": {
                "nodes": [
                    {
                        "name": "target-0",
                        "addr": "192.168.1.1:8080"
                    }
                ]
            }
        }
    ],
    "chains": [
        {
            "name": "chain-0",
            "hops": [
                {
                    "name": "hop-0",
                    "nodes": [
                        {
                            "name": "node-0",
                            "addr": "192.168.1.3:8091",
                            "connector": {
                                "type": "http"
                            },
                            "dialer": {
                                "type": "tls"
                            }
                        }
                    ]
                },
                {
                    "name": "hop-1",
                    "nodes": [
                        {
                            "name": "node-0",
                            "addr": "192.168.1.2:8090",
                            "connector": {
                                "type": "http"
                            },
                            "dialer": {
                                "type": "tls"
                            }
                        }
                    ]
                }
            ]
        }
    ]
}
</blockquote></details>
