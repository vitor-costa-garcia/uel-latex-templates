# beamer-uel

Tema Beamer compacto, em 16:9, para a Universidade Estadual de Londrina, com o
logotipo do Departamento de Computação (DC). Feito para texto em 10pt.

| Slide de título | Slide de conteúdo |
|---|---|
| ![Slide de título](previews/title.png) | ![Slide de blocos](previews/blocos.png) |

Cores: Verde UEL na estrutura e azul do DC em ênfases, exemplos e links.
Tipografia: Faustina nos títulos e Lato no texto, como no manual de identidade
visual.

## Uso

Requer **XeLaTeX ou LuaLaTeX**. A Lato precisa estar instalada
([Google Fonts](https://fonts.google.com/specimen/Lato)); a Faustina já está
incluída em `../fonts/` (SIL OFL, veja `../fonts/OFL.txt`).

```sh
cd beamer-uel
latexmk exemplo.tex      # gera exemplo.pdf com XeLaTeX
```

```latex
\documentclass[aspectratio=169,10pt]{beamer}
\usetheme{UEL}
```

O tema procura `fonts/` e `img/logos/pdf/` na pasta do documento e na pasta acima
dela. Para usá-lo em outro lugar, copie os três arquivos `.sty` e essas duas
pastas para junto do seu `.tex`, ou aponte para elas com as opções abaixo.

| Opção | Efeito |
|---|---|
| `fontpath=<pasta>` | pasta com os arquivos `.ttf` da Faustina |
| `logopath=<pasta>` | pasta com os PDFs dos logotipos |
| `nodc` | omite o logotipo do DC (slides apenas da UEL) |
| `nowatermark` | sem o símbolo translúcido nos slides de título e de seção |
| `nosectionpage` | sem o slide separador automático em cada `\section` |

Use `\maketitle` para o slide de título. Defina as formas curtas do rodapé com
`\title[curto]{...}` e `\author[curto]{...}`.

Para um guia completo de como montar uma apresentação, veja o
[README principal](../README.md).
