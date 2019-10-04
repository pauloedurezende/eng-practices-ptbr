# Pequenas CLs



## Por Que Escrever Pequenas CLs? {#porque}

Pequena, simples é a CL:

-   **Revisado mais rapidamente.** É mais fácil para um revisor encontrar cinco
    minutos várias vezes para revisar CLs pequenas do que reservar um bloco de
    30 minutos para revisar uma CL grande.
-   **Revisado mais detalhadamente.** Com grandes alterações, revisores e autores
    tendem a ficar frustrados com grandes volumes de comentários detalhados
    mudando de um lado para outro - às vezes até o ponto em que pontos
    importantes são perdidos ou descartados.
-   **Menor probabilidade de apresentar bugs.** Como você está fazendo menos
    alterações, é mais fácil para você e seu revisor pensarem efetivamente sobre
    o impacto da CL e ver se um bug foi introduzido.
-   **Menos trabalho desperdiçado se eles forem rejeitados.** Se você escrever uma
    CL enorme e, em seguida, seu revisor disser que a direção geral está errada,
    você desperdiçou muito trabalho.
-   **Mais fácil de mesclar.** Trabalhar em uma CL grande leva muito tempo,
    portanto você terá muitos conflitos ao mesclar e terá que mesclar com
    frequência.
-   **Mais fácil de ser bem projetar.** É muito mais fácil aperfeiçoar o design
    e codificar a integridade de uma pequena alteração do que refinar todos os
    detalhes de uma alteração.
-   **Menos bloqueio nas revisões.** O envio de partes independentes da sua
    alteração geral permite que você continue a codificar enquanto aguarda sua
    CL atual na revisão.
-   **Mais simples de reverter.** É provável que uma CL grande toque em arquivos
    atualizados entre o envio inicial da CL e uma CL de reversão, complicando a
    reversão (as CLs intermediárias provavelmente precisarão ser revertidos também).

Observe que os **revisores têm o poder de rejeitar sua alteração imediatamente
pelo simples fato de ser muito grande.** Geralmente eles agradecem sua contribuição,
mas solicitam que você faça de alguma forma uma série de alterações menores. Pode
ser muito trabalhoso dividir uma alteração depois que você já tiver escrito ou
exigir muito tempo para discutir por que o revisor deve aceitar sua grande alteração.
É mais fácil escrever CLs pequenas em primeiro lugar.

## O que é pequeno? {#o-que-e-pequeno}

Em geral, o tamanho certo para um CL é **uma alteração independente**. Isso
significa que:

-   O CL faz uma alteração mínima que aborda **apenas uma coisa**. Geralmente,
    isso é apenas uma parte de um recurso, e não um recurso inteiro de uma só vez.
    Em geral, é melhor errar ao escrever CLs bem pequenas vs. CLs bem
    grandes. Trabalhe com seu revisor para descobrir qual é um tamanho aceitável.
-   Tudo o que o revisor precisa entender sobre a CL (exceto desenvolvimento
    futuro) está na CL, na descrição da CL, na base de código existente ou em um
    CL que eles já revisaram.
-   O sistema continuará funcionando bem para seus usuários e desenvolvedores após
    a check-in da sua CL.
-   A CL não é tão pequena a ponto de que suas implicações sejam difíceis de
    entender. Se você adicionar uma nova API, inclua um uso da API no mesmo CL
    para que os revisores possam entender melhor como a API será usada. Isso
    também impede o check-in de APIs não utilizadas.

Não há regras rígidas e rápidas sobre o seria "grande demais". 100 linhas
geralmente é um tamanho razoável para uma CL e 1000 linhas geralmente são bem
grandes, mas depende do julgamento do revisor. O número de arquivos pelos quais
uma alteração está espalhada também afeta seu "tamanho". Uma alteração de 200
linhas em um arquivo pode ser boa, mas espalhada por 50 arquivos, geralmente
seria bem grande.

Lembre-se de que, embora você tenha se envolvido intimamente com seu código desde
o momento em que começou a escrevê-lo, o revisor geralmente não tem contexto. O
que parece uma CL de tamanho aceitável para você pode ser esmagador para o seu
revisor. Em caso de dúvida, escreva CLs menores do que você pensa que precisa. Os
revisores raramente se queixam de obter CLs pequenas.

## Quando CLs Grandes São Aceitáveis? {#aceitavel}

Existem algumas situações em que grandes mudanças não são tão ruins:

-   Geralmente, você pode contar com a exclusão de um arquivo inteiro como sendo
    apenas uma linha de alteração, pois não leva muito tempo para seu revisor
    revisa-lo.
-   Às vezes, uma CL grande é gerado por uma ferramenta de refatoração automática
    em que você confia completamente, e o trabalho do revisor é apenas verificar
    a integridade e dizer que ele realmente deseja a mudança. Esses CLs podem ser
    maiores, embora algumas das ressalvas acima (como mesclagem e teste) ainda se
    apliquem.

### Dividindo por Arquivos {#dividindo-arquivos}

Outra maneira de dividir uma CL é por agrupamentos de arquivos que exigirão
revisores diferentes, mas que são mudanças independentes.

Por exemplo: você envia uma CL para modificações em um buffer de protocolo e
outra CL para alterações no código que usa esse proto. Você deve enviar a CL do proto
antes da CL de modificações, mas ambos podem ser revisados simultaneamente. Se você
fizer isso, convém informar os dois conjuntos de revisores sobre a outra CL que
você escreveu, para que eles tenham contexto para suas alterações.

Outro exemplo: você envia uma CL para uma alteração no código e outro para a
configuração ou experiência que usa esse código; também é mais fácil reverter,
se necessário, pois os arquivos de configuração/experimento às vezes são enviados
para produção mais rapidamente do que as alterações de código.

## Refatorações Separadas {#refatoracao}

Geralmente, é melhor fazer refatorações em uma CL separada de alterações de recursos
ou correções de erros. Por exemplo, mover e renomear uma classe deve estar em um CL
diferente da correção de um bug referente a esta classe. É muito mais fácil para os
revisores entenderem as alterações introduzidas por cada CL quando estão separadas.

Pequenas limpezas, como a fixação de um nome de variável local, podem ser incluídas
dentro de uma alteração de recurso ou uma CL de correção de bug. Depende do julgamento
dos desenvolvedores e revisores decidir quando uma refatoração é tão grande que
dificultará a revisão se incluída na CL atual.

## Mantenha o Código de Teste Relacionado na Mesma CL {#codigo-de-testes}

Evite dividir o código de teste em uma CL separada. Os testes que validam suas
modificações de código devem ser inseridos na mesma CL, mesmo se aumentar a contagem
de linhas de código.

No entanto, modificações de teste <i>independentes</i> podem entrar primeiro em CLs
separadas, semelhante às diretrizes de refatoração. Isso inclui:

*   validando código pré-existente enviado com novos testes.
*   refatorar o código de teste (por exemplo, introduzir funções auxiliares).
*   introdução de um código de estrutura de teste maior (por exemplo, um teste de
    integração).

## Não Quebre a Compilação {#quebrar}

Se você tiver várias CLs que dependem uma da outra, precisará encontrar uma maneira
de garantir que todo o sistema continue funcionando após o envio de cada CL. Caso
contrário, você poderá interromper a compilação de todos os seus colegas desenvolvedores
por alguns minutos entre os envios de CL (ou ainda mais, se algo der errado
inesperadamente com os envios posteriores de CL).

## Não Pode Ser Mais Pequeno o Suficiente {#nao-pode}

Às vezes, você encontrará situações em que sua CL *precisa* ser grande. Isso
raramente é verdade. Os autores que praticam a escrita de CLs pequenos quase
sempre conseguem encontrar uma maneira de decompor a funcionalidade em uma
série de pequenas alterações.

Antes de escrever uma CL grande, considere precedê-lo com uma CL somente para
refatoração onde poderia preparar o caminho para uma implementação mais limpa.
Converse com seus colegas de equipe e veja se alguém pensa em como implementar
a funcionalidade em pequenas CLs.

Se todas essas opções falharem (o que deve ser extremamente raro), obtenha o
consentimento dos revisores com antecedência para revisar uma CL grande, para que
sejam avisados sobre o que está por vir. Nessa situação, espere passar pelo
processo de revisão por um longo tempo, fique atento a não introduzir bugs e seja
mais diligente em escrever testes.

Próximo: [Como Lidar Com Comentários de Revisores](handling-comments.md)
