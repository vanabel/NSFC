# MNSFC v1.0.2

数学类国家自然科学基金申请书 LaTeX 模板 v1.0.2

**完整变更**：见 [Compare v1.0.1...v1.0.2](https://github.com/vanabel/mNSFC/compare/v1.0.1...v1.0.2)。

## 🎉 新功能

### 项目名称支持中英文

- `\mnsfcProjectTitle` 命令现在支持**中英文两个参数**：
  - 第一个参数：中文项目名称。
  - 第二个参数：英文项目名称（`Project Title`）。
- 标题页上会同时显示中文和英文项目名称。

### 申请代码支持

- 新增 `\mnsfcApplicationCode{申请代码1}{申请代码2}` 命令。
- 申请代码显示在项目标题和研究属性之间。
- 支持只填写一个申请代码（另一个留空）或两个都填写。

### 主要研究领域

- 新增 `\mnsfcResearchField{主要研究领域}` 命令。
- 主要研究领域显示在英文关键词之后。
- 该字段为可选，默认留空不显示。

## 📝 使用示例

```latex
\mnsfcProjectTitle{（填写项目名称）}{（Project Title）}
\mnsfcApplicationCode{申请代码1}{申请代码2}  % 申请代码
\mnsfcKeywordsZH{关键词1；关键词2；关键词3}
\mnsfcKeywordsEN{keywords1; keywords2; keywords3}
\mnsfcResearchField{主要研究领域}  % 主要研究领域（可选）
```

## 🔧 技术改进

- 优化标题页的整体布局，使中英文项目名称以及申请代码的信息排版更加清晰。
- 改进申请代码的显示逻辑，在只填一个或两个代码的情况下都能合理展示。
- 同步更新文档说明和示例文件，让用户更容易上手配置项目信息。

## 📦 发布包内容

本发布包含以下主要文件：

- `mnsfc.dtx` — 源代码文件。
- `mnsfc.sty` — 样式包（可直接在文档中 `\usepackage{mnsfc}` 使用）。
- `mnsfc.pdf` — 完整文档（从 `mnsfc.dtx` 生成）。
- `mnsfc-main.tex` — 示例主文档。
- `mnsfc-main.pdf` — 示例 PDF。
- `mnsfc-refs.bib` — 示例参考文献数据。
- `README.md` — 使用说明与快速开始指南。
- `Makefile` — 构建与安装脚本。

## 🚀 快速开始

1. 解压 `mnsfc-v1.0.2.zip`。
2. 查看 `README.md` 获取安装和使用说明。
3. 以 `mnsfc-main.tex` 为模板，根据需要修改项目名称、申请代码和主要研究领域等信息。

## 📄 许可证

本项目采用 [LaTeX Project Public License (LPPL) v1.3c](http://www.latex-project.org/lppl.txt) 许可证。

