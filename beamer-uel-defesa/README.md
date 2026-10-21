# beamer-uel-defesa

Beamer theme for thesis (TCC) defenses at the Universidade Estadual de Londrina,
with the Departamento de Computação (DC) logo. Light and quiet, with a progress
bar above the footer to keep track of the time. Written for 10pt, 16:9.

| Title slide | Content slide |
|---|---|
| ![Title slide](previews/title.png) | ![Results slide](previews/resultados.png) |

Same palette and fonts as [`beamer-uel`](../beamer-uel/) (Verde UEL, DC blue,
Faustina and Lato), but white slides, a narrow green stripe, no section divider
slides, and defense-specific title and closing slides.

## Usage

Requires **XeLaTeX or LuaLaTeX**. Lato must be installed
([Google Fonts](https://fonts.google.com/specimen/Lato)); Faustina is bundled in
`../fonts/`.

```sh
cd beamer-uel-defesa
latexmk exemplo.tex      # builds exemplo.pdf with XeLaTeX
```

```latex
\documentclass[aspectratio=169,10pt]{beamer}
\usetheme{UELdefesa}

\title{Título do trabalho}
\subtitle{Subtítulo, se houver}
\author{Nome do Autor}
\orientador{Prof. Dr. Nome do Orientador}
\banca{Prof. Dr. Nome do Membro 2\\Profa. Dra. Nome do Membro 3}
\curso{Ciência da Computação}
\date{\today}

\begin{document}
\maketitle
% ...
\obrigado[nome.autor@exemplo.uel.br]
\end{document}
```

| Command | Effect |
|---|---|
| `\orientador{…}`, `\banca{…}` | advisor and board on the title slide (`\\` between names) |
| `\curso{…}`, `\tipotrabalho{…}`, `\local{…}` | course, type of work (default *Trabalho de Conclusão de Curso*), place (default Londrina) |
| `\obrigado[contact]` | closing slide with an optional contact line |

The progress bar counts the frames between the title and closing slides.
Set short forms for the footer with `\title[short]{…}` and `\author[short]{…}`.

| Option | Effect |
|---|---|
| `fontpath=<dir>` | directory with the Faustina `.ttf` files |
| `logopath=<dir>` | directory with the logo PDFs |
| `nodc` | leave out the DC logo (plain UEL slides) |
| `noprogress` | no progress bar |

The theme looks for `fonts/` and `img/logos/pdf/` in the document's directory
and its parent. To use it elsewhere, copy the three `.sty` files and those two
directories next to your `.tex`.
