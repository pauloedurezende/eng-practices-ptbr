# O que procurar em uma revisão de código



Nota: Sempre leve em consideração
[O Padrão para Revisão de Código](standard.md) ao considerar cada um desses pontos.

## Design

A coisa mais importante a ser abordada em uma revisão é o design geral da CL.
As interações de várias partes do código na CL fazem sentido? Essa alteração
pertence à sua base de código ou a uma biblioteca? Ele se integra bem ao resto do
seu sistema? Agora é um bom momento para adicionar essa funcionalidade?

## Funcionalidade

Esta CL faz o que o desenvolvedor pretendia? O que o desenvolvedor pretendeu ser
bom para os usuários desse código? Os "usuários" geralmente são usuários finais
(quando afetados pela mudança) e desenvolvedores (que terão que "usar" esse código
no futuro).

Principalmente, esperamos que os desenvolvedores testem CLs suficientemente bem
para que funcionem corretamente no momento em que chegam à revisão do código. No
entanto, como revisor, você ainda deve estar pensando em casos extremos, procurando
problemas de simultaneidade, tentando pensar como um usuário e certificando-se
de que não haja erros que você vê apenas lendo o código.

Você *pode* validar a CL se desejar - o momento em que é mais importante para um
revisor verificar o comportamento de uma CL é quando ele tem um impacto voltado para
o usuário, como uma **alteração na interface do usuário**. É difícil entender
como algumas mudanças afetarão um usuário quando você estiver lendo o código. Para
mudanças como essa, você pode solicitar ao desenvolvedor uma demonstração da
funcionalidade, se for muito inconveniente corrigir a CL e tentar você mesmo.

Outro momento em que é particularmente importante pensar na funcionalidade durante
uma revisão de código é se há algum tipo de **programação paralela** em andamento
na CL que teoricamente poderia causar conflitos ou condições de corrida. Esses tipos
de problemas são muito difíceis de detectar, basta executar o código e geralmente
precisam de alguém (tanto o desenvolvedor quanto o revisor) para pensar neles com
cuidado para garantir que os problemas não estejam sendo introduzidos. (Observe que
esse também é um bom motivo para não usar modelos de simultaneidade onde são
possíveis condições de corrida ou impasses - pode ser muito complexo fazer revisões
de código ou entender o código.)

## Complexidade

A CL é mais complexa do que deveria? Verifique isso em todos os níveis da CL - as
linhas individuais são muito complexas? As funções são muito complexas? As classes
são muito complexas? "Muito complexo" geralmente significa **"não pode ser entendido
rapidamente pelos leitores de código."** Também pode significar **"os desenvolvedores
provavelmente introduzirão bugs quando tentarem chamar ou modificar esse código."**

Um tipo específico de complexidade é o excesso de engenharia, no qual os
desenvolvedores tornaram o código mais genérico do que o necessário, ou adicionaram
funcionalidades que atualmente não são necessárias pelo sistema. Os revisores devem
estar especialmente vigilantes com o excesso de engenharia. Incentive os desenvolvedores
a resolver o problema que eles sabem que precisa ser resolvido *agora*, e não o problema
que o desenvolvedor especula *pode* precisar ser resolvido no futuro. O problema futuro
deve ser resolvido assim que chegar e você poderá ver sua forma e requisitos reais no
universo físico.

## Testes

Peça por testes de unitários, integração ou end-to-end, conforme apropriado para
a mudança. Em geral, os testes devem ser adicionados na mesmo CL que o código de
produção, a menos que a CL esteja lidando com uma [emergência](../emergencies.md)

Verifique se os testes no CL são corretos, sensíveis e úteis. Os testes não se
testam e raramente escrevemos testes para nossos testes - um ser humano deve
garantir que os testes sejam válidos.

Os testes realmente falharão quando o código for quebrado? Se o código mudar
abaixo deles, eles começarão a produzir falsos positivos? Cada teste faz
afirmações simples e úteis? Os testes são separados adequadamente entre
diferentes métodos de teste?

Lembre-se de que testes também são códigos que precisam ser mantidos. Não
aceite a complexidade nos testes apenas porque eles não fazem parte do
binário principal.

## Nomeação

O desenvolvedor escolheu bons nomes para tudo? Um bom nome é longo o suficiente
para comunicar completamente o que o item é ou faz, sem ser tão longo que se torne
difícil de ler.

## Comentários

O desenvolvedor escreveu comentários claros em inglês de forma compreensível?
Todos os comentários são realmente necessários? Geralmente, os comentários são
úteis quando eles **explicam o porquê** de algum código existir e não devem
explicar *o que* algum código está fazendo. Se o código não for suficientemente
claro para se explicar, o código deverá ser simplificado. Existem algumas
exceções (expressões regulares e algoritmos complexos geralmente se beneficiam
muito de comentários que explicam o que estão fazendo, por exemplo), mas a maioria
dos comentários é para informações que o próprio código não pode conter, como o
raciocínio por trás de uma decisão.

Também pode ser útil examinar os comentários que existiam antes desta CL. Talvez
haja um TODO que possa ser removido agora, um comentário desaconselhando essa
alteração, etc.

Observe que os comentários são diferentes da *documentação* de classes, módulos
ou funções, que devem expressar o objetivo de um pedaço de código, como ele
deve ser usado e como se comporta quando usado.

## Estilo

Temos [guias de estilo](http://google.github.io/styleguide/) no Google para todas
as principais linguagens e até para a maioria das menores linguagens. Verifique se
a CL segue os guias de estilos apropriados.

Se você deseja melhorar algum ponto de estilo que não está no guia de estilo,
prefixe seu comentário com "Nit:" para informar ao desenvolvedor que é um detalhe
que você acha que melhoraria o código, mas não é obrigatório. Não impeça o envio de
CLs com base apenas nas preferências de estilo pessoal.

O autor da CL não deve incluir grandes alterações de estilo combinadas com outras
alterações. Torna difícil ver o que está sendo alterado no CL, torna as fusões e
reversões mais complexas e causa outros problemas. Por exemplo, se o autor quiser
reformatar o arquivo inteiro, peça que ele envie apenas a reformatação como uma CL e,
em seguida, envie outra CL com suas alterações funcionais depois disso.

## Documentação

Se uma CL alterar como os usuários criam, testam, interagem ou liberam código,
verifique se também necessita atualizar a documentação associada, incluindo READMEs,
páginas g3doc e quaisquer documentos de referência gerados. Se a CL excluir ou
descontinuar o código, considere se a documentação também deve ser excluída. Se a
documentação estiver faltando, solicite-a.

## Cada Linha {#cada-linha}

Observe *toda* linha de código que você foi designado para revisar. Algumas vezes,
como arquivos de dados, código gerado ou grandes estruturas de dados, você pode
verificar algumas vezes, mas não verifica uma classe, função ou bloco de código
escrito por humanos e assume que o conteúdo está correto. Obviamente, algum código
merece uma análise mais cuidadoso do que outro código&mdash;é uma decisão que você deve
fazer&mdash;mas você deve pelo menos ter certeza de que *entende* o que todo o código
está fazendo.

Se for muito difícil para você ler o código e isso estiver atrasando a revisão,
informe o desenvolvedor e espere que ele esclareça antes de tentar revisá-lo. No
Google, contratamos ótimos engenheiros de software e você é um deles. Se você não
consegue entender o código, é muito provável que outros desenvolvedores também não.
Então, você também está ajudando futuros desenvolvedores a entender esse código,
quando solicita que o esclareça.

Se você entende o código, mas não se sente qualificado para fazer parte da revisão,
verifique se há um revisor na CL qualificado, principalmente para problemas complexos,
como segurança, concorrência, acessibilidade, internacionalização etc.

## Contexto

Muitas vezes, é útil olhar para a CL em um contexto amplo. Geralmente, a ferramenta
de revisão de código mostra apenas algumas linhas de código nas partes que estão sendo
alteradas. Às vezes, é necessário examinar o arquivo inteiro para garantir que a
alteração realmente faça sentido. Por exemplo, você pode ver apenas quatro novas linhas
sendo adicionadas, mas quando você olha para o arquivo inteiro, essas quatro linhas estão
em um método de 50 linhas que agora realmente precisa ser dividido em métodos menores.

Também é útil pensar na CL no contexto do sistema como um todo. Esse CL está melhorando
a integridade do código do sistema ou está tornando o sistema inteiro mais complexo, menos
testado etc.? **Não aceite CLs que degradam a integridade do código do sistema.** A maioria
dos sistemas se torna complexa por meio de muitas pequenas alterações, portanto é importante
evitar até pequenas complexidades em novas alterações.

## Boas Coisas {#boas-coisas}

Se você encontrar algo legal na CL, informe ao desenvolvedor, especialmente quando eles
abordaram um de seus comentários de uma maneira excelente. As revisões de código geralmente
se concentram nos erros, mas também devem oferecer incentivo e apreço pelas boas práticas.
Às vezes, é ainda mais valioso, em termos de orientação, contar a um desenvolvedor o que eles
fizeram certo do que dizer o que fizeram de errado.

## Sumário

Ao fazer uma revisão de código, verifique se:

-   O código está bem desenhado.
-   A funcionalidade é boa para os usuários do código.
-   Quaisquer alterações na interface do usuário são sensatas e com boa aparência.
-   Qualquer programação paralela é feita com segurança.
-   O código não é mais complexo do que precisa ser.
-   O desenvolvedor não está implementando coisas que eles *precisam* no futuro, mas
    não sei o que eles precisam agora.
-   O código possui testes de unidade apropriados.
-   Os testes são bem projetados.
-   O desenvolvedor usou nomes claros para tudo.
-   Os comentários são claros e úteis, e explicam principalmente *por que* em vez de *o que*.
-   O código está devidamente documentado (geralmente no g3doc).
-   O código está em conformidade com nossos guias de estilo.

Make sure to review **every line** of code you've been asked to review, look at
the **context**, make sure you're **improving code health**, and compliment
developers on **good things** that they do.

Leia **todas as linhas** de código que você foi solicitado a revisar, verifique o **contexto**,
verifique se está **melhorando a integridade do código** e elogie os desenvolvedores por
**coisas boas** que eles fazem.

Próximo: [Navegando em uma CL na Revisão](navigate.md)
