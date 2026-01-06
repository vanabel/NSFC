# NSFC Proposal Template

国家自然科学基金申请书 LaTeX 模板

## 功能特性

### 1. 双模式支持

- **`draft` 模式**（默认）：
  - 显示标题页（项目名称）
  - 显示中文和英文摘要
  - 显示写作提示（`\nsfcNote`）
  - 显示行号（每 5 行显示一次）
  - 显示字数统计页面
  - 显示 `zhlipsum` 占位文本

- **`final` 模式**：
  - 隐藏标题页
  - 隐藏摘要内容
  - 隐藏所有写作提示
  - 隐藏行号
  - 隐藏字数统计
  - 隐藏占位文本
  - 仅显示符合 NSFC 规范的正文内容

### 2. 页面布局与格式

- **页面设置**：
  - A4 纸张
  - 页边距：左右 30mm，上下 25mm
  - 无页眉页脚

- **正文字体与格式**：
  - 字体：宋体（`\songti`）
  - 字号：小四号（`\zihao{-4}`）
  - 行距：22 磅（`\baselineskip=22pt`）
  - 首行缩进：0.74 cm
  - 段落间距：0.45em

- **分页控制**：
  - 避免孤行和寡行（`\clubpenalty=300`, `\widowpenalty=300`）

### 3. 标题格式

- **`\section`**：
  - 格式：`（一）`、`（二）`...（中文数字）
  - 字体：楷体四号，蓝色，加粗
  - 支持可选参数：`\section[说明文字]{标题}`
  - 自动跳过行号

- **`\subsection`**：
  - 格式：`1.`、`2.`...（阿拉伯数字）
  - 字体：楷体四号，蓝色，加粗
  - 支持可选参数：`\subsection[说明文字]{标题}`
  - 自动跳过行号

- **`\subsubsection`**：
  - 格式：`(1)`、`(2)`...（带括号的阿拉伯数字）
  - 字体：宋体小四号，加粗
  - 自动跳过行号

- **`\paragraph`**：
  - 格式：不带编号
  - 字体：宋体小四号，加粗
  - 自动跳过行号

### 4. 列表环境

- **`enumerate`（有序列表）**：
  - 第一层：`1)`, `2)`, `3)`...
  - 第二层：`a)`, `b)`, `c)`...
  - 第三层：`i)`, `ii)`, `iii)`...

- **`itemize`（无序列表）**：
  - 第一层：实心圆点 `•`
  - 第二层：空心圆点 `○`
  - 第三层：短横线 `-`

- 所有列表项使用宋体小四号，首行缩进 0.74cm

### 5. 行号功能（仅 `draft` 模式）

- 自动在正文开始后启用行号
- 每 5 行显示一次行号（`mod=5`）
- 自动跳过所有标题行（section/subsection/subsubsection/paragraph）
- 行号字体：小四号无衬线字体
- 使用 `\nsfcExcludeLine{内容}` 可以排除短行（如 "无。"）的行号显示

### 6. 字数统计（仅 `draft` 模式）

- **基于行号计算**（如果启用行号）：
  - 计算公式：`字数 = (行号 - 1) × 35字/行`
  - 每行按 35 个汉字（包括符号）计算
  - 自动排除使用 `\nsfcExcludeLine` 标记的短行

- **基于页数估算**（如果未启用行号）：
  - 计算公式：`字数 ≈ 页数 × 35行/页 × 35字/行`

- 显示信息：
  - 正文总页数（不含封面和摘要）
  - 正文行数
  - 已排除短行数（如果有）
  - 正文字数估算

- 字数统计页面不显示行号

### 7. 参考文献支持

- 使用 `amsrefs` 包管理参考文献
- 提供 `\nsfcReferences{文件名}` 命令
- 自动居中显示"参考文献"标题
- 使用楷体四号标题，宋体小四号正文

### 8. 其他功能

- **项目信息**：
  - `\nsfcProjectTitle{项目名称}`
  - `\nsfcKeywordsZH{关键词1；关键词2；关键词3}`
  - `\nsfcKeywordsEN{keywords1; keywords2; keywords3}`

- **写作提示**：
  - `\nsfcNote{提示内容}`：仅在 `draft` 模式下显示灰色提示文字

- **标题页**：
  - `\nsfcTitlePage`：仅在 `draft` 模式下显示

- **摘要环境**：
  - `\begin{nsfcAbstractZH}...\end{nsfcAbstractZH}`：中文摘要
  - `\begin{nsfcAbstractEN}...\end{nsfcAbstractEN}`：英文摘要
  - 仅在 `draft` 模式下显示，`final` 模式下自动隐藏

- **自动插入正文标题**：
  - 在英文摘要结束后自动插入"报告正文（2026版）"标题
  - 自动插入格式说明文字

## 使用方法

### 1. 基本设置

在 `nsfc-main.tex` 中切换模式：

```latex
\documentclass[zihao=-4,fontset=macnew]{ctexart}
% 切换这里
\usepackage[draft]{nsfc}  % 或 \usepackage[final]{nsfc}

% 加载 amsrefs 包（可选）
\usepackage[alphabetic,abbrev,lite,msc-links]{amsrefs}
```

### 2. 填写项目信息

```latex
\nsfcProjectTitle{（填写项目名称）}
\nsfcKeywordsZH{关键词1；关键词2；关键词3}
\nsfcKeywordsEN{keywords1; keywords2; keywords3}
```

### 3. 文档结构

```latex
\begin{document}
  \nsfcTitlePage
  
  \begin{nsfcAbstractZH}
    中文摘要内容...
  \end{nsfcAbstractZH}
  
  \begin{nsfcAbstractEN}
    English abstract...
  \end{nsfcAbstractEN}
  
  \nsfcNote{正文开始...}
  
  \section[说明文字]{标题}
  正文内容...
  
  \subsection[说明文字]{标题}
  正文内容...
  
  \subsubsection{三级标题}
  正文内容...
  
  \paragraph{段落标题}
  正文内容...
  
  % 列表示例
  \begin{enumerate}
    \item 第一项
    \begin{enumerate}
      \item 子项
    \end{enumerate}
  \end{enumerate}
  
  \begin{itemize}
    \item 第一项
    \begin{itemize}
      \item 子项
    \end{itemize}
  \end{itemize}
  
  % 排除短行
  \nsfcExcludeLine{无。}
  
  % 参考文献
  \nsfcReferences{nsfc-refs}
  
  % 字数统计（仅在 draft 模式下显示）
  \nsfcWordCount
\end{document}
```

### 4. 编译文档

```bash
pdflatex nsfc-main.tex
bibtex nsfc-main
pdflatex nsfc-main.tex
pdflatex nsfc-main.tex
```

## 文件说明

- `nsfc-main.tex`：主文档文件
- `nsfc.sty`：样式包文件
- `nsfc-refs.bib`：参考文献数据库（BibTeX 格式）
- `.gitignore`：Git 忽略文件配置

## 命令参考

### 项目信息命令

- `\nsfcProjectTitle{项目名称}`：设置项目标题
- `\nsfcKeywordsZH{关键词}`：设置中文关键词
- `\nsfcKeywordsEN{关键词}`：设置英文关键词

### 文档结构命令

- `\nsfcTitlePage`：插入标题页（仅 `draft` 模式）
- `\nsfcNote{提示}`：插入写作提示（仅 `draft` 模式）
- `\nsfcReferences{文件名}`：插入参考文献（不含 `.bib` 扩展名）
- `\nsfcWordCount`：插入字数统计页面（仅 `draft` 模式）

### 行号控制命令

- `\nsfcExcludeLine{内容}`：排除短行，不显示行号（仅 `draft` 模式）

### 向后兼容命令

- `\NSFCsection[说明]{标题}`：等同于 `\section[说明]{标题}`
- `\NSFCsubsection[说明]{标题}`：等同于 `\subsection[说明]{标题}`

## 注意事项

1. **字体设置**：
   - 正文使用宋体小四号，行距 22 磅
   - 标题使用楷体四号
   - 确保系统已安装中文字体

2. **行号功能**：
   - 仅在 `draft` 模式下启用
   - 每 5 行显示一次
   - 自动跳过所有标题行

3. **字数统计**：
   - 仅在 `draft` 模式下显示
   - 基于行号计算，每行按 35 字估算
   - 为估算值，仅供参考

4. **参考文献**：
   - 需要在文档中手动加载 `amsrefs` 包
   - 使用标准 BibTeX 格式的 `.bib` 文件
   - 编译时需要运行 `bibtex`

5. **模式切换**：
   - 提交前切换到 `final` 模式
   - `final` 模式会隐藏所有辅助信息
   - 确保在 `final` 模式下检查最终输出

## 技术细节

- **依赖包**：`geometry`, `setspace`, `fancyhdr`, `lastpage`, `refcount`, `graphicx`, `xcolor`, `hyperref`, `bookmark`, `enumitem`, `amsmath`, `amssymb`, `microtype`, `environ`, `etoolbox`, `xparse`, `totcount`, `lineno`, `ctex`
- **LaTeX 版本**：LaTeX2e
- **编译引擎**：XeLaTeX（推荐，支持中文字体）或 pdfLaTeX

## 许可证

本项目为 NSFC 申请书模板，供学术研究使用。
