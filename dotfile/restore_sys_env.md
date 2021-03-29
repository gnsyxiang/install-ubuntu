# restore_sys_env

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

> 添加到使用的shell当中
