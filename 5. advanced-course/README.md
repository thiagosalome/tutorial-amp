# 5. Curso avançado

## Recursos a serem criados
Nesse tópico aprenderemos como alterar a aparência ou o conteúdo da página com base em como os usuários interagem com nosso site. Você verá sobre:
* Armazenamento de informações nas variáveis ​​de estado do aplicativo em resposta às ações do usuário.
* Alteração do conteúdo ou da aparência de um site quando as variáveis ​​de estado forem atualizadas.
* Recuperação e exibição de dados do servidor em sua página usando modelos.
* Alteração dinamica do conteúdo na tela (por exemplo, filtrando e classificando dados).

## Armazenando informações no estado do aplicativo
Exemplo de como definir uma variável de estado a partir de um clique no botão:
```HTML
<button on="tap:AMP.setState({wasPressed: true})">
  Press Me
</button>
```

Definindo o estado inicial das variáveis utilizando `amp-state`
```HTML
<amp-state id="accordionState"/>
  <script type="application/json">
    {
      "isOpen": false
    }
  </script>
<amp-state>
<button on="tap:AMP.setState({ accordionState: { isOpen: !accordionState.isOpen }})">
  Open/Close All Sections
</button>
```

## Alterando conteúdo e aparência do site quando as variáveis são atualizadas
Pegando o valor de um estado e o apresentando dentro de uma tag `p`
```HTML
<button on="tap:AMP.setState({message: ‘Hello AMP!’})">
  Say Hello!
</button>
<p [text]="message"></p>
```
Outros exemplos de atributos além do `[text]` são `[width]`, `[height]`, `[hidden]` e `[class]`. A lista completa de propriedades vinculáveis pode ser encontrada [aqui](https://amp.dev/documentation/components/amp-bind/#element-specific-attributes).
**Observação:** Para garantir que seus componentes tenham uma aparência razoável no carregamento da página, sempre inclua um valor padrão para uma propriedade vinculada.

Validando se duas senhas correspondem
```HTML
<input type="text" placeholder="Password" on="change:AMP.setState({ firstPassword: event.value })" />
<input type="text" placeholder="Re-Enter Password" on="change:AMP.setState({ secondPassword: event.value })" />
<p hidden [hidden]="firstPassword == secondPassword">
  The passwords don't match!
</p>
```

## Recuperação e exibição de dados do servidor
O componente que usamos para recuperar e exibir dados do servidor como este é chamado `<amp-list>`. Também usaremos os modelos `<amp-mustache>`