## linux最小包环境

教程：https://cloud.tencent.com/developer/article/1701451
uname -r
yum -y update
yum install vim -y
yum install net-tools
设置网络：https://www.cnblogs.com/freeweb/p/5335973.html

## 安装docker

yum remove docker  docker-common docker-selinux docker-engine
yum install -y yum-utils device-mapper-persistent-data lvm2
yum-config-manager --add-repo http://download.docker.com/linux/centos/docker-ce.repo（中央仓库）
yum list docker-ce --showduplicates | sort -r
yum -y install docker-ce-18.03.1.ce

