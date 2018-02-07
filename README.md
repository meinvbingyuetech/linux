```
使用 文件内容
mysql -uroot -p'cat /dara/passwd.txt'
```

```
查看文件大小
du -sh lumen.log
```

```
查看/搜索文件
cat lumen.log |grep '错误'|more
cat lumen.log|wc -l
cat lumen.log |head
cat lumen.log |grep '2018-02-06'|grep '错误' >>/tmp/123.txt
```

```
计算 文件相关数据
wc log.txt -l  统计行数
wc log.txt -c  统计Bytes数
wc log.txt -w  统计字数
```
