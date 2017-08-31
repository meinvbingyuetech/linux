## https://linux.cn/article-5926-1.html  #服务的详细说明
 
## cd /lib/systemd/system/

## vim redis.service

```
[Unit]
Description=Redis
After=network.target

[Service]
ExecStart=/usr/local/redis/src/redis-server /usr/local/redis/redis.conf --daemonize no
ExecStop=/usr/local/bin/redis-cli -h 127.0.0.1 -p 6379 shutdown

[Install]
WantedBy=multi-user.target
```

## 刷新配置
systemctl daemon-reload
 
## 启动、重启、停止、状态、开机启动
- systemctl start redis
- systemctl restart redis
- systemctl stop redis
- systemctl status redis
- systemctl enable redis
  - ll /etc/systemd/system/multi-user.target.wants/
