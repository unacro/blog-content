---
title: 灵感 & 计划
layout: simple
---

{{< lead >}}
还就那个点子王
{{< / lead >}}

---

## 博客更新选题

- [ ] [Windows Terminal](https://github.com/microsoft/terminal) + [PowerShell 7](https://github.com/PowerShell/PowerShell)（Windows 默认自带的是 5）
- [ ] [Scoop](https://scoop.sh/)
- [ ] 系统美化：动态桌面壁纸、鼠标
- [ ] [uTools](https://u.tools/)
- [ ] [OBS](https://obsproject.com/zh-cn/download)
- [ ] [Voicemeeter](https://voicemeeter.com/)
- [ ] [PowerToys](https://github.com/microsoft/PowerToys) & [DSC 自动配置](https://learn.microsoft.com/zh-cn/windows/powertoys/dsc-configure)

## 开发

### 综合

- [ ] 利用 [Koishi.js](https://koishi.chat/zh-CN/) 搭建 <ruby><abbr title="Instant Messaging，即时通讯">IM</abbr> 软件<rp>(</rp><rt>聊天工具</rt><rp>)</rp></ruby> bot。
- [ ] 能否将 [Notion Database API](https://developers.notion.com/reference/intro) 二次封装为 [NocoDB](https://github.com/nocodb/nocodb) 的 [API 标准](https://data-apis-v2.nocodb.com/) 以实现无缝切换数据库引擎？\
      有必要吗？是否为舍本逐末？
- [ ] 利用 [NotionNext](https://github.com/tangly1024/NotionNext) 反向代理 Notion 页面。

### 博客改进

- [ ] 优化 {{< spoiler "剧透条" >}}（[`spoiler` shortcode](https://github.com/unacro/hugo-theme-blowfish-mod/blob/main/layouts/shortcodes/spoiler.html)）表现效果，拦截解析器实现自定义 Markdown 语法 `||剧透文本||`。
- [ ] 优化 <mark>高亮文本</mark>（`<mark>` 标签）表现效果，拦截解析器实现自定义 Markdown 语法 `==高亮文本==`。
- [ ] 博客文章排版，[pangu.js](https://github.com/vinta/pangu.js) 仍然不够优雅，考虑魔改（为了适配）[赫蹏](https://github.com/sivan/heti)（[原版](https://sivan.github.io/heti/)无法自定义字体）以进行自动优化排版。
- [ ] 通过 Hugo [v0.126.0](https://github.com/gohugoio/hugo/releases/tag/v0.126.0) 新增的 [Content Adapters](https://gohugo.io/content-management/content-adapters/) 功能渲染数据。\
      Markdown 和 CSV [只能放在 `./assets/` 目录下](https://gohugo.io/content-management/data-sources/)，再通过 [`resources.Get`](https://gohugo.io/functions/resources/get/) 函数获取。\
     至于  [`./data/`](https://gohugo.io/methods/site/data/) 目录下只能放 JSON、TOML、YAML、XML（会自动读取并解析）。
- [ ] 利用 SVG 素材（如 [tile-art](https://github.com/WarL0ckNet/tile-art) / [riichi-mahjong-tiles](https://github.com/FluffyStuff/riichi-mahjong-tiles)） 自制字体，渲染麻将 emoji（参考 [I.Mahjong](https://github.com/SyaoranHinata/I.Mahjong)）。
- [ ] 根据给定的代码渲染麻将生成图片的 shortcode（之前见过类似的轮子，写之前找一下）。

## 游戏

### 综合

- [ ] [完善并发布](/projects/tech/logitech-lua-scripts/) 罗技驱动「Logitech G HUB」的 [Lua 脚本](https://github.com/unacro/logitech-lua-scripts)。
- [ ] 各种益智解谜类小游戏的辅助工具，如：数独、[Gauguin](https://github.com/meikpiep/gauguin)，以及网页小游戏 [Figure](https://figure.game)、[<abbr title="神奇形色牌">Set</abbr>](https://www.setgame.com/set/puzzle) 等。\
      （算法参考：[Offline Puzzle Solver](https://gitlab.com/20kdc/offline-puzzle-solver)。）
- [ ] 兼容移动端的桌游辅助工具网站：Dice 模拟、给定选项随机选择、记分板……~~考虑 [WebGL](https://developer.mozilla.org/zh-CN/docs/Web/API/WebGL_API) 实现 _掷骰子_ 的物理模拟。~~\
      （功能参考：[GM Dice](https://github.com/ge0rg/gamemasterdice)。相关技术栈参考 [这个 React 俄罗斯方块](https://github.com/chvin/react-tetris)。呈现效果参考：[Dice Tray](https://dicetray.gg/)。）
- [ ] 棋牌类桌游（主要是麻将）记分工具。\
      优先本地局域网通信（小程序 [mDNS](https://developers.weixin.qq.com/miniprogram/dev/framework/ability/mDNS.html) & 网页版 [WebRTC](https://developer.mozilla.org/zh-CN/docs/Web/API/WebRTC_API)），如果建立连接失败将会自动<ruby>回退<rp>(</rp><rt>fallback</rt><rp>)</rp></ruby>到 [WebSocket](https://developer.mozilla.org/zh-CN/docs/Web/API/WebSocket)。\
      （功能参考：[poker chips](https://pokerchips.io/)）
- [ ] 需要一个在各种游戏里都可以通用的 _规划 / 地图绘制_ 工具（类似 [RimWorld 中那种](https://steamcommunity.com/sharedfiles/filedetails/?id=3144381419)），可以通过 [Canvas API](https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API) 实现。
- [ ] [games-static-data](https://github.com/unacro/games-static-data) 跑通 Notion 数据库流程：[官方 SDK](https://github.com/makenotion/notion-sdk-js) / [RESTful API](https://developers.notion.com/reference/create-a-database)。
- [ ] 结合 [Notion Database API](https://developers.notion.com/reference/intro) 实现的 Steam 成就追踪工具。
- [ ] 编写 [Tampermonkey](https://www.tampermonkey.net/) 脚本自动爬取 Steam 指定游戏成就页面（例如《[黑神话：悟空](https://steamcommunity.com/stats/2358720/achievements/)》）的成就完成情况。

### 特定游戏

- [ ] Rust 开发麻将牌效计算工具（和牌判定 / 向听数计算等）。\
      （算法参考：[mahjong-helper](https://github.com/EndlessCheng/mahjong-helper) / [Majsoul-Helper](https://github.com/Fr0stbyteR/Majsoul-Helper) / [mahjong_AI](https://github.com/EricDDK/mahjong_AI)。）
- [ ] [Godot](https://godotengine.org/) 开发麻将（日麻 / 川麻）游戏。（实现参考 [Laya 引擎的联网麻将](https://github.com/liumengniu/majiang)。）
- [ ] 魔方解答工具，呈现效果参考 [魔方栈](https://cuber.heheda.top/)（[源码](https://gitee.com/huazhechen/cuber)）。\
      （算法参考 [Online Rubik's Cube Solver](https://rubiks-cube-solver.com/)。）
- [ ] **纯前端** 游戏王卡查，利用浏览器本地缓存卡牌数据（<abbr title="cards database，本质上是一个 SQLite 数据库"><code>.cdb</code></abbr>）实现。\
      （技术栈参考 [sqlite-web](https://github.com/coleifer/sqlite-web)。）
- [ ] TypeScript 复刻《[恶魔轮盘](https://store.steampowered.com/app/2835570/)》游戏，做成 _可在线游玩_ 的网页游戏，并考虑实现为 Discord bot 插件。\
      预留扩展性给 _多人模式_（[《恶魔轮盘》多人模式进展报告](https://store.steampowered.com/news/app/2835570/view/4276817570975737568?l=schinese) / [恶魔轮盘——多人测试版上线窗口期公布](https://store.steampowered.com/news/app/2835570/view/4657374275883684328?l=schinese)）。\
      利用已实现的游戏逻辑自动计算决策概率，制作最佳策略计算器。
- [ ] 《[缺氧](https://store.steampowered.com/app/457140/)》官方 debug 模式下的选区功能 & 模组 [Blueprints fixed](https://github.com/Pt-Djefferson/ONIMods) 都能将指定的区域信息保存到本地文件。\
      能否开发一个网站读取这类文件并将其渲染为分层概览，以便更好地~~抄作业~~ 参考模块设计？\
      读取蓝图文件数据，并列出所需材料，可快速替换建造材料并生成新的蓝图。
- [ ] 《[药剂工艺：炼金模拟器](https://store.steampowered.com/app/1210320/)》于 2023.12.13 的 [v1.1 更新](https://store.steampowered.com/news/app/1210320/view/3861337227494285542?l=schinese) 让大多数游戏机制与帧率解耦（不再挂钩）。\
      这是否意味着可以利用 _按键模拟类工具_（如 [AutoHotKey](https://www.autohotkey.com/) / [AutoIt](https://www.autoitscript.com/site/)）实现类似 TAS 的效果？

## 生活

### 提升

- [ ] 入门无线电，成为新鲜<ruby>火腿<rp>(</rp><rt>HAM</rt><rp>)</rp></ruby>[^ham]。\
      无线电台执照（工业和信息化部）、中国无线电协会业余电台操作证书（[CRAC](http://www.crac.org.cn/)），这个证必须要考，否则是**违法**的。\
      考试信息可以参考网站「[业务无线电模拟考试平台](https://www.cqid.cn/)」，以及《[中国 A 类业余无线电台操作证快速复习指北](https://www.jimmytian.com/archives/crac-aro-licence-a-review-guide.html)》这篇文章。\
      入门级手台：宝峰 UV-5R、泉盛 UV-K5、森海克斯 8800……系统学习教材：《业余无线电通信》。集邮系统：<abbr title="收听证明卡。QSL = 我收到了你的信息">QSL 卡</abbr>。\
      （热知识：各国的**民用**<ruby><abbr title="空中交通管制（Air Traffic Control，简称 ATC）">空管</abbr>信息<rp>(</rp><rt>航空频率</rt><rp>)</rp></ruby>是公开的；甚至可能都不需要电台，搞个好点的收音机都能听，~~懂我什么意思吧~~[^atc]。）
- [ ] 入门无人机，拍点自己想看的东西。\
      无人机四大证书：<abbr title="飞行人员驾驶执照&#13;由「国家交通运输部」下设的民航局管理，直接记录在民航系统里&#13;含金量和权威性最高（考试费用也最贵，最高可以上万）">CAAC</abbr>、[<abbr title="民用无人驾驶航空器系统驾驶员合格证&#13;「国际航空器拥有者及驾驶员协会」在中国的分支机构&#13;如果考过了 CAAC 可以直接同步申请，无需额外考试">AOPA</abbr>](http://www.aopa.org.cn/)、<abbr title="无人驾驶航空器系统操作手合格证&#13;大疆旗下培训机构颁发的证书，相当于大疆的包教包会服务&#13;这个证只能飞大疆">UTC</abbr>、<abbr title="遥控航空模型飞行员执照&#13;「国家体育总局」主管的「中国航空运动协会」&#13;主要适用于穿越机之类的竞赛类运动，无法用作商业行为的执照（不是冲着比赛去的这个证就没用）">ASFC</abbr>，现在都可以**不用考**了。\
      中央军委 2023.6.28 发布，2024.1.1 开始施行的《[无人驾驶航空器飞行管理暂行条例](https://www.gov.cn/zhengce/content/202306/content_6888799.htm)》明确了——
	- 第十七条：「操控微型、轻型民用无人驾驶航空器飞行的人员，无需取得操控员执照」。
	- 第十九条：「具有完全民事行为能力」且培训合格的人员（成年人）才能飞（真高）120 米以上（属于管制空域）。
	- 第二十二条：一般都不允许飞 300 米以上。

[^ham]: 真的很早之前就有这个念头了，并不是看了《我们生活在南京》才产生想法的；倒不如说正是因为对无线电感兴趣才会把这书读下去。
[^atc]: 甚至有专门做转播的，比如 [LiveATC](https://www.liveatc.net/map/feedmap.php) 这个网站；B 站也有很多专门剪国内机场 ATC 录音的 <abbr title="UP 主，即视频上传者。源自世上首个弹幕视频网站，日本的 N 站（www.nicovideo.jp）">UP</abbr>（关键词搜「[ATC 录音](https://search.bilibili.com/all?keyword=ATC%E5%BD%95%E9%9F%B3)」）。

### 娱乐

- [ ] 结合 [Notion Database API](https://developers.notion.com/reference/intro) 实现的小说追更工具。
