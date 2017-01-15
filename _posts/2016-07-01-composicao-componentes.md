---
layout: post
title: "Composição de componentes"
description: "A composição de componentes representados como funções é bastante
poderosa"
image: /public/images/posts/composition/component-composition-hero.png
date:   2016-07-01 17:42
favorite: true
---

Composição de funções, na matemática, é a aplicação de uma função sobre o valor
de outra para produzir uma terceira função. Portanto, dadas as funções `f(x)` e
`g(x)`, a composição de `f` com `g` é a função `ƒ: x → f(g(x))`. Em um exemplo
mais abordável, a composição de `add2: x → x + 2` com `add4: x → x + 4` é uma 
função ƒ que podemos chamar de `add6`, já que `add6: num → add2(add4(num))`. A 
aplicação de `add6` com `4` pode ser representada como:
`add6(4) = add2(add4(4)) = add2(8) = 10`.

![Exemplo de composição de componentes (Box ∘ Button)]({{ site.baseurl }}/public/images/posts/composition/component-composition-hero.png)

Como já escrevi em outro post aqui no blog, [componentes de interface podem ser
representados como funções][components-post]. Funções não são estritamente matemáticas no
JavaScript, mas elas também podem ser compostas. Isso significa que podemos
utilizar o retorno de um componente dentro de outro para formar nossa interface.

Já estamos bem acostumados a utilizar elementos HTML aninhados:

```js
+-<body>----------------------------+
| +-<div>-------------------------+ |
| |  <span>                       | |
| |  Deseja continuar?            | |
| |                               | |
| |  <button>          <button>   | |
| |  +--------+        +--------+ | |
| |  | Cancel |        | Ok     | | |
| |  +--------+        +--------+ | |
| +-------------------------------+ |
+-----------------------------------+
```

Com componentes representados como funções, podemos criar interfaces com
mais do que apenas elementos HTML aninhados. **Estrutura, comportamento e 
estilos podem ser aninhados** para construir interfaces.

[React][react] foi a primeira biblioteca JavaScript largamente utilizada a 
propor uma forma de compor componentes com simplicidade. A interface ilustrada
acima poderia ser representada desta forma com React (usando [JSX][jsx]):

```html
<SectionBox>
  <Modal>
    <InfoMessage>Deseja continuar?</InfoMessage>
    <Button>Cancel</Button>
    <Button>Ok</Button>
  </Modal>
</SectionBox>
```

Cada componente (`<SectionBox>`, `<Modal>`, `<InfoMessage>`, `<Button>`) traz
seu comportamento personalizado. Essa simplicidade de aninhar componentes é, na
minha opinião, a maior vantagem do React. Se você ainda não está familiar com
React, leia [este artigo][comecando-com-react] introdutório antes de prosseguir.

## Um ícone e um botão

Um conjunto que sempre aparece nas interfaces que implemento é um botão com
algum ícone e um texto de ação. Ele é um exemplo simples de como compor
componentes. Imagine que você precisa implementar um assim:

```
+---------------+
| Adicionar (+) |
+---------------+
```

Podemos chamar esse componente de `IconButton`. Ele recebe as *props* `icon`,
`children` e `onClick`. Uma simples implementação seria:

```html
let IconButton = ({icon, children, onClick}) => 
  <Button onClick={onClick}>
    {children}
    <Icon icon={icon} /> 
  </Button>
```

Dentro do novo componente `IconButton` utilizamos `Button` e `Icon`. Apesar de
ser bem simples, esse exemplo já mostra como podemos criar uma abstração da
utilização de dois componentes juntos. `Button`, por exemplo, pode ter toda uma
lógica de como tratar o *callback* `onClick` e isso será transparente para o
`IconButton`.

## Um botão e uma tooltip

Interfaces mais complexas podem precisar mostrar algumas dicas para o usuário
enquanto ele as utiliza, guiando-o pelas funcionalidades disponíveis. Em outro
projeto recente eu precisei criar um componente bem parecido com isso:

```
+--------------------+
|                    |
| Texto explicativo  |
|                    |
+---------V----------+
   +--------------+
   |    Button    |
   +--------------+
```

Este conjunto de `Button` com `Tooltip` não parece muito complexo de se
implementar. `Button` é igual ao que utilizamos anteriormente. `Tooltip` é um
componente que recebe `children`, `direction` e `hidden` para renderizar um balão
explicativo flutuante.

```html
let Tooltip = ({direction, hidden, children}) =>
  <div className={`Tooltip is-${direction} ${hidden ? 'is-hidden' : ''}`}>
    {children}
  </div>

Tooltip.propTypes = {
  direction: React.PropTypes.oneOf(['up', 'down'])
}
```

Nosso componente que renderiza o botão e o texto explicativos juntos os
utilizaria da seguinte forma:

```html
class ActionWrapper extends Component {
  constructor (props) {
    super(props)
    this.state = {isTipOpen: false}
  }

  onButtonClick () {
    this.setState({isTipOpen: !this.state.isTipOpen})
  }

  render () {
    return (
      <div>
        <Tooltip direction='up' hidden={!this.state.isTipOpen} />
        <Button onClick={onButtonClick.bind(this)}>Button</Button>
      </div>
    )
  }
}
```

O método `onButtonClick` mostra/esconde a `Tooltip`. Ele é chamado no evento de
*click* do botão. Esse tipo de componente é bem simples também, nenhum mistério
aqui.

No projeto em que implementei este componente, havia um detalhe pequeno, mas bem
importante, na funcionalidade da `Tooltip`: ela deveria abrir evitando ser
escondida pela tela. Então, se o botão estiver muito em cima na tela, o balão de
dica não poderia ficar escondido e sim abrir para baixo.

```
            Normal                  Automático
    +--------------------+   
    |                    |   
    | Texto explicativo  |   
===========================tela==========================
    |                    |   
    +---------V----------+   
       +--------------+            +--------------+
       |    Button    |            |    Button    |
       +--------------+            +--------------+
                                +---------ʌ----------+
                                |                    |
                                | Texto explicativo  |
                                |                    |
                                +--------------------+
```

É inviável implementar a lógica necessária para este comportamento em cada
componente que utiliza `Tooltip`. Em vez disso, essa lógica é abstraída pela
`Tooltip` e reutilizada em todos os lugares que a renderizam.

## Layout

Os componentes mais utilizados nos projetos React que desenvolvi foram os de
layout. Estes componentes abstraem a lógica e os estilos de como compor outros
componentes para formar uma interface completa.

O lugar onde eles são mais usados são em componentes que representam páginas. Se
construirmos os componentes corretos e utilizarmos a composição ao nosso favor,
todas as páginas serão apenas a composição de um conjunto de componentes, sem 
estilo ou lógica personalizada.

Isso pode parecer muito trabalho para pouco retorno. Na minha experiência,
manter componentes desacoplados de suas páginas oferece uma facilidade sem igual
na hora de alterar o design de uma página e reutilizar algum componente em
outra.

Componentes de layout ajudam a manter a disposição dos elementos como uma
responsabilidade da página, já que os componentes não devem saber quais estarão
por perto.

`Spacing` é um componente que utilizei com sucesso em alguns projetos. A
responsabilidade dele é apenas embrulhar todos os seus filhos em uma `div` e
cuidar do espaçamento entre eles.

```html
<Spacing>
  <Button>Ok</Button>
  <Button>Cancel</Button>
</Spacing>
```

Esse código iria renderizar os dois botões separados por um espaço. `Spacing`s
também podem ser aninhados para formar layouts mais complexos.

```html
<Spacing>
  <span>Deseja continuar?</span>
  <Spacing direction='horizontal'>
    <Button>Cancel</Button>
    <Button>Ok</Button>
  </Spacing>
</Spacing>
```
```
+-<Spacing>----------------------+
|  Deseja continuar?             |
|                                |
| +-<Spacing>------------------+ |
| |+--------+        +--------+| |
| || Cancel |        | Ok     || |
| |+--------+        +--------+| |
| +----------------------------+ |
+--------------------------------+
```

Páginas bem complexas, poderiam compor diversos componentes e `Spacing`s para
formar um layout simples.

A implementação do `Spacing` é bem simples:

```html
let Spacing = ({children = [], direction = 'vertical'}) =>
  <div className={`Spacing is-${direction}`}>
    {[].concat(children).map((child) =>
      <div className='Spacing-item'>{child}</div>
    )}
  </div>
```

Os estilos também (em versão simplificada):

```css
.Spacing {
  display: flex;
}

.Spacing.is-vertical {
  flex-direction: column;
}

.Spacing.is-horizontal {
  flex-direction: row;
}

.Spacing-item {
  padding: 5px;
}
```

Para layouts mais complexos, sugiro que você dê uma olhada no
[Reflexbox][reflexbox], um conjunto de componentes bem interessantes que
permitem que você construa layouts utilizando Flexbox.

## Componentes flexíveis

O último exemplo de composição que eu queria mostrar é a ideia de componentes
flexíveis. Interfaces de usuário mudam o tempo inteiro (pelo menos as que eu
trabalhei). Designers têm novas ideias, testes A/B mostram melhores soluções,
novos requerimentos trazem novos estilos.

Como desenvolvedores de interfaces, precisamos sempre levar isso em conta quando
estamos construindo nossos projetos. Ter um código altamente rígido não é algo
que você quer quando os pedidos de mudança começarem a chegar.

Uma forma de mitigar este problema é criando componentes mais flexíveis. Vamos
usar um exemplo de um Modal. Poderíamos implementá-lo de uma forma em que todo o
modal é renderizado a partir de *props* previamente definidas:

```html
<Modal
  title='Deseja continuar?'
  message='Esta operação cancelará todas as suas alterações'
  onOk={}
  onCancel={} />
```

Apesar de ser bem conciso, este componente é bastante rígido. Não é possível
mudar quais botões são renderizados, inserir um componente entre o título e a
mensagem e dentre outras coisas.

Uma forma de resolver isso é separando o componente `Modal`. Ele pode ser
separado em `ModalTitle`, `ModalMessage`, `ModalActions`. O uso seria assim:

```html
<Modal>
  <ModalTitle>Deseja continuar?</ModalTitle>
  <ModalMessage>
    Esta operação cancelará todas as suas alterações
  </ModalMessage>
  <ModalActions>
    <Button onClick={}>Ok</Button>
    <Button onClick={}>Cancel</Button>
  </ModalActions>
</Modal>
```

Separar cada componente dá uma grande flexibilidade para quem utilizará o
`Modal`. É bem mais fácil controlar os botões, a disposição do conteúdo e
alterar o design do modal. Esse é um bom exemplo do poder que vem da composição
de componentes.

Como eles podem ser compostos livremente, caso você perceba algum padrão que se
repete frequentemente no seu código, é possível abstraí-lo em outro componente.
Simples assim.

***

Estas foram apenas algumas coisas que aprendi após mais de um ano utilizando 
React e outras bibliotecas similares. Ainda na primeira versão, este artigo com
certeza precisa de algumas melhorias. Sinta-se à vontade de entrar em contato
comigo para esclarecer alguma ideia.

[components-post]: http://hugobessa.com.br/dev/2015/09/25/componentes/
[Haskell]: https://www.haskell.org/
[Elm]: http://elm-lang.org/
[hyperscrit-helpers]: https://github.com/ohanhi/hyperscript-helpers
[react]: http://reactjs.com/
[jsx]: https://facebook.github.io/jsx/
[comecando-com-react]: http://hugobessa.com.br/2015/01/17/comecando-com-react/
[reflexbox]: https://github.com/jxnblk/reflexbox
