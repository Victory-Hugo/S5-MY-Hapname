# MY-HapName

[中文](README.md) | [English](README_EN.md)

人类 mtDNA 单倍群命名查询与标准化工具，内置 **Mitotree 20260601** 与 **PhyloTree Build 17.2** 两棵树。单文件，只需 Python 3，无其他依赖。

## 安装

```bash
pip install git+https://github.com/Victory-Hugo/S5-MY-Hapname.git
```

不用 pip，直接下载单个文件（Linux / macOS / WSL）：

```bash
mkdir -p ~/.local/bin && curl -fsSL https://raw.githubusercontent.com/Victory-Hugo/S5-MY-Hapname/main/my_hapname.py -o ~/.local/bin/my_hapname && chmod +x ~/.local/bin/my_hapname
```

Windows：下载 [my_hapname.py](https://raw.githubusercontent.com/Victory-Hugo/S5-MY-Hapname/main/my_hapname.py)，用 `python my_hapname.py` 运行。

## 使用

```bash
my_hapname --help
```

常用示例：

```bash
my_hapname trees                          # 列出内嵌的树
my_hapname lineage H1a1                   # 从根到 H1a1 的上游路径
my_hapname info H1a1                      # 层级、突变、macro 等汇总
my_hapname children H1a                   # 直接下游
my_hapname descendants H1a --depth 2      # 两层以内的全部下游
my_hapname mrca H1a1 H2a                  # 最近共同祖先
my_hapname find "H1a*"                    # 按名称搜索
my_hapname mutation A235G                 # 按定义突变搜索
my_hapname macro M7b1a H1a1 D4a1          # macro-haplogroup 归类（v1 / v2）
my_hapname by-macro D                     # 反查 macro D 下的单倍群
my_hapname newick H1a > H1a.nwk           # 导出 Newick 子树
my_hapname -t phylotree17 lineage H1a1    # 改用 PhyloTree Build 17
my_hapname --json info H1a1               # JSON 输出
```

Python 调用：

```python
from my_hapname import lineage, mrca, macro

lineage("H1a1")
mrca("H1a1", "H2a")
macro("M7b1a")
```

## 许可

MIT
