---
title: Arquitetura e topologias de implantação do AEM Forms
description: Detalhes da arquitetura do AEM Forms e topologias recomendadas para clientes e clientes novos e existentes do AEM que estão atualizando do LiveCycle ES4 para o AEM Forms.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
role: Admin
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Foundation Components
exl-id: 23ffbaa6-1bd9-48c3-afa3-19737bb15de0
source-git-commit: 060bb23d64a90f0b2da487ead4c672cbf471c9a8
workflow-type: tm+mt
source-wordcount: '1471'
ht-degree: 1%

---

# Arquitetura e topologias de implantação do AEM Forms {#architecture-and-deployment-topologies-for-aem-forms}

| Versão | Link do artigo |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Clique aqui](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/forms-overview/aem-forms-cloud-service-architecture.html?lang=pt-BR) |
| AEM 6.5 | Este artigo |

## Arquitetura {#architecture}

O AEM Forms é um aplicativo implantado no AEM como um pacote do AEM. O pacote é conhecido como pacote complementar do AEM Forms. O pacote complementar do AEM Forms contém serviços (provedores de API), que são implantados no contêiner OSGi do AEM, e servlets ou JSPs (fornecendo funcionalidade de front-end e REST API) gerenciados pela estrutura do AEM Sling. O diagrama a seguir descreve essa configuração:

![arquitetura](assets/architecture.png)

A arquitetura do AEM Forms inclui os seguintes componentes:

* **Serviços principais da AEM:** serviços básicos que a AEM fornece a um aplicativo implantado. Esses serviços incluem um repositório de conteúdo compatível com JCR, um contêiner de serviço OSGI, um mecanismo de fluxo de trabalho, uma loja de confiança, uma loja de chaves e assim por diante. Esses serviços estão disponíveis para o aplicativo do AEM Forms, mas não são fornecidos por pacotes do AEM Forms. Esses serviços são parte integrante da pilha geral do AEM e vários componentes da AEM Forms usam esses serviços.
* **Serviços do Forms:** forneça funcionalidades relacionadas a formulários, como criar, reunir, distribuir e arquivar documentos do PDF, adicionar assinaturas digitais para limitar o acesso a documentos e decodificar formulários com código de barras. Esses serviços estão disponíveis publicamente para consumo por código personalizado coimplantado no AEM.
* **Camada da Web:** JSPs ou servlets, criados sobre serviços comuns e de formulários, que fornecem as seguintes funcionalidades:

   * **Front-end de criação**: uma interface de usuário de criação e gerenciamento de formulários para criação e gerenciamento de formulários.
   * **Front-end de representação e envio de formulário**: uma interface para o usuário final a ser usada pelos usuários finais da AEM Forms (por exemplo, cidadãos que acessam um site do governo). Isso fornece funcionalidades de representação de formulário (formulário de exibição em um navegador da Web) e envio.
   * **REST APIs**: JSPs e servlets exportam um subconjunto de serviços de formulários para consumo remoto por clientes baseados em HTTP, como o SDK móvel de formulários.

**AEM Forms no OSGi:** um ambiente do AEM Forms no OSGi é um Autor padrão do AEM ou uma Publicação do AEM com o pacote do AEM Forms implantado nele. Você pode executar o AEM Forms no OSGi em um [ambiente de servidor único, Farm e configurações em cluster](/help/sites-deploying/recommended-deploys.md). A configuração do cluster está disponível somente para instâncias do AEM Author.

<!--

**AEM Forms on JEE:** AEM Forms on JEE is AEM Forms server running on JEE stack. It has AEM Author with AEM Forms add-on packages and additional AEM Forms JEE capabilities co-deployed on a single JEE stack running on an application server. You can run AEM Forms on JEE in single-server and clustered setups. AEM Forms on JEE is required only to run document security, process management, and for LiveCycle customers upgrading to AEM Forms. Here are a few additional scenarios to use AEM Forms on JEE:

* **HTML workspace support (for customers using HTML workspace):** AEM Forms on JEE enables single sign-on with Processing instances, serves certain assets rendered on Processing instances, and handles submission of forms rendered within the HTML workspace.
* **Advanced additional form/interactive communication data processing**: AEM Forms on JEE can be utilized for additionally processing form/interactive communication data (and saving the results to a suitable data store) in complex use-cases where advanced process-management capabilities are required.

AEM Forms on JEE also includes provides following supporting services to the AEM components:

* **Integrated user management:** Allows users of AEM Forms on JEE to be recognized as AEM forms on OSGi users and helps enable SSO for both OSGi and JEE users. This is required for scenarios where single sign-on between AEM forms on OSGi and AEM Forms on JEE is required (for example, HTML workspace).
* **Asset hosting:** AEM Forms on JEE can serve assets (for example, HTML5 forms) rendered on AEM Forms on OSGi.

-->

A interface do usuário de criação do AEM Forms não oferece suporte à criação de Documentos de registro (DOR), PDF forms e HTML5 Forms. Esses ativos são projetados usando o aplicativo Forms Designer independente e carregados individualmente no AEM Forms Manager. <!--Alternatively, for AEM Forms on JEE, forms can be designed as application (in AEM Forms Workbench) assets and deployed into AEM Forms on JEE server.-->

O AEM Forms no OSGi <!--and AEM Forms on JEE both--> tem recursos de fluxo de trabalho. Você pode criar e implantar rapidamente fluxos de trabalho básicos para várias tarefas nos formulários AEM no OSGi.<!--, without having to install the full-fledged Process Management capability of AEM Forms on JEE. There is some difference in the [features of Form-centric workflow on AEM Forms on OSGi and Process Management capability of AEM Forms on JEE](capabilities-osgi-jee-workflows.md). The development and management of Form-centric workflows on AEM Forms on OSGi uses the familiar AEM Workflow and AEM Inbox capabilities.-->

## Terminologias {#terminologies}

A imagem a seguir exibe várias configurações de servidor do AEM Form e seus componentes que são usados em uma implantação típica do AEM Forms:

![aem_forms_-_recommendations_topology](assets/aem_forms_-_recommendedtopology.png)

**Autor:** uma instância do autor é um servidor do AEM Forms em execução no modo de execução padrão do Autor. <!--It can be AEM Forms on JEE or AEM Forms on OSGi environment.--> Destina-se a usuários internos, designers de comunicações interativas e de formulários e desenvolvedores. Ela permite as seguintes funcionalidades:

* **Criação e gerenciamento de formulários e comunicações interativas:** designers e desenvolvedores podem criar e editar formulários adaptáveis e comunicações interativas, carregar outros tipos de formulários criados externamente, por exemplo, formulários criados no Adobe Forms Designer, e gerenciar esses ativos usando o console do Forms Manager.
* **Publicação de formulário e comunicação interativa:** O Assets hospedado em uma instância de autor pode ser publicado em uma instância de publicação para executar operações de tempo de execução. A publicação de ativos usa os recursos de replicação do AEM. A Adobe recomenda que um agente de replicação seja configurado em todas as instâncias de autor para enviar manualmente formulários publicados para instâncias de processamento, e outro agente de replicação seja configurado nas instâncias de processamento com o gatilho *Em Recebimento* habilitado para replicar automaticamente os formulários recebidos para publicar instâncias.

**Publicar:** uma instância de publicação é um servidor do AEM Forms em execução no modo de execução padrão Publicar. As instâncias de publicação destinam-se aos usuários finais de aplicativos baseados em formulário, por exemplo, usuários que acessam um site público e enviam formulários. Ela permite as seguintes funcionalidades:

* Renderização e envio do Forms para usuários finais.
* Transporte de dados brutos de formulário enviados para instâncias de processamento para processamento posterior e armazenamento no sistema de registro final. A implementação padrão fornecida no AEM Forms faz isso usando os recursos de replicação reversa do AEM. Uma implementação alternativa também está disponível para enviar diretamente os dados de formulário para servidores de processamento, em vez de salvá-los localmente primeiro (o último é um pré-requisito para a ativação da replicação reversa). Os clientes que se preocupam com o armazenamento de dados potencialmente confidenciais em instâncias de publicação podem entrar nesta [implementação alternativa](/help/forms/using/configuring-draft-submission-storage.md), já que as instâncias de processamento normalmente ficam em uma zona mais segura.
* Renderização e envio de comunicações e cartas interativas: uma comunicação e uma carta interativas são renderizadas em instâncias de publicação e os dados correspondentes são enviados às instâncias de processamento para armazenamento e pós-processamento. Os dados podem ser salvos localmente em uma instância de publicação e replicados revertidos para uma instância de processamento (a opção padrão) posteriormente ou enviados diretamente para a instância de processamento sem serem salvos na instância de publicação. A última implementação é útil para clientes preocupados com a segurança.

**Processando:** uma instância do AEM Forms em execução no modo de execução do Autor sem usuários atribuídos ao grupo de gerenciadores de formulários. Você pode implantar o AEM Forms <!--AEM Forms on JEE or--> no OSGi como uma instância de processamento. Os usuários não são atribuídos para garantir que as atividades de criação e gerenciamento de formulários não sejam executadas na instância de Processamento e ocorram somente na instância de Autor. Uma instância de Processamento permite as seguintes funcionalidades:

* **Processamento de dados brutos de formulário provenientes de uma instância de Publicação:** isso é obtido principalmente em uma instância de Processamento, por meio de fluxos de trabalho do AEM que são acionados quando os dados chegam. Os workflows podem usar a etapa Modelo de dados de formulário fornecida pronta para uso para arquivar os dados ou documentos em um armazenamento de dados adequado.
* **Armazenamento seguro de dados de formulário**: o processamento fornece um repositório atrás do firewall para dados brutos de formulário que são isolados dos usuários. Nem os designers de formulário na instância do Autor nem os usuários finais na instância de Publicação podem acessar esse repositório.

  >[!NOTE]
  >
  >A Adobe recomenda usar um armazenamento de dados de terceiros para salvar os dados processados finais em vez de usar o repositório do AEM.

* **Armazenamento e pós-processamento de dados de correspondência provenientes de uma instância de Publicação:** os fluxos de trabalho do AEM executam o pós-processamento opcional das definições de correspondência correspondentes. Esses workflows podem salvar os dados processados finais em um armazenamento de dados externo adequado.

* **Hospedagem do HTML Workspace**: uma instância de processamento hospeda o front-end para o HTML Workspace. O espaço de trabalho do HTML fornece a interface para atribuição de tarefas/grupos associada para processos de revisão e aprovação.

Uma instância de Processamento é configurada para ser executada no modo de execução do Autor porque:

* Ela permite a replicação reversa de dados de formulário brutos de uma instância de publicação. O manipulador de armazenamento de dados padrão requer o recurso de replicação reversa.
* Os fluxos de trabalho do AEM, que são o principal meio de processar dados de formulário brutos provenientes de uma instância de publicação, são recomendados para serem executados em um sistema no estilo do autor.

<!--

## Sample physical topologies for AEM Forms on JEE {#sample-physical-topologies-for-aem-forms-on-jee}

The AEM Forms on JEE topologies recommended below are mainly for customers upgrading from LiveCycle or a previous version of AEM Forms on JEE. Adobe recommends using AEM Forms on OSGi for fresh installations. A fresh installation of AEM Forms on JEE only recommended for using Document Security and Process Management capabilities.

### Topology for using document services or document security capabilities {#topology-for-using-document-services-or-document-security-capabilities}

AEM Forms customers planning to use only document services or document security capabilities can have a topology similar to the one displayed below. This topology recommends using a single instance of AEM Forms. You can also create a cluster or farm of AEM Forms servers, if necessary. This topology is recommended when most users programmatically access capabilities of AEM Forms server and intervention through the user interface is minimum. The topology is helpful in batch processing operations of document services. For example, using output service to create hundreds of non-editable PDF documents on daily basis.

Although, AEM Forms lets you set up and run all the functionalities from a single server, yet, you should do capacity planning, load balancing, and set up dedicated servers for specific capabilities in a production environment. For example, for an environment using the PDF Generator service to convert thousands of pages a day and add digital signatures to limit access to documents, set up separate AEM Forms servers for the PDF Generator service and digital signature capabilities. It helps provide optimum performance and scale the servers independent of each other.

![basic-features](assets/basic-features.png)

### Topology for using AEM Forms process management {#topology-for-using-aem-forms-process-management}

AEM Forms customers planning to use AEM Forms process management features, for example, HTML Workspace can have a topology similar to the one displayed below. The AEM Forms on JEE server can be in a single server or cluster configuration.

If you are upgrading from LiveCycle ES4, this topology closely mirrors with what you already have in LiveCycle except for the addition of AEM Author built-in to AEM Forms on JEE. Moreover, there is no change in the clustering requirements for customers performing an upgrade. If you were using AEM Forms in a clustered environment, you can continue with same in AEM 6.5 Forms. For a fresh installation of AEM Forms of JEE for using HTML Workspace, running AEM author instance built-in to the JEE environment is an additional requirement.

Form data store is a third-party data store used for storing final processed data of forms and interactive communications. This is an optional element in the topology. You can also choose to set up a processing instance and use its repository as the final system-of-record system, if necessary.

![topology_for_usinghtmlworkspaceandformsapp](assets/topology_for_usinghtmlworkspaceandformsapp.png)

The topology is recommended to the customers planning to use AEM Forms on JEE server for process management capabilities (HTML Workspace) without using any post-processing, adaptive forms, HTML5 forms, and interactive communication capabilities.

### Topology for using adaptive forms, HTML5 forms, interactive communication capabilities {#topology-for-using-adaptive-forms-html-forms-interactive-communication-capabilities}

AEM Forms customers planning to use AEM Forms data capture capabilities, for example, adaptive forms, HTML5 Forms, PDF Forms, can have a topology similar to the one displayed below. This topology is also recommended for using interactive communication capabilities of AEM Forms.

![topology-for-using-forms-osgi-modules](assets/topology-for-using-forms-osgi-modules.png)

You can make the following changes/customizations to the above-suggested topology:

* Using HTML Workspace and AEM Forms app requires an AEM author or processing instance. You can use the AEM author instance built-in to AEM Forms on JEE server instead of setting up an additional external AEM author server.
* An AEM Author or Processing instance is required only for Forms-centric workflows on OSGi, adaptive forms, forms portal, and interactive communication.
* interactive communication Agent UI is generally run within the organization. So, you can keep a publish server for Agent UI within the private network.
* AEM forms on OSGi instance built-in to AEM Forms on JEE server can also run Forms-centric workflows on OSGi and Watched Folders.

-->

## Exemplos de topologias físicas para usar o AEM Forms no OSGi {#sample-physical-topologies-for-using-aem-forms-on-osgi}

### Topologia para captura de dados, comunicação interativa, fluxo de trabalho centrado em formulários nos recursos do OSGi {#topology-for-data-capture-interactive-communication-form-centric-workflow-on-osgi-capabilities}

Os clientes do AEM Forms que planejam usar os recursos de captura de dados do AEM Forms, por exemplo, formulários adaptáveis, HTML5 Forms, PDF forms, podem ter uma topologia semelhante à exibida abaixo. Essa topologia também é recomendada para usar comunicações interativas e fluxos de trabalho centrados no Forms no recurso OSGi, por exemplo, para usar a Caixa de entrada do AEM e o aplicativo AEM Forms para fluxos de trabalho de processo comercial.

![interative-use-cases-af-cm-osgi-workflow](assets/interactive-use-cases-af-cm-osgi-workflow.png)

### Topologia para usar recursos de pastas monitoradas para processamento em lote offline {#topology-for-using-watched-folder-capabilities-for-offline-batch-processing}

Os clientes do AEM Forms que planejam usar Pastas monitoradas para processamento em lote podem ter uma topologia semelhante à exibida abaixo. A topologia exibe um ambiente em cluster, mas você decide usar uma única instância ou um farm de servidores do AEM Forms, dependendo da carga. A fonte de dados de terceiros é seu próprio sistema de registro. Ele age como uma fonte de entrada para Pastas monitoradas. A topologia também exibe a saída no formato de um arquivo impresso. Você também pode armazenar o conteúdo de saída em um sistema de arquivos, enviar por email e usar outros métodos personalizados para consumir saída.

![offline-batch-processing-via-watch-folders](assets/offline-batch-processing-via-watched-folders.png)

### Topologia para usar recursos de serviços de documentos para processamento offline baseado em API {#topology-for-using-document-services-capabilities-for-offline-api-based-processing}

Os clientes da AEM Forms que planejam usar somente o recurso de serviços de documento podem ter uma topologia semelhante à exibida abaixo. Essa topologia recomenda usar um cluster de AEM Forms em servidores OSGi. Essa topologia é recomendada quando a maioria dos usuários acessa programaticamente (usando APIs) os recursos do servidor do AEM Forms e a intervenção por meio da interface do usuário é mínima. A topologia é bastante útil em vários cenários de cliente de software. Por exemplo, vários clientes usando o serviço PDF Generator para criar documentos do PDF sob demanda.

Embora o AEM Forms permita configurar e executar todas as funcionalidades de um único servidor, você deve fazer o planejamento de capacidade, o balanceamento de carga e configurar servidores dedicados para recursos específicos em um ambiente de produção. Por exemplo, para um ambiente que usa o serviço PDF Generator para converter milhares de páginas por dia e vários formulários adaptáveis para capturar dados, configure servidores AEM Forms separados para o serviço PDF Generator e recursos de formulários adaptáveis. Ele ajuda a fornecer o melhor desempenho e a dimensionar os servidores independentemente uns dos outros.

![processamento baseado em api offline](assets/offline-api-based-processing.png)
