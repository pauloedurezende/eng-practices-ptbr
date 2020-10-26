# Como escrever comentários de revisão de código


## Sumário

-   Seja gentil.
-   Explique seu raciocínio.
-   Equilibre dando orientações explícitas, apenas apontando problemas e
    deixando o desenvolvedor decidir.
-   Incentive os desenvolvedores a simplificar o código ou adicionar
    comentários ao invés de apenas explicar a complexidade para você.

## Cortesia

Em geral, é importante ser cortês e respeitoso, além de ser muito claro e útil
para o desenvolvedor cujo código você está revisando. Uma maneira de fazer isso é
ter certeza de que você está sempre fazendo comentários sobre o *código* e nunca
fazendo comentários sobre o *desenvolvedor*. Você nem sempre precisa seguir essa
prática, mas definitivamente deve usá-la ao dizer algo que poderia ser perturbador
ou controverso. Por exemplo:

Ruim: "Por que **você** usou as threads aqui quando obviamente não há benefícios
a serem obtidos com a simultaneidade?"

Bom: "O modelo de simultaneidade aqui está adicionando complexidade ao sistema
sem nenhum benefício real de desempenho que eu possa ver. Como não há benefício
de desempenho, é melhor que esse código seja de uma única thread em vez de usar
várias threads."

## Explique o Por Que {#porque}

Uma coisa que você notará sobre o exemplo "bom" acima é que ele ajuda o
desenvolvedor a entender *por que* você está fazendo seu comentário. Você nem
sempre precisa incluir essas informações nos comentários da revisão, mas às vezes
é apropriado dar um pouco mais de explicação sobre sua intenção, a melhor prática
que você está seguindo ou como sua sugestão melhora a integridade do código.

## Dê Orientação {#orientacao}

**Em geral, é responsabilidade do desenvolvedor corrigir uma CL, não o revisor.**
Você não é obrigado a criar um projeto detalhado de uma solução ou escrever um
código para o desenvolvedor.

Isso não significa que o revisor deva ser inútil. Em geral, você deve encontrar
um equilíbrio adequado entre apontar problemas e fornecer orientação direta.
Apontar problemas e deixar que o desenvolvedor tome uma decisão geralmente ajuda
o desenvolvedor a aprender e facilita a revisão de código. Também pode resultar
em uma solução melhor, porque o desenvolvedor está mais próximo do código do que
o revisor.

No entanto, às vezes instruções diretas, sugestões ou mesmo códigos são mais úteis.
O principal objetivo da revisão de código é de obter a melhor CL possível. Um objetivo
secundário é melhorar as habilidades dos desenvolvedores, para que exijam cada vez
menos revisões ao longo do tempo.

## Aceitando Explicações {#explicacoes}

Se você pedir a um desenvolvedor que explique um pedaço de código que você não
entende, isso geralmente deve resultar em **reescrever o código mais claramente**.
Ocasionalmente, adicionar um comentário no código também é uma resposta apropriada,
desde que não esteja apenas explicando código excessivamente complexo.

**As explicações escritas apenas na ferramenta de revisão de código não são úteis
para futuros leitores de código.** Elas são aceitáveis apenas em algumas
circunstâncias, como quando você está revendo uma área com a qual não está muito
familiarizado e o desenvolvedor explica algo normal em que os leitores do código
já sabiam.

Próximo: [Manipulando Pushback em Revisões de Código](pushback.md)
