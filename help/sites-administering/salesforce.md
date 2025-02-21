---
title: Integração com o Salesforce
description: Saiba mais sobre a integração do Adobe Experience Manager (AEM) com o Salesforce.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '1530'
ht-degree: 0%

---


# Integração com o Salesforce {#integrating-with-salesforce}

A integração do Salesforce com o Adobe Experience Manager (AEM) fornece recursos de gerenciamento de clientes potenciais e usa os recursos existentes fornecidos prontos para uso pela Salesforce. Você pode configurar o AEM para publicar leads no Salesforce e criar componentes que acessam dados diretamente da Salesforce.

A integração bidirecional e extensível entre o AEM e o Salesforce permite:

* Organizações para usar e corrigir totalmente os dados e aprimorar a experiência do cliente.
* Engajamento de marketing em atividades de vendas.
* Organizações para transmitir e receber dados automaticamente de um armazenamento de dados da Salesforce.

Este documento descreve o seguinte:

* como configurar o Salesforce Cloud Services (configure o AEM para integrar com o Salesforce).
* como usar informações de lead/contato da Salesforce no Client Context e para o Personalization.
* como usar o modelo de fluxo de trabalho do Salesforce para publicar usuários do AEM como clientes potenciais no Salesforce.
* como criar um componente que mostra dados do Salesforce.

## Configuração do AEM para integração com o Salesforce {#configuring-aem-to-integrate-with-salesforce}

Para configurar o AEM para integrar com o Salesforce, primeiro configure um aplicativo de acesso remoto no Salesforce. Em seguida, você configura o serviço de nuvem Salesforce para apontar para esse aplicativo de acesso remoto.

>[!NOTE]
>
>Você pode criar uma conta de desenvolvedor gratuita no Salesforce.

Para configurar o AEM para integração com o Salesforce:

>[!CAUTION]
>
>Instale o pacote de integração [Salesforce Force API](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?fulltext=salesforce*&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;orderby.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=2&amp;package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffeaturepack%2Fcom.adobe.cq.mcm.salesforce.content-1.0.4.zip) antes de continuar com o procedimento. Para obter mais detalhes sobre como trabalhar com pacotes, consulte a página [Como trabalhar com pacotes](/help/sites-administering/package-manager.md#package-share).

1. No AEM, navegue até **Cloud Services**. Em Serviços de Terceiros, clique em **Configurar Agora** no **Salesforce**.

   ![chlimage_1-70](assets/chlimage_1-70.png)

1. Crie uma configuração, por exemplo, **desenvolvedor**.

   >[!NOTE]
   >
   >A nova configuração redireciona para uma nova página: **http://localhost:4502/etc/cloudservices/salesforce/developer.html**. Esse é exatamente o mesmo valor que você deve especificar na URL de retorno de chamada ao criar o aplicativo de acesso remoto no Salesforce. Esses valores devem corresponder a.

1. Faça logon na sua conta da Salesforce (ou caso não tenha uma, crie uma em [https://developer.salesforce.com](https://developer.salesforce.com).)
1. No Salesforce, navegue até **Criar** > **Aplicativos** para acessar **Aplicativos Conectados** (nas versões anteriores do Salesforce, o fluxo de trabalho era **Implantar** > **Acesso Remoto**).
1. Clique em **Novo** para conectar o AEM ao Salesforce.

   ![chlimage_1-71](assets/chlimage_1-71.png)

1. Insira o **Nome do Aplicativo Conectado**, **Nome da API** e **Email de Contato**. Marque a caixa de seleção **Habilitar configurações do OAuth**, insira a **URL de retorno de chamada** e adicione um escopo do OAuth (por exemplo, acesso completo). A URL de retorno é semelhante a esta: `http://localhost:4502/etc/cloudservices/salesforce/developer.html`

   Altere o nome do servidor/número da porta e o nome da página para corresponder à sua configuração.

   ![chlimage_1-72](assets/chlimage_1-72.png)

1. Clique em **Salvar** para salvar a configuração do Salesforce. O Salesforce cria uma **chave do consumidor** e um **segredo do consumidor**, necessários para a configuração do AEM.

   ![chlimage_1-73](assets/chlimage_1-73.png)

   >[!NOTE]
   >
   >Aguarde vários minutos (até 15 minutos) para que o aplicativo de acesso remoto no Salesforce seja ativado.

1. No AEM, navegue até **Cloud Services** e acesse a configuração do Salesforce criada anteriormente (por exemplo, **desenvolvedor**). Clique em **Editar** e insira a chave do cliente e o segredo do cliente em salesforce.com.

   ![chlimage_1-15](assets/chlimage_1-15.jpeg)

   | URL de login | Este é o Ponto de Extremidade de Autorização do Salesforce. Seu valor é pré-preenchido e serve a maioria dos casos. |
   |---|---|
   | Chave do cliente | Insira o valor obtido da página Registro de aplicativo de acesso remoto em salesforce.com |
   | Segredo do cliente | Insira o valor obtido da página Registro de aplicativo de acesso remoto em salesforce.com |

1. Clique em **Conectar ao Salesforce** para se conectar. O Salesforce solicita que você permita que a configuração se conecte ao Salesforce.

   ![chlimage_1-74](assets/chlimage_1-74.png)

   No AEM, uma caixa de diálogo de confirmação é aberta, informando que você se conectou com êxito.

1. Navegue até a página raiz do site e clique em **Propriedades da página**. Em seguida, selecione **Cloud Services**, adicione **Salesforce** e selecione a configuração correta (por exemplo, **desenvolvedor**).

   ![chlimage_1-75](assets/chlimage_1-75.png)

   Agora você pode usar o modelo de fluxo de trabalho para publicar leads no Salesforce e criar componentes que acessam dados do Salesforce.

## Exportar usuários do AEM como clientes em potencial do Salesforce {#exporting-aem-users-as-salesforce-leads}

Se quiser exportar um usuário do AEM como cliente potencial do Salesforce, configure o fluxo de trabalho para publicar clientes potenciais no Salesforce.

Para exportar usuários do AEM como clientes potenciais do Salesforce:

1. Navegue até o fluxo de trabalho do Salesforce em `http://localhost:4502/workflow` clicando com o botão direito do mouse no fluxo de trabalho **Salesforce.com Export** e clicando em **Start**.

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. Selecione o usuário do AEM que deseja criar como cliente potencial como a **Carga** deste fluxo de trabalho (início > usuários). Selecione o nó de perfil do usuário, pois ele contém informações como **givenName** e **familyName**, que estão mapeadas para os campos **FirstName** e **LastName** do cliente potencial da Salesforce.

   ![chlimage_1-77](assets/chlimage_1-77.png)

   >[!NOTE]
   >
   >Antes de iniciar esse fluxo de trabalho, há determinados campos obrigatórios que um nó principal no AEM deve ter antes de ser publicado no Salesforce. Estes são **givenName**, **familyName**, **company** e **email**. Para ver uma lista completa de mapeamentos entre o usuário do AEM e o cliente potencial do Salesforce, consulte [Configuração de Mapeamento entre o usuário do AEM e o cliente potencial do Salesforce.](#mapping-configuration-between-aem-user-and-salesforce-lead)

1. Clique em **OK**. As informações do usuário são exportadas para salesforce.com. Você pode verificá-lo em salesforce.com.

   >[!NOTE]
   >
   >Os logs de erros mostram se um cliente potencial foi importado. Verifique o log de erros para obter mais informações.

### Configuração do workflow de exportação do Salesforce.com {#configuring-the-salesforce-com-export-workflow}

Se necessário, configure o workflow de exportação do Salesforce.com para corresponder à configuração correta do Salesforce.com ou para fazer outras alterações.

Para configurar o workflow de exportação do Salesforce.com:

1. Navegue até `http://localhost:4502/cf#/etc/workflow/models/salesforce-com-export.html.`

   ![chlimage_1-16](assets/chlimage_1-16.jpeg)

1. Abra a etapa Exportação do Salesforce.com, selecione a guia **Argumentos**, selecione a configuração correta selecionada e clique em **OK**. Além disso, se desejar que o fluxo de trabalho recrie um lead que foi excluído no Salesforce, marque a caixa de seleção.

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. Clique em **Salvar** para salvar as alterações.

   ![chlimage_1-79](assets/chlimage_1-79.png)

### Configuração de mapeamento entre o usuário do AEM e o líder da Salesforce {#mapping-configuration-between-aem-user-and-salesforce-lead}

Para exibir ou editar a configuração de mapeamento atual entre um usuário do AEM e um cliente potencial do Salesforce, abra o Gerenciador de Configurações: `https://<hostname>:<port>/system/console/configMgr` e pesquise a **Configuração de Mapeamento de Cliente Potencial do Salesforce**.

1. Abra o Configuration Manager clicando em **Console da Web** ou indo diretamente para `https://<hostname>:<port>/system/console/configMgr.`
1. Pesquisar por **Configuração de Mapeamento de Cliente Potencial da Salesforce**.

   ![chlimage_1-80](assets/chlimage_1-80.png)

1. Altere os mapeamentos, conforme necessário. O mapeamento padrão segue o padrão **aemUserAttribute=sfLeadAttribute**. Clique em **Salvar** para salvar as alterações.

## Configuração do Salesforce Client Context Store {#configuring-salesforce-client-context-store}

O armazenamento de contexto do cliente do Salesforce mostra informações adicionais sobre o usuário conectado no momento além das que já estão disponíveis no AEM. Ele extrai essas informações adicionais do Salesforce, dependendo da conexão do usuário com o Salesforce.

Para fazer isso, configure o seguinte:

1. Vincule um usuário do AEM com uma Salesforce ID por meio do componente Salesforce Connect.
1. Adicione os Dados de perfil do Salesforce na página de contexto do cliente para configurar as propriedades que deseja ver.
1. (Opcional) Crie um segmento que use os dados do Salesforce Client Context Store.

### Vincular um usuário do AEM a uma Salesforce ID {#linking-an-aem-user-with-a-salesforce-id}

Mapear um usuário do AEM com uma Salesforce ID para carregá-la no contexto do cliente. Em um cenário real, você estaria vinculando com base em dados de usuário conhecidos com validação. Para fins de demonstração, use o componente **Salesforce Connect** neste procedimento.

1. Navegue até um site na AEM, entre, arraste e solte o componente **Salesforce Connect** do sidekick.

   >[!NOTE]
   >
   >Se o componente **Salesforce Connect** não estiver disponível, vá para o modo de exibição **Design** e selecione-o para torná-lo disponível no modo de exibição **Editar**.

   ![chlimage_1-17](assets/chlimage_1-17.jpeg)

   Ao arrastar o componente para a página, ele exibe **Link to Salesforce=Off**.

   ![chlimage_1-81](assets/chlimage_1-81.png)

   >[!NOTE]
   >
   >Este componente é apenas para fins de demonstração. Para cenários do mundo real, haveria outro processo para vincular/combinar usuários com leads.

1. Depois de arrastar o componente na página, abra-o para configurá-lo. Selecione a configuração, o tipo de contato e o cliente em potencial ou contato da Salesforce e clique em **OK**.

   ![chlimage_1-82](assets/chlimage_1-82.png)

   O AEM vincula o usuário ao contato ou lead da Salesforce.

   ![chlimage_1-83](assets/chlimage_1-83.png)

### Adicionar dados do Salesforce ao Client Context {#adding-salesforce-data-to-client-context}

Você pode carregar dados do usuário do Salesforce no Client Context para usar na personalização:

1. Abra o contexto de cliente que você deseja estender navegando até lá, por exemplo, `http://localhost:4502/etc/clientcontext/default/content.html.`

   ![chlimage_1-18](assets/chlimage_1-18.jpeg)

1. Arraste o componente **Dados de perfil do Salesforce** para o contexto do cliente.

   ![chlimage_1-19](assets/chlimage_1-19.jpeg)

1. Abra o componente clicando duas vezes nele. Selecione **Adicionar item** e selecione uma propriedade na lista suspensa. Adicione quantas propriedades desejar e selecione **OK**.

   ![chlimage_1-84](assets/chlimage_1-84.png)

1. Agora, você vê as propriedades específicas do Salesforce no Salesforce exibidas no contexto do cliente.

   ![chlimage_1-85](assets/chlimage_1-85.png)

### Criar um segmento usando dados do Salesforce Client Context Store {#building-a-segment-using-data-from-salesforce-client-context-store}

Você pode criar um segmento que use dados do Salesforce Client Context Store. Para fazer isso:

1. Navegue até a segmentação no AEM, acessando **Ferramentas** > **Segmentação** ou [http://localhost:4502/miscadmin#/etc/segmentation](http://localhost:4502/miscadmin#/etc/segmentation).
1. Crie ou atualize um segmento para incluir dados do Salesforce. Para obter mais informações, consulte [Segmentação](/help/sites-administering/campaign-segmentation.md).

## Pesquisar clientes em potencial {#searching-leads}

O AEM vem com um componente de Pesquisa de amostra que pesquisa clientes potenciais no Salesforce de acordo com os critérios fornecidos. Este componente mostra como usar a API REST do Salesforce para pesquisar objetos do Salesforce. Para acionar uma chamada para salesforce.com, vincule uma página a uma configuração do Salesforce.

>[!NOTE]
>
>Este é um componente de exemplo que mostra como usar a API REST do Salesforce para consultar objetos do Salesforce. Use-o como exemplo para criar componentes mais complexos com base em suas necessidades.

Para usar este componente:

1. Navegue até a página onde deseja usar essa configuração. Abra as propriedades da página e selecione **Cloud Services.** Clique em **Adicionar Serviços** e selecione **Salesforce** e a configuração apropriada e clique em **OK**.

   ![chlimage_1-20](assets/chlimage_1-20.jpeg)

1. Arraste o componente de pesquisa do Salesforce para a página (desde que tenha sido ativado). Para ativá-lo, vá para o modo Design e adicione-o à área apropriada).

   ![chlimage_1-21](assets/chlimage_1-21.jpeg)

1. Abra o componente de Pesquisa, especifique os parâmetros de pesquisa e clique em **OK.**

   ![chlimage_1-86](assets/chlimage_1-86.png)

1. O AEM exibe os clientes em potencial especificados no componente de pesquisa que correspondem aos critérios especificados.

   ![chlimage_1-87](assets/chlimage_1-87.png)
