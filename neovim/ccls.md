# ccls

<!-- vim-markdown-toc GFM -->

* [介绍](#介绍)
* [安装](#安装)
* [使用](#使用)
  - [生成`compile_commands.json`](#生成compile_commandsjson)

<!-- vim-markdown-toc -->

## 介绍

## 安装

```shell
$ sudo apt install -y ccls
$ ccls --version
ccls version 0.20190823.6-1~ubuntu1.20.04.1
clang version 10.0.0-4ubuntu1
```

## 使用

### 生成`compile_commands.json`

* `linux`内核使用自带的脚本`scripts/clang-tools/gen_compile_commands.py`，这样的话就不用更改一次`.config`就重新编译整个内核。
* 用`Makefile`的用`bear`来生成
```shell
$ bear make
```
* cmake工程

```shell
$ cmake -H. -BDebug -DCMAKE_BUILD_TYPE=Debug -DCMAKE_EXPORT_COMPILE_COMMANDS=YES
$ ln -s Debug/compile_commands.json .
```

* [更多请参考](https://github.com/MaskRay/ccls/wiki/Project-Setup) 

