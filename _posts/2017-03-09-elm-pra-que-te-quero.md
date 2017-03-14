---
layout: post
title: "Elm, pra que te quero?"
description: "Uma visão pragmática de um desenvolvedor JavaScript sobre Elm.
Palestra realizada no meetup JavaScript São Paulo"
image: /public/images/posts/elm-pra-que-te-quero/elm.001.png
date:   2017-03-09 19:09:00
favorite: true
---

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" alt="Elm, pra que te quero?" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.001.png">

Esta é uma versão modificada da palestra que realizei no dia 8 de março de 2017
no meetup [JavaScript São Paulo][jssp]. Um [PDF com todos os slides][pdf] também
está disponível.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" alt="Emoji de um punho fechado e levantado" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.002.png">

Dia 8 de março é o Dia Internacional da Mulher. É um dia que é um marco na luta
das mulheres por melhores condições de vida e de trabalho. Ainda hoje, a
indústria de TI não é um ambiente saudável para muitas mulheres. Isso é errado.
Se você também já se convenceu que o sexismo não é legal, lute
ativamente contra ele. Não seja passivo.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.003.png">

Antes de começar, queria te convidar a respirar. Não é fácil aprender algo
completamente novo. Às vezes, durante uma apresentação, nos sentimos perdidos ou
não entendemos algo completamente. Isso é normal e faz parte do processo de
aprendizagem.

Minha palestra foi elaborada para um público que está familiarizado com
JavaScript utilizado no contexto de construção de webapps. Nem todo mundo se
encaixa perfeitamente neste público. Se você tem alguma dúvida, me pergunte.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.004.png">

Eu adoro JavaScript. É a linguagem que uso desde que comecei a desenvolver para
a web e também é a linguagem em que desenvolvo profissionalmente. Não há nenhuma
dúvida de que muitas outras pessoas amam JavaScript. Muitas empresas também
utilizam-no para construir software para web e outras plataformas.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.005.png">

Entretanto, existem algumas coisas no JavaScript que partem meu coração.
Problemas que podem ser resolvidos, mas que continuam aparecendo mesmo em
projetos realizados com equipes altamente experientes em que já trabalhei. E foi
por sofrer com estes problemas que eu comecei a procurar por uma alternativa.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.006.png">

O JavaScript é uma linguagem dinâmica. Isto significa que variáveis podem ter um
valor de um tipo em um momento e de outro tipo no futuro, o que é libertador
quando se comparado com toda a cerimônia em volta dos tipos em linguagens como
Java. Com essa vantagem também vem uma grande desvantagem, na minha opinião: não
é possível assegurar que o tipo de uma variável será constante.

A quantidade de bugs relacionados a tipos que eu tenho contato diariamente chega
a ser desmotivador. Não é tão raro ver um `Undefined is not a function` explodir
só porque alguém digitou uma letra errada no nome do método.

Como não é possível expressar tipos em código, os desenvolvedores acabam
precisando assumir o trabalho de pensar quais tipos estão fluindo por todo o
programa — uma alta carga cognitiva.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.007.png">

Refatorar grandes projetos não foi uma tarefa fácil para mim e para muitas
equipes em que trabalhei. Não acredito que seja realmente fácil realizar
refatorações mais complexas em qualquer outra linguagem, mas em uma linguagem
dinâmica como JavaScript, isto é uma grande tarefa.

Nas vezes em que precisei refatorar um pedaço de código utilizado por muitas partes
de um webapp, dependi basicamente de testes de unidade já escritos para as
funcionalidades afetadas. Depender apenas dos testes não é algo muito bom quando
você não tem certeza que todas as partes do sistema estão cobertas. 
Logo, testes manuais acabaram sendo necessários e viraram uma grande caça a
erros de execução.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.008.png">

Outro grande problema que já encontrei em projetos JavaScript é a falta de
gerenciamento de efeitos colaterais. A linguagem não força o uso de nenhuma
técnica para gerenciar efeitos colaterais como requisições HTTP e interação com o
DOM. As consequências disso são comportamentos inesperados por causa de simples
chamadas a funções, quando estas escondem efeitos colaterais indesejados.

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.009.png">

O último item da lista de coisas que me desapontam no JavaScript é a mutabilidade.
Objetos e arrays são mutáveis, o que significa que seus valores podem
ser alterados e o valor de uma variável pode mudar sem que um novo valor seja
explicitamente definido a ela.

Infelizmente não existem estruturas de dados imutáveis embutidas na linguagem.
Bibliotecas como [ImmutableJS][immutablejs] oferecem uma ótima alternativa, mas
a falta de compatibilidade direta com o resto do ecossistema previne que todas
as garantias de uma estrutura de dados imutável sejam garantidas.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.010.png">

Funções puras e gerenciamento de efeitos colaterais estão no coração da
programação funcional. Apesar do JavaScript ser uma linguagem amigável
para aplicar este paradigma, é bem difícil aproveitar suas vantagens
quando tantas funcionalidades da linguagem jogam no time inimigo.

Em meio aos meus estudos sobre programação funcional acabei descobrindo a
linguagem de programação Elm. Ela é uma linguagem desenvolvida especificamente
para a criação de webapps. Elm também é uma linguagem puramente funcional
fortemente tipada.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.011.png">

Linguagens de programação fortemente tipadas garantem que todos os dados que
fluem dentro de um programa durante sua execução têm o tipo esperado. Uma função
que recebe um `Int` nunca vai receber `String` por engano.

O compilador do Elm também é bem inteligente e consegue adivinhar qual o tipo de
cada função, tirando do desenvolvedor o trabalho de declará-los.

Alguns tipos básicos são:

- `Int` para números inteiros;
- `String` para trechos de texto;
- `List` para listas de um tipo específico. Parecido com arrays do JavaScript;
- `Record` para uma estrutura de dados bastante parecida com objetos no
    JavaScript. Representado pelas chaves (`{}`).

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.012.png">

Uma parte legal de ter tipos estáticos é que quando cometemos um engano, nosso
amigo compilador nos avisa. Neste exemplo, tentei
chamar a função `List.length` — que calcula o tamanho de uma `List` — passando
`"a"` que na verdade é uma `String`. Isso claramente é um erro! E o compilador
nos avisa o mais rápido possível.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.013.png">

Ele não é só útil com tipos, não! Eu já perdi as contas de quantas vezes eu
escrevi o nome de uma função errado e percebi só um bom tempo depois que esse
era o problema. Bom, isto é mais uma coisa que o compilador vai te avisar. Como
se não fosse o suficiente, ele também nos oferece uma solução!

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.014.png">

Em uma linguagem funcional, é de se esperar que funções estejam no centro,
certo? É bem fácil criar funções no Elm: basta escrever o nome da função, seus
argumentos, `=` e o corpo da função. Nada de palavras como `function`, diversos
parênteses e `return`. Elm tem uma sintaxe com apenas o essencial.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.015.png">

Apesar de o compilador do Elm ser capaz de adivinhar tipos, é útil defini-los
explicitamente como uma forma de documentação e para melhorar ainda mais as
mensagens de erro do compilador.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.016.png">

A função `greet` do nosso exemplo tem o tipo `User -> String`. Isso significa
que ela recebe um argumento do tipo `User` e retorna uma `String`. O tipo depois
da última seta (`->`) é o retorno e todos os outros são os argumentos da função.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.017.png">

Você já pensou em nunca se preocupar em esquecer de tratar `undefined` e `null`
no seu programa? Bom, o Elm não tem nenhum dos dois. Para tratar valores que
podem não estar definidos, o Elm conta com o tipo `Maybe`.

`Maybe` é um tipo que engloba outros dois tipos: `Just` e `Nothing`. Tipos como
`Maybe` são chamados de *union types*.

Uma variável do tipo `Maybe String`, por exemplo, representa um valor que pode
ser uma `String` (`Just String`) ou nada (`Nothing`). `Maybe` pode ser utilizado 
com qualquer outro tipo, como `User`.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.018.png">

Um dos casos de uso do tipo `Maybe` é expressar que algum dado ainda não está
disponível. Podemos, por exemplo, ter um variável com o tipo `Nothing` enquanto
os dados do usuário logado ainda não carregaram e `Just User` quando eles
estiverem voltado do servidor.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.019.png">

Para conseguir extrair o valor de um `Maybe` podemos utilizar uma *case
expression*, que é bem parecida com o `switch` do JavaScript.

Dentro de *case expressions* é necessário tratar todos os valores possíveis de
um tipo. Logo, é impossível não tratar valores `Nothing`!

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.020.png">

Um bom exemplo da aplicação do tipo `Maybe` é na função `List.head`. Esta função
retorna o valor do primeiro item de um `List`. O problema é que não é possível
assegurar no sistema de tipos que uma `List` sempre terá pelo menos um item.

Então, a função `List.head` retorna um `Maybe` do valor da lista. Dessa forma o
desenvolvedor pode definir o que acontecerá caso esta lista tenha ou não tenha itens.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.021.png">

Uma outra garantia que o Elm nos traz é a de que o valor de nenhuma variável
será alterado a não ser que definido explicitamente no código. Não é possível
alterar o valor de uma variável de dentro de uma outra função.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.022.png">

Sempre que você alterar uma `List`, por exemplo, um novo valor será retornado.
Fica a cargo do desenvolvedor gerenciar como estes dados são armazenados e
definidos.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.023.png">

Para fechar a lista de garantias do Elm, é importante deixar claro que todas as
funções do Elm são puras. Funções puras são funções que sempre retornam o mesmo
valor quando recebem os mesmos argumentos e que não alteram o mundo exterior
quando executadas.

Em JavaScript, por exemplo, é possível realizar chamadas ao servidor a partir de
qualquer função. No Elm, isto não é possível. Esta garantia livra o
desenvolvedor de pensar muito além do que a declaração de tipos enquanto avalia
o que uma função faz. Uma função que retorna uma `String` jamais realizará
chamadas HTTP.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.024.png">

Então, se não é possível realizar efeitos colaterais de dentro de funções do
Elm, como webapps criados com esta linguagem conversam com o mundo exterior?
Como enviam chamadas HTTP, renderizam interfaces na tela e recebem dados dos
usuários?

A ideia de ter apenas funções puras não é eliminar todos os tipos de efeitos
colaterais. Uma linguagem que não oferece uma forma do programa interagir com o
mundo não é útil.

Na verdade, a grande vantagem de limitar tanto os efeitos colaterais é obrigar
que todos eles sejam gerenciados adequadamente.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.025.png">

A forma que o Elm soluciona este problema é através da *Elm Runtime*. *Elm
Runtime* é a parte da linguagem que é executada no navegador do usuário e
gerencia todos os tipos de efeitos colaterais.

Pense no *Elm Runtime* como uma fronteira entre seu webapp Elm e o mundo real.
Esta fronteira gerencia o fluxo de informação que entra e sai do aplicativo e
garante que tudo rode perfeitamente.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.026.png">

Para construir aplicativos com Elm, utilizamos a "arquitetura Elm" (*Elm
Architecture*, em inglês). Ela é a arquitetura padrão adotada por toda a
comunidade da linguagem e oferece uma forma de dividir o seu aplicativo em três
partes com responsabilidades bem distintas: **Model**, estrutura de dados que
representa o estado da sua aplicação; **View**, uma função que retorna uma
interface de usuário dado o estado atual; e **Update**, uma função que
transforma o estado da aplicação a partir de mensagens geradas pela
interação do usuário e outras fontes externas.

Vamos dissecar cada uma dessas partes criando um simples contador.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.027.png">

A sua aplicação possui um estado. O estado é a estrutura de dados que contém dados
como o número atual do contador. Basicamente todos os dados necessários para
renderizar sua aplicação.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.028.png">

Para uma aplicação de contador, podemos representar o estado como uma chave
`counter` de tipo `Int` dentro de um `Record`.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.029.png">

Para inicializar nosso aplicativo, precisamos de um modelo inicial. Neste caso,
o valor de `counter` será `1`.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.030.png">

Agora, precisamos representar nosso estado com a interface que será de fato
renderizada para o usuário. A função que faz isso chama-se `view`.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.031.png">

`view` é uma função que recebe como único argumento o valor atual do estado e
retorna uma representação do que será renderizado na tela pelo *Elm runtime*.

No nosso caso queremos renderizar um botão com o número do contador dentro. No
Elm, elementos do DOM são representados por funções que recebem uma lista de
atributos e uma lista de filhos. A função `button`, então, recebe uma lista
vazia de atributos e um `text` como seu único filho.

O resultado disso é um botão com o texto do número do contador dentro.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.032.png">

Para alterar o estado conforme o usuário interage com a aplicação, utilizamos a
função `update`.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.033.png">

A função `update` recebe mensagens. Mensagens são do tipo `Messages`, que
definimos usando a seguinte sintaxe. No nosso caso, uma mensagem pode tanto ser
`Increment` quanto `Decrement`.


<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.034.png">

Para tratar cada tipo de mensagem, usaremos a expressão `case message of`.
Se `message` for `Increment`, aumentaremos a chave `counter`.
Caso seja `Decrement`, diminuiremos a chave `counter`.

A sintaxe `{ model | counter = ... }` é apenas uma forma de alterar o valor da
chave `counter` que está dentro do `model`. Lembrando que esta alteração retorna
um novo modelo.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.035.png">

Por fim, precisamos voltar lá na função `view` para de fato tratar cliques no
botão. A função `onClick` recebe uma `Message`, que será enviada à função
`update` quando o usuário clicar no botão.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.036.png">

`model`, `view` e `update` constituem a arquitetura Elm. Pelo menos uma visão
básica dela. Existem outros conceitos, como `subscriptions`, que decidi
não abordar no momento.

O mais importante de entender é que cada parte dessa aplicação apenas transforma
dados de um formato para outro. Estas três funções básicas representam tudo o
que pode acontecer no nosso webapp.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.037.png">

No nosso exemplo, representamos o botão com o estado inicial e conectamos a
mensagem `Increment` ao seu evento de clique com a função `view`. Esta mensagem
é futuramente tratada pela função `update`, que retorna um novo estado. A
função `view` é chamada com o novo estado e temos a nova representação do botão,
com o número diferente.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.038.png">

Para conectar `model`, `view` e `update` e realmente criar um aplicativo
interativo, utilizamos a função `Html.beginnerProgram`. Ela vai tomar conta de tudo o
que acontece por baixo dos panos na nossa aplicação.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.039.png">

Finalmente, podemos compilar nosso código e vê-lo funcionar no navegador. Para
isso, usamos a ferramenta de linha de comando `elm-make`. Supondo que escrevemos
todo esse código em `App.elm`, basta rodar `elm-make App.elm`.

(Para manter a palestra breve e sucinta, não mostrei como instalar o Elm e
escondi alguns trechos de código. Se você quiser ver um exemplo real desta
aplicação, basta acessar [https://ellie-app.com/D9Q8Xy9sdza1/2](https://ellie-app.com/D9Q8Xy9sdza1/2))

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.040.png">

Por seguir uma série de boas práticas e forçar a criação de um código puro e
fortemente tipado, o Elm nos traz simplicidade e confiança. Um ótimo resultado
desta simplicidade e confiança é que a manutenibilidade do webapp sobe já que é
muito mais fácil discernir sobre o que está acontecendo no código. Não existem
infinitos caminhos a se trilhar, apenas funções que recebem e retornam valores.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.041.png">

Todas estas garantias vêm com vantagens interessantes, como um compilador
inteligente e uma linguagem simplificada. Estruturas de dados que são sempre
imutáveis e uma arquitetura única vão bem além da bagunça que aplicativos
JavaScript podem se tornar.

Outra vantagem do Elm, não abordada anteriormente, são pacotes versionados
corretamente. É impossível atualizar um pacote com mudanças que quebrariam o
código das outras pessoas sem realizar uma mudança `major` em sua versão, por
exemplo.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.042.png">

Entretanto, nem tudo é um mar de rosas. Elm possui algumas desvantagens, ou —
como prefiro dizer — desafios. Ir de um mundo imperativo, onde enviar uma
requisição HTTP está apenas a uma chamada de função de distância, para um mundo
declarativo não é fácil. Bom, não foi fácil para mim pelo menos. Com prática
ficou mais fácil e agora eu já não quero mais programar imperativamente.

A comunidade do Elm também é relativamente pequena, mas crescendo a cada dia.

Com seu foco em webapps, muitas coisas que você consegue fazer com JavaScript,
como escrever aplicações back-end ou até aplicativos nativos, não estão disponíveis
em Elm. O foco do Elm é a criação de webapps interativos.

A presença de apenas um estado para representar toda a interface é também uma
diferença significativa comparando com outros modelos de desenvolvimento de
interface como os adotados com React. Estas diferenças exigem prática para que
você se acostume.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.043.png">

Explore! Esta é a minha mensagem final. Se você se interessou por Elm, existe
bastante conteúdo para você se aprofundar. Aprenda e participe desta comunidade
em desenvolvimento!

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.044.png">

Isso é tudo. Siga-me no Twitter em [@hugobessaa][@hugobessaa] e acompanhe este blog para mais
conteúdo sobre Elm. Obrigado 👍.

<div class="cf"></div>

{% include _elm-newsletter.html %}

[jssp]: https://www.meetup.com/Javascript-SP/
[immutablejs]: https://facebook.github.io/immutable-js/
[@hugobessaa]: https://twitter.com/hugobessaa
[pdf]: {{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.pdf
