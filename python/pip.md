# pip

[pip · PyPI](https://pypi.org/project/pip/)

[pip documentation](https://pip.pypa.io/en/stable/)

## 介绍

* `pip`是一个用来安装`Python`软件包的工具
* 通过`pip`可以从`python`软件包索引(`PyPi`)和其他软件包索引中搜索，下载并安装软件
* 查找软件包的相关信息和依赖

## 安装

> 仅仅在没有模块对应的`deb`包的情况下，才使用`pip`来全局安装一个模块。

### 为`python3`安装`pip`

```
$ sudo apt update
$ sudo apt install python3-pip
```

```
$ pip3 --version
pip 20.0.2 from /usr/lib/python3/dist-packages/pip (python 3.8)
```

### 为`python2`安装`pip`


## 使用

```
$ pip3 --help
```

### 安装软件包

```
$ pip3 install xxx          // 安装最新版本
$ pip3 install xxx==1.5     // 安装制定版本
```

### 列出安装的软件包

```
$ pip3 list
```

### 升级软件包

```
$ pip3 install --upgrade xxx
```


### 卸载软件包

```
$ pip3 uninstall xxx
```

