# Velocidade de um Revisões de Código



## Por Que as Revisões de Código Devem Ser Rápidas? {#por-que}

**No Google, otimizamos a velocidade com que uma equipe de desenvolvedores pode
produzir um produto juntos**, em vez de otimizar a velocidade com que um desenvolvedor
individual pode escrever código. A velocidade do desenvolvimento individual é
importante, apenas não é tão importante _quanto_ a velocidade de toda a equipe.

Quando as revisões de código são lentas, várias coisas acontecem:

*   **A velocidade da equipe como um todo diminui.** Sim, o indivíduo, que não
    responde rapidamente à revisão, realiza outro trabalho. No entanto, novos
    recursos e correções de erros para o restante da equipe são adiados por dias,
    semanas ou meses, pois cada CL aguarda a revisão e uma nova revisão.
*   **Os desenvolvedores começam a protestar contra o processo de revisão de código.**
    Se um revisor responder apenas a cada poucos dias, mas solicitar alterações
    importantes no CL a cada vez, isso poderá ser frustrante e difícil para os
    desenvolvedores. Muitas vezes, isso é expressado como reclamações sobre o quão
    "rigoroso" o revisor está sendo. Se o revisor solicitar as mesmas alterações
    substanciais (alterações que realmente melhoram a integridade do código),
    mas responder rapidamente, sempre que o desenvolvedor fizer uma atualização,
    as reclamações tendem a desaparecer. **A maioria das reclamações sobre o processo
    de revisão de código é realmente resolvida, tornando o processo mais rápido.**
*   **A integridade do código pode ser afetada.** Quando as revisões são lentas, há
    uma pressão crescente para permitir que os desenvolvedores enviem CLs que não são
    tão boas quanto poderiam ser. Revisões lentas também desencorajam a limpeza de
    códigos, refatorações e melhorias adicionais nas CLs existentes.

## O Quão Rápido Uma Revisão de Código Deveria Ser {#rapido}

Se você não está no meio de uma tarefa focada, **deve fazer uma revisão de código
logo após a entrada.**

**Um dia útil é o tempo máximo que leva para responder** a uma solicitação de
revisão de código (ou seja, a primeira coisa na manhã seguinte).

Seguir essas diretrizes significa que uma CL típica deve receber várias rodadas
de revisão (se necessário) em um único dia.

## Velocidade vs. Interrupção {#interrupcao}

Há um momento em que a consideração da velocidade pessoal supera a velocidade da
equipe. **Se você estiver no meio de uma tarefa focada, como escrever código, não
se interrompa para fazer uma revisão de código.** Pesquisas mostraram que pode
demorar muito tempo para que um desenvolvedor volte a um fluxo normal de
desenvolvimento após ser interrompido. Portanto, interromper-se durante a codificação
é realmente _mais_ caro para a equipe do que fazer outro desenvolvedor esperar um pouco
por uma revisão de código.

Em vez disso, aguarde um ponto de interrupção no seu trabalho antes de responder
a uma solicitação de revisão. Pode ser quando sua tarefa de codificação atual for
concluída, após o almoço, voltando de uma reunião, voltando da micro-cozinha etc.

## Respostas Rápida {#respostas}

Quando falamos sobre a velocidade das revisões de código, é o tempo de resposta
com que estamos preocupados, ao contrário de quanto tempo leva uma CL para passar
por toda a revisão e ser submetida. Todo o processo também deve ser rápido,
idealmente, mas **é ainda mais importante que as _respostas individuais_ venham
rapidamente do que é que todo o processo ocorra rapidamente.**

Mesmo que às vezes demore muito tempo para passar por todo o processo de revisão,
ter respostas rápidas do revisor ao longo do _processo_ facilita significativamente
a frustração que os desenvolvedores podem sentir com as revisões de código "lentas".

Se você estiver ocupado demais para fazer uma revisão completa de um CL quando ela entrar,
ainda poderá enviar uma resposta rápida que informe ao desenvolvedor quando você chegará a
ele, sugerir outros revisores que possam responder mais rapidamente ou [fornecer alguns
comentários gerais amplos](navigate.md). (Nota: nada disso significa que você deve
interromper a codificação mesmo para enviar uma resposta como esta&mdash;envie a
resposta em um ponto de interrupção razoável em seu trabalho.)

**É importante que os revisores gastem tempo suficiente em uma revisão para garantir
que "LGTM" significa "este código [atende aos nossos padrões](standard.md)".**
Entretanto, as respostas individuais ainda devem, idealmente, ser rápidas.

## Comentários com Fuso Horário {#fh}

Ao lidar com diferenças de fuso horário, tente retornar ao autor quando ele ainda
estiver no escritório. Se eles já foram para casa, tente garantir que sua revisão
seja feita antes que eles voltem ao escritório no dia seguinte.

## LGTM Com Comentários {#lgtm-com-comentarios}

Para acelerar as revisões de código, há certas situações nas quais um revisor
deve conceder o LGTM/aprovação, mesmo deixando comentários não resolvidos no CL.
Isso é feito quando:

*   O revisor está confiante de que o desenvolvedor abordará adequadamente
    todos os comentários restantes do revisor.
*   As alterações restantes são pequenas e não _precisam_ ser feitas pelo
    desenvolvedor.

O revisor deve especificar quais dessas opções eles pretendem, se não estiver
claro.

O LGTM com comentários vale especialmente a pena ser considerado quando o
desenvolvedor e o revisor estão em fusos horários diferentes; caso contrário,
o desenvolvedor estaria esperando o dia inteiro apenas para obter uma aprovação.

## Grandes CLs {#grande}

Se alguém enviar a você uma revisão de código tão grande que você não tiver certeza
de quando poderá ter tempo para analisá-la, sua resposta típica será pedir ao
desenvolvedor que [divida a CL em várias CLs menores](../developer/small-cls.md)
que integram um ao outro, em vez de uma CL enorme que precisa ser revisado de uma
só vez. Isso geralmente é possível e muito útil para os revisores, mesmo que exija
trabalho adicional do desenvolvedor.

Se uma CL *não puder* ser dividida em CLs menores e você não tiver tempo para
revisar a coisa toda rapidamente, pelo menos escreva alguns comentários sobre o
design geral da CL e envie-o de volta ao desenvolvedor para melhoria. Um de seus
objetivos como revisor deve ser sempre desbloquear o desenvolvedor ou permitir
que ele execute algum tipo de ação adicional rapidamente, sem sacrificar a
integridade do código.

## Melhorias na Revisão de Código ao Longo do Tempo {#tempo}

Se você seguir estas diretrizes e for rigoroso com suas revisões de código, deverá
descobrir que todo o processo de revisão de código tende a ir cada vez mais rápido
ao longo do tempo. Os desenvolvedores aprendem o que é necessário para um código
íntegro e enviam CLs excelentes desde o início, exigindo cada vez menos tempo de
revisão. Os revisores aprendem a responder rapidamente e a não adicionar latência
desnecessária ao processo de revisão.
Mas **não comprometa os [padrões de revisão de código](standard.md) ou a qualidade
para uma melhoria imaginada na velocidade**&mdash;isso não fará nada acontecer mais
rapidamente, a longo prazo.

## Emergências

Também existem emergências nas quais as CLs devem passar por _todo_ o processo de
revisão muito rapidamente e onde as diretrizes de qualidade seriam deixadas de lado.
No entanto, consulte [O Que é Uma Emergência?](../emergencies.md#what) para uma
descrição de quais situações realmente se qualificam como emergências e quais não.

Próximo: [Como Escrever Comentários de Revisão de Código](comments.md)
