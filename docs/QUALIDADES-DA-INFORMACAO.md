# As oito qualidades da informação

> Contrato de dado do **Controle Popular**. Vale para toda página que publica
> acervo ou lista de dados: licenciamento, TACs, convênios, decisões, barragens,
> estudos, contratos, compras e territórios.

1. **Linkável e verificado — fonte oficial direta.** Todo registro publicado
   (contrato, convênio, lei, processo, ato oficial, órgão, edital, parlamentar,
   fornecedor) tem hiperlink direto e específico para a fonte pública, aberto e
   conferido na hora da coleta. Link para home genérica é proibido quando o ato
   tem URL canônica ou protocolo próprio.

2. **Buscável e filtrável.** Busca textual em tempo real, tolerante a acentos,
   e filtros por facetas reais (status, UF, ano, categoria, tags). Filtro que
   devolve vazio sempre é pior que filtro nenhum.

3. **Classificável e ordenável por coluna.** Ordenação crescente e decrescente
   em todas as colunas relevantes: nomes (classes/categorias), valores
   monetários e datas — nunca só a data.

4. **Resumo, microresumo e cartões de topo.** Resumo em português direto e
   cartões com agregados que respondem “quanto é isso no total?”, sempre com
   número medido e datado, nunca digitado à mão.

5. **Assistente com contexto cívico.** Toda base ou entidade alimenta o
   assistente (RAG) com tags contextuais, metadados e respostas em frases
   curtas, apontando links oficiais.

6. **Exportável e imprimível.** CSV do que está filtrado na tela, com
   separador `;` e BOM UTF-8 (`\uFEFF`) para o Excel brasileiro; gráfico SVG
   nativo acessível, sem biblioteca pesada; layout de impressão via CSS
   `@media print`.

7. **Responsiva — celular, tablet e desktop.** A mesma página se abre legível a
   390 px, 768 px e desktop, sem rolagem lateral falsa, sem coluna cortada e sem
   rótulo escondido. Conteúdo largo (tabela, gráfico, mapa) rola **dentro do
   quadro**, nunca estoura a tela. Conferência: em 390 px,
   `document.documentElement.scrollWidth === window.innerWidth`.

8. **Rastreável no tempo.** Página de dado e post com número mostram a data da
   coleta da fonte, visível e derivada do próprio dado (`<time>`, carimbo do
   arquivo gravado na coleta). Data digitada à mão é tão dano quanto número
   digitado à mão: apodrece sozinha e o leitor não tem como saber.

Nenhuma qualidade dispensa:

- **a régua do celular vem antes de todas:** se a coluna não é legível e a
  página não cabe em 390 px, as outras sete não valem;
- gráfico com alternativa em texto ou tabela; cor nunca é o único canal;
- número na tela vem de constante medida com data;
- a página importa o **agregado**, nunca o array inteiro, para o build não
  pesar;
- post de serviço segue a mesma régua: tabela filtrável e ordenável, número
  animado que entrega o valor final no HTML e data de consulta no corpo.

## Como isso conversa com o design system

| Qualidade | Componente que sustenta |
|---|---|
| 2 e 3 | tabela com busca, filtro e ordenação |
| 4 | cartões de topo e resumo sob o `<h1>` (≥ 12 px) |
| 6 | botão de CSV com BOM e `@media print` |
| 7 | tokens responsivos, `min-width: 0` no `<main>`, tabela com rolagem interna |
| 8 | `<time>` e carimbo de coleta |

## Origem

Adaptado de `docs/04-arquitetura/QUALIDADES-DA-INFORMACAO.md` do portal
Controle Popular (18/10/2026, atualizado em 18/11/2026).
