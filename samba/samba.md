# samba

## 安装服务端


### 安装
```
$ sudo apt install samba samba-common
```


### 修改配置文件

```
$ sudo cp /etc/samba/smb.conf /etc/samba/smb.conf-bak
$ sudo vim /etc/samba/smb.conf

[uos-samba]
    comment = uos-pc samba
    path = /opt
    browseable = yes
    writable = yes
    available = yes
    valid users = uos
```

### 添加`samba`用户

```
$ sudo smbpasswd -a uos
```


### 重启服务端

```
$ sudo service smbd restart
```

## 安装客户端

### 安装

```
sudo apt-get install smbclient
```

### 查看某个ip提供的samba的服务

```
$ smbclient -L 192.168.1.204
Enter WORKGROUP\uos's password: 

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	uos-samba       Disk      uos-pc samba
	IPC$            IPC       IPC Service (uos-pc server (Samba, Ubuntu))
SMB1 disabled -- no workgroup available
```

