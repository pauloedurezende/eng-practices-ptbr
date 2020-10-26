# Navegando em uma CL na Revisão



## Sumário

Agora que você sabe [o que procurar](looking-for.md), qual é a maneira mais
eficiente de gerenciar uma revisão que se espalha por vários arquivos?

1.  A mudança faz sentido? Tem uma boa
    [descrição](../developer/cl-descriptions.md)?
2.  Observe primeiro a parte mais importante da mudança. Está bem desenhado
    No geral?
3.  Observe o restante da CL em uma sequência apropriada.

## Etapa 1: Ter Uma Visão Ampla da Mudança {#etapa-um}

Veja a [descrição da CL](../developer/cl-descriptions.md) e o que a CL faz
em geral. Essa mudança faz sentido? Se essa mudança não deveria ter acontecido
em primeiro lugar, responda imediatamente com uma explicação de por que a
mudança não deveria estar acontecendo. Quando você rejeita uma alteração como
essa, também é uma boa ideia sugerir ao desenvolvedor o que eles deveriam ter
feito.

Por exemplo, você pode dizer "Parece que você fez um bom trabalho nisso, obrigado!
No entanto, na verdade, estamos indo na direção de remover o sistema FooWidget que
você está modificando aqui e, portanto, não queremos fazer novas modificações no
momento. Que tal refatorar nossa nova classe BarWidget?"

Observe que o revisor não apenas rejeitou a CL atual e forneceu uma sugestão
alternativa, mas também o fez *com cortesia*. Esse tipo de cortesia é importante
porque queremos mostrar que nos respeitamos como desenvolvedores, mesmo quando
discordamos.

Se você obtiver mais do que algumas CLs que representam alterações que não deseja
realizar, considere refazer o processo de desenvolvimento de sua equipe ou o
processo publicado para colaboradores externos, para que haja mais comunicação
antes que as CLs sejam escritas. É melhor dizer às pessoas "não" antes de fazerem
uma tonelada de trabalho que agora precisa ser jogado fora ou drasticamente
reescrito.

## Etapa 3: Examine as Principais Partes da CL {#etapa-dois}

Encontre o arquivo ou arquivos que são a parte "principal" desta CL.
Frequentemente, há um arquivo que possui o maior número de alterações lógicas e é
a parte principal da CL. Veja essas partes principais primeiro. Isso ajuda a
contextualizar todas as partes menores da CL e geralmente acelera a revisão do
código. Se a CL for muito grande para você descobrir quais são as partes principais,
pergunte ao desenvolvedor o que deve procurar primeiro ou peça que ele
[divida a CL em várias outras CLs](../developer/small-cls.md).

Se você encontrar alguns problemas de design importantes nessa parte da CL, envie
esses comentários imediatamente, mesmo se não tiver tempo para revisar o restante da
CL agora. De fato, revisar o resto da CL pode ser um desperdício de tempo, porque se
os problemas de design forem significativos o suficiente, muitos dos outros códigos
em revisão desaparecerão de qualquer maneira, não importa como.

Há duas razões principais para a importância de enviar esses comentários
importantes de design imediatamente:

-   Os desenvolvedores geralmente enviam uma CL e depois iniciam imediatamente um
    novo trabalho com base nessa CL enquanto aguardam a revisão. Se houver grandes
    problemas de design na CL que você está revisando, eles também terão que
    refazer a CL posterior. Você quer pegar estes pontos antes que eles tenham feito
    muito trabalho extra em cima do design problemático.
-   As principais alterações de design levam mais tempo do que as pequenas alterações.
    Quase todos os desenvolvedores possuem prazos; para cumprir esses prazos e ainda
    ter qualidade de código na base atual, o desenvolvedor precisa iniciar qualquer
    grande re-trabalho de uma CL o mais rápido possível.

## Etapa 3: Examine o Restante da CL em Uma Sequência Apropriada {#etapa-3}

Depois de confirmar que não há grandes problemas de design com o CL como um todo,
tente descobrir uma sequência lógica para examinar os arquivos, além de garantir
que você não perca a revisão de nenhum arquivo. Geralmente, depois de examinar os
arquivos principais, é mais simples analisar cada arquivo na ordem em que a
ferramenta de revisão de código os apresenta a você. Às vezes, também é útil ler
os testes antes de ler o código principal, porque então você tem uma idéia do que
a mudança deve estar fazendo.

Próximo: [Velocidade de um Revisões de Código](speed.md)
