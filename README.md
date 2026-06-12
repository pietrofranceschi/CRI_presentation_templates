# CRI Presentation Templates

Presentation templates matching the CRI / FEM (Fondazione E. Mach) institutional style.
Two output formats are supported: **LaTeX Beamer** (PDF) and **reveal.js** (HTML).

**[Live reveal.js demo](https://pietrofranceschi.github.io/CRI_presentation_templates/cri_revealjs_example.html)**

---

## Requirements

**Beamer:** R, `rmarkdown` package, and a LaTeX distribution with `pdflatex` (e.g. TeX Live).

**reveal.js:** R, `rmarkdown` package, and the `revealjs` package (`install.packages("revealjs")`).

---

## Files

| File | Description |
|---|---|
| `cri_beamer_preamble.tex` | LaTeX Beamer preamble — current template |
| `cri_beamer_preamble_legacy.tex` | Older Beamer preamble (Madrid theme, original palette) |
| `cri_beamer_example.Rmd` | Example Beamer presentation via R Markdown |
| `cri_css.css` | reveal.js CSS theme |
| `cri_revealjs_example.Rmd` | Example reveal.js HTML presentation via R Markdown |
| `fem_logo.png` | FEM logo — must be in the same directory as the source file |

---

## LaTeX Beamer

### Usage in R Markdown

```yaml
---
title: "My Talk"
author: "Your Name"
date: "\\scriptsize \\textit{your.email@fmach.it}"
output:
  beamer_presentation:
    latex_engine: pdflatex
    includes:
      in_header: "cri_beamer_preamble.tex"
---
```

Render with:

```bash
Rscript -e "rmarkdown::render('your_talk.Rmd')"
```

### Layout

- **Header:** FEM logo (`fem_logo.png`) on the left, "Centro Ricerca e Innovazione" on the right.
- **Footer:** Author email on the left, slide number (`N / total`) on the right.
- Header and footer are suppressed on the title slide automatically.
- Navigation symbols are disabled.

To change the footer email, edit the `\textit{...}` line inside `\setbeamertemplate{footline}` in `cri_beamer_preamble.tex`.

### Usage in standard LaTeX

```latex
\documentclass{beamer}
\input{cri_beamer_preamble}

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

Compile with:

```bash
pdflatex your_talk.tex
```

---

## reveal.js HTML

### Usage in R Markdown

```yaml
---
title: "My Talk"
subtitle: "Optional subtitle"
author: "Your Name | your.email@fmach.it"
date: "Month Year"
output:
  revealjs::revealjs_presentation:
    css: cri_css.css
    self_contained: true
    center: false
    transition: fade
    reveal_options:
      slideNumber: "c/t"
      controls: false
      progress: false
---
```

Render with:

```bash
Rscript -e "rmarkdown::render('your_talk.Rmd')"
```

### Layout

- No header/footer bars.
- The FEM logo (`fem_logo.png`) appears as a small fixed logo in the top-right corner of every content slide; suppressed on the title slide.
- Slide titles have a MachLightGreen bottom border rule.

### CSS utility classes

| Class | Use |
|---|---|
| `.box-green` | MachGreen border, gray background |
| `.box-lightgreen` | MachLightGreen border, light green background |
| `.box-key` | Centered key-message box |
| `.box-red` | Muted red — caveats, warnings |
| `.box-blue` | Teal-blue — info, context |
| `.cols` / `.col` | Two-column layout |
| `[text]{#notes}` | MachLightGreen inline text |
| `[text]{#highlights}` | Muted red inline text |

---

## Color scheme

| Name | Hex | Usage |
|---|---|---|
| `MachGreen` | `#3C5454` | Titles, structure, strong |
| `MachLightGreen` | `#8CB932` | Bullets, accents, separators |
| `MachGray` | `#F5F5F5` | Block backgrounds |
