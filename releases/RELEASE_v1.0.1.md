# MNSFC v1.0.1

数学类国家自然科学基金申请书 LaTeX 模板 v1.0.1

**完整变更**：见 [Compare v1.0.0...v1.0.1](https://github.com/vanabel/mNSFC/compare/v1.0.0...v1.0.1)。

## 🎉 主要更新

### 模板更新

- 根据官方 NSFC Word 模板更新章节结构，使排版和条目顺序更贴近正式申请书格式。
- 重新组织“其他需要说明的情况”部分，使条目结构更清晰，便于补充说明。
- 添加生成式人工智能使用相关的详细指引和规范要求（包括声明、核实责任和禁止事项等）。

### 技术改进

- 更新文件编码声明为标准的 Emacs 兼容格式，便于编辑器自动识别。
- 初步优化代码结构与命名，提升可读性和后续维护性。

### 包命名调整

- 包从 `nsfc` 重命名为 `mnsfc`（m 表示“math”），以突出数学类模板定位。
- 所有公开命令和内部变量统一使用 `\mnsfc*` 前缀，避免与其他包冲突。
- 更新仓库名称及文档中的所有相关引用。

## 📦 安装与使用（与 v1.0.0 相比的要点）

1. **下载并解压发布包**

   ```bash
   unzip mnsfc-v1.0.1.zip
   cd mnsfc-v1.0.1
   ```

2. **生成样式包**

   ```bash
   make pkg
   ```

3. **编译示例文档**

   ```bash
   make main
   ```

4. **在自己的申请书中使用**

   ```latex
   \documentclass[UTF8,zihao=-4]{ctexart}
   \usepackage[final]{mnsfc}  % 或 [draft]

   \mnsfcProjectTitle{（填写项目名称）}
   \mnsfcKeywordsZH{关键词1；关键词2；关键词3}
   \mnsfcKeywordsEN{keywords1; keywords2; keywords3}
   ```

完整使用说明请参考发布包中的 `README.md` 与编译得到的 `mnsfc.pdf`。

