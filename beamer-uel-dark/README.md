# beamer-uel-dark

Tema Beamer escuro para a Universidade Estadual de Londrina, com o logotipo do
Departamento de Computação (DC). Compacto, em 16:9, feito para 10pt.

| Slide de título | Slide de conteúdo |
|---|---|
| ![Slide de título](previews/title.png) | ![Slide de blocos](previews/blocos.png) |

## Paleta

Um fundo verde-esmeralda escuro, derivado do matiz do Verde UEL, no lugar do
preto do manual, que ficava áspero demais na tela. O manual de identidade visual é
seguido de forma flexível aqui:

- **Mantido do manual:** o Verde UEL (`#00753B`) preenche os slides de seção; as
  **versões negativas (brancas) dos logotipos** são usadas em todo o tema; Faustina
  nos títulos e Lato no texto.
- **Derivado:** fundo `#0E3A2A`, um verde mais claro `#0F8A4F` para filetes,
  faixas e títulos de blocos, e um verde-menta `#7CE9B0` para marcadores, números
  e outros destaques de texto. O próprio Verde UEL é escuro demais para ler sobre
  esse fundo.
- **Do logotipo do DC:** o azul nos blocos de exemplo, clareado (`#8DB8E6`) para
  ênfase no texto. O logotipo do DC não tem versão negativa, então fica sobre uma
  pequena placa branca; `nodc` o omite.
- O símbolo esmaecido nos slides de título e de seção lembra a capa do manual;
  `nowatermark` o remove.

## Uso

Requer **XeLaTeX ou LuaLaTeX**. A Lato precisa estar instalada
([Google Fonts](https://fonts.google.com/specimen/Lato)); a Faustina já está
incluída em `../fonts/`.

```sh
cd beamer-uel-dark
latexmk exemplo.tex      # gera exemplo.pdf com XeLaTeX
```

```latex
\documentclass[aspectratio=169,10pt]{beamer}
\usetheme{UELdark}
```

Use `\maketitle` para o slide de título e defina as formas curtas do rodapé com
`\title[curto]{…}` e `\author[curto]{…}`.

| Opção | Efeito |
|---|---|
| `fontpath=<pasta>` | pasta com os arquivos `.ttf` da Faustina |
| `logopath=<pasta>` | pasta com os PDFs dos logotipos |
| `nodc` | omite o logotipo do DC (slides apenas da UEL) |
| `nowatermark` | sem o símbolo esmaecido nos slides de título e de seção |
| `nosectionpage` | sem o slide separador automático em cada `\section` |

O tema procura `fonts/` e `img/logos/pdf/` na pasta do documento e na pasta acima
dela. Para usá-lo em outro lugar, copie os três arquivos `.sty` e essas duas
pastas para junto do seu `.tex`.

Slides escuros combinam com salas com pouca luz e com telas. Para uma sala
iluminada ou para impressão, prefira o [`beamer-uel`](../beamer-uel/).

Para um guia completo de como montar uma apresentação, veja o
[README principal](../README.md).
