# rcm

## 安装

### mac安装

```shell
$ brew tap thoughtbot/formulae
$ brew install rcm
```

### ubuntu安装

```shell
$ wget -qO - https://apt.thoughtbot.com/thoughtbot.gpg.key | sudo apt-key add -
$ echo "deb https://apt.thoughtbot.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/thoughtbot.list
$ sudo apt-get update
$ sudo apt-get install rcm
```

## 使用

### mkrc

```shell
$ mkrc -v .gitconfig
$ mkrc -v -t ubuntu .gitconfig
```

> note: 把家目录下的`.gitconfig`移动到`~/dotfiles/gitconfig`，同时建立软链接文件
>
> 管理的文件可以是目录，在`dotfiles`目录与原目录一致
>
> 按照tag来管理配置文件，会生成`tag-ubuntu`目录

## rcup

```shell
$ rcup -v
$ rcup -t test
```

> note: 把`mkrc`没有带参数的保存的文件全部恢复
>
> note: 把`tag-test`目录下的配置文件恢复



