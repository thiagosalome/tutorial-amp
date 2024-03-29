# 3. Curso de Iniciação

## Por que AMP?
O AMP foi criado para facilitar aos desenvolvedores o foco na criação de melhores recursos **sem oferecer aos clientes uma má experiência do usuário.**

## Como o AMP ajuda?
O AMP trabalha para melhorar o desempenho da web considerando os seguintes aspectos:
* Estendendo o HTML adicionando tags para recursos comuns do site.
* Reduzindo a quantidade de JavaScript. Os componentes AMP fornecem grande parte da funcionalidade para a qual os desenvolvedores usariam JavaScript.
* Detectando problemas cedo e frequentemente durante o desenvolvimento do site, fornecendo um validador que procura problemas no site que possam afetar o desempenho ou a acessibilidade.

**Os sites AMP são:**
* Construídos usando HTML, CSS e JavaScript padrão.
* Compatíveis com **todos** os navegadores modernos.
* Não dependem de ferramentas ou softwares especiais.

---

## Validação e o cache AMP
O cache é uma parte poderosa da arquitetura AMP. É uma rede de entrega de conteúdo (CDN) projetada para:
* Servir apenas páginas AMP válidas.
* Permitir que as páginas AMP sejam pré-carregadas com eficiência e segurança.
* Executar várias otimizações de desempenho nas páginas do cache.

Se seu site estiver no cache AMP, ele poderá ser efetivamente pré-carregado em segundo plano quando você estiver usando mecanismos de pesquisa como o Google. Além disso, o cache do AMP executará otimizações automáticas no seu site, como:
* Armazenando em cache fontes.
* Armazenando em cache e compactando imagens e convertendo-as em formatos mais recentes, como o WebP.
* Limpar documentos AMP para impedir ataques de script entre sites ou outras vulnerabilidades.
* Corrigindo problemas de HTML que podem resultar em renderização inconsistente em vários navegadores.

## A anatomia de uma página AMP
As páginas AMP válidas devem:
* Começar com o `<!doctype html>`.
* Conter as tags `<head>` e `<body>`.
* Conter uma `<meta charset="utf-8">` tag como o primeiro filho da tag `<head>`.
* Conter uma `<meta name="viewport" content="width=device-width,minimum-scale=1">` dentro da `<head>`
* Conter `<html amp>`
* Conter `<script async src="https://cdn.ampproject.org/v0.js"></script>` dentro da tag `<head>`.
* Conter `<link rel="canonical" href="$SOME_URL">` dentro da tag `<head>`.
* Conter `<style amp-boilerplate>`. 
  * **Observação:** Esse CSS oculta o conteúdo da página até que a biblioteca AMP termine de carregar

## CSS e AMP
O AMP impõe algumas restrições ao uso de CSS:
* Os estilos podem estar apenas no cabeçalho do documento, dentro de uma `<style amp-custom>`
* Uma página AMP pode ter apenas uma `<style amp-custom>`
* A página pode incluir não mais que 50K de CSS.
* A regra **!important** é restrita.

## Pensando em componentes
Os componentes em AMP tem as seguintes características:
* Um nome (por exemplo `<amp-img>`) usado como o nome da marca para identificar o componente.
* Atributos personalizados que alteram o comportamento, estilo ou conteúdo de um componente (como `width`, `height`, `src`, e `attribution`).
* Eventos que podem capturar entradas do usuário no componente (como o atributo `on`).

O sistema de componentes do AMP ajuda a criar rapidamente recursos eficientes e responsivos em suas páginas com o mínimo de esforço.  Existem componentes para criar formulários e carrosséis, para integrar a análise de páginas, para fazer solicitações XHR para servidores e muito mais. A lista completa de componentes pode ser vista [aqui](https://amp.dev/documentation/components/?format=websites)

**Observação:** Quase todos os componentes AMP são executados por pelo menos algum JavaScript, sendo necessária a inclusão de uma tag de script separada. E há uma boa razão para isso: você inclui apenas os scripts que realmente usa no seu site. Há algumas exceções, como é o caso da tag `<amp-img>`, que já é incorporado no script de tempo de execução do AMP.

## Encontrando o componente certo
Uma maneira de encontrar o componente certo é utilizando a página de [referência de componentes AMP](https://amp.dev/documentation/components/?format=websites). Ele contém uma lista dos componentes suportados pelo AMP. Cada entrada do componente inclui o nome do componente e uma breve descrição de qual funcionalidade o componente fornece. Além desse há um link com os [exemplos](https://amp.dev/documentation/examples/?format=websites) de utilização de alguns componentes AMP.

Os atributos no contexto do amp podem ser divididos em 3 tipos:
* Atributos comuns a todos os elementos HTML (`id`)
* Atributos comuns a todos os componentes do AMP (`width`, `height`, e `layout`)
* Atributos únicos para o componente (`type` no caso do `<amp-carousel>`)

#### Componente de vídeo
``` HTML
<amp-youtube data-videoid="BlpMQ7fMCzA" height="270" width="480" layout="responsive"></amp-youtube>
```

#### Componente de carousel
``` HTML
<amp-carousel width="412" height="309" layout="responsive" type="slides" loop>
  <amp-img src="https://cdn.glitch.com/d7f46a57-0ca4-4cca-ab0f-69068dec6631/cheddar-chaser.jpg" width="412" height="309" layout="responsive" ></amp-img>
  <amp-img src="https://cdn.glitch.com/d7f46a57-0ca4-4cca-ab0f-69068dec6631/cheese.jpg" width="412" height="309" layout="responsive" ></amp-img>
  <amp-img src="https://cdn.glitch.com/d7f46a57-0ca4-4cca-ab0f-69068dec6631/mouse.jpg" width="412" height="309" layout="responsive" ></amp-img>
</amp-carousel>
```

#### Componente de mídia social
```HTML
<div class="social-bar">
  <amp-social-share class="rounded" type="email" width="44" height="44"></amp-social-share>
  <amp-social-share class="rounded" type="linkedin" width="44" height="44"></amp-social-share>
  <amp-social-share class="rounded" type="tumblr" width="44" height="44"></amp-social-share>
  <amp-social-share class="rounded" type="twitter" width="44" height="44"></amp-social-share>
</div>
```