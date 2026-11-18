# Princípios

> Regras que valem para **todo** componente deste design system. Se uma peça
> nova precisa de animação, de hover ou de uma seta, ela segue o que está
> aqui — não inventa.

## 1. Nativo antes de JavaScript

`<details>`/`<summary>`, `<select>`, `<dialog>` e `<input>` resolvem teclado,
leitor de tela e funcionamento sem hidratação. Só troque por componente
próprio quando o nativo não der conta — e, quando trocar, reproduza o
comportamento nativo (foco, Escape, estado anunciado).

## 2. Movimento é escolha

Toda animação decorativa para em:

```css
@media (prefers-reduced-motion: reduce) {
  .animacao { animation: none; transition: none; }
}
```

Pulso, giro e transição **nunca** são o único sinal de estado.

## 3. Estado sempre visível

Fechado, aberto, hover, foco e carregando têm aparência própria. Cor nunca é o
único indicador: use também forma, ícone ou texto.

## 4. O celular é a régua

- 390 px é a largura de teste.
- Nada de rolagem lateral falsa.
- Alvo de toque ≥ 36 px.
- Texto de interface ≥ 12 px (leia-se 12 px mesmo, não 11,2).
- Para encurtar um card, reduza padding e entrelinha, nunca a fonte.

## 5. Contraste medido

- Texto normal ≥ 4,5:1; texto grande ≥ 3:1.
- Bordas decorativas não contam como contraste de informação.
- A rampa `--cp-ord-*` dos gráficos foi escolhida para passar em daltonismo —
  não reordene as cores sem remedir.

## 6. Tokens, não cor solta

Use `var(--cp-*)`. Hex fixo quebra o tema e a auditoria de contraste. O nome do
token é o contrato; o valor muda por tema.

## 7. Um lugar para o CSS

Efeito compartilhado mora num bloco único (aqui, `temas/temas.css` e os
componentes). Não copie animação para dentro de cada página.

## 8. Dado com fonte

Número publicado tem fonte oficial e data. A oitava qualidade é a
rastreabilidade temporal: quando o dado foi coletado e quando foi conferido.
Ver [as oito qualidades da informação](QUALIDADES-DA-INFORMACAO.md).

## 9. Acessibilidade de teclado

- Tab alcança; Enter/Espaço acionam.
- `:focus-visible` desenha anel com contraste, sem depender do mouse.
- Modal prende foco e fecha com Escape.
- O leitor de tela anuncia o estado (`aria-expanded`, `aria-pressed`).

## 10. Documentar antes de replicar

Componente novo entra em `docs/` e em `exemplos/` antes de ser espalhado.
Padrão sem exemplo escrito vira dez versões diferentes na primeira semana.
