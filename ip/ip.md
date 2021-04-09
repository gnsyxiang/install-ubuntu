# ip

<!-- vim-markdown-toc GFM -->

* [配置](#配置)
  - [修改网络接口配置](#修改网络接口配置)
  - [配置DNS](#配置dns)
  - [重新启动网络](#重新启动网络)
  - [测试网络](#测试网络)
  - [终端设置ip](#终端设置ip)
  - [详解ifconfig](#详解ifconfig)

<!-- vim-markdown-toc -->

## 配置

### 修改网络接口配置

```txt
  $ sudo cp /etc/network/interfaces /etc/network/interfaces.bak
  $ sudo vim /etc/network/interfaces

  在文件后面增加如下内容:
    # xia add for static IP
    auto eth0
    iface eth0 inet static
    address 192.168.1.101
    gateway 192.168.1.1
    netmask 255.255.255.0

  设定第二个IP地址(虚拟IP地址):
    auto eth0:1
    iface eth0:1 inet static
    address 192.168.1.60
    netmask 255.255.255.0
    network x.x.x.x
    broadcast x.x.x.x
    gateway x.x.x.x

  设置DHCP方式:
    # The primary network interface - use DHCP to find our address
    auto eth0
    iface eth0 inet dhcp
```

### 配置DNS

```txt
  $ sudo vim /etc/resolv.conf

  添加如下内容：

  # xia add
    nameserver 202.96.128.86
    nameserver 202.96.134.133
    nameserver 192.168.1.1

  $ sudo cp /etc/resolv.conf /etc/resolv.conf.bak
```
>注意: (默认情况下这个文件是不存在的,最多只能添加3个)

### 重新启动网络

```txt
  $ sudo /etc/init.d/networking restart
```

### 测试网络

```sh
  $ ping www.baidu.com
```

### 终端设置ip

* DHCP获取ip

```sh
  $ sudo dhclient eth0
```

* 设置IP

```sh
  $ sudo ifconfig eth0 192.168.1.103 netmask 255.255.255.0
```

* 设置网关

```sh
  $ sudo route add default gw 192.168.1.1
```

* ping 网关就可以ping通了

```sh
  $ ping 192.168.1.1
```

* 设置DNS 修改/etc/resolv.conf，在其中加入

```sh
  nameserver DNS的地址1
  nameserver DNS的地址2

```
> 注意: 这样设置之后，下次开机时候似乎IP又不存在了

### 详解ifconfig

* 作用  
  查看和配置网络接口的地址和参数，包括IP、掩码、广播地址，它的使用权限是超级用户。

* 常见参数

```txt
  interface          //指定网络接口名，如eth0和eth1
  up                 //激活指定的网络接口卡
  down               //关闭指定的网络接口卡
  broadcast address  //设置接口的广播地址
  poin to poin       //启用点对点方式
  address            //设置指定接口设备的IP地址
  netmask address    //设置接口的子网掩码
```

* 使用实例  
  查看网络的配置（所有活动的接口）

  ```sh
  $ ifconfig
  ```

  查看指定的网络接口

  ```sh
  $ ifconfig eth0
  ```

  显示所有接口（包括非活跃接口）

  ```sh
  $ ifconfig -a
  ```

  关闭指定网络接口

  ```sh
  $ ifconfig eth0 down
  ```

  开启指定网络接口

  ```sh
  $ ifconfig eth0 up
  ```

  临时设置eth0的IP地址、子网掩码，不需要重启，立即生效。重启后就会失效。

  ```sh
  $ifconfig eth0 192.168.7.119 netmask 255.255.255.0
  ```

