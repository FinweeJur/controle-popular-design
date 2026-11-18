# Efeitos

> Ímã, hover, pulso, brilho, borda elétrica e contador. O que é decoração, o
> que é informação e onde cada efeito pode aparecer.

## Orçamento de movimento

Uma página não é uma demonstração de efeitos. Use **um efeito por bloco** e
reserve o movimento para onde ele **orienta**:

| Efeito | Classe / arquivo | Para quê | Custo |
|---|---|---|---|
| **Pulso** | `.pulso` (`efeitos.css`) | dizer “isto abre / isto é clicável” | CSS, sem JS |
| **Elevação** | `.eleva` | separar o cartão clicável do estático | CSS |
| **Brilho** | `.brilho` + `data-brilho` | indicar a área sob o ponteiro | 1 listener global |
| **Borda elétrica** | `.eletrico` | destaque de um cartão principal (no máximo um por tela) | CSS (`@property`) |
| **Ímã** | `.magnet` + `data-magnet` | botão pequeno com alvo generoso | 1 listener global |
| **Contador** | `data-contador` | número que importa, ao entrar na tela | 1 observer |
| **Barra** | `.barra__preenchida` + `--valor` | proporção comparável | 1 observer |

## Regras que não se negociam

1. **Sem efeito, o conteúdo continua certo.** O número final já está no HTML;
   a barra já tem a largura em `--valor`. JS só anima.
2. **`prefers-reduced-motion` desliga tudo.** Pulso, borda e ímã param;
   contador e barra mostram o valor final de imediato.
3. **Ponteiro só em mouse.** `@media (hover: hover) and (pointer: fine)`.
   No dedo nada segue o cursor — o alvo de toque é que resolve.
4. **Um listener para todos.** `magnet.js` registra todos os elementos e pinta
   em `requestAnimationFrame`; não crie um listener por componente.
5. **O efeito não é canal de informação.** Cor, brilho e movimento não podem
   ser o único sinal de estado (regra de acessibilidade).
6. **Contraste medido no repouso.** O brilho pode clarear a borda; o texto e o
   dado precisam passar o piso sem ele.
7. **Nada de biblioteca para isso.** São poucas linhas de CSS e um arquivo de
   JS; o portal já paga o custo de um framework — o design system não.

## Contador: o valor mora no HTML

```html
<p class="contador" data-contador="337">337</p>
<p class="contador" data-contador="1250000" data-prefixo="R$ ">R$ 1.250.000</p>
<p class="contador" data-contador="61" data-sufixo="%">61%</p>
```

- `data-contador` é o valor numérico; o texto entre as tags é o **valor final
  formatado** (é o que o robô, o leitor de tela e o “sem JS” leem);
- `data-casas`, `data-duracao`, `data-prefixo` e `data-sufixo` são opcionais;
- o observador dispara uma vez, ao entrar na tela.

Barra:

```html
<div class="barra">
  <div class="barra__preenchida" style="--valor:61%"></div>
</div>
```

## Borda elétrica (electric card)

Inspirada no padrão **Lightswind**. O contêiner tem 1 px de padding; o miolo é
opaco. O gradiente cônico gira atrás e aparece como a borda:

```html
<div class="eletrico">
  <div class="eletrico__miolo">conteúdo</div>
</div>
```

`@property --angulo` faz a animação rodar sem JS em navegador moderno; onde
não houver suporte, a borda fica estática — nunca quebra.

## Ímã

```html
<a class="magnet" data-magnet data-forca="0.3" data-afastamento="56">…</a>
```

- `data-forca`: fração da distância (0–1). Acima de 0,4 o elemento “foge” e
  atrapalha o clique.
- `data-afastamento`: quantos px antes de tocar o elemento o ímã começa.

## Créditos

- **Magnet** e **BorderGlow**: padrão do React Bits (MIT), reescrito aqui sem
  dependência e com um listener global.
- **Electric card** e **count-up**: padrão Lightswind, reimplementado em CSS +
  JS nativos.
- O portal usa as versões React em `apps/web/app/components/react-bits/`.

## Checklist antes de publicar

- [ ] Sem JS, o texto e o número continuam corretos
- [ ] `prefers-reduced-motion` testado (movimento e contador)
- [ ] Testado no celular a 390 px
- [ ] Foco de teclado visível em todo elemento clicável com efeito
- [ ] Um efeito por bloco; no máximo uma borda elétrica por tela
- [ ] Nada de `setState`/re-render por pixel
