---
title: uni-app
date: 2020-04-08 12:34:17
tags:
---
1、uni-app目录结构**
***
​	1.1目录截图



1.2 操作流程（流程时序图）

​	使用hbuilderX工具新建uni-app默认项目

1.3 目录功能描述

```dif
┌─pages               				//页面文件夹
│  ├─index								
│  │  └─index.vue    
│  └─login
│     └─login.vue    
├─static           					//静态文件夹
├─main.js       					//入口文件
├─App.vue          					//项目根组件
├─manifest.json  					//多平台配置文件
└─pages.json 						//页面路由，导航，tabBar配置文件
```

1.4 目录相关代码：

​	无

1.5 目录说明或者备注：

​	**pages.json的配置项**

| 属性                                                         | 类型         | 必填 | 描述                    | 平台兼容   |
| :----------------------------------------------------------- | :----------- | :--- | :---------------------- | :--------- |
| [globalStyle](https://uniapp.dcloud.io/collocation/pages?id=globalstyle) | Object       | 否   | 设置默认页面的窗口表现  |            |
| [pages](https://uniapp.dcloud.io/collocation/pages?id=pages) | Object Array | 是   | 设置页面路径及窗口表现  |            |
| [easycom](https://uniapp.dcloud.io/collocation/pages?id=easycom) | Object       | 否   | 组件自动引入规则        | 2.5.5+     |
| [tabBar](https://uniapp.dcloud.io/collocation/pages?id=tabbar) | Object       | 否   | 设置底部 tab 的表现     |            |
| [condition](https://uniapp.dcloud.io/collocation/pages?id=condition) | Object       | 否   | 启动模式配置            |            |
| [subPackages](https://uniapp.dcloud.io/collocation/pages?id=subpackages) | Object Array | 否   | 分包加载配置            |            |
| [preloadRule](https://uniapp.dcloud.io/collocation/pages?id=preloadrule) | Object       | 否   | 分包预下载规则          | 微信小程序 |
| [workers](https://developers.weixin.qq.com/miniprogram/dev/framework/workers.html) | String       | 否   | `Worker` 代码放置的目录 | 微信小程序 |

**2.获取用户信息**

2.1 获取用户信息截图

2.2 获取用户信息流程

2.3功能描述

通过授权来获取当前用户的信息，用户名、头像、地址等。

> 获取用户信息分两种情况：

* 已经授权的情况下，直接调用`uni.getUserInfo()`来获取。

* 未授权的情况下，需要用户点击按钮，出现授权的弹窗来获取授权。

2.4说明或者备注
