# GOST 

> 所有教程环境基于Linux

## 安装


- 下载
```
wget https://github.com/go-gost/gost/releases/download/v3.0.0-beta.2/gost-linux-amd64-3.0.0-beta.2.gz #下载
gunzip gost-linux-amd64-3.0.0-beta.2.gz #解压
mv gost-linux-amd64-3.0.0-beta.2 gost #重命名为gost
cp gost /usr/bin/gost #移动到系统路径
chmod +x /usr/bin/gost #给予执行权限
```

- 配置系统服务

* 以下内容写入`/etc/systemd/system/gost.service`
```
[Unit]
Description=gost
After=network-online.target
Wants=network-online.target systemd-networkd-wait-online.service

[Service]
Type=simple
User=root
Restart=always
RestartSec=1
DynamicUser=true
LimitNOFILE=4000000
ExecStart=/usr/bin/gost -C /etc/gost/gost.yaml

[Install]
WantedBy=multi-user.target
```

备注:`ExecStart`根据实际情况改写，推荐以上格式