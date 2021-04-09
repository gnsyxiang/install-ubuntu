# ftp

<!-- vim-markdown-toc GFM -->

* [vsftpd](#vsftpd)
* [tftp](#tftp)
  - [安装](#安装)
  - [配置tftpd-hpa](#配置tftpd-hpa)
  - [开启、停止、重启](#开启停止重启)
  - [查看](#查看)
* [自动启动服务tftp服务](#自动启动服务tftp服务)
  - [openbsd-inetd](#openbsd-inetd)
  - [xinetd](#xinetd)
    + [安装](#安装-1)
    + [设置xinetd](#设置xinetd)
    + [配置tftp](#配置tftp)
    + [开启、停止、重启](#开启停止重启-1)

<!-- vim-markdown-toc -->

* vsftpd是一款在Linux发行版中最受推崇的FTP服务器程序。你可以通过ftp客户端上传下载软件。可设置访问用户名密码，或匿名anonymous登陆。默认端口是TCP:21

* TFTP（Trivial File Transfer Protocol,简单文件传输协议）是TCP/IP协议族中的一个用来在客户机与服务器之间进行简单文件传输的协议，提供不复杂、开销不大的文件传输服务。只能从服务器上获取文件，或者向服务器写入文件，不能列出目录，也不能进行认证。端口号为UDP:69。 路由器，交换机等网络设备升级硬件系统可用，PXE安装系统需要配置tftp服务。


* FTP 是完整、面向会话、常规用途文件传输协议。而 TFTP 用作 bones bare - 特殊目的文件传输协议。

* 交互使用 FTP。 TFTP 允许仅单向传输的文件。

* FTP 提供身份验证。而TFTP 不。

## vsftpd

## tftp

### 安装

```sh
$ sudo apt install -y tftp tftpd
$ sudo apt install -y tftp-hpa tftpd-hpa     (升级版)
```

> 要注意 tftp 和 tftp-hpa 之间存在冲突，不能一起装。

### 配置tftpd-hpa

```shell
$ sudo cp /etc/default/tftpd-hpa /etc/default/tftpd-hpa-bak
$ sudo vim /etc/default/tftpd-hpa
```

文件修改如下：

```txt
# /etc/default/tftpd-hpa

TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/opt/tftp"          # tftpd-hpa服务目录
TFTP_ADDRESS=":69"
TFTP_OPTIONS="-l -c -s"             # 这里是选项,-c是可以上传文件的参数，-s是指定tftpd-hpa服务目录，上面已经指定
```

### 开启、停止、重启

```sh
$ sudo service tftpd-hpa restart/start/stop/status
```
> 记住，每次修改完配置文件后，都需要重新启动一下服务。

### 查看

```sh
  $ tftp 192.168.1.119
  $ tftp>get uImage
  $ tftp>quit
```

## 自动启动服务tftp服务

### openbsd-inetd

### xinetd

#### 安装

```sh
$ sudo apt install -y xinetd                 (网络守护进程)
```

#### 设置xinetd

```sh
$ sudo vim /etc/xinetd.conf
```

确保该文件设置如下：

```txt
# Simple configuration file for xinetd
#
# Some defaults, and include /etc/xinetd.d/

defaults
{

# Please note that you need a log_type line to be able to use log_on_success
# and log_on_failure. The default is the following :
# log_type = SYSLOG daemon info

}

includedir /etc/xinetd.d
```

#### 配置tftp

```
$ sudo vim /etc/xinetd.d/tftp

service tftp
{
	socket_type = dgram
	wait = yes
	disable = no
	user = root
	protocol = udp
	server = /usr/sbin/in.tftpd
	server_args = -s /opt/tftp             # 设置服务目录
	log_on_success += PID HOST DURATION
	log_on_failure += HOST
	per_source = 11
	cps =100 2
	flags =IPv4
}

```

#### 开启、停止、重启

```sh
$ sudo service xinetd restart/start/stop/status
```
> 记住，每次修改完配置文件后，都需要重新启动一下服务。

