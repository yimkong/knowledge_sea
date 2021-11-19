## linux最小包环境

[安装教程]( https://cloud.tencent.com/developer/article/1701451 )

uname -r

yum -y update

yum install vim -y

yum install net-tools

[设置静态ip网络]( https://www.cnblogs.com/freeweb/p/5335973.html )

!> 需要主意的是，设置静态ip的时候需要与常用ip地址隔开一段间隔，否则很多设备连接路由器自动分配ip的时候会覆盖设置的ip，例如我本机ip是
`192.168.0.108`,那就不能设为`192.168.0.109`,而应该从`192.168.0.200`开始

[ssh 设置地址]( https://segmentfault.com/a/1190000014532520 )

## 安装docker

yum remove docker docker-common docker-selinux docker-engine

yum install -y yum-utils device-mapper-persistent-data lvm2

yum-config-manager --add-repo http://download.docker.com/linux/centos/docker-ce.repo（中央仓库）

yum list docker-ce --showduplicates | sort -r

yum -y install docker-ce-18.03.1.ce

