# 北工大答辩 Beamer 模板（中文简洁版）

> ⚠️ **非官方模板**：本项目由个人维护，与北京工业大学官方无关，不代表学校立场。

从一份实际的硕士答辩简报中剥离内容后得到的纯模板，适合硕士 / 博士答辩。
主题使用 `CambridgeUS + seahorse`——学术场合常见、清爽，不花哨。

## 环境要求

| 工具 | 说明 |
|---|---|
| **TeX 发行版** | TeX Live 2020+（推荐）、MacTeX 2020+、MiKTeX |
| **编译引擎** | **XeLaTeX**（必须，ctexbeamer 需要） |
| **ctex 包** | 已包含在 TeX Live / MacTeX 完整安装中 |

### 安装 TeX 发行版

**macOS**
```bash
# 推荐：MacTeX（约 5 GB，包含全部宏包）
brew install --cask mactex

# 或轻量版（需手动安装缺失宏包）
brew install --cask mactex-no-gui
```

**Windows**
下载并安装 [TeX Live](https://tug.org/texlive/)（选 full scheme）或 [MiKTeX](https://miktex.org/download)。

**Linux**
```bash
# Ubuntu / Debian
sudo apt install texlive-full

# Arch
sudo pacman -S texlive-most
```

**Overleaf**（无需本地安装）：新建项目 → 上传所有文件 → 编译器改为 **XeLaTeX**。

## 目录结构

```
beamer_defense_template/
├── defense.tex          # 主文件（填写内容的地方）
├── README.md
└── figs/
    └── bjut_logo_color.pdf   # 封面 logo（替换为自己学校的）
```

## 编译方法

```bash
xelatex defense
xelatex defense    # 第二次以正确生成页码
```

或使用 latexmk（自动判断编译次数）：
```bash
latexmk -xelatex defense
```

## 使用步骤

### 第一步：填写论文信息

打开 `defense.tex`，修改开头标有 `% <-- 填` 的几行：

```latex
\title{论文完整题目}                       % ← 改这里
\subtitle{硕士 / 博士学位论文答辩}        % ← 改这里（或删除）
\author{作者姓名}                          % ← 改这里
\institute{学院 \\ 北京工业大学 \\ \medskip 导师：\emph{导师姓名}~教授}    % ← 改学院
\date{2025年6月}                          % ← 改这里
```

### 第二步：替换 logo

把 `figs/bjut_logo_color.pdf` 替换为自己学校的 logo，或直接删除这一行：
```latex
\titlegraphic{\includegraphics[height=1.3cm]{figs/bjut_logo_color.pdf}}
```

### 第三步：逐张填内容

> **答辩流程参考**：报告约 20 分钟，随后委员提问约 10 分钟。具体要求以《北京工业大学研究生工作手册》及所在学院通知为准。

模板共 9 张幻灯片，内容结构仅供参考，请根据自身学科和研究内容自行调整：

| # | 内容（参考） |
|---|---|
| 1 | 封面 |
| 2 | 研究背景与目标 |
| 3 | 设置与符号 |
| 4 | 核心定理 |
| 5 | 算例一 |
| 6 | 算例二 |
| 7 | 总结与展望 |
| 8 | 感谢 |
| 9+ | 备用（按需复制） |

需要更多算例：复制第 5 或第 6 个 frame 块粘贴即可。

**第四步：准备备用幻灯片**

针对预期的委员提问，每张备用幻灯片对应一个问题（建议 3–8 张）。
复制 `defense.tex` 末尾的备用 frame 块即可。

## 常用 Beamer 语法速查

```latex
% 分栏（左文字右图）
\begin{columns}[T]
  \begin{column}{0.50\textwidth} ... \end{column}
  \begin{column}{0.48\textwidth} ... \end{column}
\end{columns}

% 强调文字
\alert{重要内容}

% 带标题的色块
\begin{block}{定理名称} ... \end{block}

% 逐步显示
\pause

% 带编号公式
\begin{equation} E = mc^2 \end{equation}
```

## 许可证

MIT License — 可自由使用、修改、再发布。
