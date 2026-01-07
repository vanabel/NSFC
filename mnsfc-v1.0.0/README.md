# MNSFC Proposal Template

[![License](https://img.shields.io/badge/license-LPPL%201.3c-blue.svg)](http://www.latex-project.org/lppl.txt)
[![Version](https://img.shields.io/badge/version-v1.0.0-green.svg)](https://github.com/vanabel/MNSFC/releases)
[![LaTeX](https://img.shields.io/badge/LaTeX-2.09%2B-orange.svg)](https://www.latex-project.org/)

数学类国家自然科学基金申请书 LaTeX 模板

## 从源代码生成文件

本项目使用 DTX (DocStrip) 格式，所有文件都从 `mnsfc.dtx` 生成。

### 生成步骤

```bash
# 1. 生成样式包和示例文件
make pkg

# 这会生成：
# - mnsfc.sty (样式包)
# - mnsfc.ins (安装脚本，自动生成)
# - mnsfc-main.tex (示例主文档)
# - mnsfc-refs.bib (示例参考文献)
# - README.txt (简要说明)
```

### 编译文档

```bash
# 编译示例文档
make main

# 或编译完整文档（包括包文档）
make all

# 查看所有可用命令
make help
```

## 功能特性

- **双模式支持**：`draft` 模式（显示辅助信息）和 `final` 模式（仅显示正文）
- **NSFC 规范格式**：A4 纸张，小四号宋体，22 磅行距，符合 NSFC 要求
- **标题格式**：支持 section/subsection/subsubsection/paragraph，自动编号
- **行号功能**：draft 模式下自动显示行号（每 5 行一次）
- **字数统计**：基于行号自动计算正文字数
- **参考文献**：支持 `amsrefs` 包，自动生成 MR 链接
- **列表环境**：自动配置 enumerate 和 itemize 格式

详细功能说明和使用方法请参考 `mnsfc.dtx` 编译生成的文档（运行 `make doc`）。

## 快速开始

1. **生成文件**：
   ```bash
   make pkg
   ```

2. **编辑示例文档**：
   编辑 `mnsfc-main.tex`，设置项目信息：
   ```latex
   \mnsfcProjectTitle{（填写项目名称）}
   \mnsfcKeywordsZH{关键词1；关键词2；关键词3}
   \mnsfcKeywordsEN{keywords1; keywords2; keywords3}
   ```

3. **切换模式**：
   ```latex
   \usepackage[draft]{mnsfc}  % 或 [final]
   ```

4. **编译**：
   ```bash
   make main
   ```

## 文件说明

- `mnsfc.dtx` - 源代码文件（包含所有代码和文档）
- `mnsfc.sty` - 样式包（从 `mnsfc.dtx` 生成）
- `mnsfc.ins` - 安装脚本（从 `mnsfc.dtx` 生成）
- `mnsfc-main.tex` - 示例主文档（从 `mnsfc.dtx` 生成）
- `mnsfc-refs.bib` - 示例参考文献（从 `mnsfc.dtx` 生成）
- `Makefile` - 编译自动化脚本
- `.latexmkrc` - latexmk 配置文件

**注意**：所有生成的文件（`.sty`, `.ins`, `.tex`, `.bib`, `.pdf` 等）都在 `.gitignore` 中，不会被版本控制。只跟踪源文件 `mnsfc.dtx`。

## 依赖要求

- LaTeX2e
- XeLaTeX（推荐，支持中文字体）
- 必需包：`ctex`, `geometry`, `setspace`, `fancyhdr`, `lastpage`, `refcount`, `graphicx`, `xcolor`, `hyperref`, `bookmark`, `enumitem`, `amsmath`, `amssymb`, `microtype`, `environ`, `etoolbox`, `xparse`, `totcount`, `lineno`
- 可选包：`amsrefs`（用于参考文献）

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！

## 📄 许可证

本项目采用 [LaTeX Project Public License (LPPL) v1.3c](http://www.latex-project.org/lppl.txt) 许可证。

## 👤 作者

**Van Abel**
- Email: van141.abel@gmail.com
- GitHub: [@vanabel](https://github.com/vanabel)

## 🙏 致谢

本项目最初开发于2026年，用于准备面上项目。感谢所有贡献者和使用者！

---

⭐ 如果这个项目对你有帮助，请给个 Star！
