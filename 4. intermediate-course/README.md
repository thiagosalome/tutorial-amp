# 4. Curso Intermediário

## Recursos a serem criados
Nesse tópico serão implementados os seguintes itens:
* Um menu deslizante, para que os usuários possam navegar entre as páginas
* Um formulário, para coletar informações dos usuários
* Armazenamento de dados no servidor e exibição de uma mensagem de sucesso.

## Eventos e ações no AMP
Imagine que, ao clicar em um botão, eu queira que uma mensagem desapareça. No HTML, o código seria algo como:
```HTML
<div id="warning">This is a warning.</div>
<button onclick="document.getElementById(‘warning’).hidden = true;">
  Hide Warning
</button>
```
Já no AMP, funcionaria da seguinte forma:
```HTML
<div id="warning">This is a warning.</div>
<button on="tap:warning.hide">
  Hide Warning
</button>
```
`tab` = evento
`warning`= id
`hide`= action

## Criando o menu

```HTML
<amp-sidebar class="sidebar" id="sidebar-menu" layout="nodisplay" side="left">
  <div class="navbar-trigger" role="button" tabindex="0" on="tap:sidebar-menu.toggle">X</div>
  <nav class="nav">
    <ul class="label">
      <li class="nav-item"><a href="#">Our Story</a></li>
      <li class="nav-item"><a href="#">Our Bikes</a></li>
      <li class="nav-item"><a href="#">Latest Models</a></li>
      <li class="nav-item"><a href="#">Contact</a></li>
    </ul>
  </nav>
</amp-sidebar>
```

**Observações:**
* O atributo `role="button"` é necessário por questões de acessibilidade. Ele demonstra para o leitor de tela que o elemento se trata de um botão.
* O atributo `tabindex="0"` permite que aqueles usuários que navegarem na página usando apenas um teclado possam destacar e interagir com o componente de foco.

## Criando submenu
```HTML
<li class="nav-item nav-dropdown">
  <amp-accordion>
    <section>
      <header>Our Bikes</header>
      <ul class="dropdown-items">
        <li class="dropdown-item"><a href="#">Ricotta Racer</a></li>
        <li class="dropdown-item"><a href="#">Cheddar Chaser</a></li>
        <li class="dropdown-item"><a href="#">Parmesan Pacer</a></li>
      </ul>
    </section>
  </amp-accordion>
</li>
```

## Usando templates para dar feedback
Os modelos/templates são uma maneira de converter dados dinâmicos (geralmente gerados a partir de um servidor) em pedaços de HTML que são inseridos na página. O tipo mais comum de modelo usado nas páginas AMP é `<amp-mustache>`.
Por exemplo, quando dados os seguintes:
```JSON
{ 
  "name" :  "Bob" , 
  "job" :  "builder" 
}
```
E o seguinte modelo:
```HTML
<template type="amp-mustache">
  <p>{{name}} is an excellent {{job}}!</p>
</template>
```
Resultado
```HTML
<p>Bob is an excellent builder!</p>
```