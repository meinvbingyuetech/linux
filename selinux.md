#关闭selinux
- vim /etc/selinux/config
```
将SELINUX=enforcing改为selinux=disabled,保存并退出
```
- setenforce 0
