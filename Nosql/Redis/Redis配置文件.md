# Redis.conf详解

启动的时候, 通过配置文件来启动!

>网络

```bash
bind 127.0.0.1
#绑定的ip
protected-mode yes #保护模式
port 6379 # 端口设置
```

> 通用GENERAL 

```bash
daemonize yes # 以守护进程的方式运行，默认是no,我们需要自己开启为yes!
pidfile /var/run/redis. _6379.pid # 如果以后台的方式运行，我们就需要指定一个pid文件!
#日志

# specify the server verbosity leve1.

# This can be one of:

# debug (a 1ot of information, usefu1 for deve lopment/testing)

# verbose (many rarely usefu1 info， but not a mess like the debug leve1)

# notice (moderately verbose, what you want in production probab1y)

# warning Conly very important / critica1 messages are logged) !

logleve1 notice
logfile "" # 日志的文件位置名
databases 16 # 数据库的数量,默认16个

```

> 快照

​	持久化, 在规定的时间内, 执行了多少次操作, 则会持久化到文件, rdb, aof

​	redis是内存数据库, 如果没有持久化, 数据断电丢失

```bash
# 如果900s内，如果至少有一个1 key进行了修改，我们及进行持久化操作
save 900 1
# 如果300s内，如果至少10 keyi进行 了修改，我们及进行持久化操作
save 300 10
# 如果60s内，如果至少10000 key进行了修改，我们及进行持久化操作
save 60 10000

stop-writes-on-bgsave-error yes
# 并持久化如果出错，是否还需要继续工作!

rdbcompression yes # 是否压缩rdb文件，需妥消耗一些cpu资源 ! 
rdbchecksum yes # 保存rdb 文件的时候，进行错误的检查校验!
dir ./ # rdb文件保存的目录:

```

> SECURITY


```bash
# 可在配置文件中设置密码, 默认没有密码
config get requirepass # 获取密码
config set requirepass # 设置密码
auth ......  密码登录
```

> APPEND ONLY模式 aof配置

```bash
appendonly no
# 默认是不开启aof模式的，默认是使用rdb方式持久化的，在大部分所有的情况下，rdb完全够用!
appendfilename "appendonly. aof" # 持久化的文件的名字
# appendfsync always
#每次修改都会sync。消耗性能
appendfsync everysec
# 每秒执行一次sync， 可能会丢失这1s的数据!
# appendfsync no
# 不执行sync, 这个时候操作系统自己同步数据，速度最快:
 
```

