# update-alternatives

https://blog.csdn.net/hellocsz/article/details/82701689

## 获取帮助

```
$ update-alternatives --help
```

## 注册软件

```
$ update-alternatives --install link name path priority [--slave slink sname spath]

link: 是在/usr/bin/,/usr/local/bin/等默认PATH搜索目录
name: 是在/etc/alternatives目录中的链接名
path: 是真正的可执行程序的位置,可以在任何位置
priority: 是优先级，优先级，数字越大优先级越高
```

## 查看已注册列表


```
$ update-alternatives --display java
```

## 修改命令版本


### 交互式修改

update-alternatives --config java
update-alternatives --auto java


### 立即修改

update-alternatives --set java /opt/jdk1.8.0_91/bin/java
cd /opt/jdk1.8.0_91/bin/
update-alternatives --set java $PWD/java

## 管理软件包

事实上，update-alternatives的原理是软链管理，可以处理目录。那么我们就可以把整个软件包目录都纳入管理。




