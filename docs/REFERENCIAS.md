# Referências e inspiração

> Catálogo de fora do repositório: o que vale extrair, o que já foi adotado e o
> que **não** entra. Serve para não redescobrir a roda nem importar peso morto.

Regra de entrada: só entra o que respeita os [princípios](PRINCIPIOS.md) —
nativo antes de JS, movimento é escolha, tokens do tema, sem biblioteca pesada
para efeito decorativo. **Licença é conferida antes de copiar código.**

## Animação e interface

| Referência | O que aproveitar | Situação |
|---|---|---|
| **React Bits** (reactbits.dev) | Ímã, brilho de borda, texto brilhante, cartão com holofote. Componentes pequenos, fáceis de reescrever sem dependência. | **Adotado** — `Magnet`, `BorderGlow`, ímã e brilho em `efeitos/`. Reescritos sem React e com um listener global. |
| **Componentry** (componentry.dev) | Micro-interações com Framer Motion; referência de timing e easing. | Avaliar — exige React + Framer Motion; copiar só o desenho, não a dependência. |
| **Skiper UI** | Micro-interações de SaaS (hover, câmara, revelação). Boa referência visual. | Avaliar — biblioteca comercial; usar como referência, não como pacote. |
| **GSAP** | Linhas do tempo, scroll-driven, SVG. O que há de mais controlável. | **Não adotado** — licença própria e peso alto. Nosso scroll é nativo; para o resto, CSS resolve. |
| **Lenis** | Rolagem suave e "scroll sniffing". | **Não adotado como biblioteca**: o portal usa `scroll-behavior: smooth` + `scroll-margin`. A ideia de progresso de leitura virou a barra da navbar. |
| **Vanta.js** | Fundos 3D em WebGL. | **Não adotado** — WebGL decorativo pesa no celular e distrai de dado. O fundo do portal é textura CSS. |
| **thinking-orbs** | Indicador de "pensando" para interfaces de IA, em canvas 2D. | **Adotado em CSS** — orbe de três pontos (`.orbe`) no robô, sem canvas. |
| **Framer — componentes reativos ao mouse** | Grade interativa, texto que foge, cartão pendurado. | Referência de ideia. No portal, ímã e brilho cobrem o caso sem dependência. |

## Tokens, tipografia e documentação de design

| Referência | O que aproveitar | Situação |
|---|---|---|
| **awesome-design-md / getdesign.md** | `DESIGN.md` por marca, para agente gerar UI coerente. | **Adotado como formato** — este repositório é o `DESIGN.md` do portal, em Markdown + CSS executável. |
| **Fontshare** (Clash Display, General Sans) | Tipografia do portal, aberta e sem custo. | **Adotado** — `fontes/fontshare.css`. Em produção, auto-hospedar. |

## Creative coding

| Referência | O que aproveitar | Situação |
|---|---|---|
| **p5.brush** | Pincéis orgânicos, aquarela, campos vetoriais. | Não entra no portal; referência para as aquarelas dos eixos. |
| **Strudel** | Música ao vivo no navegador. | Fora de escopo — o portal tem rádio, não síntese. |

## IA, agentes e protocolos

Estes não são componentes de interface; entram aqui porque orientam a operação
do portal e a relação com dado público.

| Referência | O que aproveitar | Situação |
|---|---|---|
| **MCP (Model Context Protocol)** | Conectar assistentes a bases públicas com contrato explícito. | Referência para o assistente do portal e futuras integrações. |
| **ONS MCP TIAGO** | Primeiro MCP do setor elétrico: dado aberto exposto a IA com código público. | Referência de arquitetura cívica. |
| **Manacá-1B (LNCC/MCTI)** | Modelo aberto em português, treinado do zero. | Referência de soberania de dados; não é componente. |
| **Playwright CLI** | Automação de browser por agente; gravar e gerar código. | **Adotado no processo** — a suíte de verificação usa Playwright. |
| **Cinco MCP universais** (GitHub, Context7, Playwright, Filesystem, Brave) | Checklist de ferramentas para agente de código. | Referência de fluxo de trabalho, não de UI. |
| **JARVIS OS 2.0 / universal-modder / ComfyUI / logo skill / prompts de consistência** | Fluxos de agente, geração de mídia e consistência de personagem. | Fora de escopo do design system. |

## Infraestrutura e privacidade

| Referência | O que aproveitar | Situação |
|---|---|---|
| **quiche (Cloudflare)** | QUIC/HTTP3 em Rust. | Fora de escopo — infraestrutura de borda. |
| **Cover Your Tracks (EFF)** | Teste de fingerprint do navegador. | Referência de privacidade; lembrete para não adicionar rastreador ao portal. |
| **Project N.O.M.A.D.** | Nó offline de arquivo e mídia. | Referência de resiliência (dado que funciona sem nuvem). |

## Fila de adaptação sugerida

1. **Orbe de pensamento** no robô — feito (CSS, sem canvas).
2. **Cartão com holofote** mais suave que o brilho atual — avaliar contraste.
3. **Revelação em cascata** de listas longas (stagger) — só com `reduced-motion`
   desligando.
4. **Texto brilhante** (shiny text) para selo de "medido" — medir contraste antes.

## Como avaliar uma referência nova

- [ ] Dá para fazer com CSS nativo? Se sim, não traga biblioteca.
- [ ] A licença permite cópia e adaptação? (MIT/Apache: sim; comercial: só ideia.)
- [ ] Funciona sem JS e para em `prefers-reduced-motion`?
- [ ] Usa os tokens `--cp-*` ou traz paleta própria?
- [ ] Pesa menos que o problema que resolve?
- [ ] O efeito **orienta** o leitor ou só enfeita?

## Origem

Compilado em 18/11/2026 a partir de uma lista de ferramentas de IA, front-end e
infraestrutura. As descrições são nossas; os links levam à fonte.
