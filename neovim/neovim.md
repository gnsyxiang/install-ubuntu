# install neovim

<!-- vim-markdown-toc GFM -->

* [安装](#安装)
  - [安装](#安装-1)
  - [检查`checkhealth`](#检查checkhealth)
* [安装`neovim`相关依赖](#安装neovim相关依赖)
  - [`Configuration`](#configuration)
  - [Python 2 provider (optional)](#python-2-provider-optional)
  - [`Python 3 provider (optional)`](#python-3-provider-optional)
  - [`Ruby provider (optional)`](#ruby-provider-optional)
  - [`Node.js provider (optional)`](#nodejs-provider-optional)
  - [Node.js provider (optional)](#nodejs-provider-optional-1)
  - [Require msgpack 1.0.0+ was not successful](#require-msgpack-100-was-not-successful)
* [验证`checkhealth`](#验证checkhealth)

<!-- vim-markdown-toc -->

## 安装

### 安装

```
$ sudo apt install -y neovim
$ sudo apt install -y vim-gtk3
```

### 检查`checkhealth`

```txt
health#nvim#check
========================================================================
## Configuration
  - WARNING: Missing user config file: /home/uos/.config/nvim/init.vim
    - ADVICE:
      - :help init.vim
  - ERROR: shada file is not readable:
    /home/uos/.local/share/nvim/shada/main.shada

## Performance
  - OK: Build type: Release

## Remote Plugins
  - OK: Up to date

## terminal
  - INFO: key_backspace (kbs) terminfo entry: key_backspace=\177
  - INFO: key_dc (kdch1) terminfo entry: key_dc=\E[3~
  - INFO: $VTE_VERSION='6003'
  - INFO: $COLORTERM='truecolor'

health#provider#check
========================================================================
## Clipboard (optional)
  - OK: Clipboard tool found: xclip

## Python 2 provider (optional)
  - WARNING: No Python executable found that can `import neovim`. Using the first available executable for diagnostics.
  - ERROR: Python provider error:
    - ADVICE:
      - provider/pythonx: Could not load Python 2:
          python2 not found in search path or not executable.
          python2.7 not found in search path or not executable.
          python2.6 not found in search path or not executable.
          python not found in search path or not executable.
  - INFO: Executable: Not found

## Python 3 provider (optional)
  - INFO: `g:python3_host_prog` is not set.  Searching for python3 in the environment.
  - INFO: Multiple python3 executables found.  Set `g:python3_host_prog` to avoid surprises.
  - INFO: Executable: /usr/bin/python3
  - INFO: Other python executable: /bin/python3
  - INFO: Python version: 3.8.5
  - INFO: pynvim version: 0.4.1
  - WARNING: Could not contact PyPI to get latest version.
  - ERROR: HTTP request failed: error: missing `curl` and `python`, cannot make web request

## Ruby provider (optional)
  - WARNING: `ruby` and `gem` must be in $PATH.
    - ADVICE:
      - Install Ruby and verify that `ruby` and `gem` commands work.

## Node.js provider (optional)
  - WARNING: `node` and `npm` (or `yarn`) must be in $PATH.
    - ADVICE:
      - Install Node.js and verify that `node` and `npm` (or `yarn`) commands work.
```

## 安装`neovim`相关依赖

### `Configuration`

```txt
## Configuration
  - WARNING: Missing user config file: /home/uos/.config/nvim/init.vim
    - ADVICE:
      - :help init.vim
  - ERROR: shada file is not readable:
    /home/uos/.local/share/nvim/shada/main.shada
```

这个不需要处理，第二次启动时就会消失


### Python 2 provider (optional)

```txt
## Python 2 provider (optional)
  - WARNING: No Python executable found that can `import neovim`. Using the first available executable for diagnostics.
  - ERROR: Python provider error:
    - ADVICE:
      - provider/pythonx: Could not load Python 2:
          python2 not found in search path or not executable.
          python2.7 not found in search path or not executable.
          python2.6 not found in search path or not executable.
          python not found in search path or not executable.
  - INFO: Executable: Not found
```

不需要处理，python2已经慢慢在弃用了

### `Python 3 provider (optional)`

```txt
## Python 3 provider (optional)
  - INFO: `g:python3_host_prog` is not set.  Searching for python3 in the environment.
  - INFO: Multiple python3 executables found.  Set `g:python3_host_prog` to avoid surprises.
  - INFO: Executable: /usr/bin/python3
  - INFO: Other python executable: /bin/python3
  - INFO: Python version: 3.8.5
  - INFO: pynvim version: 0.4.1
  - WARNING: Could not contact PyPI to get latest version.
  - ERROR: HTTP request failed: error: missing `curl` and `python`, cannot make web request
```

安装`curl`和`python`

```
$ sudo apt install -y curl
$ sudo update-alternatives --install /usr/bin/python python /usr/bin/python3 300
```

```txt
## Python 3 provider (optional)
  - INFO: `g:python3_host_prog` is not set.  Searching for python3 in the environment.
  - INFO: Multiple python3 executables found.  Set `g:python3_host_prog` to avoid surprises.
  - INFO: Executable: /usr/bin/python3
  - INFO: Other python executable: /bin/python3
  - INFO: Python version: 3.8.5
  - INFO: pynvim version: 0.4.1 (outdated; from /usr/lib/python3/dist-packages/neovim)
  - WARNING: Latest pynvim is NOT installed: 0.4.3
```

安装`pynvim`

```
$ sudo apt install -y python3-pip
$ pip3 install --upgrade pynvim
```

### `Ruby provider (optional)`

```txt
## Ruby provider (optional)
  - WARNING: `ruby` and `gem` must be in $PATH.
    - ADVICE:
      - Install Ruby and verify that `ruby` and `gem` commands work.
```

```shell 
$ sudo apt install -y ruby-dev
```

```txt
## Ruby provider (optional)
  - INFO: Ruby: ruby 2.7.0p0 (2019-12-25 revision 647ee6f091) [x86_64-linux-gnu]
  - WARNING: `neovim-ruby-host` not found.
    - ADVICE:
      - Run `gem install neovim` to ensure the neovim RubyGem is installed.
      - Run `gem environment` to ensure the gem bin directory is in $PATH.
      - If you are using rvm/rbenv/chruby, try "rehashing".
      - See :help g:ruby_host_prog for non-standard gem installations.
```


```shell
$ sudo gem install neovim
```

### `Node.js provider (optional)`

```txt
## Node.js provider (optional)
  - WARNING: `node` and `npm` (or `yarn`) must be in $PATH.
    - ADVICE:
      - Install Node.js and verify that `node` and `npm` (or `yarn`) commands work.
```

> 安装npm和yarm，参考对应文档


### Node.js provider (optional)

```txt
## Node.js provider (optional)
  - INFO: Node.js: v10.19.0
  - WARNING: Missing "neovim" npm (or yarn) package.
    - ADVICE:
      - Run in shell: npm install -g neovim
      - Run in shell (if you use yarn): yarn global add neovim
```

```shell
$ sudo npm install -g neovim
```
### Require msgpack 1.0.0+ was not successful

```txt
health#denite#check
========================================================================
## denite.nvim
  - OK: has("python3") was successful
  - OK: Python 3.6.1+ was successful
  - ERROR: Require msgpack 1.0.0+ was not successful
    - ADVICE:
      - Please install/upgrade msgpack 1.0.0+.
```

```shell
$ python3 -mpip install --user -U msgpack
```

## 验证`checkhealth`

```txt
health#nvim#check
========================================================================
## Configuration
  - WARNING: Missing user config file: /home/uos/.config/nvim/init.vim
    - ADVICE:
      - :help |init.vim|

## Performance
  - OK: Build type: Release

## Remote Plugins
  - OK: Up to date

## terminal
  - INFO: key_backspace (kbs) terminfo entry: key_backspace=\177
  - INFO: key_dc (kdch1) terminfo entry: key_dc=\E[3~
  - INFO: $VTE_VERSION='6003'
  - INFO: $COLORTERM='truecolor'

health#provider#check
========================================================================
## Clipboard (optional)
  - OK: Clipboard tool found: xclip

## Python 2 provider (optional)
  - WARNING: No Python executable found that can `import neovim`. Using the first available executable for diagnostics.
  - ERROR: Python provider error:
    - ADVICE:
      - provider/pythonx: Could not load Python 2:
          /usr/bin/python2 does not have the "neovim" module. :help |provider-python|
          /usr/bin/python2.7 does not have the "neovim" module. :help |provider-python|
          python2.6 not found in search path or not executable.
          /usr/bin/python is Python 3.8 and cannot provide Python 2.
  - INFO: Executable: Not found

## Python 3 provider (optional)
  - INFO: `g:python3_host_prog` is not set.  Searching for python3 in the environment.
  - INFO: Multiple python3 executables found.  Set `g:python3_host_prog` to avoid surprises.
  - INFO: Executable: /usr/bin/python3
  - INFO: Other python executable: /bin/python3
  - INFO: Python version: 3.8.5
  - INFO: pynvim version: 0.4.3
  - OK: Latest pynvim is installed.

## Ruby provider (optional)
  - INFO: Ruby: ruby 2.7.0p0 (2019-12-25 revision 647ee6f091) [x86_64-linux-gnu]
  - INFO: Host: /usr/local/bin/neovim-ruby-host
  - OK: Latest "neovim" gem is installed: 0.8.1

## Node.js provider (optional)
  - INFO: Node.js: v10.19.0
  - INFO: Neovim node.js host: /usr/local/lib/node_modules/neovim/bin/cli.js
  - OK: Latest "neovim" npm/yarn package is installed: 4.9.0
```

