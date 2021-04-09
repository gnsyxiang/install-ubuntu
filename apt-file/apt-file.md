# apt-file

<!-- vim-markdown-toc GFM -->

* [install](#install)
  - [安装](#安装)
  - [更新软件包的文件库](#更新软件包的文件库)
  - [查找缺失的包](#查找缺失的包)
* [使用](#使用)
  - [查找需要包](#查找需要包)

<!-- vim-markdown-toc -->

apt-file 是一个命令行界面的`APT`包搜索工具。当我们在编译源代码时，时有缺少文件的情况发生。此时，通过`apt-file`就可以找出该缺失文件所在的包，然后将缺失的包安装后即可让编译顺利进行了。

## install

### 安装

```sh
$ sudo apt install -y apt-file
```

### 更新软件包的文件库

```sh
$ sudo apt-file update
```
> 注意: 第一次使用,执行apt update和修改了 sources.list，仍需执行该操作。

### 查找缺失的包

```sh
$ apt-file search 文件名
eg:
apt-file search xxx/xxx.h
apt-file search libxxx.so
```
> 根据显示的搜索结果，你可以判断哪些包是需要的。查找该文件存在于哪些软件包中。

* 列出包中的文件

```sh
    $ apt-file list 包名称
```

  可以列出包中所含的文件。

## 使用

### 查找需要包

* 当你第一次使用 apt-file serch makeinfo 出现如下：

```txt
  The program 'apt-file' is currently not installed.
  You can install it by typing:
  sudo apt-get install apt-file
```

* 再次使用：apt-file search makeinfo 出现如：

```txt
  E: The cache is empty. You need to run 'apt-file update' first.
```

* 输入如下：sudo apt-file update 出现如下：

```txt
  ...
  texinfo: /usr/bin/makeinfo
  ...
```

