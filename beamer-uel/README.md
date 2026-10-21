# beamer-uel

Compact 16:9 Beamer theme for the Universidade Estadual de Londrina, with the
Departamento de Computação (DC) logo. Written for 10pt text.

| Title slide | Content slide |
|---|---|
| ![Title slide](previews/title.png) | ![Blocks slide](previews/blocos.png) |

Colours: Verde UEL for structure, DC blue for emphasis, examples and links.
Type: Faustina for titles and Lato for body text, as in the identity manual.

## Usage

Requires **XeLaTeX or LuaLaTeX**. Lato must be installed
([Google Fonts](https://fonts.google.com/specimen/Lato)); Faustina is bundled in
`../fonts/` (SIL OFL, see `../fonts/OFL.txt`).

```sh
cd beamer-uel
latexmk exemplo.tex      # builds exemplo.pdf with XeLaTeX
```

```latex
\documentclass[aspectratio=169,10pt]{beamer}
\usetheme{UEL}
```

The theme looks for `fonts/` and `img/logos/pdf/` in the document's directory
and its parent. To use it elsewhere, copy the three `.sty` files and those two
directories next to your `.tex`, or point to them with the options below.

| Option | Effect |
|---|---|
| `fontpath=<dir>` | directory with the Faustina `.ttf` files |
| `logopath=<dir>` | directory with the logo PDFs |
| `nodc` | leave out the DC logo (plain UEL slides) |
| `nowatermark` | no translucent symbol on title and section slides |
| `nosectionpage` | no automatic divider slide at each `\section` |

Use `\maketitle` for the title slide. Set short forms for the footer with
`\title[short]{...}` and `\author[short]{...}`.
