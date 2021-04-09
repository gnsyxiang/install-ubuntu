# install

<!-- vim-markdown-toc GFM -->

* [安装输入法](#安装输入法)
  - [下载](#下载)
  - [安装](#安装)
* [problem](#problem)
  - [不能输入中文](#不能输入中文)

<!-- vim-markdown-toc -->

## 安装输入法

### 下载

website: http://pinyin.sogou.com/linux/

下载好安装包

### 安装

```sh
$ sudo dpkg -i sogoupinyin_2.1.0.0086_amd64.deb
$ sudo apt install -f
```

> 注意: 配置完成后需要注销，重新登入后才可以使用搜狗输入法

## problem

### 不能输入中文

* 方法一： 重启输入法

```sh
$ killall fcitx
$ killall sogou-qinpanel
$ fcitx
```

* 方法二： 查看是否时候缺少依赖文件

```sh
$ sudo apt install -f
```

* 方法三：删除配置文件

```sh
$ rm ~/.config/SogouPY -rf
$ rm ~/.config/SogouPY.users -rf
$ rm ~/.config/sogou-qimpanel -rf
```

