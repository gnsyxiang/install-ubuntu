# mount data disk

## 挂载数据盘

### 查看数据盘UUID

```shell
$ sudo blkid
/dev/sda5: UUID="xxx" TYPE="ext4" PARTUUID="xxx"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: UUID="xxx" TYPE="vfat" PARTUUID="xxx"
/dev/sdb5: UUID="xxx" TYPE="ext4" PARTUUID="xxx"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
```

### 设置开机自动挂载

```shell
$ sudo vim /etc/fstab
 UUID="xxx"    /data_path     ext4     defaults       0 0
```

> uuid: 用上面命令显示的，本机是sdb5
>
> data_path: 用户指定挂载点，本机是~/data


