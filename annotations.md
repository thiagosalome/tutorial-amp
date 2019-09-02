# Tutorial AMP

1. Recomendado a utilização de protocolo HTTPS
2. Os documentos HTML com amp devem:
* Conter o doctype
* Conter `<html amp>`
* Conter `<head>` e `<body>`
* Conter uma `<meta charset="utf-8">` como primeiro filho
* Conter `<script async src="https://cdn.ampproject.org/v0.js"></script>` no head
  * Inclui e carrega a biblioteca JS do AMP.
* Conter `<link rel="canonical" href="$SOME_URL">` dentro da tag head
  * Aponta para a versão HTML comum do documento

### Inserindo uma imagem
`<amp-img src="welcome.jpg" alt="Welcome" height="400" width="800"></amp-img>`

### Inserindo conteúdo CSS
**Obeservações:**
* Deve-se adicionar o atributo *amp-custom* na tag `<style>`
* Toda página AMP pode ter apenas **uma única** folha de estilo.

### Vinculando páginas
Há casos em que é necessário ter a versão de uma página AMP e não AMP, como de notícias por exemplo. Nesse caso, se o Google encontrar a versão não AMP, como faria para saber se ela tem a versão com AMP? Para isso é adicionada a seguinte tag:
* Página não AMP
`<link rel="amphtml" href="https://www.example.com/url/to/amp/document.html">`

* Página AMP
`<link rel="canonical" href="https://www.example.com/url/to/full/document.html">`

**Observação:** Se você tiver apenas uma página e ela for AMP, deve-se criar um link apontando para ela.