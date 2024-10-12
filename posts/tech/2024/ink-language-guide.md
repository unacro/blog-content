---
title: 「ink」语言开发互动小说项目入门实战
description: ""
date: 2024-10-12T00:09:24+08:00
categories:
  - develop-tools
tags:
  - game-develop
summary: "TypeScript + ink 开发文字游戏（个人）最佳实践"
---

- [inkle](https://www.inklestudios.com/)：开源这套工具的游戏工作室
- [ink](https://github.com/inkle/ink)：用于互动小说 / 文字游戏的叙述性脚本语言
- [Inky](https://github.com/inkle/inky)：官方推出的 ink 语言专用编辑器

## 前言

我当初是从《八十天环游地球》的[游戏](https://store.steampowered.com/app/381780/)知道 [ink](https://www.inklestudios.com/ink/) 的。

简单了解后发现~~小别致挺东西~~ 有点意思，于是兴致勃勃地上手把玩了一段时间。\
但一时没有成熟的想法去实现，只能当作小玩具，玩腻了自然热情就渐渐冷却了。

期间偶尔想起了也有关注，但相关项目的发展进度嘛……只能说社区生态近乎没有。

后来发现比懒狗官方更新勤奋十倍~~甚至九倍~~的 [inkjs](https://github.com/y-lohse/inkjs) 这个第三方库，非常好用。

> 说是第三方库，其实早在 [inkjs v1.0.2](https://www.npmjs.com/package/inkjs/v/1.0.2) 就[被官方招安](https://github.com/inkle/inky/blob/e1d812c5feca60edfc3b2a9355bd3b4636f80d7e/app/package.json)（Inky 的导出到 Web）了。

吃完<dfn title="2024 年 9 月底 10 月初">最近</dfn> Godot 社区「觉醒」风波的瓜，顺便回顾游戏引擎的时候突然又想起这玩意。

怎么说。整吗？整吧。

## 工作流

1. 仍旧是正常写 `.ink`
2. 编译为网页可读的格式（以前是用官方的命令行工具 [inklecate](https://github.com/inkle/ink/releases)，现在是 [inkjs](https://github.com/y-lohse/inkjs)）
3. 部署到云端

网页模板参考：
- [官方编辑器 - Inky 仓库里的模板](https://github.com/inkle/inky/tree/master/app/export-for-web-template)
- [第三方 JavaScript 实现 - inkjs 仓库里的模板](https://github.com/y-lohse/inkjs/tree/master/templates)

## 技术选型

### JavaScript or TypeScript

和你一样，我对 TS 的 _类型体操_ 深恶痛绝。\
当实际上根本无影响，但别说编译时、就是代码层面都通不过 Lint 检查时，真的抓狂。

但必须承认的是，TS 引入的 _类型约束_ 极大降低了项目混乱度熵增的速度。\
对于**长期维护**或者**规模较大**的项目，用 TS 绝对是比 JS 更**健壮**的。

用人话来讲，这么说吧：
- 以前用 JS 写的屎山，我现在连看都不想看一眼，只能说辣眼睛；
- 以前用 TS 写的屎山，硬着头皮捏着鼻子重读，偶尔还是能翻出点有用的东西的。

用 TS 的心智负担确实重，但本质上是把可能会出现的问题尽量提前解决（防御性编程的本意），而不是鸵鸟心态把头一埋~~留给后人的智慧~~。就这一点而言，我是认可的。\
开发环境代码报错肯定是好事；装睡可以，等进了生产环境才出问题，你就知道错了。

### 脚手架

用什么引擎？[Node.js](https://nodejs.org/)？[Deno](https://deno.com/)？\
用什么包管理器？[npm](https://www.npmjs.com/)？[yarn](https://yarnpkg.com/)？[pnpm](https://pnpm.io/)？\
用什么脚手架？Webpack？Rollup？Parcel？Rolldown？esbuild？rsbuild？……

老子是真的烦死了这些搞所谓「大前端」然后疯狂重复造轮子的。\
~~没活去咬打火机好吗？~~ 非得凭空生造需求、硬混 KPI？

> 拓展阅读：《[尤雨溪成立 VoidZero，Rust 要一统 JavaScript 工具链？](https://juejin.cn/post/7422404598360948748)》

人生苦短，我用[<ruby>包子<rp>(</rp><rt>Bun</rt><rp>)</rp></ruby>](https://bun.sh/)。

> BTW：Bun 并不是用 [Rust](https://www.rust-lang.org/) 开发的，而是 [Zig](https://ziglang.org/) 语言。

一把梭就完事了，顶多加个非常符合我开发美学的 linter 工具 [Biome](https://biomejs.dev/)（格式化代码）。

截至本文撰写时，Bun 的最新版是 `v1.1.30`（[更新于 2024.10.9](https://bun.sh/blog/bun-v1.1.30)）。\
作为从公测伊始就一直关注到现在的人，看着这个项目一路走来，更新速度真的没话说。

早已完善支持 [Scoop](https://scoop.sh/)，一行命令搞定安装：
```PowerShell
$ scoop install bun

$ scoop info bun # 查看 Scoop 软件包信息
$ bun --version  # 直接运行查看版本
```

## （个人的）最佳实践

初始化项目：
```PowerShell
$ git init
$ bun init
$ bun install inkjs
```

编辑 `package.json` 新增脚本命令：
```JSON
{
	……,
	"scripts": {
		"dev": "bun run ./src/index.ts dev",
		"start": "bun --watch run ./src/index.ts dev",
		"build": "bunx inkjs ./src/ink/main.ink -o ./dist/story.json",
		"deploy": "bunx wrangler pages deploy dist"
	},
	……,
}
```

编辑 `src/index.ts` 在线编译 `.ink`：\
（参考了《[Differences with the C# Compiler](https://github.com/y-lohse/inkjs/blob/master/docs/compiler-differences.md)》这篇文档）
```TypeScript
import { Compiler } from "inkjs/compiler/Compiler";
import { PosixFileHandler, type CompilerOptions } from "inkjs/types";
import type { ErrorHandler } from "inkjs/engine/Error";

// inkjs 的 fileHandler 以 package.json 所在路径为根目录
const inkFileRoot = "./src/ink";
const inkFileEntry = await Bun.file(`${inkFileRoot}/main.ink`).text();
// console.debug(inkFileEntry);

const fileHandler = new PosixFileHandler(`${inkFileRoot}/`);
const errorHandler: ErrorHandler = (message, errorType) => {
	console.error(`${errorType}: ${message}\n`);
};
const compilerOptions = {
	fileHandler,
	errorHandler,
} as unknown as CompilerOptions;

const inkStory = new Compiler(inkFileEntry, compilerOptions).Compile();
// console.debug(inkStory.ContinueMaximally());

const inkStoryJson = inkStory.ToJson();
if (inkStoryJson) {
	// console.debug(inkStoryJson);
	await Bun.write("./dist/story.json", inkStoryJson);
}
```

兼容 `INCLUDE 其他.ink` 的 TypeScript 无报错自动编译 `.ink`，大功告成：
```PowerShell
# 代码实现的自动编译
$ bun run dev

# 自动编译加上热更新
$ bun run start

# 手动编译
$ bun run build
```

另外可以用 TS 重写 `main.js`，引入 [Vite](https://cn.vitejs.dev/) 等构建工具，实现 HMR 等各种扩展功能。\
正常写 TS，最后编译成 ES2015 即可；样式同理，写 Sass 自动编译 CSS 之类的。\
总之可以根据个人需求按需扩展，此处不再赘述。

---

接下来**可能**会翻译一下 ink 语法的[官方文档](https://github.com/inkle/ink/blob/master/Documentation/WritingWithInk.md)？有机会再说吧，咕咕咕。
