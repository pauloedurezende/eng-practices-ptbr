# Manipulando pushback em revisões de código



Às vezes, um desenvolvedor adia uma revisão de código. Eles não concordam com sua
sugestão ou reclamam que você está sendo muito rigoroso em geral.

## Quem está certo? {#quem-esta-certo}

Quando um desenvolvedor discordar de sua sugestão, primeiro reserve um momento
para considerar se elas estão corretas. Muitas vezes, eles estão mais próximos
do código do que você e, portanto, podem realmente ter uma melhor visão sobre
certos aspectos. O argumento deles faz sentido? Faz sentido da perspectiva
de integridade do código? Nesse caso, informe-os de que estão certos e deixe
o problema cair.

No entanto, os desenvolvedores nem sempre estão certos. Nesse caso, o revisor
deve explicar melhor por que eles acreditam que sua sugestão está correta. Uma
boa explicação demonstra um entendimento da resposta do desenvolvedor e
informações adicionais sobre o motivo pelo qual a alteração está sendo solicitada.

Em particular, quando o revisor acredita que sua sugestão melhorará a integridade
do código, deve continuar advogando pela mudança, se acreditar que a melhoria na
qualidade do código resultante justifica o trabalho adicional solicitado.
**A melhoria da integridade do código tende a acontecer em pequenas etapas.**

Às vezes, é preciso algumas rodadas para explicar uma sugestão antes que ela
realmente apareça. Apenas certifique-se de sempre ser
[educado](comments.md#cortesia) e deixe o desenvolvedor saber que você *ouve* o
que eles estão dizendo, você simplesmente não *concorda*.

## Desenvolvedor Perturbado {#desenvolvedor-perturbado}

Os revisores às vezes acreditam que o desenvolvedor ficará chateado se insistir
em uma melhoria. Às vezes, os desenvolvedores ficam chateados, mas geralmente é
breve e eles ficam muito agradecidos depois que você os ajudou a melhorar a
qualidade de seu código. Geralmente, se você é [educado](comments.md#cortesia)
em seus comentários, os desenvolvedores não ficam nem um pouco chateados e a
preocupação está apenas na mente do revisor. Os transtornos geralmente são mais
sobre [a maneira como os comentários são escritos](comments.md#cortesia) do que
sobre a insistência do revisor na qualidade do código.

## Limpando Mais Tarde {#tarde}

Uma fonte comum de resposta é que os desenvolvedores (compreensivelmente) querem
fazer as coisas. Eles não querem passar por outra rodada de revisão apenas para
obter esta CL. Portanto, eles dizem que limparão algo em um CL posterior e,
portanto, você deve aprovar *esta* CL agora. Alguns desenvolvedores são muito bons
nisso e escreverão imediatamente um CL de acompanhamento que corrige o problema. No
entanto, a experiência mostra que, quanto mais tempo passa depois que um
desenvolvedor escreve a CL original, menos provável é que essa limpeza ocorra. De
fato, geralmente, a menos que o desenvolvedor faça a limpeza *imediatamente*
após a CL atual, isso nunca acontece. Isso não ocorre porque os desenvolvedores são
irresponsáveis, mas porque eles têm muito trabalho a fazer e a limpeza é perdida ou
esquecida na pressão de outros trabalhos. Portanto, geralmente é melhor insistir que
o desenvolvedor limpe sua CL *agora*, antes que o código esteja na base de código e
"pronto". Deixar as pessoas "limparem as coisas mais tarde" é uma maneira comum de
degenerar as bases de código.

Se uma CL introduzir novas complexidades, ele deverá ser limpo antes do envio, a
menos que seja uma [emergência](../emergencies.md). Se o CL expuser problemas ao
redor e eles não puderem ser solucionados no momento, o desenvolvedor deve registrar
um bug para a limpeza e atribuí-lo a si mesmo para que não se perca. Opcionalmente,
eles também podem escrever um comentário TODO no código que referencia o bug arquivado.

## Reclamações Gerais Sobre Rigidez {#rigor}

Se você já teve revisões de código bastante fracas e passou a ter revisões
rigorosas, alguns desenvolvedores reclamam muito alto. Melhorar a [velocidade](speed.md)
das suas revisões de código geralmente faz com que essas reclamações desapareçam.

Às vezes, essas reclamações podem levar meses para desaparecer, mas, eventualmente,
os desenvolvedores tendem a ver o valor de revisões rigorosas de código, à medida que
veem o grande código que ajudam a gerar. Às vezes, os manifestantes mais barulhentos
até se tornam seus defensores mais fortes quando algo acontece que os faz realmente
ver o valor que você está agregando por ser rigoroso.

## Resolvendo Conflitos {#conflitos}

Se você está seguindo todas as opções acima, mas ainda encontra um conflito entre
você e um desenvolvedor que não pode ser resolvida, consulte
[O Padrão para Revisão de Código](standard.md) para obter diretrizes e princípios
que podem ajudar a resolver o conflito.
