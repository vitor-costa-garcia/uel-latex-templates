# uel-latex-templates

Modelos não oficiais de slides em Beamer para a Universidade Estadual de Londrina
(UEL), seguindo o [manual de identidade visual](docs/identitymanual.pdf): Verde
UEL, logotipos oficiais, Faustina nos títulos e Lato no texto. Todos os modelos
trazem também o logotipo do Departamento de Computação (DC), que pode ser
desligado.

## Modelos

| Modelo | Aparência | Para quê |
|---|---|---|
| [`beamer-uel`](beamer-uel/) | slides brancos, bloco verde no título | palestras, aulas, seminários |
| [`beamer-uel-dark`](beamer-uel-dark/) | slides em verde-esmeralda escuro | salas com pouca luz, telas |
| [`beamer-uel-defesa`](beamer-uel-defesa/) | branco, discreto, com barra de progresso | defesas de TCC |
| [`beamer-uel-defesa-dark`](beamer-uel-defesa-dark/) | o mesmo, em esmeralda escuro | defesas de TCC, salas com pouca luz |

Os modelos de defesa acrescentam `\orientador`, `\banca` e `\curso` ao slide de
título, uma barra de progresso acima do rodapé para acompanhar o tempo, um slide
final (`\obrigado`) e não têm slides separadores de seção.

### Exemplos

Cada modelo tem um exemplo, `exemplo.tex`, que mostra o slide de título e os
tipos de slide mais comuns. A primeira imagem de cada linha é o slide de título.

| `beamer-uel` |
|---|
| <img src="beamer-uel/previews/title.png" width="330"> <img src="beamer-uel/previews/blocos.png" width="330"> |

| `beamer-uel-dark` |
|---|
| <img src="beamer-uel-dark/previews/title.png" width="330"> <img src="beamer-uel-dark/previews/blocos.png" width="330"> |

| `beamer-uel-defesa` |
|---|
| <img src="beamer-uel-defesa/previews/title.png" width="330"> <img src="beamer-uel-defesa/previews/resultados.png" width="330"> |

| `beamer-uel-defesa-dark` |
|---|
| <img src="beamer-uel-defesa-dark/previews/title.png" width="330"> <img src="beamer-uel-defesa-dark/previews/resultados.png" width="330"> |

## Requisitos

- **XeLaTeX ou LuaLaTeX** e `latexmk`; os temas não funcionam com pdfLaTeX.
  Foram desenvolvidos e testados com o TeX Live 2026.
- **Lato**, instalada no sistema: `sudo apt install fonts-lato` no Debian e no
  Ubuntu, ou baixe no [Google Fonts](https://fonts.google.com/specimen/Lato). Sem
  ela, o tema avisa e usa a Latin Modern Sans.
- A Faustina já está incluída em [`fonts/`](fonts/) (licença SIL OFL); não há
  nada para instalar.

## Início rápido

1. Clone o repositório e compile um exemplo para conferir se o ambiente está
   certo:

   ```sh
   git clone <este repositório>
   cd uel-latex-templates/beamer-uel
   latexmk exemplo.tex        # gera exemplo.pdf
   ```

2. Comece a sua apresentação copiando a pasta do modelo para junto de `fonts/` e
   `img/`, para que o tema as encontre:

   ```sh
   cd uel-latex-templates
   cp -r beamer-uel minha-apresentacao
   cd minha-apresentacao
   mv exemplo.tex slides.tex  # opcional
   ```

3. Edite o `slides.tex` e compile:

   ```sh
   latexmk slides.tex                # XeLaTeX (definido no latexmkrc)
   latexmk -lualatex slides.tex      # ou LuaLaTeX
   latexmk -pvc slides.tex           # recompila a cada alteração do arquivo
   ```

   O slide de título posiciona os logotipos com TikZ, o que exige duas
   compilações; o `latexmk` faz as duas. Se um logotipo ou o layout do título
   parecer errado depois de uma única execução do `xelatex`, execute-o de novo.

## Escrevendo uma apresentação

Uma apresentação mínima:

```latex
\documentclass[aspectratio=169,10pt]{beamer}
\usepackage[brazil]{babel}

\usetheme{UEL}                 % ou UELdark, UELdefesa, UELdefesadark

\title[Título curto]{Título da apresentação}   % [forma curta] aparece no rodapé
\subtitle{Subtítulo, se houver}
\author[Nome]{Nome do Autor}
\institute{Departamento de Computação\\Universidade Estadual de Londrina}
\date{\today}

\begin{document}

\maketitle                     % o slide de título; não o coloque dentro de um frame

\begin{frame}{Sumário}
  \tableofcontents
\end{frame}

\section{Introdução}           % cria um slide separador automaticamente (não nos modelos de defesa)

\begin{frame}{Um título de slide}{Subtítulo opcional}
  \begin{itemize}
    \item Um item com \alert{destaque}
    \item Outro item
  \end{itemize}
\end{frame}

\end{document}
```

O que os temas estilizam e como usar:

| Você escreve | Você obtém |
|---|---|
| `\begin{frame}{Título}{Subtítulo}` | título do slide, com subtítulo opcional |
| `\section{…}`, `\tableofcontents` | slides separadores (não nos temas de defesa) e uma lista de conteúdo |
| `itemize`, `enumerate` | marcadores quadrados e numeração na cor de destaque do tema |
| `\alert{…}` | ênfase em negrito, no azul do DC |
| `block`, `alertblock`, `exampleblock` | blocos verde, cinza e azul |
| `columns` | conteúdo lado a lado |
| `\begin{frame}[fragile]` | necessário em volta de `verbatim` e de listagens de código |
| `\begin{frame}[plain]` | slide sem rodapé, para figuras que ocupam toda a largura |

Dicas:

- Os temas foram feitos para **16:9 e 10pt**; mantenha
  `\documentclass[aspectratio=169,10pt]{beamer}`. O texto é menor que o padrão
  do Beamer de propósito.
- Defina formas curtas com `\title[…]{…}` e `\author[…]{…}`; elas aparecem no
  rodapé, onde as formas longas não caberiam.
- Coloque as figuras numa subpasta, como `figuras/`, e use `\includegraphics`.
  Para diagramas, prefira PDF ou SVG convertido para PDF em vez de PNG.
- Numa defesa, defina os campos extras antes de `\maketitle` e termine com
  `\obrigado[linha de contato]`:

  ```latex
  \usetheme{UELdefesa}
  \orientador{Prof. Dr. Nome do Orientador}
  \banca{Prof. Dr. Nome do Membro 2\\Profa. Dra. Nome do Membro 3}
  \curso{Ciência da Computação}
  % ...
  \obrigado[nome.autor@exemplo.uel.br]
  ```

- Para todo o resto sobre slides, consulte o
  [guia do usuário do Beamer](https://ctan.org/pkg/beamer): os temas mudam apenas
  a aparência.

### Opções dos temas

Passe as opções ao tema, por exemplo `\usetheme[nodc,nowatermark]{UEL}`.

| Opção | Efeito | Modelos |
|---|---|---|
| `nodc` | omite o logotipo do DC, para slides apenas da UEL | todos |
| `nowatermark` | sem o símbolo esmaecido nos slides de título e de seção | `beamer-uel`, `beamer-uel-dark` |
| `nosectionpage` | sem o slide separador automático em cada `\section` | `beamer-uel`, `beamer-uel-dark` |
| `noprogress` | sem a barra de progresso | modelos de defesa |
| `fontpath=<pasta>` | onde estão os arquivos `.ttf` da Faustina, terminando com `/` | todos |
| `logopath=<pasta>` | onde estão os PDFs dos logotipos, terminando com `/` | todos |

O README de cada modelo lista todos os seus comandos.

## Usando um tema fora deste repositório

Um tema procura `fonts/` e `img/logos/pdf/` na pasta do seu documento e na pasta
acima dela. Qualquer uma destas configurações funciona:

- **Copiar a pasta dentro do repositório**, como no início rápido. Não há mais
  nada a configurar.
- **Copiar os arquivos para o seu projeto**: os três arquivos `.sty` do modelo,
  mais `fonts/` e `img/logos/pdf/` deste repositório, ao lado do seu `.tex` (ou
  uma pasta acima).
- **Deixar o repositório onde está** e apontar para ele. Coloque a pasta do
  modelo no `TEXINPUTS` (note o `//` e o `:` final) e informe os caminhos dos
  recursos:

  ```latex
  \usetheme[fontpath=/home/voce/uel-latex-templates/fonts/,
            logopath=/home/voce/uel-latex-templates/img/logos/pdf/]{UEL}
  ```

  ```sh
  TEXINPUTS=/home/voce/uel-latex-templates/beamer-uel//: latexmk -xelatex slides.tex
  ```

  Para não digitar o `TEXINPUTS`, copie os três arquivos `.sty` para
  `~/texmf/tex/latex/uel/` e mantenha as duas opções acima.

## Solução de problemas

| Mensagem ou sintoma | Causa e solução |
|---|---|
| `The UEL theme needs XeLaTeX or LuaLaTeX` | você executou o `pdflatex`; use `latexmk` ou `xelatex` |
| `Logo files not found` | copie `img/logos/pdf/` para junto do documento ou defina `logopath` |
| aviso `Faustina not found` | copie `fonts/` para junto do documento ou defina `fontpath`; os títulos usam uma fonte serifada padrão |
| aviso `Lato not found` | instale a Lato (veja Requisitos) |
| Logotipos ou bloco do título fora do lugar | compile uma segunda vez (o `latexmk` faz isso) |
| `verbatim` ou código dentro de um frame dá erro | adicione `[fragile]`: `\begin{frame}[fragile]` |

## Estrutura do repositório

```
beamer-uel/               uma pasta por modelo: tema (.sty), exemplo.tex, README
beamer-uel-dark/
beamer-uel-defesa/
beamer-uel-defesa-dark/
fonts/                    Faustina (instâncias estáticas das fontes variáveis do Google Fonts)
img/logos/                logotipos da UEL (eps/, png/ originais; pdf/ para o LaTeX) e do DC (dc/ SVGs)
docs/                     o manual de identidade visual
```

Os modelos escuros se afastam do manual de propósito: usam um fundo verde-esmeralda
escuro e verdes derivados, e o logotipo do DC fica sobre uma placa branca porque
não tem versão negativa. O README de cada um diz exatamente o que é derivado.

Estes modelos não são endossados pela UEL. Use os logotipos conforme as regras de
identidade da universidade e consulte o manual antes de mudar a posição ou as
cores deles.
