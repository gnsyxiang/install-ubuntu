# yarn


<!-- vim-markdown-toc Marked -->

- [安装](#安装)
  - [添加apt软件源](#添加apt软件源)
  - [安装](#安装)
  - [检测](#检测)
- [使用](#使用)
  - [创建工程](#创建工程)
  - [添加依赖](#添加依赖)
  - [升级依赖](#升级依赖)
  - [移除依赖](#移除依赖)
  - [安装所有项目依赖](#安装所有项目依赖)

<!-- vim-markdown-toc -->

官网[yarn](https://classic.yarnpkg.com/lang/en/)


`yarn`是一个`JavaScript`包管理器，它兼容于`npm`，
可以帮助你自动处理安装，升级，配置，和移除`npm`包。
它被创建，用于解决`npm`的一系列问题，
例如通过并行操作提高软件包安装处理速度并且减少网络连接相关的错误。

## 安装

### 添加apt软件源

```
$ curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
$ echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
```

### 安装

```
$ sudo apt update
$ sudo apt install yarn
$ sudo apt install --no-install-recommends yarn     // 跳过node.js安装，因为npm中已经安装了
```

### 检测

```
$ yarn --version
1.22.5
```

### 设置镜像加速源

```
$ yarn config set registry https://registry.npm.taobao.org/
$ yarn config get registry
```

## 使用

```
$ yarn --help
```

### 创建工程

```
$ yarn init demo
```

### 添加依赖

```
$ yarn add xxx              // 更新package.json和yarn.lock文件
$ yarn add xxx@version      // 安装指定版本
```

### 升级依赖

```
$ yarn upgrade              // package.json指定的版本范围
$ yarn upgrade xxx
$ yarn upgrade xxx@version
```

### 移除依赖

```
$ yarn remove xxx           // 升级项目的package.json和yarn.lock文件
```

### 安装所有项目依赖

```
$ yarn
$ yarn install
```



