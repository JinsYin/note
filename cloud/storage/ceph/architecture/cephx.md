# Cephx 身份认证系统

```c
+--------+                      +---------+
| Client |                      | Monitor |
+--------+                      +---------+
    |    request to create a user    |
    |------------------------------->|--------+ create user
    |                                |        | and
    |<-------------------------------|<-------+ store key
    |          transmit key          |
```

* 为了使用 cephx，管理员必须首先设置用户
* `client.admin` 用户从命令行调用 `ceph auth get-or-create-key` 以生成用户名和密钥
* Ceph 的认证子系统生成用户名和密钥，与监视器一同存储副本，并将用户密钥发送回 `client.admin` 用户，意味着客户端和 Monitor 共享一个密钥

```c
+--------+                       +---------+
| Client |                       | Monitor |
+--------+                       +---------+
    |         authenticate           |
    |------------------------------->|--------+ generate and
    |                                |        | encrypt
    |<-------------------------------|<-------+ session key
    | transmit encrypted session key |
    |                                |
    |--------+ decrypt               |
    |        | session               |
    |<-------+ key                   |
    |                                |
    |          req.ticket            |
    |------------------------------->|--------+ generate and
    |                                |        | encrypt
    |<-------------------------------|--------+ ticket
    |          recv.ticket           |
    |                                |
    |--------+                       |
    |        | decrypt tick          |
    |<-------+                       |
```

* 要通过 Monitor 进行身份验证，客户端会将用户名传递给 Monitor，Monitor 会生成会话密钥并使用

```c
+--------+                       +---------+                        +-----+            +-----+
| Client |                       | Monitor |                        | MDS |            | OSD |
+--------+                       +---------+                        +-----+            +-----+
    |     request to create a user   |                                 |                  |
    |------------------------------->|                                 |                  |
    |<-------------------------------|                                 |                  |
    |     receive shared secret      | mon and client share a secret   |                  |
    |                                |<------------------------------->|                  |
    |                                |<-------------------------------------------------->|
    |                                | mon, mds and osd share a secret |                  |
    |          authenticate          |                                 |                  |
    |------------------------------->|                                 |                  |
    |<-------------------------------|                                 |                  |
    |          ression key           |                                 |                  |
    |                                |                                 |                  |
    |           req.ticket           |                                 |                  |
    |------------------------------->|                                 |                  |
    |<-------------------------------|                                 |                  |
    |           recv.ticket          |                                 |                  |
    |                                |                                 |                  |
    |                       make request (CephFS only)                 |                  |
    |----------------------------------------------------------------->|                  |
    |<-----------------------------------------------------------------|                  |
    |                     receive response (CephFs only)                                  |
    |                                                                                     |
    |                                  make request                                       |
    |------------------------------------------------------------------------------------>|
    |<------------------------------------------------------------------------------------|
    |                                receive response                                     |
```

## 参考