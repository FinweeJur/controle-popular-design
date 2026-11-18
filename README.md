# Design System — Controle Popular

> Vocabulário visual e editorial do portal **controlepopular.com.br**, publicado
> como repositório aberto para que outros sites cívicos usem o mesmo padrão.
>
> Sem build, sem framework obrigatório: HTML, CSS e os tokens dos temas.

## O que tem aqui

| Pasta | O que é |
|---|---|
| [`temas/`](temas/) | Os 8 temas do portal (Pequi, Cerrado, Mata Atlântica, Caatinga, Pantanal, Claro, Escuro, Alto contraste) em CSS variables + metadados em JSON |
| [`componentes/`](componentes/) | Peças prontas para copiar: sanfona (`<details>`), seta de `<select>`, tabela ordenável, navbar, sumário, rodapé e robô |
| [`efeitos/`](efeitos/) | CSS e JS dos efeitos + contador de números e barras |
| [`fontes/`](fontes/) | Clash Display + General Sans via Fontshare, com os tokens de tipografia |
| [`docs/`](docs/) | Princípios de design, as oito qualidades da informação e as regras de cada componente |
| [`exemplos/`](exemplos/) | Galeria de demonstração com troca de tema ao vivo |

## Comece por

1. [Princípios](docs/PRINCIPIOS.md) — o que vale para todo componente.
2. [As oito qualidades da informação](docs/QUALIDADES-DA-INFORMACAO.md) — o
   contrato de dado do portal.
3. [Sanfona](docs/SANFONA.md) — o componente de referência.
4. [Casca](docs/CASCA.md) — navbar, sumário com Topo/Próxima, tabela, robô e rodapé.
5. [Efeitos](docs/EFEITOS.md) — ímã, hover, pulso, brilho, borda elétrica e contador.
6. [Temas](docs/TEMAS.md) — a paleta de cada bioma.
7. [Referências](docs/REFERENCIAS.md) — o que vale extrair de fora, com licença e peso na balança.

## Uso em 3 passos

```html
<!-- 1. os tokens de todos os temas -->
<link rel="stylesheet" href="temas/temas.css">

<!-- 2. escolha o tema no elemento raiz -->
<html data-theme="pequi">

<!-- 3. use os tokens nos seus componentes -->
<style>
  .cartao {
    background: var(--cp-surface);
    color: var(--cp-text);
    border: 1px solid var(--cp-border);
  }
</style>
```

A galeria em [`exemplos/index.html`](exemplos/index.html) abre direto no
navegador e troca de tema sem servidor.

## Contrato dos tokens

Os nomes são estáveis; os valores mudam por tema.

| Token | Papel |
|---|---|
| `--cp-bg` | fundo da página |
| `--cp-surface` / `--cp-surface-2` | cartões e superfícies elevadas |
| `--cp-text` / `--cp-text-soft` | texto principal / secundário |
| `--cp-primary` / `--cp-primary-ink` | cor de marca e texto sobre ela |
| `--cp-accent`, `--cp-secondary`, `--cp-tertiary` | apoio, com `*-ink` para contraste |
| `--cp-border` | bordas |
| `--cp-focus` | anel de foco |
| `--cp-alert` | erro e alerta |
| `--cp-eixo-*` | cores dos eixos temáticos |
| `--cp-ord-*` | rampa ordinal de gráficos (ordem + daltonismo) |

## Regras que não se negociam

- **Contraste medido**, não estimado: texto normal ≥ 4,5:1, texto grande ≥ 3:1.
- **Movimento é escolha:** toda animação para em `prefers-reduced-motion`.
- **Nativo antes de JavaScript:** `<details>`, `<select>` e `<dialog>` primeiro.
- **Texto de interface ≥ 12 px** e alvo de toque ≥ 36 px.
- **Cor nunca é o único sinal** de estado.
- **Dado com fonte:** número publicado tem fonte oficial linkável e data.

Detalhe em [docs/PRINCIPIOS.md](docs/PRINCIPIOS.md).

## Licença

Código (CSS/HTML/JS) sob MIT; textos editoriais sob CC BY 4.0.
Ver [LICENCA.md](LICENCA.md).
