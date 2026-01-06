# NSFC Proposal Template

国家自然科学基金申请书 LaTeX 模板

## 功能特性

- **双模式支持**：`draft` 和 `final` 模式
  - `draft` 模式：显示摘要、写作提示、行号、字数统计
  - `final` 模式：隐藏所有辅助信息，仅显示正文内容

- **行号功能**：在 `draft` 模式下自动显示行号（每 5 行显示一次），自动跳过标题

- **字数统计**：基于页数估算正文字数（仅在 `draft` 模式下显示）

- **参考文献支持**：使用 `amsrefs` 包管理参考文献

- **自定义格式**：
  - `\section` 和 `\subsection` 支持说明文字
  - `\subsubsection`、`\paragraph`、`enumerate`、`itemize` 已配置格式

## 使用方法

1. 在 `nsfc-main.tex` 中切换 `draft`/`final` 模式：
   ```latex
   \usepackage[draft]{nsfc}  % 或 \usepackage[final]{nsfc}
   ```

2. 填写项目信息：
   ```latex
   \nsfcProjectTitle{（填写项目名称）}
   \nsfcKeywordsZH{关键词1；关键词2；关键词3}
   \nsfcKeywordsEN{keywords1; keywords2; keywords3}
   ```

3. 编译文档：
   ```bash
   pdflatex nsfc-main.tex
   bibtex nsfc-main
   pdflatex nsfc-main.tex
   pdflatex nsfc-main.tex
   ```

## 文件说明

- `nsfc-main.tex`：主文档文件
- `nsfc.sty`：样式包文件
- `nsfc-refs.bib`：参考文献数据库

## 注意事项

- 正文使用宋体小四号，行距 22 磅
- 标题使用楷体四号
- 行号仅在 `draft` 模式下显示
- 字数统计为估算值，仅供参考

