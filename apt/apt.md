# apt

<!-- vim-markdown-toc GFM -->

* [替换系统源](#替换系统源)
* [problem](#problem)
  - [获取不到锁](#获取不到锁)

<!-- vim-markdown-toc -->

## 替换系统源

* 备份原来的源

```shell
$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

* 更换指定的系统源

```shell
$ sudo vim /etc/apt/sources.list
```

> 较快的国内系统源： 清华，阿里，华为等

* 更新系统

```shell
$ sudo apt update
```


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

