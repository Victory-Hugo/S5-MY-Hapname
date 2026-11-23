# MY-HapName

[中文](README.md) | [English](README_EN.md)

Query and standardize human mtDNA haplogroup nomenclature, with **Mitotree 20260601** and **PhyloTree Build 17.2** built in. Single file, Python 3 only, no other dependencies.

## Install

```bash
pip install git+https://github.com/Victory-Hugo/S5-MY-Hapname.git
```

Without pip, download the single file (Linux / macOS / WSL):

```bash
mkdir -p ~/.local/bin && curl -fsSL https://raw.githubusercontent.com/Victory-Hugo/S5-MY-Hapname/main/my_hapname.py -o ~/.local/bin/my_hapname && chmod +x ~/.local/bin/my_hapname
```

Windows: download [my_hapname.py](https://raw.githubusercontent.com/Victory-Hugo/S5-MY-Hapname/main/my_hapname.py) and run it with `python my_hapname.py`.

## Usage

```bash
my_hapname --help
```

Most common examples:

```bash
my_hapname trees                          # list embedded trees
my_hapname lineage H1a1                   # path from root to H1a1
my_hapname info H1a1                      # level, mutations, macro, etc.
my_hapname children H1a                   # direct descendants
my_hapname descendants H1a --depth 2      # descendants within 2 levels
my_hapname mrca H1a1 H2a                  # most recent common ancestor
my_hapname find "H1a*"                    # search by name
my_hapname mutation A235G                 # search by defining mutation
my_hapname macro M7b1a H1a1 D4a1          # macro-haplogroup (v1 / v2)
my_hapname by-macro D                     # haplogroups under macro D
my_hapname newick H1a > H1a.nwk           # export a Newick subtree
my_hapname -t phylotree17 lineage H1a1    # use PhyloTree Build 17
my_hapname --json info H1a1               # JSON output
```

Python:

```python
from my_hapname import lineage, mrca, macro

lineage("H1a1")
mrca("H1a1", "H2a")
macro("M7b1a")
```

## License

MIT
