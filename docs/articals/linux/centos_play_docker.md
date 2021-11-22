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

## 安装Nextcloud
[教程地址]( https://zhuanlan.zhihu.com/p/107820215 )
[安装docker-compose]( https://yeasy.gitbook.io/docker_practice/compose/install )

将compose yml文件放在用户～路径下，以便每次登录的时候执行`docker-compose up -d`就能调用到这个文件

`GRANT ALL PRIVILEGES ON nextcloud.* TO 'nextcloud'@'%' WITH GRANT OPTION;`

`FLUSH privileges;`

```shell
docker run -d --name nextcloud \
-v /volume1/SYNC/nextcloud:/var/www/html \
--link mysql:mysql \
--link redis:redis \
--restart unless-stopped \
-p 8000:80 nextcloud
```
## docker trouble shooting
用这个指令来查看详细日志：`journalctl -eu docker`

## 安装filerun
?> 偶然发现另一个比nextcloud好的云盘工具，折腾一下
[安装教程]( https://post.smzdm.com/p/ag82pn83/ )

## 安装redis
[官方教程]( https://www.apiref.com/docker-zh/docker-install-redis.html )

`docker run --name redis -p 6379:6379 -v $PWD/data:/data  -d redis redis-server --appendonly yes`

`docker run -d --name nextcloud -v /volume1/SYNC/nextcloud:/var/www/html --link mysql:mysql --link redis:redis --restart unless-stopped -p 8000:80 nextcloud`
### docker 结合 redis 
https://www.cmdschool.org/archives/12091
## 工具
### 资源
[docker常用指令]( https://www.cnblogs.com/jpfss/p/11227384.html )

[防火墙开放对应端口]( https://br-bai.github.io/2020/12/25/docker部署nextcloud%2020.0.4%20最新版个人网盘/ )

[高性能搭建nextcloud]( https://hexo.chensmallx.top/2021/04/08/nextcloud-on-docker/#稍微带过一下安装docker的方法)

[硬盘挂载]( https://cloud.tencent.com/developer/article/1776730 )
### 常用指令
`service docker restart`

`scp ddd root@192.168.0.200:/root/docker-compose.yml`

mysql 创建用户以及数据库
```roomsql
CREATE USER 'nextcloud'@'localhost' IDENTIFIED BY 'password';
CREATE DATABASE IF NOT EXISTS nextcloud CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
GRANT ALL PRIVILEGES on nextcloud.* to 'nextcloud'@'localhost';
FLUSH privileges;
```

防火墙

`firewall-cmd --zone=public --add-port=8088/tcp --permanent`

`firewall-cmd --reload`

`firewall-cmd --query-port=8088/tcp`

`docker stop $(docker ps -aq)`

查看容器日志：`docker logs --since 30m CONTAINER_ID`

遇到问题`(38)Function not implemented: AH00141: Could not initialize random number generator`解决方案：
[更新linux内核]( https://phoenixnap.com/kb/how-to-upgrade-kernel-centos )

` 4047 InnoDB refuses to write tables with ROW_FORMAT=COMPRESSED or KEY_BLOCK_SIZE.` [解决方案]( https://techoverflow.net/2021/08/17/how-to-fix-nextcloud-4047-innodb-refuses-to-write-tables-with-row_formatcompressed-or-key_block_size/ )

`Nextcloud 出现 请求过多 ` 解决方案:登录mysql对应的nextcloud数据库oc_bruteforce_attempts表清空

!> 需要主意的是，只是内网登录的时候，必须要把登录界面的数据库的地址改为docker的mysql实例名，虽然不知道啥原因

## 后记
喜极而泣，终于搞定。。。