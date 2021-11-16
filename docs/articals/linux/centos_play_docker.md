## 安装centos
安装docker的时候走了歪路，一开始按照别的教程，后面找到一份对的教程，才发现有冲突了`Error: docker-ce-cli conflicts with 2:docker-1.13.1-208.git7d71120.el7_9.x86_64`，于是需要通过命令`yum list installed | grep docker`找出已安装的，然后再`yum -y remove ..`删除对应的docker

