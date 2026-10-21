# evento

Temas Beamer para eventos, cursos e palestras de extensão na Universidade Estadual
de Londrina, com o logotipo do Departamento de Computação (DC). O slide de título
tem uma faixa com o nome do evento, cartões dos palestrantes (com foto opcional) e
uma linha para os logotipos dos apoiadores. Feitos para 10pt, em 16:9.

| | Slide de título | Slide de conteúdo |
|---|---|---|
| **Claro** (`UELevento`) | <img src="previews/title.png" width="330"> | <img src="previews/conteudo.png" width="330"> |
| **Escuro** (`UELeventodark`) | <img src="previews/dark-title.png" width="330"> | <img src="previews/dark-conteudo.png" width="330"> |

Mesma paleta e mesmas fontes da pasta [`geral`](../geral/); o tema escuro usa a
paleta verde-esmeralda descrita no README daquela pasta.

## Uso

Requer **XeLaTeX ou LuaLaTeX**. A Lato precisa estar instalada
([Google Fonts](https://fonts.google.com/specimen/Lato)); a Faustina já está
incluída em `../../fonts/`.

```sh
cd slides/evento
latexmk exemplo.tex          # tema claro
latexmk exemplo-dark.tex     # tema escuro
```

```latex
\documentclass[aspectratio=169,10pt]{beamer}
\usetheme{UELevento}        % ou UELeventodark

\title{Introdução ao LaTeX}
\subtitle{Documentos científicos sem dor de cabeça}
\evento{Semana da Computação 2026}
\datalocal{12 de março de 2026 \textbullet{} Auditório do CCE, UEL}
\palestrante[foto.jpg]{Prof. Dr. Nome do Palestrante}{Departamento de Computação, UEL}
\palestrante{Nome da Palestrante}{Universidade Parceira}
\apoio{\includegraphics[height=.7cm]{logo-parceiro.pdf}}

\begin{document}
\maketitle
% ...
\obrigado[nome.palestrante@exemplo.uel.br]
\end{document}
```

| Comando | Efeito |
|---|---|
| `\evento{…}`, `\datalocal{…}` | nome, data e local do evento, na faixa do topo |
| `\palestrante[foto]{nome}{afiliação}` | um cartão de palestrante; repita o comando para cada um. A foto é opcional e é recortada em círculo |
| `\apoio{…}` | conteúdo da linha *Realização e apoio*, em geral logotipos com `\includegraphics` |
| `\obrigado[contato]` | slide final, com a mesma faixa do título |

O rodapé mostra o nome do evento, o título curto (`\title[curto]{…}`) e a página.
Os cartões e a linha de apoio só aparecem se você usar os comandos
correspondentes. O exemplo usa `foto-exemplo.png`, uma imagem neutra; troque pela
foto real.

Dica: o `\LaTeX` fica mal formatado em fontes que não são do TeX, como a Faustina
dos títulos; escreva “LaTeX” em texto simples nos títulos.

| Opção | Efeito |
|---|---|
| `fontpath=<pasta>` | pasta com os arquivos `.ttf` da Faustina |
| `logopath=<pasta>` | pasta com os PDFs dos logotipos |
| `nodc` | omite o logotipo do DC (slides apenas da UEL) |

O tema procura `fonts/` e `img/logos/pdf/` na pasta do documento e nas duas
pastas acima dela. Para usá-lo em outro lugar, copie os arquivos `.sty` desta
pasta e essas duas pastas para junto do seu `.tex`.

Para um guia completo de como montar uma apresentação, veja o
[README principal](../../README.md).
