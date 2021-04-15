# restore_sys_env

<!-- vim-markdown-toc GFM -->

* [恢复`apt`相关信息](#恢复apt相关信息)
  - [恢复`apt`目录到系统中](#恢复apt目录到系统中)
  - [恢复`deb`目录到系统中](#恢复deb目录到系统中)
* [恢复`npm`相关信息](#恢复npm相关信息)
  - [恢复`node_modules`目录到系统中](#恢复node_modules目录到系统中)
* [恢复`python`相关信息](#恢复python相关信息)
  - [恢复`python3.8`目录到系统中](#恢复python38目录到系统中)
* [恢复`vim`相关信息](#恢复vim相关信息)
  - [恢复`SpaceVim`到`neovim`中](#恢复spacevim到neovim中)
  - [恢复`vimfiles`目录到系统中](#恢复vimfiles目录到系统中)
  - [恢复`coc`目录到系统中](#恢复coc目录到系统中)
* [恢复`toolchains`到系统中](#恢复toolchains到系统中)
* [恢复`dotfile`中的配置到系统中](#恢复dotfile中的配置到系统中)
* [把用户添加的命令放到`PATH`搜索目录中](#把用户添加的命令放到path搜索目录中)

<!-- vim-markdown-toc -->

## 恢复`apt`相关信息

### 恢复`apt`目录到系统中

```shell
$ sudo ln -s ~/data/opt/apt-ubuntu20.04 /etc/apt
```

### 恢复`deb`目录到系统中

```shell
$ ln -s ~/data/opt/archives /var/cache/apt/archives
```

> 加快换系统时`sudo apt upgrade`的速度

## 恢复`npm`相关信息

### 恢复`node_modules`目录到系统中

```shell
$ ln -s ~/data/opt/node_modules /usr/local/lib/node_modules
```

> 加快`npm install -g xxx`的速度

## 恢复`python`相关信息

### 恢复`python3.8`目录到系统中

```shell
$ ln -s ~/data/opt/python3.8 ~/.local/lib/python3.8
```

## 恢复`vim`相关信息

### 恢复`SpaceVim`到`neovim`中

```shell
$ ln -s ~/data/opt/SpaceVim ~/.config/neovim
```

### 恢复`vimfiles`目录到系统中

```shell
$ ln -s ~/data/opt/vimfiles ~/.cache/vimfiles
```

### 恢复`coc`目录到系统中

```shell
$ ln -s ~/data/opt/coc ~/.config/coc
```

## 恢复`toolchains`到系统中

```shell
$ ln -s ~/data/opt/toolchains /opt/toolchains
```

> 避免重新拷贝相关工具链

## 恢复`dotfile`中的配置到系统中

* 创建`dotfiles`链接文件

```shell
$ ln -s ~/data/opt/dotfiles .dotfiles
```

* 通过`rcm`来恢复系统相关配置

```shell
$ rcup -v -t ubuntu
```

* 验证环境是否恢复成功，可以在`HOME`目录下查看是否有相关软链接建立


## 把用户添加的命令放到`PATH`搜索目录中

```shell
$ vim .bashrc

# xia add
if [ -f ~/.export_variables ]; then
    . ~/.export_variables
fi
```

> 添加到当前使用的shell中

