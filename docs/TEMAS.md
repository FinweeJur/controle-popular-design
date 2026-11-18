# Temas

Oito temas, cada um um conjunto de tokens `--cp-*` aplicado por
`data-theme` no `<html>`. Os arquivos estão em
[`../temas/temas.css`](../temas/temas.css) e
[`../temas/temas.json`](../temas/temas.json).

| Tema | Cores | Descrição | Contraste medido |
|---|---|---|---|
| **Pequi** (padrão) | `#f2701d` + `#0d0b08` | Laranja-pequi e quase-preto quente | texto ~16,6:1; texto-soft ~10,4:1; primária 6,25:1 |
| **Cerrado** | `#c97b5a` + `#ffc300` | Terracota e amarelo-ipê | medido no portal |
| **Mata Atlântica** | `#3a6b35` + `#ffd700` | Verde-serra e dourado | medido no portal |
| **Caatinga** | `#d97724` + `#eab308` | Âmbar e sol do sertão | medido no portal |
| **Pantanal** | `#0284c7` + `#f59e0b` | Azul-águas e tuiuiú | medido no portal |
| **Claro** | `#12467b` + `#f7f8fa` | Azul institucional e branco | tema de leitura diurna |
| **Escuro** | `#4a90d9` + `#0b1220` | Azul-noite e grafite | alternativa neutra |
| **Alto contraste** | `#000000` + `#ffffff` | Preto e branco puro | acessibilidade |

## Como escolher

- **Conteúdo de bioma** (Cerrado, Mata Atlântica, Caatinga, Pantanal): a cor
  acompanha o território; use quando o site já organiza o acervo por região.
- **Identidade cívica neutra**: Pequi (padrão do portal) ou Claro/Escuro.
- **Acessibilidade**: Alto contraste, com `color-scheme: light` forçado e
  rampa ordinal própria.

## Daltonismo

Cada tema tem uma variante `[data-theme="..."][data-cvd="on"]` que troca as
cores ordinais dos gráficos por uma rampa segura. A rampa normal já foi
escolhida para passar nos pisos de contraste; a variante é reforço, não
desculpa para escolher cor por estética.

## Regras

1. **Não crie tema novo sem medir contraste** de texto, texto-soft e das
   séries de gráfico contra a `--cp-surface` daquele tema.
2. Mantenha os nomes dos tokens; um tema não inventa variável.
3. Borda é decorativa — mas texto e séries nunca dependem dela.
4. O tema padrão é decisão editorial: no portal, Pequi desde 08/11/2026.

## Origem

Tokens extraídos de `apps/web/app/globals.css` do Controle Popular. As
medições de contraste citadas foram feitas no portal em 04/09/2026 e
remedidas a cada mudança de token.
