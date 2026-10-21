# uel-latex-templates

Unofficial LaTeX templates for the Universidade Estadual de Londrina (UEL),
following the [manual de identidade visual](docs/identitymanual.pdf).

## Templates

| Template | Description |
|---|---|
| [`beamer-uel`](beamer-uel/) | Compact 16:9 slides with UEL and DC logos |

![beamer-uel title slide](beamer-uel/previews/title.png)

## Shared assets

Templates share these directories, which they find in the repository root:

- `fonts/` — Faustina (SIL OFL) as static `.ttf` instances, generated from the
  Google Fonts variable fonts.
- `img/logos/` — official UEL logos (`eps/`, `png/` originals; `pdf/` converted
  for LaTeX) and the DC logo (`dc/` SVG originals, `pdf/dc-*.pdf`).
- `docs/` — the identity manual.

The templates use the logos under the university's identity rules; see the
manual before changing how they are placed or recoloured.
