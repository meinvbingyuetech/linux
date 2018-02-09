- 配置文件
```
[program:store-assistant-rank-mysql-task]
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
