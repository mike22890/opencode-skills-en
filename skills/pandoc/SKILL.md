---
name: pandoc
description: 文档格式转换与批量处理。当需要在 markdown/docx/pdf/html/epub/latex/rtf/odt 之间转换文档、批量导出、生成学术论文（LaTeX）、制作幻灯片、文档自动化处理、CI 中的文档构建、静态站点生成时使用。
version: 1.0.1
metadata:
  author: Mike
  tags: documentation converter pandoc
---

# Pandoc Document Converter

## 何时触发

关键词命中即触发：转换/格式/md转docx/md转pdf/html/epub/latex/批量导出/幻灯片/文档自动化。


pandoc 是瑞士军刀级别的文档转换工具。

## 常用转换

### Markdown → 其他
```bash
# md → docx（Word 文档）
pandoc input.md -o output.docx

# md → pdf（需 LaTeX）
pandoc input.md -o output.pdf

# md → html（独立网页）
pandoc input.md -o output.html --standalone

# md → epub（电子书）
pandoc input.md -o output.epub
```

### 其他 → Markdown
```bash
# docx → md
pandoc input.docx -o output.md

# html → md
pandoc input.html -o output.md

# pdf → md（需 pdf 解析工具）
pandoc input.pdf -o output.md
```

### 批量转换
```bash
# 当前目录所有 md → docx
for f in *.md; do pandoc "$f" -o "${f%.md}.docx"; done
```

## 实用选项

| 选项 | 干啥 |
|---|---|
| `--toc` | 自动生成目录 |
| `--toc-depth=N` | 目录深度（N=2 = h1+h2）|
| `--reference-doc=template.docx` | 用 Word 模板（保留样式）|
| `--css=style.css` | HTML 用自定义 CSS |
| `-V geometry:margin=2cm` | PDF 设置边距 |
| `--pdf-engine=xelatex` | 中文 PDF 用 xelatex |
| `--listings` | 代码块高亮 |
| `-s` / `--standalone` | 输出完整文件（含 header）|

## 中文支持（已实测）

### 推荐字体
**Noto Sans CJK SC**（已装 noto-fonts-cjk）

### 中文 PDF 命令
```bash
pandoc input.md -o output.pdf --pdf-engine=xelatex \
  -V mainfont="Noto Sans CJK SC" \
  -V CJKmainfont="Noto Sans CJK SC"
```

或写在 frontmatter：

```markdown
---
mainfont: Noto Sans CJK SC
CJKmainfont: Noto Sans CJK SC
---
```

### Arch 装中文 PDF 完整 6 件套（踩坑总结）

```bash
sudo pacman -S --needed \
  texlive-bin \
  texlive-basic \
  texlive-xetex \
  texlive-latexrecommended \
  texlive-fontsrecommended \
  texlive-langchinese
```

**坑**：
1. **Arch 拆包**：每个包独立装，**不会自动依赖链**
2. **`xelatex.fmt` 在 `/var/lib/texmf/web2c/xetex/`**，不在主目录
3. **必须装 `texlive-xetex`**才有 xelatex 格式
4. **必须装 `texlive-fontsrecommended`**才有 Latin Modern（PDF 默认字体）
5. **必须装 `texlive-latexrecommended`**才有 fontspec（指定字体的 LaTeX 包）
6. **fmtutil.cnf 不自动注册**新格式，跑 `sudo fmtutil-sys --all` 没用——直接装好 xetex 包就有

### 中文 PDF 故障排查

| 错误 | 原因 | 修复 |
|---|---|---|
| `I can't find the format file 'xelatex.fmt'` | texlive-xetex 没装 | `sudo pacman -S texlive-xetex` |
| `fontspec not found` | texlive-latexrecommended 没装 | `sudo pacman -S texlive-latexrecommended` |
| `Metric (TFM) file not found` (Latin Modern) | texlive-fontsrecommended 没装 | `sudo pacman -S texlive-fontsrecommended` |
| 中文方框 | mainfont 没设或字体名错 | 加 `-V mainfont="Noto Sans CJK SC"` |
| 代码块中文方框 | mono 字体没中文 | 在 frontmatter 加 `CJKmonofont: Noto Sans Mono CJK SC` |

### 完整中文 frontmatter 模板

```markdown
---
title: "文档标题"
author: Mike
date: "2026-08-28"
mainfont: Noto Sans CJK SC
CJKmainfont: Noto Sans CJK SC
CJKmonofont: Noto Sans Mono CJK SC
geometry: margin=2.5cm
toc: true
---

# 正文
```

## 何时使用

| 场景 | 命令 |
|---|---|
| 写完 README 给非技术同事 | md → docx |
| 设计文档要分享给老板 | md → pdf（中文 xelatex）|
| 项目文档做电子书 | md → epub |
| 收到 docx 想改 | docx → md → 改 → docx |
| 批量转换 100 个文档 | `for f in *.md; do pandoc ... ; done` |

## 反 AI 味

转换前先过 `masterpiece-writing` skill 检查一遍 —— **AI 味不会因为格式转换自动消失**。

## 排错

| 错误 | 修复 |
|---|---|
| `pdflatex not found` | `sudo pacman -S texlive-core texlive-bin` |
| `pandoc: command not found` | `sudo pacman -S pandoc`（已装 3.10.2）|
| docx 样式丢了 | 用 `--reference-doc` 指定模板 |
| 中文行间距过密 | 加 `-V linestretch=1.5` |