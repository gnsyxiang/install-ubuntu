# nfs

<!-- vim-markdown-toc GFM -->

* [安装服务端](#安装服务端)
  - [安装](#安装)
  - [修改配置文件](#修改配置文件)
  - [创建挂载目录](#创建挂载目录)
  - [重启服务端](#重启服务端)
* [安装客户端](#安装客户端)
  - [安装](#安装-1)
  - [挂载远程目录](#挂载远程目录)
  - [取消挂载点](#取消挂载点)
* [嵌入式设备](#嵌入式设备)
  - [配置内核支持NFS](#配置内核支持nfs)

<!-- vim-markdown-toc -->

## 安装服务端

### 安装

```shell
$ sudo apt update
$ sudo apt install -y nfs-kernel-server
```

### 修改配置文件

```shell
$ sudo cp /etc/exports /etc/exports-bak
$ sudo vim /etc/exports 

/opt/nfs 192.168.1.*(rw,async,no_root_squash) 

/opt/filesystem     #目标系统的根文件系统最后映射的路径
*:                  #所有IP都可以和我相连，也可以用某一个具体IP替换
subtree_check:      #子目录权限检查
rw:                 #数据具有写权限
no_root_squash:     #当访问这个目录，具有root权限
async:              #动态同步
```

### 创建挂载目录

```shell
$ mkdir /opt/nfs
$ chmod 777 /opt/nfs
```

### 重启服务端

```
$ sudo systemctl restart nfs-kernel-server
```

## 安装客户端

### 安装

```
$ sudo apt install nfs-common
```

### 挂载远程目录

```shell
$ mount -t nfs -o nolock 192.168.1.137:/opt/nfs /mnt/sdcard/

192.168.1.137       被挂载点ip地址
/opt/nfs            被挂载的目录
/mnt/sdcard/        挂载点
-t nfs              固定选项
```

### 取消挂载点  

```txt
$ umount -t nfs 192.168.1.137:/opt/nfs /mnt/sdcard/
```

## 嵌入式设备

### 配置内核支持NFS  

```txt
    File systems  --->
        Network File Systems  --->
        [*]   NFS client support                 ## 必选
        [*]     NFS client support for NFS version 3   ## 可选

        [*] Root file system on NFS        ## 必选

    [*] Networking support
        Networking options  --->
            [*]   IP: kernel level autoconfiguration       ## 必选
                [*]     IP: DHCP support                   ## 必选
                [*]     IP: BOOTP support                  ## 必选
                [*]     IP: RARP support                   ## 必选
```

> 注意： NFS Client Support不能是模块，必须编译进内核

