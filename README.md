# TJA Title & Subtitle Swap Utility (`tool-tja-swap`)

<p align="center">
  <img src="https://img.shields.io/badge/Format-Taiko%20no%20Tatsujin%20(.tja)-e60012.svg?style=flat-square" alt="TJA Format">
  <img src="https://img.shields.io/badge/Language-Python%203-3776ab.svg?style=flat-square" alt="Python 3">
  <img src="https://img.shields.io/badge/Target-ESE%20Project%20%7C%20TJAPlayer-orange.svg?style=flat-square" alt="Target">
  <img src="https://img.shields.io/badge/Encoding-UTF--8%20with%20BOM%20(utf--8--sig)-brightgreen.svg?style=flat-square" alt="Encoding">
</p>

[中文说明](#中文说明) · [English](#english)

---

## 中文说明

专为太鼓达人（Taiko no Tatsujin）模拟器（如 ESE Project、TJAPlayer 等）谱面制作设计的轻量 Python 自动化批处理脚本。用于批量互换 `.tja` 谱面文件头部的主副标题及多语言本地化字段。

### 字段互换处理逻辑

脚本针对目标目录下所有 `.tja` 文件的前 10 行头部元数据进行智能匹配与双向对调：
- **标题对调**：优先互换 `TITLE` $\leftrightarrow$ `TITLEJA`（日文主副标题），若无则互换 `TITLE` $\leftrightarrow$ `TITLEZH`（中文主副标题）；
- **副标题对调**：优先互换 `SUBTITLE` $\leftrightarrow$ `SUBTITLEJA`，若无则互换 `SUBTITLE` $\leftrightarrow$ `SUBTITLEZH`；
- **编码与数据安全**：以 `utf-8-sig` (带 BOM 的 UTF-8) 格式安全读写，严防乱码，且绝不改动头部 10 行以外的实际音符节奏谱面数据。

### 使用方法

> [!TIP]
> 运行批量修改前，建议对原始谱面文件夹进行副本备份。

```powershell
# 1. 克隆工具
git clone https://github.com/Electr0Whale/tool-tja-swap.git
cd tool-tja-swap

# 2. 运行脚本
python modify_tja_files.py
```

在终端提示中输入包含 `.tja` 文件的路径即可完成一键批量互换。

---

## English

A batch Python utility for swapping localized `TITLE` and `SUBTITLE` fields in Taiko no Tatsujin `.tja` chart files, primarily used when converting chart sets for ESE Project or TJAPlayer.

### Behavior
- Header line inspection (first 10 lines only)
- Swaps `TITLE` $\leftrightarrow$ `TITLEJA` (or `TITLEZH`)
- Swaps `SUBTITLE` $\leftrightarrow$ `SUBTITLEJA` (or `SUBTITLEZH`)
- Preserves full chart payload with `utf-8-sig` encoding
