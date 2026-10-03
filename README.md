# obsidian-notes

个人笔记库，用 [Obsidian](https://obsidian.md) 维护，主题为 [Minimal](https://github.com/kepano/obsidian-minimal)，纯 Markdown 存储，内容以中文为主。

## 结构

```text
notes/          全部笔记（平铺存放，按需再分目录）
attachments/    笔记引用的图片和 PDF
.obsidian/      Obsidian 配置（主题、CSS 片段、核心插件开关）
```

## 说明

- 笔记使用标准 Markdown 和相对路径链接，不依赖 Obsidian 专属语法，换编辑器也能读。
- 图片、PDF 统一放在 `attachments/`，不为单篇笔记建图片目录。
- `.obsidian/workspace.json`、缓存、回收站和系统文件由 `.gitignore` 排除，属于设备本地状态，换设备后自动重新生成。

## 外观与 CSS

主题和 CSS 片段决定了笔记长什么样，换设备时靠本仓库里的副本恢复，所以在这里记一笔。

- **主题：Minimal**（`appearance.json` 的 `cssTheme`）。主题文件本身也在仓库里（`.obsidian/themes/`），换设备会自动生效，但不会自动更新——想升级要在 Obsidian 里手动检查。
- **CSS 片段两个，缺一不可**：
  - `base.css`：只管排版（字号、行距、间距、标题），移植自 Typora 的 github 主题。
  - `github-markdown.css`：只管配色，把 Obsidian 变量重映射到 GitHub 调色板（`--gh-page`、`--gh-border`、`--gh-link` 等）。
- **改表格样子只需要动 `github-markdown.css` 里四个变量**：`--gh-table-border`（单元格线）、`--gh-table-head`（表头底）、`--gh-table-stripe`（隔行）、`--gh-table-hover`（行悬停，亮 `#e6d8f9` / 暗 `#3d2f5b`，写死的紫色系；想改成跟随强调色，见该处注释）。`base.css` 只引用这四个变量并带兜底值，不用改规则。
- **换主题前先看两个文件的注释**：Minimal 默认一根表格线都不画、表格开关要靠 Style Settings 插件（本库没装），所以表格观感实际上由这两个片段提供；换主题后需复核 `base.css` 第 9 节与 `github-markdown.css` 第 1 节。
- 其他关键设置：亮色基础色 `moonstone`、正文字号 20、字体 Hack、标准 Markdown 链接 + 相对路径、附件目录 `attachments`。
- **正文栏宽度由 `github-markdown.css` 第 4 节的 `--line-width` 控制，且必须定义在 `body` 层**。Minimal 在 body 上根据它推导 `--content-margin-start`、`--container-table-margin` 等一整套几何变量，这些派生值在 body 层就完成了 `var()` 替换；若把 `--line-width` 写到 `.markdown-preview-view` 这类视图元素上，body 层仍按默认 640px 计算，而其中的百分比按真实栏宽解析，表格容器会被推右约 110px（表现为表格无法与正文左对齐）。

## 关于内容

私人笔记，以随手记为主：计算机、数学、学习方法和个人思考。不保证准确，也不构成任何建议。
