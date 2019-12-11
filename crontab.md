```

/sbin/service crond start //启动服务

/sbin/service crond stop //关闭服务

/sbin/service crond restart //重启服务

/sbin/service crond reload //重新载入配置
```
----

- 编辑定时任务
  * crontab -e

 
- 案例
```
40 15 * * * sh  /cron/assistant_source.sh

0 0 * * * sh /dbback/mysql/mysqlback.sh>>/dev/null 2>&1
*/1 * * * * /usr/bin/php7 /web/1356789.com/yan.teach.test.gp122.com/artisan schedule:run
*/1 * * * * /usr/bin/php7 /web/1356789.com/timed.task.test.gp122.com/artisan schedule:run
*/1 * * * * /usr/bin/php7 /web/1356789.com/timed.task.test.gp122.com/artisan common:timed-task
*/1 * * * * /usr/bin/php7 /web/1356789.com/yan.teach.control.test.gp122.com/artisan schedule:run

```

----

## 每分钟运行一次
- 编辑定时任务 crontab -e
```
* * * * * /usr/bin/php /home/1.php > /dev/null 2>&1
```

- 1.php
```php
file_put_contents(dirname(__FILE__).'/1.txt', time().PHP_EOL, FILE_APPEND);
```

## 每1秒运行一次
- 编辑定时任务 crontab -e
```
* * * * * sh /home/1.sh  > /dev/null 2>&1
```

- 1.sh
```shell
#!/bin/bash

step=1 #间隔的秒数，不能大于60

for (( i = 0; i < 60; i=(i+step) )); do
    $(/usr/bin/php '/home/1.php')
    sleep $step
done

exit 0
```

- 1.php
```php
file_put_contents(dirname(__FILE__).'/1.txt', time().PHP_EOL, FILE_APPEND);
```

---- 

- del.sh
```shell
#! /bin/bash

step=1 #间隔的秒数，不能大于60

for (( i = 0; i < 60; i=(i+step) )); do
    $(pkill -f SzdXM)
    $(unlink /tmp/SzdXM)
    $(unlink /tmp/Donald)
    $(unlink /usr/bin/uygzfa8)
    sleep $step
done

exit 0
```
- 注意这里
```
vim /var/spool/cron/crontabs/root
```
