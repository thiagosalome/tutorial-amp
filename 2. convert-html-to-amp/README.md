# Tutorial AMP

## 2. Conversão de HTML para AMP

**NOTA** - Você não precisa nomear seus arquivos AMP como `.amp.html`. De fato, os arquivos AMP podem ter qualquer extensão que você desejar. É comum ver editores diferenciando páginas AMP de suas versões canônicas usando parâmetros no URL. Por exemplo: `http://publisher.com/article.html?amp.`

### Resolvendo erros de validação
* Adicionar `<script async src="https://cdn.ampproject.org/v0.js"></script>` na tag `<head>`
* Adicionar a tag `<meta charset="utf-8" />` dentro do `<head>`
* Adicionar `<link rel="canonical" href="article.amp.html">` abaixo do `<meta charset="utf-8" />`
* Adicionar o atributo `amp` na tag `<html>`
* Adicionar a tag `<meta name="viewport" content="width=device-width,minimum-scale=1,initial-scale=1">`
* Trocar a tag `<link rel="stylesheet">` por `<style amp-custom></style>`
  * **Observação 1:** No AMP, para manter o tempo de carregamento dos documentos o mais rápido possível, não é possível incluir folhas de estilo externas
  * **Observação 2:** Há um limite de 50kb para todas as informações de estilo. Recomenda-se a utilização de pré-processadores CSS.
* Excluir JavaScript de terceiros
  * **Observação:** Os scripts no AMP só são permitidos se forem assíncronos (incluírem a tag `async`) e se forem para a bilioteca AMP ou qualquer componente AMP na página
* Incluir o AMP CSS boilerplate
  `<style amp-boilerplate>[...]</style></noscript>`
* Substituir `<img>` por `<amp-img>`. O AMP não suporta os equivalentes HTML padrão para exibir mídia.
  * **Observação 1:** Deve-se adicionar o `width`e `height` na tag `<amp-img>`
  * **Observação 2:** Para que a imagem se enquadre a largura da tela basta adicionar o atributo `layout="responsive"`

### Tornando a página detectável
Uma abordagem comum ao adicionar AMP a um site é gerar versões AMP de páginas HTML tradicionais não AMP. Ambas as versões têm geralmente o mesmo conteúdo (por exemplo, o texto de um artigo), mas podem ter apresentações diferentes.

* Página AMP (article.amp.html)
`<link rel="canonical" href="/article.html">`
* Página não AMP (article.html)
`<link rel="amphtml" href="/article.amp.html">`

**Observação:** É necessário configurar esse link bidirecional para que os mecanismos de pesquisa entendam a relação entre nosso documento canônico HTML comum e nosso documento AMP.