# Solução de Canary Release no Azure Webapp

A Solução encontrada para efetuar a implantação do Canary Release dentro do Azure Webapp é bastante simples, parte da ideia de criar dentro da própria aplicação do Webapp um slot de "Stage" onde vai ser deployado a nova versão do sistema em questão.

Tanto o ambiente de Produção e o ambiente de Stage vão estar no ar enquanto o canary é realizado, o usuário que estiver fazendo essa implantação vai precisar ficar trocando o nível de tráfego que esses dois ambientes vão compartilhar. Ex: O ambiente de Produção com 90% de todo o tráfego de requesições enquanto o Stage com a nova versão do sistema está apenas com 10%.

Quando a implatação estiver finalizada e totalmente estável, a Pipeline vai pedir um aprove de algum gestor para que o ambiente de Stage e Produção sejam trocados e o Stage seja desligado para não gerar custos adicionais.

Primeiro passo é criar o ambiente de Stage dentro da aplicação.

![Desktop Screenshot 2019 06 07 - 16 31 55 17](https://user-images.githubusercontent.com/45598049/59128970-e044de00-8941-11e9-9ed7-b9ebc31f0d85.png)

Depois iremos criar a pipeline de release do CanaryRelease, o aprove de algum gestor depois da etapa de Stage é necessaria para a segurança das aplicações.

![Desktop Screenshot 2019 06 07 - 16 34 09 81](https://user-images.githubusercontent.com/45598049/59129073-2ac65a80-8942-11e9-8ef7-1b4f012f0987.png)

No Stage, iremos criar 2  etapas, primeiro iremos iniciar nosso ambiente de Stage.

![Desktop Screenshot 2019 06 07 - 16 37 44 46](https://user-images.githubusercontent.com/45598049/59129250-ac1ded00-8942-11e9-9426-3c928ce02dcc.png)

E em seguida, iremos deployar a nova versão do sistema nesse slot.

![Desktop Screenshot 2019 06 07 - 16 38 54 78](https://user-images.githubusercontent.com/45598049/59129330-eab3a780-8942-11e9-924b-f736e4e04c4c.png)

Com isso, já vamos ter uma versão funcional da nova versão do sistema no ar, agora só falta dividir o trafego entre as duas aplicações.

Basta ir em slots de implantação no aplicativo do Webapp em questão, e ir mudando o trafego manualmente das aplicações.

![Desktop Screenshot 2019 06 07 - 16 31 34 73](https://user-images.githubusercontent.com/45598049/59129476-5138c580-8943-11e9-8fcd-0983d880a8cc.png)

Se estiver tudo certo com o ambiente de Stage e com o aprove do Gestor, a pipeline vai dar continuidade e entrará na etapa de Produção.

Em Produção, iremos criar mais duas etapas, iniciando com o Swap do Stage para a Produção.

![Desktop Screenshot 2019 06 07 - 16 49 25 24](https://user-images.githubusercontent.com/45598049/59129905-6cf09b80-8944-11e9-8c7d-02666cee87a1.png)

Próxima etapa vai ser a de parar o ambiente de Stage para não gerar custos extras.

![Desktop Screenshot 2019 06 07 - 16 53 12 55](https://user-images.githubusercontent.com/45598049/59130097-e25c6c00-8944-11e9-8b21-f6d3695f6c90.png)

Com isso o CanaryRelease fica completo, a aplicação vai ser atualizada para a nova versão.
