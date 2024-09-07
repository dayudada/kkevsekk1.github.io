---
sidebar_position: 2
---

# 在 vscode 开发

在第二代 api，创建 v7 项目和创建普通的 nodejs 项目一样，你可以使用 ts 语言，各种构建工具和框架，并且 v7 api 全部使用 ts 开发，对 ts 项目有很好的支持

## ts 项目模板

你可以在[此页面](https://github.com/aiselp/AutoX/releases/tag/v7.0.0-alpha4)中下载`v7-project-demo.rar`得到一个基本 ts 项目模板，解压后使用 vscode 打开，随后运行
`npm install`安装所有依赖。

在根目录下有一个 scr 文件夹，这里存放你所有的源代码。

运行`npm run build`编译源代码并生成 dist 文目录，该文件夹输出的是能运行在 autox 中的项目。

## 启用 v7 模块代码提示

首先，进入项目目录，安装 autox-v7-api

```
npm i -D autox-v7-api
```

:::tip
当 autox v7 新增 api 后可重新运行以上命令获取更新
:::

随后，如果你使用打包工具，可直接从`autox-v7-api/[模块id]`导入模块，如

```js
import { showToast } from "autox-v7-api/toast";
```

<font color="red">此方式会将模块代码一起打包到输出的文件</font>。

否则，如果你不使用打包工具或不想用上面的方式，输入`npx install-autox-types`根据提示选择项目类型，接着在项目中使用正常的模块导入如

```js
import { showToast } from "toast";
```

<font color="red">此方式会修改项目中的 `tsconfig.json` 文件</font>
