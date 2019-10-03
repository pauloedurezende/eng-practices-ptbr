# Como lidar com os comentários dos revisores



Quando você envia uma CL para revisão, é provável que o revisor responda com
vários comentários na sua CL. Aqui estão algumas informações úteis sobre como
lidar com os comentários dos revisores.

## Não leve para o lado pessoal {#pessoal}

O objetivo da revisão é manter a qualidade da nossa base de código e dos nossos
produtos. Quando um revisor faz uma crítica ao seu código, pense nele como uma
tentativa de ajudá-lo, a base de código e o Google, e não como um ataque
pessoal a você ou a suas habilidades.

Às vezes, os revisores se sentem frustrados e expressam essa frustração em seus
comentários. Essa não é uma boa prática para revisores, mas como desenvolvedor,
você deve estar preparado para isso. Pergunte a si mesmo: "Qual é a coisa
construtiva que o revisor está tentando me comunicar?" e depois opere como se
fosse o que eles realmente disseram.

**Nunca responda com raiva aos comentários de revisão de código.** Essa é uma
violação grave da etiqueta profissional que permanecerá para sempre na
ferramenta de revisão de código. Se você estiver com muita raiva ou irritado
para responder gentilmente, afaste-se do computador por um tempo ou trabalhe em
outra coisa até sentir-se calmo o suficiente para responder educadamente.

Em geral, se um revisor não estiver fornecendo feedback de forma construtiva e
educada, explique isso pessoalmente. Se você não puder falar com eles
pessoalmente ou em uma vídeo chamada, envie um e-mail particular. Explique a
eles de uma maneira gentil o que você não gosta e o que gostaria que eles
fizessem de maneira diferente. Se eles também responderem de maneira não
construtiva a essa discussão particular, ou se não tiver o efeito pretendido,
encaminhe para o gerente, conforme apropriado.

## Corrigir o código {#codigo}

Se um revisor disser que não entende algo no seu código, sua primeira resposta
deve ser esclarecer o próprio código. Se o código não puder ser esclarecido,
adicione um comentário que explique por que o código está lá. Se um comentário
parecer inútil, somente então sua resposta deve ser uma explicação na ferramenta
de revisão de código.

Se um revisor não entendeu parte do seu código, provavelmente outros leitores do
código também não entenderão. Escrever uma resposta na ferramenta de revisão de
código não ajuda futuros leitores de código, mas esclarecer o seu código ou
adicionar comentários ao código os ajuda.

## Pense por você mesmo {#pense}

Escrever uma CL pode exigir muito trabalho. Muitas vezes, é realmente muito bom
finalmente enviar para revisão, sentir que está pronto e ter certeza de que
não é necessário mais trabalho. Portanto, quando um revisor retorna com
comentários sobre coisas que podem ser aprimoradas, é fácil pensar
reflexivamente que os comentários estão errados, o revisor está bloqueando você
desnecessariamente ou eles devem permitir que você envie a sua CL.
No entanto, **não importa o quão certo você esteja**, neste momento, reserve um
momento para voltar e considerar se o revisor está fornecendo feedback valioso
que ajudará a base de código e o Google. Sua primeira pergunta para si mesmo
deve sempre ser: "O revisor está correto?"

Se você não conseguir responder a essa pergunta, é provável que o revisor
precise esclarecer seus comentários.

Se você *o considerou* e ainda acha que está certo, sinta-se à vontade para
responder com uma explicação de por que seu método de fazer as coisas é melhor
para a base de código, os usuários e / ou o Google. Frequentemente, os revisores
estão realmente fornecendo *sugestões* e desejam que você pense por si mesmo sobre
o que é melhor. Você pode realmente saber algo sobre os usuários, base de código
ou CL que o revisor não conhece. Então, preencha-os; dê a eles mais contexto.
Geralmente, você pode chegar a um consenso entre você e o revisor com base em fatos
técnicos.

## Resolvendo Conflitos {#conflitos}

Seu primeiro passo na resolução de conflitos deve sempre ser tentar chegar a
um consenso com seu revisor. Se você não conseguir obter consenso, consulte
[Os Padrões da Revisão de Código](../reviewer/standard.md), que fornece os princípios
a serem seguidos em tal situação.
