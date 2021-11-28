# 简单笔记

## 好用的指令
把所有退出状态的container移除掉`$ docker rm $(docker ps -a -q -f status=exited)`,最新版本的docker可用
`docker container prune`同样效果，

｜指令｜解释｜
｜:---:｜:----:｜
｜`docker rm $(docker ps -a -q -f status=exited)`｜把所有退出状态的container移除掉｜