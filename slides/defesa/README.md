# defesa

Temas Beamer para defesas de TCC na Universidade Estadual de Londrina, com o
logotipo do Departamento de Computação (DC). Discretos, com uma barra de progresso
acima do rodapé para acompanhar o tempo. Feitos para 10pt, em 16:9.

| | Slide de título | Slide de conteúdo |
|---|---|---|
| **Claro** (`UELdefesa`) | <img src="previews/title.png" width="330"> | <img src="previews/resultados.png" width="330"> |
| **Escuro** (`UELdefesadark`) | <img src="previews/dark-title.png" width="330"> | <img src="previews/dark-resultados.png" width="330"> |

Mesma paleta e mesmas fontes da pasta [`geral`](../geral/) (Verde UEL, azul do DC,
Faustina e Lato), mas com uma faixa verde estreita à esquerda, sem slides
separadores de seção e com slides de título e de encerramento próprios para
defesas. O tema escuro usa a paleta verde-esmeralda descrita no README da pasta
`geral`.

## Uso

Requer **XeLaTeX ou LuaLaTeX**. A Lato precisa estar instalada
([Google Fonts](https://fonts.google.com/specimen/Lato)); a Faustina já está
incluída em `../../fonts/`.

```sh
cd slides/defesa
latexmk exemplo.tex          # tema claro
latexmk exemplo-dark.tex     # tema escuro
```

```latex
\documentclass[aspectratio=169,10pt]{beamer}
\usetheme{UELdefesa}        % ou UELdefesadark

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

O tema procura `fonts/` e `img/logos/pdf/` na pasta do documento e nas duas
pastas acima dela. Para usá-lo em outro lugar, copie os arquivos `.sty` desta
pasta e essas duas pastas para junto do seu `.tex`.

Para um guia completo de como montar uma apresentação, veja o
[README principal](../../README.md).
