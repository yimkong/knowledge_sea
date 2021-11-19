## linux最小包环境

教程：https://cloud.tencent.com/developer/article/1701451 </br>
uname -r</br>
yum -y update</br>
yum install vim -y</br>
yum install net-tools</br>
设置静态ip网络：https://www.cnblogs.com/freeweb/p/5335973.html </br>
ssh 设置：https://segmentfault.com/a/1190000014532520

## 安装docker

yum remove docker  docker-common docker-selinux docker-engine
yum install -y yum-utils device-mapper-persistent-data lvm2
yum-config-manager --add-repo http://download.docker.com/linux/centos/docker-ce.repo（中央仓库）
yum list docker-ce --showduplicates | sort -r
yum -y install docker-ce-18.03.1.ce

