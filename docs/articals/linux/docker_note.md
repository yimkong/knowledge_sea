# 简单笔记

## 好用的指令

| 指令 | 解释| 
| :----: | :----:|
| `docker rm $(docker ps -a -q -f status=exited)` |把所有退出状态的container移除掉,`docker container prune`同样效果|
|`docker run --rm <image>`|在run的时候加上--rm则可以自动在退出容器的时候删除容器|

