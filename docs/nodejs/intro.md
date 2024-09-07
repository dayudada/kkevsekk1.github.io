---
sidebar_position: 1
---

# 概述

:::warning 注意：V7 版本目前处于开发中，本文档描述的功能模块在 V6 版本不可用
:::

## 启用 nodejs 引擎

默认情况下 js 文件由第一代引擎(Rhino)运行，当文件名由 mjs,cjs,node.js 结尾时使用 nodejs 引擎运行，以 mjs 结尾还会启用 esm 模块特性，这是推荐的运行方式

## 从全局变量改为导入模块

在第 2 代 api，所有模块全部需要使用`import `关键字导入，如
`import { showToast } from 'toast'`,暂不支持`require()`和`import()`动态导入

```js
import { showToast } from "toast";
```

## 多线程与异步

在 nodejs 引擎将不再支持多线程，取而代之的是`Promise`和异步函数，第二代 api 大多数都将以返回`Promise`表示异步操作，对于来自 java 的阻塞调用（如 io 读写）可通过`java`模块中的相关函数转换成一个`Promise`而不阻塞 nodejs 线程。
:::warning
如果你强行使用`java.lang.Thread`类运行 js 代码将会使引擎崩溃
:::

........待补充

## autox v7 开发进度

- [x] **分离脚本引擎运行的进程**
      使脚本运行在与 app 不同的进程，彻底解决脚本崩溃连同 app 一起崩溃的问题
- [ ] **迁移 app 界面至 m3 风格**
- [ ] **完善的插件扩展功能**
      使用一个独立的页面显示已安装和可下载的插件，采用激活/禁用的方式在每次运行脚本时自动加载插件，无需在代码中显式加载
- [x] **集成基于[Javet](https://github.com/caoccao/Javet)的 v8/nodejs 引擎**
- [ ] **nodejs 引擎功能模块适配**
- [ ] **全新的 ui 设计框架，采用 vue3 的[vue-core](https://github.com/vuejs/core)框架与[htm](https://github.com/developit/htm)模板引擎**
      基于新的引擎设计，支持组件和 vue 一样的响应式状态

## 参与开发基本操作

V7 版本开发目前由开发者【[aiselp](https://github.com/aiselp)】组成，如有兴趣共同参与开发和测试可加入本人创建的[tg 开发群](https://t.me/+bkx23tdbM6U3N2M1)交流

1. 首先确保你已经 fork 了此仓库，并且已拉取到本地并能够完成构建
2. 打开一个终端切换到项目目录输入

```shell
git remote add aiselp git@github.com:aiselp/AutoX.git
#更新远程仓库
git fetch --all
```

3. 创建并拉取 v7 分支

```shell
git checkout -b setup-v7 aiselp/setup-v7
```

4. 推送到你的远程仓库并设置为默认
   `git push -u origin setup-v7`
   其中 origin 表示你的远程仓库名，可能并非为 origin
