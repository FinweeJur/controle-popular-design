# Prompt para agente de IA

Copie o bloco abaixo e cole no seu agente (Claude Code, Codex, Cursor,
Copilot, OpenCode). Ele entrega o repositório, as regras de qualidade e os
componentes prontos. A mesma caixa está na
[galeria](../exemplos/index.html#prompt), com botão de copiar.

```text
Você vai construir ou ajustar uma página com o Design System do Controle Popular.

Repositório: https://github.com/FinweeJur/controle-popular-design
Galeria: https://finweejur.github.io/controle-popular-design/exemplos/

1. Leia docs/PRINCIPIOS.md e docs/QUALIDADES-DA-INFORMACAO.md antes de escrever código.
2. Carregue, nesta ordem: fontes/fontshare.css, temas/temas.css, componentes/shell.css,
   componentes/select.css e efeitos/efeitos.css.
3. Escolha o tema em <html data-theme="pequi"> — Pequi, Cerrado, Mata Atlântica,
   Caatinga, Pantanal, Claro, Escuro ou Alto contraste.
4. Use só tokens --cp-*; nunca hex solto. Texto ≥ 12 px, alvo de toque ≥ 36 px,
   contraste ≥ 4.5:1.
5. Componentes prontos:
   - sanfona: <details class="sanfona"> com .sanfona__seta (CSS em componentes/sanfona.html);
   - tabela ordenável: <table data-ordenavel> + <th><button data-ordenar="texto|numero|data">;
   - navbar, sumário com Topo/Próxima e rodapé: componentes/shell.css + shell.js;
   - efeitos e contador: efeitos/efeitos.css + magnet.js; o número final fica no HTML.
6. Toda animação para em prefers-reduced-motion; nada de biblioteca para efeito decorativo.
7. Entregue HTML/CSS funcionando sem build e explique quais componentes e regras usou.

Se faltar informação, pergunte antes de inventar número, fonte ou componente.
```

## Como usar

1. Na galeria, clique em **Copiar prompt** — o botão vira **Copiado ✓**.
2. Cole no agente com `Ctrl+V` (ou `Cmd+V`).
3. Se a área de transferência estiver bloqueada, selecione o texto e copie.

## Por que o prompt é curto

- O que é **regra** está nos documentos linkados; o prompt só aponta o caminho.
- O que é **componente** está em `componentes/` e `efeitos/` — o agente lê o
  arquivo, não precisa que o prompt descreva cada classe.
- O que é **proibido** cabe em uma linha: hex solto, biblioteca decorativa,
  animação sem `prefers-reduced-motion`, número inventado.
