# UNetbootin

Ubuntu 下使用 UNetbootin 刻录 U 盘启动系统。

## 安装

```sh
$ sudo add-apt-repository ppa:gezakovacs/ppa
$ sudo apt-get update
$ sudo apt-get install -y unetbootin
```

## 格式化 U 盘

假设 U 盘是 /dev/sdc （通过 `fdisk -l` 命令进行查看）

```sh
$ umount /media/jins/66B1-FEF6 # 默认会挂载到 ubuntu (查看：df -h)，需要先卸载掉
$ mkfs.vfat -I /dev/sdc # 格式化整个盘为 fat32 格式（不需要分区）
$ mkdir /sdc && mount /dev/sdc /sdc ## 重新挂载
```

## 烧录

启动 UNetbootin 后选择 ISO 文件、指定 U 盘后即可刻录。

```sh
$ unetbootin
```
