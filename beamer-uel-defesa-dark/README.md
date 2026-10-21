# beamer-uel-defesa-dark

Versão escura do [`beamer-uel-defesa`](../beamer-uel-defesa/): tema Beamer para
defesas de TCC na Universidade Estadual de Londrina, com o logotipo do
Departamento de Computação (DC) e uma barra de progresso acima do rodapé para
acompanhar o tempo. Em 16:9, feito para 10pt.

| Slide de título | Slide de conteúdo |
|---|---|
| ![Slide de título](previews/title.png) | ![Slide de resultados](previews/resultados.png) |

Mesmo layout e mesmos comandos da versão clara, na paleta verde-esmeralda escura
do [`beamer-uel-dark`](../beamer-uel-dark/): fundo `#0E3A2A`, um verde mais claro
`#0F8A4F` para a faixa, os filetes e os títulos de blocos, um verde-menta
`#7CE9B0` para destaques de texto e as versões negativas (brancas) dos logotipos
do manual. O logotipo do DC não tem versão negativa, então fica sobre uma pequena
placa branca; `nodc` o omite. Faustina nos títulos, Lato no texto.

## Uso

Requer **XeLaTeX ou LuaLaTeX**. A Lato precisa estar instalada
([Google Fonts](https://fonts.google.com/specimen/Lato)); a Faustina já está
incluída em `../fonts/`.

```sh
cd beamer-uel-defesa-dark
latexmk exemplo.tex      # gera exemplo.pdf com XeLaTeX
```

```latex
\documentclass[aspectratio=169,10pt]{beamer}
\usetheme{UELdefesadark}

\title{Título do trabalho}
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

| Comando | Efeito |
|---|---|
| `\orientador{…}`, `\banca{…}` | orientador e banca no slide de título (`\\` entre os nomes) |
| `\curso{…}`, `\tipotrabalho{…}`, `\local{…}` | curso, tipo de trabalho (padrão *Trabalho de Conclusão de Curso*) e local (padrão Londrina) |
| `\obrigado[contato]` | slide de encerramento com uma linha de contato opcional |

A barra de progresso conta os frames entre o slide de título e o de encerramento.
Defina as formas curtas do rodapé com `\title[curto]{…}` e `\author[curto]{…}`.

| Opção | Efeito |
|---|---|
| `fontpath=<pasta>` | pasta com os arquivos `.ttf` da Faustina |
| `logopath=<pasta>` | pasta com os PDFs dos logotipos |
| `nodc` | omite o logotipo do DC (slides apenas da UEL) |
| `noprogress` | sem a barra de progresso |

O tema procura `fonts/` e `img/logos/pdf/` na pasta do documento e na pasta acima
dela. Para usá-lo em outro lugar, copie os três arquivos `.sty` e essas duas
pastas para junto do seu `.tex`.

Para um guia completo de como montar uma apresentação, veja o
[README principal](../README.md).
