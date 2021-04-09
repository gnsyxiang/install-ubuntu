# install gitbook


## 安装

### 检查node环境

```shell
$ node --version
v10.19.0
```

### 安装

```shell
$ sudo npm install -g gitbook-cli
```

### 检查是否安装成功

```shell
$ gitbook --version
CLI version: 2.3.2
GitBook version: 3.2.3
```

> 首次执行上面的代码时会安装`gitbook`，这一步很慢，大概需要20分钟左右

### demo

```txt
    $ mkdir demo
    $ demo
    $ touch README.md		//一本书的简介
    $ touch SUNNARY.md		//一本书的目录结构

    $ vim SUNNARY.md
	  * [简介](README.md)
	  * [第一章](chapter1/README.md)
	   - [第一节](chapter1/section1.md)
	   - [第二节](chapter1/section2.md)
	  * [第二章](chapter2/README.md)
	   - [第一节](chapter2/section1.md)
	   - [第二节](chapter2/section2.md)
	  * [结束](end/README.md)

    $ gitbook init      //生成README.md和SUMMARY.md两个文件

    $ gitbook serve		//在浏览器中查看
    $ gitbook build     //生成网页
    $ gitbook pdf       //生成pdf
```

### common commands

```txt
  * gitbook init		        //初始化目录文件
  * gitbook help  	            //列出gitbook所有的命令
  * gitbook --help 	            //输出gitbook-cli的帮助信息
  * gitbook build 	            //生成静态网页
  * gitbook serve 	            //生成静态网页并运行服务器
  * gitbook build --gitbook=2.0.1 //生成时指定gitbook的版本, 本地没有会先下载
  * gitbook ls 		            //列出本地所有的gitbook版本
  * gitbook ls-remote           //列出远程可用的gitbook版本
  * gitbook fetch 标签/版本号   //安装对应的gitbook版本
  * gitbook update 	            //更新到gitbook的最新版本
  * gitbook uninstall 2.0.1     //卸载对应的gitbook版本
  * gitbook build --log=debug   //指定log的级别
  * gitbook builid --debug      //输出错误信息
```


## see tutorial

* [GitBook 中文解說 - 2.4](https://wastemobile.gitbooks.io/gitbook-chinese/content/format/output.html)
* [GitBook 文档](https://www.gitbook.com/book/zhanghqgit/gitbook-documentation/details)
* [GitBook文档（中文版）](https://www.gitbook.com/book/chestnutme/gitbook-documentation/details)

