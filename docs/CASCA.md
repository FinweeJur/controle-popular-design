# Casca da página

> Navbar, sumário, tabela, robô e rodapé — o que fica em volta do conteúdo e
> se repete em toda página. Arquivos: `componentes/shell.css` e
> `componentes/shell.js`. Demonstração viva: a
> [galeria](../exemplos/index.html).

## Navbar superior

- Fica **sticky** no topo, com fundo translúcido e desfoque.
- Marca à esquerda; links no centro-direita; busca, botão do GitHub, seletor
  de tema e menu à direita.
- O **botão do GitHub** é um círculo de 36 px com o ícone (rótulo acessível),
  para o repositório ficar a um clique de qualquer página.
- No celular, os links entram numa **gaveta** aberta pelo botão `☰`
  (`data-menu-toggle` + `data-gaveta`).
- Uma **barra de progresso** de 2 px mostra quanto da página já foi lida
  (`data-progresso`).
- O link ativo recebe `aria-current="true"` (cor de acento).

```html
<header class="topo">
  <div class="topo__interno">
    <a class="topo__marca" href="#conteudo">…</a>
    <nav class="topo__links" aria-label="Navegação principal">…</nav>
    <div class="topo__acoes">
      <label class="topo__busca"><input type="search" aria-label="Buscar"></label>
      <select class="topo__tema" aria-label="Tema do site">…</select>
      <button class="topo__menu" data-menu-toggle aria-expanded="false">☰</button>
    </div>
  </div>
  <div class="topo__gaveta" data-gaveta="false">…</div>
  <div class="topo__progresso" data-progresso></div>
</header>
```

## Sumário com Topo e Próxima seção

Regra de leitura do portal (5.18): o sumário fica ao lado do texto no desktop e
vira bloco recolhível no celular. Ele **acompanha a leitura** (scrollspy) e
oferece três botões: **Anterior**, **Topo** e **Próxima ↓**.

```html
<aside class="sumario" aria-label="Sumário desta página">
  <button class="sumario__titulo" data-sumario-toggle aria-expanded="true">…</button>
  <ol class="sumario__lista">
    <li><a href="#sanfona">Sanfona</a></li>
  </ol>
  <div class="sumario__acoes">
    <button class="sumario__botao" data-acao="anterior">↑ Anterior</button>
    <button class="sumario__botao" data-acao="topo">Topo</button>
    <button class="sumario__botao" data-acao="proxima">Próxima ↓</button>
  </div>
</aside>
```

- O link da seção visível ganha `.is-ativo`.
- Os títulos das seções têm `tabindex="-1"` e `scroll-margin-top`, para o salto
  não esconder o título atrás da navbar.
- `prefers-reduced-motion` troca a rolagem suave por salto direto.

## Tabela ordenável

- O cabeçalho inteiro é um `<button>`; a seta (`↕ → ↑/↓`) e o `aria-sort` dão
  o estado.
- `data-ordenar="texto|numero|data"` escolhe a comparação; `data-valor` na
  célula guarda o valor bruto (R$ e dd/mm não ordenam como texto).
- Sem JS, a tabela mostra a ordem do HTML — continua correta.
- A tabela rola dentro do quadro (`.tabela`), nunca estica a página.

## Robô (chatbot)

- Botão flutuante fixo no canto inferior direito; painel com cabeçalho,
  mensagens e campo.
- `aria-live="polite"` anuncia as respostas; o botão declara `aria-expanded`.
- A demonstração responde com texto fixo: é **interface**, sem chamada de rede.
- No portal, o mesmo desenho conversa com o acervo e sempre devolve link para a
  fonte oficial.

## Rodapé

- Três colunas: marca + resumo, componentes, documentação.
- **Link visível para o GitHub** logo abaixo do resumo, em formato de botão
  com ícone (não um link perdido no meio do texto).
- Base com copyright e o botão **Voltar ao topo** (alvo de 36 px).
- Links com hover na cor de acento e sublinhado.

## Rolagem

- `scroll-behavior: smooth` no `<html>` (desligado em movimento reduzido).
- `scroll-margin-top` em cada seção compensa a navbar sticky.
- Blocos com `data-revelar` aparecem suavemente ao entrar na tela — e já vêm
  visíveis quando o navegador pediu menos movimento.

## Checklist

- [ ] Tab percorre navbar → conteúdo → sumário → rodapé → robô
- [ ] `Escape` fecha o painel do robô (o botão de fechar está sempre visível)
- [ ] No celular, a gaveta fecha ao escolher um link
- [ ] A barra de progresso não cobre o conteúdo
- [ ] O sumário destaca a seção certa ao rolar
- [ ] Tabela ordena por texto, número e data
