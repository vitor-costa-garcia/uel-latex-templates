# geral

Temas Beamer compactos, em 16:9, para a Universidade Estadual de Londrina, com o
logotipo do Departamento de Computação (DC). Feitos para texto em 10pt. Para
palestras, seminários e aulas sem necessidades especiais.

| | Slide de título | Slide de conteúdo |
|---|---|---|
| **Claro** (`UEL`) | <img src="previews/title.png" width="330"> | <img src="previews/blocos.png" width="330"> |
| **Escuro** (`UELdark`) | <img src="previews/dark-title.png" width="330"> | <img src="previews/dark-blocos.png" width="330"> |

## Temas

| Tema | Aparência |
|---|---|
| `\usetheme{UEL}` | slides brancos, bloco verde no título; Verde UEL na estrutura e azul do DC em ênfases, exemplos e links |
| `\usetheme{UELdark}` | fundo verde-esmeralda escuro, versões negativas dos logotipos |

Tipografia: Faustina nos títulos e Lato no texto, como no manual de identidade
visual. O tema escuro se afasta do manual de propósito, como descrito abaixo.

### O tema escuro

- **Mantido do manual:** o Verde UEL (`#00753B`) preenche o bloco do título e os
  slides de seção; as **versões negativas (brancas) dos logotipos** são usadas em
  todo o tema; Faustina nos títulos e Lato no texto.
- **Derivado:** fundo verde-esmeralda `#0E3A2A` (do matiz do Verde UEL, no lugar do
  preto do manual, que ficava áspero demais na tela), um verde mais claro
  `#0F8A4F` para filetes, faixas e títulos de blocos, e um verde-menta `#7CE9B0`
  para marcadores, números e destaques de texto. O Verde UEL é escuro demais para
  ler sobre esse fundo.
- **Do logotipo do DC:** o azul nos blocos de exemplo, clareado (`#8DB8E6`) para
  ênfase no texto. O logotipo do DC não tem versão negativa, então fica sobre uma
  pequena placa branca; `nodc` o omite.
- O símbolo esmaecido nos slides de título e de seção lembra a capa do manual;
  `nowatermark` o remove.

## Uso

Requer **XeLaTeX ou LuaLaTeX**. A Lato precisa estar instalada
([Google Fonts](https://fonts.google.com/specimen/Lato)); a Faustina já está
incluída em `../../fonts/` (SIL OFL, veja `../../fonts/OFL.txt`).

```sh
cd slides/geral
latexmk exemplo.tex          # tema claro, gera exemplo.pdf
latexmk exemplo-dark.tex     # tema escuro, gera exemplo-dark.pdf
```

```latex
\documentclass[aspectratio=169,10pt]{beamer}
\usetheme{UEL}        % ou UELdark
```

Use `\maketitle` para o slide de título e defina as formas curtas do rodapé com
`\title[curto]{...}` e `\author[curto]{...}`.

Para encerrar, `\obrigado` cria um slide verde no estilo dos separadores de
seção, com "Obrigado!" e uma linha opcional: `\obrigado[Perguntas?]` ou
`\obrigado[nome@uel.br]`.

| Opção | Efeito |
|---|---|
| `fontpath=<pasta>` | pasta com os arquivos `.ttf` da Faustina |
| `logopath=<pasta>` | pasta com os PDFs dos logotipos |
| `nodc` | omite o logotipo do DC (slides apenas da UEL) |
| `nowatermark` | sem o símbolo translúcido nos slides de título e de seção |
| `nosectionpage` | sem o slide separador automático em cada `\section` |

O tema procura `fonts/` e `img/logos/pdf/` na pasta do documento e nas duas
pastas acima dela. Para usá-lo em outro lugar, copie os arquivos `.sty` desta
pasta e essas duas pastas para junto do seu `.tex`.

Para um guia completo de como montar uma apresentação, veja o
[README principal](../../README.md).
