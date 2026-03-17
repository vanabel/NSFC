# MNSFC v1.0.4

数学类国家自然科学基金申请书 LaTeX 模板 v1.0.4

## 安装

- **从源码构建**：`make pkg` 后使用 `make install`（系统）或 `make install-user`（用户目录），详见 [README - 安装样式包](https://github.com/vanabel/MNSFC#安装样式包)。
- **预生成文件**：下载下方 **Source code (zip)** 解压后，将 `mnsfc.sty` 放入项目目录或 TEXMF 的 `tex/latex/mnsfc/`。

## 本版变更

### 模板行为

- 新增数学公式上下间距微调宏：通过重定义 `\selectfont`，在不改变用户文档用法的前提下，将行间公式与正文之间的垂直间距统一为更紧凑的设置（`\abovedisplayskip`, `\belowdisplayskip` 等）。
- 自动加载 `xeCJKfntef`（支持 `\uwave` 等 CJK 下划线/波浪线并可自动断行）与 `xy`（`[all]` 选项，支持 `\xymatrix` 等交换图环境）。
- 新增正文起始页设置命令 `\mnsfcBodyStartPage{<页码>}`：
  - 在英文摘要环境 `mnsfcAbstractEN` 结束后自动执行 `\setcounter{page}{<页码>}`；
  - 便于将“报告正文（2026版）”及后续内容从指定页码（例如 7 页）开始编号；
  - 若未调用该命令，则保持 TeX 默认页码计数行为不变。
 - 示例主文档 `mnsfc-main.tex` 中，“其他需要说明的情况”部分新增一段可直接使用或按需修改的**生成式人工智能使用情况声明**示例文本，方便用户按国家相关规范进行 AI 使用情况说明。

### 文档 (mnsfc.dtx & README)

- 在 `mnsfc.dtx` 文档中新增“正文起始页设置”小节，说明 `\mnsfcBodyStartPage{...}` 的用法及典型场景（封面+摘要若干页后正文从指定页起始）。
- 在 README 的“功能特性”中补充：
  - 正文起始页设置：可通过 `\mnsfcBodyStartPage{<页码>}` 指定正文起始页（通常在英文摘要结束后从第 7 页开始）。
- 在 README 的“快速开始”中提示用户可根据自身实际情况修改示例中的“生成式人工智能使用情况声明”文本。
- 在 README 的“功能特性”与“参考文献与 arXiv 支持”中，补充对 [AMSRefs arXiv Support](https://github.com/vanabel/AMSRefs-arXiv-Support) 的推荐说明，并给出可直接复制的 `\BibSpec{misc}{...}` 配置示例。
- 在 `mnsfc.dtx` 的示例主文件 `mnsfc-main.tex` 段落中，在 `amsrefs` 导入之后加入注释，提示如何结合 AMSRefs arXiv Support 配置 `\BibSpec{misc}{...}`，方便用户直接复制到自己的申请书工程中。
- 更新版本号显示为 v1.0.4。

---

**完整变更**：见 Compare v1.0.3...v1.0.4（发布时在 GitHub 上更新链接）。

