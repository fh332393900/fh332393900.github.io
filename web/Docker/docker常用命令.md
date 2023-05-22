---
id: docker常用命令
sidebar_position: 2
title: docker常用命令
data: 2023年4月26日
---

### Docker 重新加载 nginx 容器配置文件

`docker exec [容器] nginx -s reload`
例如：
```shell
docker exec node_nginx-app_1 nginx -s reload
```