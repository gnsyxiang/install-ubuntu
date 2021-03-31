# ssh

<!-- vim-markdown-toc GFM -->

* [安装服务端](#安装服务端)
  - [安装](#安装)
  - [配置](#配置)
  - [相关操作命令](#相关操作命令)
* [安装客户端](#安装客户端)
  - [安装](#安装-1)
  - [相关操作命令](#相关操作命令-1)

<!-- vim-markdown-toc -->

## 安装服务端

### 安装
```
$ sudo apt update
$ sudo apt install -y openssh-server
```

### 配置

配置文件路劲: /etc/ssh/sshd_config

* ssh服务默认的端口是`22`，可以更改端口

```shell
ssh test@192.168.1.205 -p 3344
```

> 配置文件修改后，需要重新启动服务

### 相关操作命令

```shell
$ sudo service ssh start
$ sudo service ssh restart
$ sudo service ssh stop

$ ps -e | grep sshd
 177305 ?        00:00:00 sshd
```

## 安装客户端

### 安装
```
$ sudo apt update
$ sudo apt install -y openssh-client
```

### 相关操作命令






