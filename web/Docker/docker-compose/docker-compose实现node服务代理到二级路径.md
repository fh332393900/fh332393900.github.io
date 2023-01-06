---
slug: /
sidebar_position: 1
title: docker-compose实现node服务代理到二级路径
data: 2023年1月06日
---

## 前言（背景）

我们在服务器运行了一个 Node 服务端口在 `3000`，我们要访问服务的接口就只能在 http://xxx:3000 进行访问
但是我们想直接在 `80` 端口进行访问，例如 http://xxx/api 来调用接口要怎么做呢？

我们可以使用 nginx 来配置把端口代理到二级路径实现

```js
server {
    listen       80;
    server_name  localhost;

    root   /usr/share/nginx/html;
    index  index.html index.htm;

    location /api {
        add_header X-Config A;
        proxy_pass http://47.108.210.87:3000;
    }
}
```

docker-componse 的配置

```yaml
version: "3"
services:
  node-app:
    build:
      context: .
      dockerfile: node.Dockerfile
    ports:
      - 3000:3000
  nginx-app:
    build:
      context: .
      dockerfile: nginx.Dockerfile
    ports:
      - 80:80
    volumes:
      - ./proxy.conf:/etc/nginx/conf.d/default.conf
      - .:/usr/share/nginx/html
```

说明：
我们的 node 服务是运行在 3000 端口的，在 80 端口是我们的前端页面，同时添加代理的配置

