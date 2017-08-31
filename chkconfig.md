## chkconfig 命令主要用来更新（启动或停止）和查询系统服务的运行级信息。

- chkconfig							#列出所有的系统服务
- chkconfig --list        			#列出所有的系统服务
- chkconfig --list mysqld        		#列出mysqld服务设置情况
- chkconfig --add httpd        		#增加httpd服务
- chkconfig --del httpd        		#删除httpd服务
- chkconfig --level httpd 2345 on     #设置httpd在运行级别为2、3、4、5的情况下都是on（开启）的状态
- chkconfig --level 35 mysqld on      #设定mysqld在等级3和5为开机运行服务，--level 35表示操作只在等级3和5执行，on表示启动，off表示关闭
- chkconfig mysqld on        			#设定mysqld在各等级为on，“各等级”包括2、3、4、5等级

## 如何增加一个服务：
- 1.服务脚本必须存放在/etc/ini.d/目录下；
- 2.chkconfig --add servicename
    -在chkconfig工具服务列表中增加此服务，此时服务会被在/etc/rc.d/rcN.d中赋予K/S入口了；
-3.chkconfig --level 35 mysqld on
    -修改服务的默认启动等级。
