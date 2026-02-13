# mNSFC Proposal Template

[![License](https://img.shields.io/badge/license-LPPL%201.3c-blue.svg)](http://www.latex-project.org/lppl.txt)
[![Version](https://img.shields.io/badge/version-v1.0.2-green.svg)](https://github.com/vanabel/MNSFC/releases)
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

### 安装样式包

将 `mnsfc.sty` 安装到 TeX 能找到的位置后，可在任意文档中 `\usepackage{mnsfc}` 使用。

**自动安装（推荐）**

按 TEXMF 标准一次性安装（sty → `tex/`，dtx/ins → `source/`，pdf → `doc/`，示例 → `doc/.../examples/`）：

```bash
make pkg doc
make install       # 系统：安装到 TEXMFLOCAL（需 sudo）
# 或
make install-user  # 用户：安装到 TEXMFHOME，无需 sudo
```

**方式一：用户目录（手动）**

```bash
# 1. 查看你的 TEXMFHOME（用户级 tex 树）
kpsewhich -var-value TEXMFHOME
# 若为空，默认为 ~/texmf 或 ~/Library/texmf (macOS)

# 2. 在 TEXMFHOME 下建目录并复制 .sty
mkdir -p "$(kpsewhich -var-value TEXMFHOME)/tex/latex/mnsfc"
cp mnsfc.sty "$(kpsewhich -var-value TEXMFHOME)/tex/latex/mnsfc/"

# 3. 刷新文件名数据库（TeX Live）
mktexlsr
```

**方式二：系统本地树（texmf-local）**

安装到 TeX Live 的本地树后，所有用户均可使用：

```bash
# 1. 查看 TEXMFLOCAL 路径（本地树，随 TeX Live 安装位置变化）
kpsewhich -var-value TEXMFLOCAL

# 2. 创建目录并复制 .sty
sudo mkdir -p "$(kpsewhich -var-value TEXMFLOCAL)/tex/latex/mnsfc"
sudo cp mnsfc.sty "$(kpsewhich -var-value TEXMFLOCAL)/tex/latex/mnsfc/"

# 3. 刷新文件名数据库
sudo mktexlsr
```

**方式三：与文档同目录**

将 `mnsfc.sty` 放在与你的 `.tex` 文件同一目录，无需安装。

**检查是否安装成功**

```bash
# 查看 TeX 会使用到的 mnsfc.sty 的完整路径
kpsewhich mnsfc.sty
```

若输出一个路径（例如 `…/tex/latex/mnsfc/mnsfc.sty`，具体前缀由 `TEXMFLOCAL` 或 `TEXMFHOME` 决定），说明安装成功；无输出则说明当前目录或 TEXMF 中未找到 `mnsfc.sty`。

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
   \mnsfcProjectTitle{（填写项目名称）}{（Project Title）}
   \mnsfcApplicationCode{申请代码1}{申请代码2}  % 申请代码
   \mnsfcKeywordsZH{关键词1；关键词2；关键词3}
   \mnsfcKeywordsEN{keywords1; keywords2; keywords3}
   \mnsfcResearchField{主要研究领域}  % 主要研究领域（可选）
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

## 参考文献与 arXiv 支持

本模板使用 [amsrefs](https://ctan.org/pkg/amsrefs) 管理参考文献。若需要**正确显示 arXiv 预印本**（带超链接、eprint 等），可配合 [AMSRefs-arXiv-Support](https://github.com/vanabel/AMSRefs-arXiv-Support) 使用。

### 安装 AMSRefs-arXiv-Support

将所需 `.bst` 文件复制到项目目录或 TeX 能找到的路径（如 `texmf-local/bibtex/bst/`）。常用样式：

| 样式       | 文件      | 说明           |
| ---------- | --------- | -------------- |
| 数字       | amsrn.bst | 默认，如 [1]、[2] |
| 作者-年份  | amsra.bst | 如 [Smi20]     |

### 基本用法

1. **加载包**（在 `\usepackage{mnsfc}` 之前或之后均可，amsrefs 选项按需选择）：

   ```latex
   \usepackage[backref=page]{hyperref}   % 需要引文页码时
   \usepackage[alphabetic,abbrev,lite,msc-links]{amsrefs}
   ```

2. **配置 arXiv 条目**（重要）：在加载 amsrefs 之后添加下列 `\BibSpec`，否则 arXiv 条目可能格式异常：

   ```latex
   \BibSpec{misc}{%
     +{} {\PrintAuthors} {author}
     +{,} { \textit} {title}
     +{,} { } {date}
     +{,} { } {eprint}
     +{,} { } {note}
     +{.} {} {transition}
   }
   ```

3. **正文中引用**：与平时一致，用 `\cite{key}`，参考文献处用本模板命令 `\mnsfcReferences{你的bib文件名}`。

### .bib 中 arXiv 示例

```bibtex
@misc{Parker2022,
    title={Concentrating Local Solutions of the Two-Spinor Seiberg-Witten Equations},
    author={Gregory J. Parker},
    year={2022},
    eprint={2210.08148},
    archivePrefix={arXiv},
    primaryClass={math.DG},
}
```

更多选项（手工标签、biblist 等）见 [AMSRefs-arXiv-Support 说明](https://github.com/vanabel/AMSRefs-arXiv-Support)。

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
