ss-bash
=======

Shadowsocks流量管理脚本

* 目前只支持python版Shadowsocks
* 目前只支持统计ipv4流量
* 经过turingttc的修改，可以在centos服务器上使用流量统计功能

[使用说明][User Manual]


[User Manual]:    https://github.com/hellofwy/ss-bash/wiki

**只为方便自己使用，未对代码进行改动**

使用方法
=======
centOS 6  
`yum update`  
`yum install python-pip -y`  
#搬瓦工  
`#get https://bootstrap.pypa.io/get-pip.py`  
`#sudo python get-pip.py`      
  
`pip install shadowsocks`  
`yum -y install unzip bc`  
`wget https://github.com/lixint/ss-bash/archive/master.zip`  
`unzip master.zip`  
`cd ss-bash-master/`   
#查看帮助      
`./ssadmin.sh h`      
#添加新用户，例如新增用户端口为443，密码是passwd，流量限制10G    
`./ssadmin.h add 443 passwd 10G`  
#启动服务   
`./ssadmin.sh start`   
#添加开机启动,编辑`/etc/rc.local`   
`vi /etc/rc.local`   
#在最后添加	`/home/ss-bash-master/ssadmin.sh start`  
通过修改`ssmlt.template`修改加密方式   

增加chacha20加密
==============
###到https://download.libsodium.org/libsodium/releases/  选择合适版本下载###   
`cd /root`   
`wget https://download.libsodium.org/libsodium/releases/libsodium-1.0.9.tar.gz`   
`tar zxvf libsodium-1.0.3.tar.gz`   
`cd libsodium-1.0.9`   
`./configure`   
`make`   
`make install`  
`#修复动态链接库`  
#运行命令：`vi /etc/ld.so.conf`  
#添加一行：`/usr/local/lib`  
#保存退出后，运行命令：`ldconfig`  
#重启vps，注意修改ssmlt.template中的加密方式
