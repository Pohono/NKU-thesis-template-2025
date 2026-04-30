# 南开大学本科毕业论文（设计）LaTeX 模板（2025 版）

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> 本模板为基于 [Tr0py/NKU-thesis-template-2020](https://github.com/Tr0py/NKU-thesis-template-2020) 升级的 2025 年版本，删去了原模板中大量本科生毕业论文不需要的分支，依据南开大学教务部 2025 年《本科毕业论文（设计）指导手册》全面重写了模板样式和文档示例。  

## 特色

- **严格遵循 2025 年学校格式要求**：正文小四号宋体、1.5 倍行距、脚注、图表标题、页眉页脚、页码均已自动完成。
- **封面信息宏配置**：通过 `\NKTsetup{...}` 设置中英文题目（支持第二行/第三行）、学号、姓名、指导教师等信息，无需手动调整。
- **摘要环境**：提供 `zhaiyao`（中文摘要）、`abstract`（英文摘要）、`guanjianci`、`keywords` 等环境，自动排版。
- **参考文献**：使用 `natbib` + `gbt7714-numerical` 宏包，只需准备 `.bib` 文件并按顺序引用。
- **附录支持**：提供 `\NKTappendix` 命令，生成符合手册的附录标题。
- **强制 XeLaTeX 编译**：模板检测引擎，若未使用 XeLaTeX 将报错退出。
- **内置字体设置**：使用 `fonts/` 目录下的 TrueType 字体，免去系统字体依赖。

## 编译环境

- 操作系统：Windows / macOS / Linux
- 发行版：TeX Live 2022 及以上（或 MikTeX）
- 编译链：
  ```bash
  xelatex main.tex
  bibtex main.aux
  xelatex main.tex
  xelatex main.tex
  ```
  或使用 latexmk：
  ```bash
  latexmk -xelatex main.tex
  ```

## 快速上手

1. 克隆或下载本仓库，切换到 `2025` 分支。
2. 确保 `fonts/` 目录下有所需字体文件（见下方字体清单）。
3. 在 `main.tex` 中修改封面信息：
   ```latex
   \NKTsetup{
     论文题目(中文) = 你的论文题目,
     论文题目(中文)(第二行) = 副标题（可选）,
     论文题目(英文) = {Your Thesis Title},
     论文题目(英文)(第二行) = {Subtitle (optional)},
     学号 = 20250001,
     姓名 = 某某某,
     年级 = 2025,
     专业 = 经济学,
     系别 = 经济学系,
     学院 = 经济学院,
     指导教师 = 某某教授,
     完成日期 = 2025年5月,
   }
   ```
4. 在 `zhaiyao`、`abstract` 等环境中填入摘要、关键词。
5. 按章节撰写正文，引用文献可使用 `\cite{key}`。
6. 编辑 `nkthesis.bib` 添加你的参考文献条目。
7. 编译生成 PDF。

## 文件结构

```
NKU-thesis-template-2020/
├── main.tex                # 主文档，填写内容
├── NKThesis.sty            # 模板样式文件（已包含 hyperref 等）
├── nkthesis.bib            # 参考文献数据库
├── figures/                # 插图目录
│   └── nankaidaxue.pdf     # 校名图片（封面使用）
├── fonts/                  # 字体文件（必须）
│   ├── SIMSUN.ttf
│   ├── simkai.ttf
│   ├── cusongti.ttf
│   ├── FZCKW.ttf
│   ├── simfang.ttf
│   ├── SimHei.ttf
│   ├── times.ttf
│   ├── timesbd.ttf
│   ├── timesbi.ttf
│   └── timesi.ttf
└── README.md
```

## 字体说明

模板默认使用 `fonts/` 目录下的字体，包括：

| 文件名        | 用途               |
|---------------|--------------------|
| SIMSUN.ttf    | 宋体（正文）       |
| SimHei.ttf    | 黑体（标题）       |
| simkai.ttf    | 楷体（封面信息）   |
| cusongti.ttf  | 粗宋体（校名）     |
| FZCKW.ttf     | 可能为备用字体     |
| simfang.ttf   | 仿宋               |
| times*.ttf    | Times New Roman 英文 |

> **版权提醒**：请确保你拥有这些字体的合法使用权。模板仅提供字体调用路径，不直接分发受版权保护的字体文件。如果无法获取上述字体，可以修改 `NKThesis.sty` 中的字体设置，替换为系统已安装的字体。

## 常见问题

**Q：编译时提示 `NKThesis.sty: XeLaTeX is required`**  
A：请使用 XeLaTeX 引擎编译，不要用 pdfLaTeX 或 LuaLaTeX。

**Q：中文显示为空白或乱码**  
A：检查 `fonts/` 目录下的字体文件是否齐全，并且文件名与 `NKThesis.sty` 中设置一致（区分大小写）。

**Q：参考文献没有按引用顺序排列**  
A：模板已设置 `\bibliographystyle{gbt7714-numerical}`，请确保用 `natbib` 宏包，且 BibTeX 编译成功。

**Q：如何添加附录？**  
A：在正文结束、`\bibliography` 之前使用 `\NKTappendix` 命令，然后写入附录内容。

**Q：封面第二行题目不想要怎么办？**  
A：在 `\NKTsetup` 中不写 `论文题目(中文)(第二行)` 或将其置为 `{}` 即可自动隐藏。

## 致谢

本模板基于 [Tr0py/NKU-thesis-template-2020](https://github.com/Tr0py/NKU-thesis-template-2020) 修改，遵循原仓库许可证。感谢原作者的贡献与维护。

## 许可证

MIT License. 欢迎自由使用、修改与分发。
