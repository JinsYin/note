# 常用分区

| 分区  | 用途                   | 大小 |
| ----- | ---------------------- | ---- |
| /     |                        |      |
| /boot | 存储内核和其他启动信息 |      |
| /home | 用户自定义内容         |      |
| /usr  |                        | 5GB  |

任何需要在启动时自动挂载的独立分区都必须写入到 `/etc/fstab` 文件中。
