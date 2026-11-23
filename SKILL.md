---
name: my-hapname
description: 查询人类 mtDNA 单倍群的谱系、上下游、MRCA、macro-haplogroup 归类和定义突变（Mitotree / PhyloTree）。Query human mtDNA haplogroup lineage, descendants, MRCA, macro-haplogroup and defining mutations.
---

# my_hapname

内置 Mitotree 20260601（默认）与 PhyloTree Build 17.2，单文件，仅需 Python 3。

## 安装

```bash
pip install git+https://github.com/Victory-Hugo/S5-MY-Hapname.git
```

## 常用命令

```bash
my_hapname info H1a1                    # 层级、突变、macro 等汇总
my_hapname lineage H1a1                 # 从根到该单倍群的上游路径
my_hapname children H1a                 # 直接下游
my_hapname descendants H1a --depth 2    # 两层以内的全部下游
my_hapname mrca H1a1 H2a                # 最近共同祖先
my_hapname find "H1a*"                  # 按名称搜索
my_hapname mutation A235G               # 按定义突变搜索
my_hapname macro M7b1a H1a1 D4a1        # macro 归类（v1 / v2），可一次查多个
my_hapname by-macro D                   # 反查 macro 下的单倍群
my_hapname -t phylotree17 lineage H1a1  # 改用 PhyloTree Build 17
my_hapname --json info H1a1             # JSON 输出
```

## 规则

- 单倍群的上下游、macro 归类一律以查询结果为准，不凭记忆推断。
- 批量查询时把多个单倍群一次传给 `macro`，输出为带表头的 TSV，可直接解析。
- 查不到时命令会给出相近名称，据此改正后重查。
- 汇报结果时写明所用的树（`my_hapname trees` 可列出）。
