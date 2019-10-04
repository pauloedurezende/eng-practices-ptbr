# Escrevendo boas descrições de CL



Uma descrição de CL é um registro público de **qual** mudança está sendo feita
e **por que** foi feita. Ele se tornará parte permanente do nosso histórico
de controle de versão e possivelmente será lido por centenas de pessoas, além
dos seus revisores, ao longo dos anos.

Os desenvolvedores futuros procurarão sua CL com base em sua descrição. Alguém
no futuro pode estar procurando sua alteração devido a uma fraca lembrança de
sua relevância, mas sem os detalhes úteis. Se todas as informações importantes
estiverem no código e não na descrição, será muito mais difícil localizar o CL.

## Primeira Linha {#primeira-linha}

*   Breve resumo do que está sendo feito.
*   Frase completa, escrita como se fosse uma ordem.
*   Seguida por uma linha vazia.

A **primeira linha** de uma descrição de CL deve ser um breve resumo relatando
*especificamente* sobre **o que** *está sendo feito pela CL*, seguido por uma
linha em branco. Isso é o que a maioria dos futuros pesquisadores de código
verá quando estiverem navegando no histórico de controle de versão de um trecho
de código. Portanto, essa primeira linha deve ser informativa o suficiente para
que eles não precisem ler sua CL ou sua descrição inteira apenas para obter uma
descrição geral do que a sua CL realmente *fez*.

Por tradição, a primeira linha de uma descrição de CL é uma sentença completa,
escrita como se fosse uma ordem (uma sentença imperativa). Por exemplo, diga
\"**Excluir** o RPC do FizzBuzz e **substitua** pelo novo sistema." em vez de
\"**Excluindo** o FizzBuzz RPC e **substituindo** pelo novo sistema." Você não
precisa escrever o restante da descrição como uma sentença imperativa.

## O Corpo é Informativo {#informativo}

O restante da descrição deve ser informativo. Pode incluir uma breve descrição
do problema que está sendo resolvido e por que essa é a melhor abordagem. Se
houver alguma falha na abordagem, eles devem ser mencionados. Se relevante,
inclua informações básicas, como números de erros, resultados de benchmark e
links para documentos de design.

Até CLs pequenas merecem um pouco de atenção aos detalhes. Coloque a CL no
contexto.

## Descrições Incorretas de CL {#ruim}

"Corrigir bug" é uma descrição inadequada de uma CL. Que bug? O que você fez para
consertar isso? Outras descrições igualmente ruins incluem:

-   "Corrigir build."
-   "Adicionar patch."
-   "Movendo código de A para B."
-   "Fase 1."
-   "Adicionar funções de ajuda."
-   "Mata URLs estranhas."

Algumas são descrições reais de CL. Seus autores podem acreditar que estão
fornecendo informações úteis, mas não estão servindo ao objetivo de uma descrição
de CL.

## Boas Descrições de CL {#bom}

Aqui estão alguns exemplos de boas descrições.

### Alteração de Funcionalidade

> rpc: remova o limite de tamanho no freelist de mensagens do servidor RPC.
>
> Servidores como o FizzBuzz têm mensagens muito grandes e se beneficiariam da
> reutilização.
> Aumente o freelist e adicione uma goroutine que libere as entradas freelist
> lentamente ao longo do tempo, para que os servidores inativos liberem todos as
> entradas.

As primeiras palavras descrevem o que o CL realmente faz. O restante da descrição
fala sobre o problema que está sendo resolvido, por que essa é uma boa solução e
um pouco mais de informações sobre a implementação específica.

### Refatoração

> Construa uma tarefa com um TimeKeeper para usar seus métodos TimeStr e Now.
>
> Adicione um método Now à tarefa, para que o método borglet() getter possa ser
> removido (o que foi usado apenas pelo OOMCandidate para chamar o método Now do
> borglet). Isso substitui o métodos no Borglet que delegam em um TimeKeeper.
>
> Permitir o fornecimento de tarefas Now é um passo em direção a eliminar a
> dependência do Borglet. Eventualmente, colaboradores que dependem de obter o
> Now da tarefa deve ser alterado para usar um TimeKeeper diretamente, mas essa
> foi uma preparação para refatoração em pequenos passos.
>
> Continuando o objetivo de longo prazo de refatorar a Hierarquia do Borglet.

A primeira linha descreve o que a CL faz e como isso é uma mudança do passado.
O restante da descrição fala sobre a implementação específica, o contexto da CL,
que a solução não é ideal e possível direção futura. Também explica *por que*
essa alteração está sendo feita.

### CL Pequena Que Precisa de Algum Contexto

> Crie uma regra de construção Python3 para status.py.
>
> Isso permite que os consumidores que já estão usando isso como no Python3
> dependam de um regra ao lado da regra de criação do status original, em vez de
> em algum lugar na sua própria árvore. Incentiva os novos consumidores a usar o
> Python3, se puderem, em vez de Python2 e simplificar alguns arquivos de
> compilação automatizados usando ferramentas de refatoração sendo trabalhadas
> atualmente.

A primeira frase descreve o que realmente está sendo feito. O restante da
descrição explica *por que* a alteração está sendo feita e dá ao revisor muito
contexto.

## Revise a Descrição Antes de Enviar a CL

As CLs podem sofrer alterações significativas durante a revisão. Pode valer
a pena revisar uma descrição de CL antes de enviá-la, para garantir que a
descrição ainda reflita o que a CL faz.

Próximo: [Pequenas CLs](small-cls.md)
