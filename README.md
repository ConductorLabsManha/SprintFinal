CI-CD de uma aplicações .NET no Azure WebApp utilizando o Azure DevOps

Requisitos:
- Assinatura paga do Portal Azure.
- Acesso ao Azure DevOps.
- Projeto funcional no Github.

# Iniciando no Azure DevOps

Esse tutorial inicial é bastante simples e fácil de ser realizado, nele vamos deixar o seu projeto pronto para iniciar o CI-CD.

Primeiramente, faça o login e acesse a página inicial do  [Azure Devops](https://dev.azure.com).

Crie o seu projeto, e voilá, já temos o primeiro projeto dentro do Devops.

O próximo passo é passar o seu projeto para dentro do Repos do Azure DevOps, clique em Repos e siga os passos que a ferramente disponiza.

![Desktop Screenshot 2019 06 07 - 14 56 18 45](https://user-images.githubusercontent.com/45598049/59124359-ce5d3e00-8935-11e9-9ee8-dc0fcfc642b5.png)
de 
Com o seu projeto dentro do Repos, vamos para a parte legal da ferramenta. vá para o menu de Pipelines e selecione a opção de Build.

Sim, isso mesmo o que você está imaginando, já vamos começar a fazer a pipeline de Build do seu projeto, e você vai ver como simples é criar sua pipe.

Crie uma nova Pipeline, e selecione a última opção de criar usando o editor clássico sem YAML. Você pode fazer de várias maneiras sua pipeline, escolha a que mais se encaixa com o que você está precisando ou siga o tutorial utilizando o método que adotamos.

![Desktop Screenshot 2019 06 07 - 15 12 56 86](https://user-images.githubusercontent.com/45598049/59124780-f4371280-8936-11e9-81a4-a91c756ca0cb.png)

Selecione Azure Repos Git como fonte, escolha também o projeto e o repositório que iremos utilizar.

A próxima etapa será a de escolher um Template que vai ser adotado na esteira da Pipeline, o Azure DevOps vai criar uma Pipeline quase completa para a linguagem que você selecionar, com poucas configurações tudo vai estar pronto para ser utilizado. O projeto que fizemos upload no repos é .NET, então selecione a opção que vai se encaixar com o seu projeto.

![Desktop Screenshot 2019 06 07 - 15 18 23 81](https://user-images.githubusercontent.com/45598049/59125091-bb4b6d80-8937-11e9-8c7b-3808514bb4d7.png)


