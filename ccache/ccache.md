# ccache


<!-- vim-markdown-toc GFM -->

* [安装](#安装)
* [配置](#配置)
* [使用](#使用)

<!-- vim-markdown-toc -->

`ccache`（`compiler cache`的缩写）是一个编译器缓存，该工具会高速缓存编译生成的信息，并在编译的特定部分使用高速缓存的信息，比如头文件，这样就节省了通常使用`cpp`解析这些信息所需要的时间。如果您编译清单 2 中的文件，假定 foobar.h 中包含对其他头文件的引用，ccache 会用那个文件的 cpp-parsed 版本来 取代 include 声明。就那么简单。不是真正去读取、理解并解释其内容，ccache 只是 将最终的文本拷贝到文件中，使得它可以立即被编译。

第一次编译时`ccache`缓存了`gcc -E`输出、编译选项以及.o文件到`$HOME/.ccache`。第二次编译时尽量利用缓存，必要时更新缓存。

URL: [官网地址](https://ccache.dev/) 
URL: [Manual](https://ccache.dev/manual/4.2.1.html)

## 安装

```shell
$ sudo apt install -y ccache
```

## 配置

## 使用

