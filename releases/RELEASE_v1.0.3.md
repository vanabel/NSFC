# MNSFC v1.0.3

数学类国家自然科学基金申请书 LaTeX 模板 v1.0.3

## 安装

- **从源码构建**：`make pkg` 后使用 `make install`（系统）或 `make install-user`（用户目录），详见 [README - 安装样式包](https://github.com/vanabel/MNSFC#安装样式包)。
- **预生成文件**：下载下方 **Source code (zip)** 解压后，将 `mnsfc.sty` 放入项目目录或 TEXMF 的 `tex/latex/mnsfc/`。

## 本版变更

### 构建与安装

- **Makefile** 新增 `make install`、`make install-user`，按 TEXMF 标准安装到 `tex/`、`source/`、`doc/`、`doc/.../examples/`。
- 使用 `kpsewhich -var-value TEXMFLOCAL` / `TEXMFHOME` 确定安装路径，无需写死绝对路径。

### 文档 (README)

- 新增**安装样式包**说明：自动安装（推荐）、用户目录、系统本地树、与文档同目录，以及 `kpsewhich mnsfc.sty` 检查方式。
- 新增**参考文献与 arXiv 支持**：配合 [AMSRefs-arXiv-Support](https://github.com/vanabel/AMSRefs-arXiv-Support) 的安装、`\BibSpec{misc}{...}` 配置与 .bib 示例。

### 模板行为

- **paragraph** 标题：标题与正文之间使用加粗句号分隔（`aftername = {\textbf{.}}`）。
- 示例文档与 dtx 示例统一为 `[final]` 及通用示例文字。

---

**完整变更**：见 [Compare v1.0.2...v1.0.3](https://github.com/vanabel/MNSFC/compare/v1.0.2...v1.0.3)。
