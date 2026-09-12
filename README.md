# girls_orbit_project —— 《无法校准少女》移植示例

本工程是 aliceADV 引擎的示例项目，把用 Ren'Py 开发的 demo `girls_out_of_orbit` 移植到 aliceADV，用于验证引擎的基础能力，包括对话、背景、立绘、音乐、分支与存档等。

## 前置条件

需先安装 aliceADV 引擎，参见 `../aliceadv/README.md`。

```bash
cd ../aliceadv
pip install -e .
```

## 构建与运行

```bash
# 在工程目录内
aliceadv build .

# 打开产物
# 方式一：直接双击打开
open dist/web/index.html
# 方式二：本地静态服务器
python3 -m http.server -d dist/web 8000
# 浏览器访问 http://localhost:8000
```

`file://` 协议下可直接播放（剧本已内联进 `index.html`）；使用语音、字体等本地资源时，建议用本地服务器以避免浏览器跨域限制。

## 目录结构

```
girls_orbit_project/
├── info.json            # 游戏名 / 版本 / 引擎版本
├── theme.json          # 样式与界面文本（移植自 demo 的 gui.rpy）
├── about.txt
├── story/
│   ├── ch1.json        # 第一章剧本
│   ├── characters.json # 角色档案
│   └── chapters.json   # 章节目录与播放顺序
├── gui/                # 界面图片
├── images/             # 背景(bg/)与立绘(char/)
├── audio/              # 音乐与音效
├── fonts/              # SourceHanSansLite.ttf
└── documents/          # 剧本格式说明.md / 定义.md
```

## 剧情与角色

- 章节：一章「脱出轨道的女孩们」，对应 `story/ch1.json`。
- 角色与演出资源在 `story/characters.json` 与 `images/char/` 中定义。
- 章节目录与播放顺序在 `story/chapters.json` 中维护。

## 修改与维护

- 修改 `theme.json` 或 `story/*.json` 后，必须重新运行 `aliceadv build .`，改动才会进入 `dist/web/`。
- 不要直接修改 `dist/web/` 下的产物，重新构建会被覆盖。
- 新增背景放 `images/bg/`，立绘放 `images/char/<角色ID>/`，音频放 `audio/`。
- 字体：在 `theme.json` 的 `fonts` 中声明 `src`，指向 `fonts/` 下的字体文件。

## 相关文档

- 指令手册（全部指令用法）：`../documents/指令.md`
- 剧本格式精确说明：本工程 `documents/剧本格式`
