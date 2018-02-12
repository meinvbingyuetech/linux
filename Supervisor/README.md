### 如果修改了 /etc/supervisord.conf ,需要执行 supervisorctl reload 来重新加载配置文件，否则不会生效。。。

- 安装
```
yum install supervisor
```

- 开机启动
```
# 编辑启动文件
vi /etc/rc.local
# 在新行添加要执行的命令
supervisord -c /home/supervisord/supervisord.conf
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
```
[program:test]
command=php artisan task:store-assistant-rank-mysql
process_name=%(program_name)s_%(process_num)d
numprocs=2
directory=/vagrant/www/stock-assistant-storage-task/www/assistant.task.sscf.com 

umask=0755
autorestart=true
autostart=false
startsecs=1
startretries=100
user=www-data
stdout_logfile=/etc/supervisor/logs/%(program_name)s.log
stderr_logfile=/etc/supervisor/logs/%(program_name)s-err.log
```
