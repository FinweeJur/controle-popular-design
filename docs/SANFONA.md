# Sanfona que se anuncia

Componente de referência do design system: um bloco expansível que **diz que
abre**. `<details>` nativo, sem JavaScript.

## Por que existe

Na auditoria socioambiental do Paraopeba (18/11/2026) os blocos de tema eram
`<summary>` só com texto. Nada indicava conteúdo escondido — sem seta, sem
hover, sem cara de botão — e o leitor passava reto.

## Anatomia

```
┌───────────────────────────────────────────────────────────────┐
│  Título do bloco                            ABRIR      ( ▼ )  │  ← summary = alvo do clique
├───────────────────────────────────────────────────────────────┤
│  conteúdo revelado (só quando aberto)                         │
└───────────────────────────────────────────────────────────────┘
```

1. **Linha inteira clicável** — `<summary>` ocupa toda a largura, com `cursor:
   pointer` e `list-style: none`.
2. **Seta num selo redondo** — aponta para baixo e gira 180° ao abrir.
3. **Pulso no selo** — anel suave enquanto fechado; para ao abrir.
4. **Microtexto “Abrir/Fechar”** — no desktop; no celular a seta basta.
5. **Hover e foco** — fundo no hover, anel de foco no teclado.

## Estados

| Estado | Como se vê |
|---|---|
| Fechado | borda neutra, selo pulsando, “ABRIR” |
| Hover | borda no tom do acento, fundo levemente mais claro |
| Foco (teclado) | anel de foco no `summary` |
| Aberto | borda de acento, seta girada, “FECHAR”, corpo com divisória |

## Marcação

```html
<details class="sanfona">
  <summary>
    <span class="sanfona__titulo">Flora e vegetação</span>
    <span class="sanfona__dica sanfona__dica--abrir" aria-hidden="true">Abrir</span>
    <span class="sanfona__dica sanfona__dica--fechar" aria-hidden="true">Fechar</span>
    <span class="sanfona__seta" aria-hidden="true">
      <svg viewBox="0 0 20 20" fill="none" stroke="currentColor" stroke-width="2.2"
           stroke-linecap="round" stroke-linejoin="round"><path d="M6 8l4 4 4-4"/></svg>
    </span>
  </summary>
  <div class="sanfona__corpo">
    <p>Conteúdo revelado.</p>
  </div>
</details>
```

O CSS completo está em [`../componentes/sanfona.html`](../componentes/sanfona.html)
(autossuficiente) e a demonstração com temas em
[`../exemplos/index.html`](../exemplos/index.html).

## Acessibilidade

- O `<details>` nativo já anuncia “expandido/recolhido”.
- “Abrir/Fechar” e a seta são `aria-hidden` (redundantes com o estado nativo).
- Abre por toque, Enter e Espaço; `:focus-visible` desenha o anel.
- O pulso para em `prefers-reduced-motion`.

## Regras de conteúdo

- Título curto, não uma frase inteira.
- Não aninhe sanfona em sanfona: se precisar, o conteúdo quer página própria.
- O corpo começa em `<p>`/`<ul>` e não repete o título.

## Uso no portal

`apps/web/app/components/sistema/SanfonaTema.tsx` implementa a mesma peça em
React + Tailwind, com as variantes `card` (bloco da página) e `linha`
(disclosure dentro de ficha). Mudou um? Atualize os dois.
