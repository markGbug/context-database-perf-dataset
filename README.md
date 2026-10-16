# Agent Context File Parsing Test Dataset

[中文](README.zh-CN.md) | English

This repository provides test datasets for Agent Context products to evaluate file parsing across different document formats.

Datasets are managed by file type through separate Git branches. Each branch focuses on one format or format family, making it easier to expand data, run regression tests, and evaluate parsing performance independently. The `main` branch only keeps repository documentation and the branch index; concrete test datasets live in their corresponding branches.

## Branches

| Branch | Dataset Type | Description |
| --- | --- | --- |
| `markdown` | Markdown | Markdown parsing datasets, including nested directories, long documents, chapter notes, and atomic knowledge-point cards. |
| `pdf` | PDF | PDF parsing datasets for validating layout, pagination, text extraction, and structure reconstruction. |
| `csv` | CSV | CSV parsing datasets for delimiters, headers, field types, missing values, and large-file handling. |
| `image` | Image | Image parsing datasets for OCR, image understanding, mixed image-text content, and visual information extraction. |
| `ppt` | PowerPoint | Presentation parsing datasets for slide structure, text boxes, images, tables, and reading order. |
| `word` | Word | Word document parsing datasets for paragraphs, headings, lists, tables, headers, footers, and style structure. |
| `excel` | Excel | Excel workbook parsing datasets for multiple sheets, formulas, merged cells, table regions, and data types. |

## Usage

Switch to the corresponding branch to view or maintain a dataset for a specific file format:

```bash
git switch markdown
git switch pdf
git switch csv
git switch image
git switch ppt
git switch word
git switch excel
```

When adding new test data, place it in the matching format branch and update that branch's README with dataset size, source notes, directory structure, and applicable test scenarios.

## Dataset Goals

- Cover common file parsing input formats used by Agent Context products.
- Provide reusable samples for parsing quality, performance, stability, and regression tests.
- Allow each file type to evolve independently without mixing unrelated datasets.
- Preserve realistic structural complexity, such as long documents, nested directories, tables, images, pagination, multiple sheets, and multiple slides.

## Contributors

<a href="https://github.com/markGbug/context-database-perf-dataset/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=markGbug/context-database-perf-dataset&amp;columns=12&amp;max=120" alt="contributors" />
</a>

## License

This repository is licensed under the [Apache License 2.0](LICENSE).
