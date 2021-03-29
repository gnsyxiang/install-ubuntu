# npm

安装包管理和分发工具

## 安装

```
$ sudo apt install -y npm
```

## 镜像源

```
$ npm config set registry https://registry.npm.taobao.org
$ npm config get registry
```

## 配置文件

```
$ npm config get userconfig     ## 查看配置文件路径，
$ npm config ls -l              ##　查看所有配置项
$ npm config get cache          ## 查看缓存配置，get后面可以跟任意配置项
$ npm config edit               ## 直接编辑config文件，这个会打开文本
```

## 安装软件包

* 全局安装

> 将安装包放在 /usr/local 下或者你 node 的安装目录。
> 可以直接在命令行里使用。

```
sudo npm -g install xxx
```

* 本地安装

> 将安装包放在 ./node_modules 下（运行 npm 命令时所在的目录），如果没有 node_modules 目录，会在当前执行 npm 命令的目录下生成 node_modules 目录。
> 可以通过 require() 来引入本地安装的包。

```
$ npm install xxx
```

### 升级npm

```
$ sudo npm -g install npm
$ sudo npm -g install npm@latest
```


#### 安装n

* 安装
```
$ sudo npm -g install n
```

* 切换版本

```
$ sudo n latest
$ sudo n stable
$ sudo n lts
```

```
$sudo n lts
  installing : node-v14.16.0
       mkdir : /usr/local/n/versions/node/14.16.0
       fetch : https://nodejs.org/dist/v14.16.0/node-v14.16.0-linux-x64.tar.xz
   installed : v14.16.0 (with npm 6.14.11)

Note: the node command changed location and the old location may be remembered in your current shell.
         old : /usr/bin/node
         new : /usr/local/bin/node
To reset the command location hash either start a new shell, or execute PATH="$PATH"
```

出现如上提示，无需处理，只需要重启一个新的`shell`终端即可。
通过下面可以说明优先使用更新后的node(`/usr/local/bin`)，如上是提醒当前使用终端的node可能是`/usr/bin/node`

```
$ which node
/usr/local/bin/node
$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
```

## 查看版本

```
$ npm -v
$ node -v
```


