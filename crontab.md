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
- demo
```
crontab -e

* * * * * /usr/bin/php /home/1.php > /dev/null 2>&1
```

```php
file_put_contents(dirname(__FILE__).'/1.txt', time().PHP_EOL, FILE_APPEND);
```