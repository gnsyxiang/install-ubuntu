# mount data disk

## 硬盘分区

### 显示硬盘及分区情况

```shell
sudo fdisk -l
```

### 对硬盘进行分区

```shell
sudo fdisk /dev/sde


Welcome to fdisk (util-linux 2.34).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

The old ext4 signature will be removed by a write command.

Device does not contain a recognized partition table.
Created a new DOS disklabel with disk identifier 0xd7530861.

Command (m for help): n
Partition type
   p   primary (0 primary, 0 extended, 4 free)
   e   extended (container for logical partitions)
Select (default p): e
Partition number (1-4, default 1): 
First sector (2048-104857599, default 2048): 
Last sector, +/-sectors or +/-size{K,M,G,T,P} (2048-104857599, default 104857599): 

Created a new partition 1 of type 'Extended' and of size 50 GiB.

Command (m for help): w
The partition table has been altered.
Calling ioctl() to re-read partition table.
Syncing disks.

n 新建分区
e 选择扩展分区
w 保存分区设置
```

### 对硬盘格式化

```shell
sudo mkfs -t ext4 /dev/sde

mke2fs 1.45.5 (07-Jan-2020)
Found a dos partition table in /dev/sde
Proceed anyway? (y,N) y
Creating filesystem with 13107200 4k blocks and 3276800 inodes
Filesystem UUID: a07e54b4-c0b6-443b-bb21-cf8f71e2db12
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (65536 blocks): done
Writing superblocks and filesystem accounting information: done
```

## 挂载数据盘

### 手动挂载

```shell
sudo mount -t ext4 /dev/sde /mnt/data

ls data
lost+found
```

### 系统自动挂载

#### 查看数据盘UUID

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


