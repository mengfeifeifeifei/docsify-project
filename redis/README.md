## windows下安装
`安装包下载地址：https://github.com/microsoftarchive/redis/releases`

`下载msi微软格式就行，zip是压缩包`

`打开命令行工具切换到redis目录下,运行redis-cli回车，连接成功(练习使用).`

`如果需要设置密码去redis.windows-service 中搜索 requirepass 加一行requirepass xxxx`

## Linux下安装
`wget http://download.redis.io/releases/redis-6.0.8.tar.gz`

**1.解压**

`tar -xzvf redis-6.0.8.tar.gz`

**2.安装**

`cd redis-6.0.8`
`make`
`cd src`
`make install PREFIX=/usr/local/redis`

**3.移动配置文件到安装目录下**

`cd ../`
`mkdir /usr/local/redis/ect`
`mv redis.conf /usr/local/redis/etc`

**4.切换到移动的文件下,启动后台redis服务(此时对话不能关闭，关闭后台redis服务就会关闭，所以配置redis后台启动)**

`./redis-server`

**5.配置redis为后台启动**

`vi /usr/local/redis/etc/redis.conf //将daemonize no 改成daemonize yes`

**6.再次启动redis后台服务**

`./redis-server ../etc/redis.conf`

**7.此时后台服务已经开启，开启redis**

`./redis-cli`

## String

**设置值**`set key value`

**获取值**`get key`
