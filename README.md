# CRI Beamer Template

A LaTeX Beamer template with a color scheme matching the CRI - FEM (Fondazione E. Mach) institutional style.

Two preamble files are provided:

- **`cri_preamble.tex`** — current template. Custom header (FEM logo), footer (email + slide number), rounded blocks with shadow, no navigation symbols.
- **`mypreamble.tex`** — older template based on the Madrid theme with the original CRI yellow/blue palette.

---

## Usage in R Markdown

In your `.Rmd` YAML front matter:

```yaml
---
title: "My Talk"
author: "Your Name"
date: "\\scriptsize \\textit{your.email@fmach.it}"
output:
  beamer_presentation:
    latex_engine: pdflatex
    includes:
      in_header: "cri_preamble.tex"
---
```

Make sure `cri_preamble.tex` and `fem_logo.png` are in the same directory as the `.Rmd` file. Render with RStudio's **Knit** button or from the terminal:

```bash
Rscript -e "rmarkdown::render('your_talk.Rmd')"
```

---

## Usage in standard LaTeX

```latex
\documentclass{beamer}

\input{cri_preamble}   % or \input{mypreamble}

\title{My Talk}
\author{Your Name}
\date{\scriptsize \textit{your.email@fmach.it}}

\begin{document}

\maketitle

\begin{frame}{First Slide}
  Content here.
\end{frame}

\end{document}
```

Make sure `cri_preamble.tex` and `fem_logo.png` are in the same directory. Compile with:

```bash
pdflatex your_talk.tex
```

---

## Color scheme

| Name | Hex | Usage |
|---|---|---|
| `MachGreen` | `#3C5454` | Headers, footers, block titles |
| `MachLightGreen` | `#8CB932` | Bullet points, separator line |
| `MachGray` | `#F5F5F5` | Block bodies |

To use a different email in the footer, edit the `\textit{...}` line inside `\setbeamertemplate{footline}` in `cri_preamble.tex`.
