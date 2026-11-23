# S5-MY-Hapname

MY-HapName: a single-file tool to standardize and query human mtDNA haplogroup nomenclature, based on **Mitotree 20260601** and **PhyloTree Build 17.2**. Both trees are embedded in `my_hapname.py`; Python 3 only, no third-party dependencies.

MY-HapName：基于 **Mitotree 20260601** 与 **PhyloTree Build 17.2** 的人类 mtDNA 单倍群命名标准化与查询工具。两棵树均已内嵌在 `my_hapname.py` 中，仅需 Python 3，无第三方依赖。

## Usage / 使用

```bash
python3 my_hapname.py --help           # colored bilingual help / 彩色中英双语帮助
python3 my_hapname.py trees
python3 my_hapname.py lineage H1a1
python3 my_hapname.py info H1a1
python3 my_hapname.py macro M7b1a H1a1 D4a1
python3 my_hapname.py -t phylotree17 lineage H1a1
```

Linux / WSL / macOS: `chmod +x my_hapname && ./my_hapname trees`. Windows: `python my_hapname.py ...` (or `py`).

Most common examples / 常用示例:

```text
my_hapname trees                          # 列出内嵌的树
my_hapname lineage H1a1                   # 从根到 H1a1 的上游路径
my_hapname info H1a1                      # 层级、突变、macro 等汇总
my_hapname children H1a                   # 直接下游
my_hapname descendants H1a --depth 2      # 两层以内的全部下游
my_hapname mrca H1a1 H2a                  # 最近共同祖先
my_hapname find "H1a*"                    # 按名称搜索（支持通配符）
my_hapname mutation A235G                 # 按定义突变搜索
my_hapname macro M7b1a H1a1 D4a1          # 一次查多个的 macro 归类（v1/v2）
my_hapname by-macro D                     # 反查 macro D 下的单倍群
my_hapname newick H1a > H1a.nwk           # 导出 Newick 子树
my_hapname -t phylotree17 lineage H1a1    # 改用 PhyloTree Build 17
my_hapname --json info H1a1               # 以 JSON 输出
```

Colors are used only on a terminal; set `NO_COLOR=1` to disable. Piped output is plain TSV/text. / 颜色仅在终端输出时启用，设置 `NO_COLOR=1` 可关闭；管道输出为纯文本。

## Python API

```python
from my_hapname import tree, lineage, children, mrca, macro
lineage("H1a1"); mrca("H1a1", "H2a"); macro("M7b1a")
```

## License

See `LICENSE`.
