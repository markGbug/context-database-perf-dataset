# Agent Context 文件解析测试数据集

中文 | [English](README.md)

本仓库用于提供 Agent Context 产品在不同格式文件解析场景下的测试数据集。

数据集按文件类型拆分到不同分支中维护。每个分支聚焦一种或一类文件格式，方便独立扩充、回归测试和性能评估。`main` 分支仅保留仓库说明和分支索引，不直接承载具体测试数据。

## 分支列表

| 分支 | 数据类型 | 说明 |
| --- | --- | --- |
| `markdown` | Markdown | Markdown 文档解析测试数据，包括多层级目录、长文本、章节笔记和原子知识点卡片等场景。 |
| `pdf` | PDF | PDF 文件解析测试数据，用于验证版面、分页、文本抽取和结构还原能力。 |
| `csv` | CSV | CSV 表格数据解析测试数据，用于验证分隔符、表头、字段类型、缺失值和大文件处理。 |
| `image` | Image | 图片解析测试数据，用于验证 OCR、图片内容理解、图文混排和视觉信息抽取。 |
| `ppt` | PowerPoint | 演示文稿解析测试数据，用于验证 slide 结构、文本框、图片、表格和阅读顺序。 |
| `word` | Word | Word 文档解析测试数据，用于验证段落、标题、列表、表格、页眉页脚和样式结构。 |
| `excel` | Excel | Excel 工作簿解析测试数据，用于验证多 sheet、公式、合并单元格、表格区域和数据类型。 |

## 使用方式

切换到对应分支查看或维护某类格式的数据集：

```bash
git switch markdown
git switch pdf
git switch csv
git switch image
git switch ppt
git switch word
git switch excel
```

新增测试数据时，请优先放到对应格式分支中，并在该分支 README 中补充数据规模、来源说明、目录结构和适用测试场景。

## 数据集目标

- 覆盖 Agent Context 产品常见的文件解析输入格式。
- 为解析质量、性能、稳定性和回归测试提供可复用样本。
- 支持按文件类型独立扩展，避免不同格式的数据互相干扰。
- 保留足够复杂的真实结构，例如长文档、多层目录、表格、图片、分页、多 sheet 或多 slide。

## 贡献者

<a href="https://github.com/markGbug/context-database-perf-dataset/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=markGbug/context-database-perf-dataset&amp;columns=12&amp;max=120" alt="contributors" />
</a>

## 许可证

本仓库使用 [Apache License 2.0](LICENSE) 许可证。
