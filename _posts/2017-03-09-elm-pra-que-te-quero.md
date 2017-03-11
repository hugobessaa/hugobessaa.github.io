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

Esta é uma palestra que realizei no dia 8 de março de 2017 no meetup [JavaScript
São Paulo][jssp].

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" alt="Emoji de um punho fechado e levantado" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.002.png">

Dia 8 de março é o Dia Internacional da Mulher. É um dia que serve como um
lembrete de algo que homens deveriam fazer todos os dias: respeitar as
mulheres. Se você também já se convenceu que o machismo não é legal, lute
ativamente contra ele. Não seja passivo. Essa é mensagem que quero passar nesse
dia.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.003.png">

Antes de começar, queria te convidar a respirar. Não é fácil aprender algo
completamente novo. Às vezes durante uma apresentação nos sentimos perdidos ou
não entendemos algo completamente. Isso é normal e faz parte do processo de
aprendizagem.

Minha palestra foi elaborada para um público que está familiarizado com
JavaScript utilizado no contexto de construção de webapps. Nem todo mundo se
encaixa perfeitamente neste público. Se você tem alguma dúvida, me pergunte.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.004.png">

Eu adoro JavaScript. É a linguagem que uso desde que comecei a desenvolver para
a web e também é a linguagem em que desenvolvo profissionalmente. Não há nenhuma
dúvida que muitas outras pessoas também amam JavaScript. Muitas empresas também
o utilizam para construir software para web e outras plataformas.

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
refatorações mais complexas em qualquer outra linguagem, mas com uma linguagem
dinâmica como JavaScript, isto é uma grande tarefa.

Nas vezes em que precisei refatorar um pedaço de código utilizado por muitas partes
de um webapp, dependi basicamente de testes unitários já escritos para as
funcionalidades afetadas. Depender apenas dos testes não é algo muito bom quando
você não tem certeza que todas as partes do sistema estão cobertas por tests. 
Logo, testes manuais acabaram sendo necessários e viraram uma grande caça a
erros de execução.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.008.png">

Outro grande problema que já encontrei em projetos JavaScript é a falta de
gerenciamento de efeitos colaterais. A linguagem não força o uso de nenhuma
técnica para gerencia efeitos colaterais como requisições HTTP e interação com o
DOM. As consequências disso são comportamentos inesperados por causa de simples
chamadas a funções.

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.009.png">

O último item da lista de coisas que me desapontam no JavaScript é: mutabilidade.
Objetos e arrays são mutáveis, o que significa que elas seus valores podem
ser alterados e o valor de uma variável mudar sem que um novo valor seja
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
linguagem de programação Elm. Ela é uma linguagem criada especificamente
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

- `Int` para números inteiros
- `String` para trechos de texto
- `List` para listas de um tipo específico. Parecido com arrays do JavaScript.
- `Record` para uma estrutura de dados bastante parecida com objetos no
    JavaScript. Representado pelas chaves (`{}`).

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.012.png">

Quando cometemos um engano, nosso amigo compilador avisa. Neste exemplo, tentei
chamar a função `List.length` — que calcula o tamanho de uma `List` — passando
`"a"` que na verdade é uma `String`. Isso claramente é um erro! E o compilador
avisa isso o mais rápido possível.

<div class="cf"></div>

<img class="ba b--mid-gray w-40-ns fl-ns mr3-ns" src="{{ site.baseurl }}/public/images/posts/elm-pra-que-te-quero/elm.013.png">

Ele não é só útil com tipos, não! Eu já perdi as contas de quantas vezes eu
escrevi o nome de uma função errado e percebi só um bom tempo depois que esse
era o problema. Bom, isto é mais uma coisa que o compilador vai te avisar. Como
se não fosse o suficiente, ele também nos oferece uma solução!

<div class="cf"></div>




{% include _elm-newsletter.html %}

[jssp]: https://www.meetup.com/Javascript-SP/
[immutablejs]: https://facebook.github.io/immutable-js/
