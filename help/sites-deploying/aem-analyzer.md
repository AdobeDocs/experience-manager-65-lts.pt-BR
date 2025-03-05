---
title: Avaliação da complexidade da atualização com o AEM Analyzer
description: Saiba como usar o AEM Analyzer para avaliar a complexidade da atualização.
topic-tags: upgrading
content-type: reference
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 2645745a83477509bac81cb5e122eabc44db3961
workflow-type: tm+mt
source-wordcount: '2068'
ht-degree: 15%

---


# Avaliação da complexidade da atualização com o AEM Analyzer {#assessing-the-upgrade-complexity-with-the-aem-analyzer}

## Visão geral {#overview}

O Analisador LTS do AEM 6.5 fornece uma avaliação de sua implementação atual do AEM, indicando as áreas que precisam ser atualizadas para fornecer uma experiência de atualização contínua para o 6.5 LTS.

A ferramenta gera um relatório que identifica áreas de refatoração potencial.

## Relatório do analisador AEM 6.5 LTS {#aem-65lts-analyzer-report}

O Relatório do analisador AEM 6.5 LTS é usado para obter um alto nível de compreensão da disponibilidade geral de atualização. O relatório consiste em conclusões em categorias de problemas que devem ser abordados para garantir uma atualização bem-sucedida para o AEM 6.5 LTS.

O relatório Analisador LTS do AEM 6.5 inclui as seguintes categorias:

* Funcionalidade do aplicativo que deve ser refatorado
* Itens do repositório que devem ser movidos para um local com suporte
* Problemas de configuração
* Recursos do AEM 6.5 que foram removidos pela nova funcionalidade ou que atualmente não são compatíveis com o AEM 6.5 LTS
* Remover uso da API Java e Guava

Informações adicionais sobre as categorias e possíveis implicações e soluções associadas a essas categorias são fornecidas por meio de links do Relatório do analisador LTS do AEM 6.5.

## Disponibilidade {#analyzer-availability}

O AEM Analyzer pode ser baixado como um arquivo zip no [Portal de distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). Você pode instalar o pacote por meio do [Gerenciador de Pacotes](/help/sites-administering/package-manager.md) na instância do AEM de origem.

## Considerações importantes sobre o uso do AEM Analyzer {#important-considerations-for-using-aem-analyzer}

Consulte a seção abaixo para entender considerações importantes na execução do AEM Analyzer:

* O relatório do Analyzer é criado usando a saída do [Detector de padrões](/help/sites-deploying/pattern-detector.md) do AEM. A versão do Detector de padrões usada pelo Analyzer está incluída no pacote de instalação do AEM Analyzer
* O AEM Analyzer só pode ser executado pelo usuário **administrador** ou por um usuário do grupo **administradores**
* O Analyzer é compatível com instâncias do AEM com a versão 6.5 e superior.

>[!NOTE]
>
>Para evitar um impacto em instâncias críticas para os negócios, é recomendável executar o AEM Analyzer em um ambiente de Preparo o mais próximo possível do ambiente de Produção nas áreas de personalizações, configurações, conteúdo e aplicativos de usuários. Como alternativa, ele pode ser executado em um clone do ambiente de Autor de produção.

* A geração de conteúdo do relatório do AEM Analyzer pode demorar um tempo significativo, desde vários minutos a algumas horas. O tempo necessário depende muito do tamanho e da natureza do conteúdo do repositório do AEM, da versão do AEM e de outros fatores
* Devido ao tempo significativo que pode ser necessário para gerar o conteúdo do relatório, ele é gerado por um processo em segundo plano e mantido em cache. A visualização e o download do relatório devem ser relativamente rápidos, pois ele utiliza o cache de conteúdo até expirar ou até o relatório ser atualizado. Durante a geração do conteúdo do relatório, você pode fechar a guia do navegador e retornar posteriormente para a visualização do relatório quando o conteúdo estiver disponível no cache.

## Exibição do relatório do AEM Analyzer {#viewing-the-aem-analyzer-report}

Siga as etapas abaixo para exibir o relatório do AEM Analyzer:

1. Selecione o Adobe Experience Manager e navegue até **Ferramentas - Operações - 6.5 Modernizador de LTS**

   ![Exibir Relatório do Analisador 1](/help/sites-deploying/assets/view-analyzer-report-1.png)

1. Clique em **AEM 6.5 LTS Analyzer** para abri-lo

   ![Exibir Relatório do Analisador 2](/help/sites-deploying/assets/view-analyzer-report-2.png)

1. Clique em **Gerar relatório** para executar o AEM Analyzer

   ![Exibir Relatório do Analisador 3](/help/sites-deploying/assets/view-analyzer-report-3.png)

1. Enquanto o AEM Analyzer está gerando o relatório, você pode ver o progresso feito pela ferramenta na tela. Ele exibe o progresso em termos da porcentagem concluída. Exibe também o número de itens analisados e o número de conclusões

   ![Exibir Relatório do Analisador 4](/help/sites-deploying/assets/view-analyzer-report-4.png)

1. Depois que o relatório do Analisador LTS 6.5 é gerado, ele exibe um resumo e o número de conclusões em um formato tabular organizado pelo tipo de descoberta e o nível de importância. Para obter mais detalhes sobre uma descoberta específica, clique no número que corresponde ao tipo de descoberta na tabela

   ![Exibir Relatório do Analisador 5](/help/sites-deploying/assets/view-analyzer-report-5.png)

1. Você tem a opção de baixar o relatório em um formato CSV (valores separados por vírgula) clicando em **Exportar para CSV**. Você pode forçar o Analisador a limpar seu cache e gerar novamente o relatório clicando em **Atualizar Relatório**. Se o cache expirar, você precisará gerar o relatório novamente.

## Interpretação do relatório do AEM Analyzer {#interpreting-the-aem-analyzer-report}

Quando a ferramenta Analisador LTS 6.5 é executada na instância do AEM, o relatório é exibido como resultado na janela da ferramenta.

O formato do relatório é:

* **Visão geral do relatório**: informações sobre o relatório propriamente dito, que incluem as seguintes informações:

   * **Hora do Relatório**: quando o conteúdo do relatório foi gerado e disponibilizado pela primeira vez
   * **Hora de Expiração**: quando o cache do conteúdo do relatório expirará
   * **Período de Geração**: a quantidade de tempo em que o relatório foi gerado
   * **Contagem de conclusões**: o número total de conclusões incluídas no relatório

* **Visão geral do sistema**: informações sobre o sistema AEM no qual o Analyzer foi executado
* **Categorias de conclusão**: várias seções que abordam uma ou mais conclusões da mesma categoria. Cada seção inclui o seguinte: nome da categoria, subtipos, contagem e importância das conclusões, resumo, link para a documentação da categoria e informações de conclusões individuais.

  ![Resumo do relatório do Analyzer](/help/sites-deploying/assets/analyzer-report-summary.png)

  Um nível de importância é atribuído a cada conclusão para indicar uma prioridade aproximada de ação.

>[!NOTE]
>
>Para saber mais sobre cada Categoria de Achados, consulte [Categorias do Detector de Padrões](https://experienceleague.adobe.com/en/docs/experience-manager-pattern-detection/table-of-contents/aso).

Para entender os níveis de importância, siga a tabela abaixo:

| Importância | Descrição |
|---|---|
| INFO | Essa conclusão é fornecida para fins informativos. |
| CONSULTIVO | Essa conclusão pode ser um problema de atualização. Recomenda-se uma investigação mais aprofundada. |
| CRÍTICO | Essa conclusão provavelmente será um problema de atualização que deve ser resolvido para evitar a perda de função ou do desempenho. |

## Interpretação do relatório CSV do analisador LTS do AEM 6.5 {#interpreting-the-aem-65lts-analyzer-report}

Quando você clica na opção **CSV** da sua instância do AEM, o formato CSV do relatório do Analyzer é criado a partir do cache de conteúdo e retornado ao seu navegador. Dependendo das configurações do navegador, esse relatório é baixado automaticamente como um arquivo com o nome padrão de `report.csv`.

Se o cache tiver expirado, o relatório será gerado novamente antes que o arquivo CSV seja criado e baixado.

O formato CSV do relatório inclui informações geradas a partir da saída do Detector de padrões, classificadas e organizadas por tipo de categoria, subtipo e nível de importância. Seu formato é adequado para exibição e edição em um aplicativo como o Microsoft Excel. O objetivo é fornecer todas as informações de conclusão em um formato repetível, que pode ser útil na comparação de relatórios ao longo do tempo para medir o progresso.

As colunas do relatório em formato CSV são:

* **code**: o código da categoria
* **type**: o nome da categoria
* **subtype**: o subtipo da categoria
* **importance**: o nível de importância
* **identifier**: o identificador principal da conclusão
* **message**: a mensagem fornecida para a conclusão
* **context**: uma cadeia JSON de dados de conclusões

Um valor de &quot;`\N`&quot; em uma coluna para uma conclusão individual indica que nenhum dado foi fornecido.

## Interface HTTP {#http-interface}

O Analisador LTS 6.5 fornece uma interface HTTP que pode ser usada como alternativa à interface do usuário no AEM. A interface dá suporte aos comandos `HEAD` e `GET`. Ela pode ser usada para gerar o relatório do Analyzer e retorná-lo em um dos três formatos: JSON, CSV e valores separados por tabulação (TSV).

As seguintes URLs estão disponíveis para acesso HTTP, em que `<host>` é o nome do host, juntamente com a porta, se necessário, do servidor no qual o Analyzer está instalado:

* `http://<host>/apps/aem66-analyzer/analysis/report.json` para formato JSON
* `http://<host>/apps/aem66-analyzer/analysis/report.csv` para formato CSV
* `http://<host>/apps/aem66-analyzer/analysis/report.tsv` para formato TSV

### Execução de uma solicitação HTTP {#executing-an-http-request}

Uma maneira simples de executar uma solicitação HTTP é abrir uma guia no mesmo navegador no qual você já fez logon no AEM como administrador. Você pode digitar o URL na guia do navegador e fazer com que os resultados sejam exibidos ou baixados pelo navegador.

Você também pode usar uma ferramenta de linha de comando como `curl` ou `wget` e qualquer aplicativo cliente HTTP. Quando não estiver usando uma guia do navegador com uma sessão autenticada, você deve fornecer um nome de usuário administrativo e uma senha como parte do comentário.

Este é um exemplo de como isso pode ser feito:

```shell
curl -u admin:admin 'http://localhost:4502/apps/aem66-analyzer/analysis/report.csv' > report.csv.
```

## Ajustar o tempo de vida do cache {#adjusting-the-cache-lifetime}

O tempo de vida padrão do cache do AEM 6.5 LTS Analyzer é de 24 horas. Com a opção de atualizar um relatório e regenerar o cache, tanto na instância do AEM quanto na interface HTTP, esse valor padrão provavelmente será apropriado para a maioria dos usos do AEM 6.5 LTS Analyzer. Se o tempo de geração do relatório for particularmente longo para sua instância do AEM, talvez você queira ajustar o tempo de vida do cache para minimizar a regeneração do relatório.

O valor vitalício do cache é armazenado como a propriedade `maxCacheAge` no seguinte nó do repositório:

```
/apps/aem66-analyzer/content/modernizer/analyzer/jcr:content
```

O valor dessa propriedade é o tempo de vida do cache em segundos. Um administrador pode ajustar a duração do cache usando o CRX/DE Lite.

## Usar o transformador de conteúdo {#using-content-transformer}

### Disponibilidade {#content-transformer-availability}

O transformador de conteúdo é fornecido com o analisador AEM 6.5 LTS que pode ser baixado como um arquivo zip no Portal de distribuição de software.

### Considerações importantes sobre o uso do transformador de conteúdo {#important-considerations-for-using-content-transformer}

Consulte a seção abaixo para entender as considerações importantes sobre o uso do transformador de conteúdo (CT):

* Para usar o transformador de conteúdo, primeiro execute o AEM Analyzer no seu ambiente do AEM
* Embora seja possível executar o transformador de conteúdo no ambiente de produção, é recomendável executar o transformador de conteúdo em um clone do ambiente de produção. Mais importante, é necessário garantir que o AEM Analyzer e a CT sejam executados no mesmo ambiente
* Você precisa ser um administrador no ambiente em que deseja executar o transformador de conteúdo
* Uma operação de remoção que pode alterar o conteúdo de origem criará um pacote de backup dos caminhos de origem em `/etc/packages/modernizer-content-transformation` por padrão antes da transformação. Embora a caixa de diálogo Remover operação tenha uma opção para desabilitar/habilitar a criação do pacote de backup, é altamente recomendável ter sempre a opção Habilitar criação de pacote selecionada
* Cada página no Transformador de conteúdo é configurada para listar no máximo 50 descobertas. Assim, um máximo de 50 achados pode ser transformado de cada vez. Isso é feito para fornecer uma resposta oportuna na interface do usuário.

### Abrir o transformador de conteúdo {#opening-the-content-transformer}

1. Faça logon na instância de origem do AEM como administrador e acesse a página inicial em *https://host:port/aem/start.htm*
1. Navegue até **Ferramentas - Operações - 6.5 Modernizador de LTS**

   ![Abrindo o Transformador de Conteúdo 1](/help/sites-deploying/assets/opening-content-transformer-1.png)

1. Clique no cartão **Transformador de conteúdo para o relatório do Analisador LTS 6.5**

   ![Abrindo o Transformador de Conteúdo 2](/help/sites-deploying/assets/opening-content-transformer-2.png)

1. Se o relatório do Analyzer não for gerado, a página **Transformar conteúdo** exibirá **Nenhum relatório**. A mesma mensagem **Nenhum relatório** também será exibida se todas as descobertas relacionadas a conteúdo tiverem sido removidas

   ![Abrindo o Transformador de Conteúdo 3](/help/sites-deploying/assets/opening-content-transformer-3.png)

1. Abaixo está um exemplo de como a página Visão geral do transformador de conteúdo será exibida se a criação do relatório do AEM Analyzer tiver sido bem-sucedida e se encontrar problemas relacionados ao conteúdo.

O tempo de expiração restante para o relatório do AEM Analyzer é mostrado no painel lateral. É recomendável executar o Transformador de conteúdo com o relatório mais recente do AEM Analyzer para evitar a perda de resultados relacionados ao conteúdo

![Abrindo o Transformador de Conteúdo 4](/help/sites-deploying/assets/opening-content-transformer-4.png)

1. Você pode filtrar os problemas com base no Código do padrão, Subtipo, Importância e Source

   ![Abrindo o Transformador de Conteúdo 5](/help/sites-deploying/assets/opening-content-transformer-5.png)

### Remoção de caminhos {#removing-paths}

1. Você pode selecionar todos os problemas ou problemas específicos e selecionar **Remover** para resolvê-los

   ![Removendo Caminhos 1](/help/sites-deploying/assets/removing-paths-1.png)

   >[!NOTE]
   >Uma operação Remove cria um pacote de backup dos caminhos de origem em `/etc/packages/modernizer-content-transformation` por padrão, antes da transformação. Embora a caixa de diálogo Remover operação tenha uma opção para desabilitar/habilitar a criação do pacote de backup, é altamente recomendável ter sempre a opção Habilitar criação de pacote selecionada.

   ![Removendo Caminhos 2](/help/sites-deploying/assets/removing-paths-2.png)

1. Um exemplo de um pacote de backup criado para a operação de remoção dos caminhos é mostrado abaixo. Você pode clicar em **Instalar** para trazer de volta os caminhos de origem

   ![Removendo Caminhos 3](/help/sites-deploying/assets/removing-paths-3.png)

   >[!CAUTION]
   >
   >Não exclua `/etc/packages/modernizer-content-transformation`, pois este é o local onde residem os pacotes de backup. Você pode excluir este local para reduzir o tamanho do repositório somente quando tiver certeza de que não precisa mais desses pacotes.

1. Como opção, você pode criar um pacote de descobertas de conteúdo selecionadas para uso futuro. Para fazer isso, selecione as descobertas que deseja incluir e clique em **Pacote** na parte superior esquerda. Insira um nome de pacote, escolha um caminho de pacote e clique no botão **Pacote** para concluir o processo.

   ![Removendo Caminhos 3](/help/sites-deploying/assets/removing-paths-4.png)

### Problemas conhecidos {#known-issues}

* Às vezes, a operação Remover pode exibir a notificação: *&quot;Alguns caminhos não foram removidos com êxito. Verifique os logs e tente novamente.*&quot;. No entanto, se os caminhos tiverem sido realmente removidos, você poderá ignorar essa mensagem com segurança
* Da mesma forma, a operação Package pode falhar com o erro: *&quot;Erro ao executar a operação desejada. Verifique os logs e tente novamente.*&quot;. Isso provavelmente ocorre devido à expiração da sessão. Nesses casos, tentar novamente a operação deve resolver o problema.





