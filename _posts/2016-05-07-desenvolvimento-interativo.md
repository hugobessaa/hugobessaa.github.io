---
layout: post
title: "Desenvolvimento interativo"
description: "Uma história de como comecei com desenvolvimento interativo e quais suas vantagens"
date:   2016-05-07 04:09:00
favorite: true
redirect_from: /2016/05/07/desenvolvimento-interativo/
---

Nos últimos projetos de desenvolvimento de interface que trabalhei havia uma
demanda muito grande por um resultado interativo e fluido. Nada mais justo:
usuários estão agora se acostumando com produtos que possuem UIs refinadas e bem
suaves. Aplicativos como Instagram, Twitter e até mesmo os sistemas operacionais
móveis mais modernos levantaram o padrão de qualidade esperado pelos usuários.

Apesar do resultado final de algumas funcionalidades muitas vezes parecer ser
bem simples, algumas interações mais completas tomam um belo tempo no processo
de desenvolvimento.

Ao longo dos últimos 2 anos, venho melhorando meu processo de desenvolvimento
para permitir que eu passe mais tempo focado nestes detalhes sem prejudicar o
projeto. E, agora, acredito que encontrei uma ótima forma de desenvolver
interfaces.

### desenvolvimento interativo

Se as interfaces que produzimos são interativas e fluidas, por que nosso
processo de desenvolvimento seria diferente? Quanto menor o tempo de feedback
entre escrever o código e ver o resultado, melhor. Com base nisso, introduzi
aos poucos algumas ferramentas nos meus últimos projetos[^projetos] até criar um
ambiente de desenvolvimento totalmente interativo.

Desenvolvimento interativo significa iterar rapidamente entre a versão inicial e
final do seu código, melhorando incrementalmente o resultado a partir do
feedback rápido (algumas vezes até instantâneo) de suas modificações.

Antes de chegar ao estado final de uma parte do código, passamos por
muitos erros e acertos, melhorando a qualidade da interface a cada iteração.
Não são muitas ferramentas que permitem esta forma de interação rápida.

Quando comecei a utilizar ClojureScript, a coisa que mais me chamou atenção foi
o foco da comunidade em criar ferramentas que suportam o desenvolvimento
interativo. Isto representou uma mudança bem grande em como crio e trabalho.

### fluxo

Com o suporte do desenvolvimento interativo, o meu fluxo de trabalho mudou
bastante. Antes eu passava um bom tempo escrevendo e imaginando como cada
alteração no código refletiria na interface. Quando o ciclo de feedback ficou
mais rápido, fui encorajado a construir e arquitetar a interface em pequenos
pedaços.

Desenvolver pedaços pequenos de código e já ter um feedback sobre eles é
essencial para não ter que manter grandes partes de código na sua cabeça. Cada
função, cada linha, cada componente se junta ao resto do programa, formando o
todo.

Desenvolvedores back-end conseguem manter um ciclo de feedback rápido
utilizando testes, que mostram se o que foi desenvolvido funciona. Na criação de
interfaces, nem sempre o que produzimos pode ser testado por uma suíte de testes
automatizados. Estilos, pequenas nuances no comportamento e outras coisas que
fazem parte do dia-a-dia do desenvolvedor front-end precisam ser vistas para
serem validadas.

Ferramentas que recarregam o código e aplicam as modificações feitas no código da
interface sem recarregar a página ajudam muito durante o fluxo de
desenvolvimento front-end. Mantendo o estado da aplicação é possível testar
rapidamente as diversas formas que um componente pode ser aplicado e corrigir
bugs que acontecem em estados específicos da aplicação.

### editor

Não é novidade que usar um ótimo editor de texto ou IDE para desenvolver uma
aplicação é muito importante. Esta é, afinal, a ferramenta na qual você
provavelmente passa mais tempo imerso.

Integrar uma aplicação em execução com meu editor de texto é outra coisa que
melhorou muito meu fluxo de desenvolvimento. Utilizando ClojureScript, o Emacs
oferece um ambiente de desenvolvimento completo. Eu consigo inspecionar o estado
atual da aplicação, executar código a partir do editor e testar cada parte nova
no sistema utilizando alguns comandos.

Com todo esse ferramental, a parte mais difícil acaba sendo criar código
compatível com o desenvolvimento interativo. Código imperativo e com muitos
efeitos colaterais não controlados não se adapta bem nesse ambiente. Na minha
experiência, forçar a escrita de código "recarregável" só me ajudou a manter
toda a aplicação mais confiável e testável.

### referências externas

Este artigo não explora a fundo cada ferramenta. Logo, listo algumas referências
externas que podem te ajudar a conhecer mais e aplicar o desenvolvimento
interativo:

- [The Blessing of Interactive Development](http://tonsky.me/blog/interactive-development/)
- [Interactive programming Flappy Bird in ClojureScript](Interactive programming Flappy Bird in ClojureScript)
- [Hot Reloading with Time Travel (react)](https://www.youtube.com/watch?v=xsSnOQynTHs)
- [A Quick Introduction to BrowserSync](https://www.youtube.com/watch?v=heNWfzc7ufQ)

Desenvolver interativamente pode chegar a ser viciante. Eu mesmo não quero mais
fazer coisas do jeito antigo. Boa jornada.

[^projetos]:
    Estes projetos incluem alguns sites utilizando WordPress, novas features em
    uma interface antiga e um produto construído do zero com o desenvolvimento
    interativo em mente.
