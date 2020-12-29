## 安装yum源的过程及问题参考
[yum安装](https://www.baidu.com)

## No module named '_ctypes'
> 我出现这个问题是python安装包的时候报错的 (pip install xxx).  
>Python3中有个内置模块叫ctypes，它是Python3的外部函数库模块，它提供兼容C语言的数据类型，并通过它调用Linux系统下的共享库(Shared library)，此模块需要使用CentOS7系统中外部函数库(Foreign function library)的开发链接库(头文件和链接库)。
 由于在CentOS7系统中没有安装外部函数库(libffi)的开发链接库软件包，所以在安装pip的时候就报了"ModuleNotFoundError: No module named '_ctypes'"的错误

`解决:`

 1.安装外部函数库(libffi)
 > yum install libffi-devel -y

 2.重新安装python 
 > yum install python

 3.用pip3 Install 安装需要的包
 > pip3 install xxx

## Error: xz compression not available
    
`下面命令中(x) 为对应的centos版本的号  例如centos7 那x为7`

> 问题: 在安装epel-release-latest-(x).noarch.rpm时出现问题  (根据centos对应的版本去下载,例如centos7下载对应的7 )

> 1.到http://ftp.riken.jp/Linux/fedora/epel/ 下载 epel-release-latest-(x).noarch.rpm  (下载对应的版本)
  
> 2.卸载epel-release-latest-(x).noarch.rpm：yum remove epel-release   (卸载之前的版本)
  
> 3.清空epel目录：rm -rf /var/cache/yum/x86_64/(x)/epel/
  
> 4.安装epel6:rpm -ivh epel-release-latest-(x).noarch.rpm

## No module named 'cryptography'

> pip install pycrypto当安装报错时  

> 执行pip install paramiko

## 安装python

`在linux下安装python3,一般情况下,服务器中有python2.7的版本 (正常情况已经命名为python),所以安装新的python3并且命名为python3`
```text
# 从上到下执行即可
yum install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gcc make
wget https://www.python.org/ftp/python/3.6.5/Python-3.6.5.tar.xz    (下载对应的python版本就行)
tar -xvJf  Python-3.6.5.tar.xz
cd Python-3.6.5
./configure --prefix=/usr/local/python3
make && make install
ln -s /usr/local/python3/bin/python3 /usr/bin/python3 
ln -s /usr/local/python3/bin/pip3 /usr/bin/pip3

# 之后用命令 python3 -V 查看版本是否为3版本 
# 之后的其他命令同样为python3 pip3 等
```
