### 如果修改了 /etc/supervisord.conf ,需要执行 supervisorctl reload 来重新加载配置文件，否则不会生效。。。

- 安装
```
yum install supervisor
```

- 开启应用
```
systemctl start supervisord
systemctl status supervisord
```

- 开机启动
```
# 编辑启动文件
vi /etc/rc.local
# 在新行添加要执行的命令
supervisord -c /home/supervisord/supervisord.conf
```
 
```
如果 ini 文件里增加了节点 
则更新 supervisorctl update
```

```
// 启动
supervisord -c /etc/supervisord.conf  

// 杀死进程
ps -aux | grep super
kill -9 PID

// 客户端
supervisorctl
    help
    status
    
    reload
    
    stop ***
    start ***
    restart ***
    
    stop all
    start all
    restart all
    
    start test:test_0   ## 启动多个进程中的某个进程
    
    restart test:*   ## 修改了代码，要重启，*代表重启所有进程
    status  test:*   ## 查看状态
```

- 配置文件
```
主配置文件
/etc/supervisord.conf
 
子配置文件目录
/etc/supervisord.d/
```

- 配置文件示例  
     * test.ini
     * 注意日志那里，如果没有该目录，则先创建，不然启动服务会失败
     * user 按实际来填写吧
     * 如果启动不起来，有可能是程序过快退出，要死循环
```
[program:test]
command=php artisan command:wechat-voice
process_name=%(program_name)s_%(process_num)d
numprocs=1
directory=/home/wwwroot/private_speech/www

autorestart=true
autostart=false
startsecs=1
startretries=100
user=root
stdout_logfile=/home/supervisor/logs/%(program_name)s.log
stderr_logfile=/home/supervisor/logs/%(program_name)s-err.log
```
