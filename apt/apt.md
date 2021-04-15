# apt

<!-- vim-markdown-toc GFM -->

* [查看系统的`codename`](#查看系统的codename)
* [选择源](#选择源)
* [替换系统源](#替换系统源)
* [`apt install`安装的目录](#apt-install安装的目录)
* [problem](#problem)
  - [获取不到锁](#获取不到锁)

<!-- vim-markdown-toc -->

## 查看系统的`codename`

```shell
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.2 LTS
Release:	20.04
Codename:	focal
```

## 选择源

* 可以选择清华源，华为源，阿里源等

* 通过网络来判断

```shell
$ ping mirrors.tuna.tsinghua.edu.cn
$ ping mirrors.aliyun.com
$ ping mirrors.huaweicloud.com
```

## 替换系统源

* 备份原来的源

```shell
$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

* 更换指定的系统源

```shell
$ sudo vim /etc/apt/sources.list
```

> 较快的国内系统源: 清华，阿里，华为等

* 更新系统

```shell
$ sudo apt update
```

## `apt install`安装的目录

映射当前系统的`deb`包到数据盘中，方便后续系统的更换

详见[`restore_sys_env`](../dotfile/restore_sys_env.md)

## problem

### 获取不到锁

```txt
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory
```

执行如下命令:

```shell
$ sudo rm /var/lib/apt/lists/lock
$ sudo rm /var/cache/apt/archives/lock
```

