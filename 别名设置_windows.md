## 创建alias.txt
```
ls=dir /ONE $*
cat=type $*
rm=del $*
pwd=cd
mkdir=md $*
www=e: && cd \centos\sscf-work\www
```
#### 解释：
- doskey就相当于Linux中的alias，
- $*表示这个命令还可能有其他参数，
- @表示执行这条命令时不显示这条命令本身
- 第二个命令type xxxxxxxxxxxx.txt的作用是读取txt文件内容并打印到屏幕，等同于Linux下的cat
