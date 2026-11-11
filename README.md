# LeafRead · 一片叶子的阅读器

> 一个**单文件、零依赖、纯离线**的网页阅读器：下载一个 `reader.html`，双击就能读书。
> 不用装软件、不用起服务器、不上传任何数据 —— 书和笔记都留在你自己的电脑/手机里。

**在线体验**：[chengyi-mountain.github.io/LeafRead](h[https://chengyi-mountain.github.io/LeafRead/reader.html)]


---

## ✨ 为什么是 LeafRead

- 🍃 **单文件交付** — 全部代码、内置书库、主题都塞进一个 `reader.html`（约 1.6 MB），拷进 U 盘就能带走
- 📴 **完全离线可用** — 运行期不发任何网络请求，断网、飞机上、没有 WiFi 的教室都能读
- 🗂️ **进度和笔记在自己手里** — 只写浏览器 localStorage，可一键导出/恢复备份，不经过任何服务器
- 📱 **手机、平板、电脑同一套界面** — 自适应布局，手机上左右点击翻页、中间点击唤出顶栏

## 📖 阅读功能

| 功能 | 说明 |
|---|---|
| 双阅读模式 | **滚动**（连续流）与 **翻页**（多列排版、整页翻动、翻书阴影）随时切换 |
| 六套主题 | 日间、夜间、护眼绿、森林、海洋、**水墨屏**，可跟随系统深色模式 |
| 字体与字号 | 衬线 / 无衬线 / 等宽三套字体，字号、行距、页宽可调 |
| TTS 朗读 | Web Speech API，播放 / 暂停 / 上句 / 下句 |
| 划词查询 | 选中文字即弹出词典与翻译 |
| 全文搜索 | 命中高亮，点击结果直接跳章定位 |
| 书签与笔记 | 选中文字加笔记，书签快速跳转，全部本地保存 |
| 阅读统计 | 累计时长、连续阅读日历 |
| 快捷键 | `←` `→` / `PageUp` `PageDown` 翻页，`Esc` 关闭面板 |

## 📥 导入格式

| 格式 | 状态 | 说明 |
|---|---|---|
| TXT / Markdown | ✅ | 自动按空行与“第 X 章”标题切分章节 |
| HTML / HTM | ✅ | 自动剥离标签、提取正文 |
| EPUB | ✅ | 内置原生 ZIP 解压 + 读取 OPF 的 spine 顺序，按真实章节结构导入 |
| DOCX | ✅ | 读取 `word/document.xml` 正文段落 |
| PPTX / XLSX / ODT / ODP / ODS | ✅ | 分别按幻灯片、工作表、ODF 正文提取文本 |
| CBZ | ✅ | 漫画压缩包，逐页图片浏览 |
| PDF | ❌ 暂不支持 | 不含 PDF 渲染库，请先转成 TXT / EPUB 再导入 |
| CBR（RAR 漫画） | ❌ | 请转换为 CBZ |
| MOBI / AZW3 | ⚠️ 部分 | 二进制格式，只能尽力提取可读文本 |
| 网址抓取 | ✅ | 粘贴文章 URL，自动提取正文（需要联网） |

> 解压 EPUB / DOCX / CBZ 用的是浏览器原生 `DecompressionStream`，**没有任何第三方 JS 库**，所以这个单文件永远不会因为 CDN 挂掉而失效（需要 Chrome / Edge / Safari 16.4+ 等现代浏览器）。

## 🚀 开始使用

**方式一：在线体验**（推荐先点开看看）
打开 <https://chengyi-mountain.github.io/LeafRead/reader.html>

**方式二：本地使用**
1. 下载本仓库的 `reader.html`
2. 双击，用 Chrome / Edge / Safari 打开
3. 直接开始读内置的四本公版书，或拖入自己的文件

## 📚 内置公版书（共 124 章 / 约 147 万字符）

| 书名 | 作者 | 章节 | 体量 |
|---|---|---|---|
| 爱丽丝漫游奇境 | Lewis Carroll | 2 章 | ~49K |
| 爱丽丝镜中奇遇 | Lewis Carroll | 1 章 | ~13K |
| 德古拉 | Bram Stoker | 18 章 | ~516K |
| 白鲸记 | Herman Melville | 103 章 | ~896K |

## 🧱 技术构成

- 纯 HTML / CSS / JavaScript（ES6+），零第三方库、零构建步骤
- 分页用 CSS 多列（`column-width` + `scrollWidth` 计算页数），`transform` 整页平移
- 数据持久化：localStorage（`reader_state_v2`、`reader_settings_v2`、`reader_bookmarks_v2`、`reader_highlights_v2`、`reader_notes_v2`、`reader_stats_v2` …）
- 文件解析：`DecompressionStream` 原生解压 + 正则提取 XML/HTML 文本
- 无障碍与移动端：触摸手势、点击热区、安全区适配

## 🐞 已知限制

- PDF、CBR、加密 MOBI 无法直接阅读（见上方格式表）
- 内置英文公版书正文在个别位置存在**单词间空格丢失**（原始文本换行拼接遗留），属内容数据问题而非解析缺陷
- 阅读数据存在浏览器本地，换浏览器 / 清缓存会丢失，重要数据请用「备份导出」留存

## 📄 License

MIT License，详见 [LICENSE](LICENSE)。内置书籍均为公有领域作品。

## ⚠️ 免责声明

本项目仅供个人学习、技术研究与合法阅读使用。内置书籍仅限已进入公有领域的作品；通过本工具导入的任何内容，其版权责任由使用者自行承担。完整条款见 [DISCLAIMER.md](DISCLAIMER.md)。
