# uptime

显示系统运行时长

## 分析

```sh
$ uptime
15:06:20 up 32 days,  4:09,  1 user,  load average: 0.00, 0.08, 0.11
```

* `15:06:20` - 当前系统时间
* `up 32 days,  4:09` - 系统运行时长（32d + 4h + 9m）
* `1 user` - 登录用户数
* `load average: 0.00, 0.08, 0.11` - 系统过去 1 分钟、5 分钟、15 分钟的平均负责

## PROC

* /proc/uptime

```sh
$ cat /proc/uptime
94102.25 271291.01
```

* /proc/loadavg

```sh
$ cat /proc/loadavg
2.60 2.22 2.01 2/1853 2135182
```

## 检查系统重启历史

```sh
$ last reboot
reboot   system boot  3.10.0-862.el7.x Fri Nov  2 10:56 - 15:13 (32+04:16)
reboot   system boot  3.10.0-862.el7.x Thu Nov  1 17:33 - 10:50  (17:17)
reboot   system boot  3.10.0-862.el7.x Thu Nov  1 17:27 - 17:27  (00:00)
reboot   system boot  3.10.0-862.el7.x Thu Nov  1 15:17 - 17:27  (02:10)
reboot   system boot  3.10.0-862.el7.x Thu Nov  1 15:14 - 17:27  (02:13)
reboot   system boot  3.10.0-862.el7.x Thu Nov  1 14:54 - 17:27  (02:33)
reboot   system boot  3.10.0-862.el7.x Thu Nov  1 14:11 - 14:16  (00:04)
reboot   system boot  3.10.0-862.el7.x Mon Oct 15 14:26 - 13:59 (16+23:33)
reboot   system boot  3.10.0-862.el7.x Mon Oct 15 09:17 - 13:59 (17+04:42)
reboot   system boot  3.10.0-862.el7.x Sun Sep 30 17:21 - 18:05 (12+00:44)
```
