# scripts/

**这里是运行版。正本在 [`research-workflow`](https://github.com/crce-ux/research-workflow) 的 `scripts/`**——开发与测试都在总仓。

改脚本请改总仓，再同步过来；**不要只改这里**。

| 脚本 | 干什么 | 服务于 |
|---|---|---|
| `check_note.py` | 笔记机检：必备信息 / 标注使用 / **定位方式与引用形式一致** | 笔记口径 |
| `build_daily_ref.py` | 由 `_文献表.json` 生成 15 列文献表 | 回填 |
| `check_skill_structure.py` | 结构校验（官方 Agent Skills 规范）+ 声明落地 | — |
| `selfcheck.py` | 一条命令自检：结构 + 语法 + 依赖 | — |

## 依赖

| 脚本 | 依赖 |
|---|---|
| `check_note.py` · `check_skill_structure.py` | 标准库 |
| `build_daily_ref.py` | `openpyxl` |

## 边界

**脚本只做可自动化的部分。**

`check_note.py` 只查「**有没有标**」，**不查「标得对不对」**——
这句到底算 `[Analysis]` 还是 `[Paper]`，是语义，人工过。

它最重要的是 **N3**：标了 `source-limited`（仅摘要）却引用 `Table 2` 或 `PDF p.3`——
摘要里没有表格页码，**属于编造**。

## 自检

```bash
python scripts/selfcheck.py --strict
```
