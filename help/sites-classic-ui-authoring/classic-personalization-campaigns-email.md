---
title: Marketing por email
description: O marketing por email (por exemplo, boletins informativos) é uma parte importante de qualquer campanha de marketing, pois é usado para enviar conteúdo aos seus clientes potenciais. No AEM, você pode criar informativos a partir de conteúdo existente do AEM e adicionar novo conteúdo, específico para os informativos.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Personalization
role: User
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '1767'
ht-degree: 0%

---


# Marketing por email{#e-mail-marketing}

>[!NOTE]
>
>A Adobe não pretende aprimorar ainda mais o rastreamento de e-mails de rejeições/aberturas (não entregues) enviadas pelo serviço SMTP da AEM.
>A recomendação é usar o [Adobe Campaign e a integração com o AEM](/help/sites-administering/campaign.md).

O marketing por email (por exemplo, boletins informativos) é uma parte importante de qualquer campanha de marketing, pois é usado para enviar conteúdo aos seus clientes potenciais. No AEM, você pode criar informativos a partir de conteúdo existente do AEM e adicionar novo conteúdo, específico para os informativos.

Depois de criado, é possível enviar informativos para o grupo específico de usuários imediatamente ou em outro horário agendado (por meio do uso de um fluxo de trabalho). Além disso, os usuários podem assinar informativos no formato que escolherem.

Além disso, o AEM permite administrar a funcionalidade do boletim informativo, incluindo manutenção de tópicos, arquivamento de boletins informativos e exibição de estatísticas.

>[!NOTE]
>
>No Geometrixx, o modelo de boletim informativo abre automaticamente o editor de email. Você pode usar o editor de email em outros modelos para os quais deseja enviar emails, como convites. O editor de email é exibido sempre que uma página é herdada de **mcm/components/newsletter/page**.

Este documento descreve as noções básicas para a criação de boletins informativos no AEM. Para obter informações mais detalhadas sobre como trabalhar com marketing por email, consulte os seguintes documentos:

* [Criação de uma página inicial efetiva de informativo](/help/sites-classic-ui-authoring/classic-personalization-campaigns-email-landingpage.md)
* [Gerenciamento de assinaturas](/help/sites-classic-ui-authoring/classic-personalization-campaigns-email-subscriptions.md)
* [Publicar um email para provedores de serviços de email](/help/sites-classic-ui-authoring/classic-personalization-campaigns-email-newsletters.md)
* [Rastreamento de emails devolvidos](/help/sites-classic-ui-authoring/classic-personalization-campaigns-email-tracking-bounces.md)

>[!NOTE]
>
>Se você atualizar provedores de email, fazer um teste de voo ou enviar um boletim informativo, essas operações falharão se o boletim informativo não for publicado primeiro na instância de publicação ou se a instância de publicação não estiver disponível. Publique seu informativo e certifique-se de que a instância de publicação esteja em execução.

## Criar uma experiência com informativos {#creating-a-newsletter-experience}

>[!NOTE]
>
>As notificações por email precisam ser configuradas por meio da configuração osgi. Consulte [Configurando Notificação por Email.](/help/sites-administering/notification.md)

1. Selecione a nova campanha no painel esquerdo ou clique duas vezes nela no painel direito.

1. Selecione a exibição de lista usando o ícone:

   ![Ícone de exibição de lista](do-not-localize/mcm_icon_listview-1.png)

1. Clique em **Novo...**

   Você pode especificar o **Título**, **Nome** e o tipo de experiência a ser criada; neste caso, Informativo.

   ![Caixa de diálogo Criar Experiência](assets/mcm_createnewsletter.png)

1. Clique em **Criar**.

1. Uma nova caixa de diálogo é aberta imediatamente. Aqui você pode inserir propriedades para o informativo.

   A **Lista de Destinatários Padrão** é um campo obrigatório, pois forma o ponto de contato para o informativo (consulte [Trabalhando com Listas](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#workingwithlists) para obter mais informações sobre listas).

   ![Caixa de diálogo Propriedades da página](assets/mcm_newnewsletterdialog.png)

   * **De Nome**
Nome que deve aparecer como remetente do informativo.

   * **Do endereço**
O endereço de e-mail que deve aparecer como o remetente do informativo.

   * **Assunto**
Assunto do informativo.

   * **Responder para**
Endereço de e-mail que deve tratar das respostas para o informativo enviado.

   * **Descrição**
Descrição do informativo.

   * **No Prazo**
A data e hora de envio do informativo.

   * **Lista de Destinatários Padrão**
Lista padrão que deve receber o informativo.

   Eles podem ser atualizados em um estágio posterior da caixa de diálogo **Propriedades...**.

1. Clique em **OK** para salvar.

## Adicionar conteúdo aos informativos {#adding-content-to-newsletters}

Você pode adicionar conteúdo, incluindo conteúdo dinâmico, ao seu informativo como faria em qualquer componente do AEM. No Geometrixx, o modelo de boletim informativo tem determinados componentes disponíveis para adicionar e modificar conteúdo em boletins informativos.

1. No MCM, clique na guia **Campanhas** e clique duas vezes no informativo ao qual deseja adicionar conteúdo ou editar. O informativo é aberto.

1. Se os componentes não estiverem visíveis, acesse a visualização Design e ative os componentes necessários (por exemplo, os componentes do Boletim informativo) antes de começar a editar.
1. Insira qualquer novo texto, imagens ou outros componentes, conforme apropriado. No exemplo do Geometrixx, 4 componentes estão disponíveis: Texto, Imagem, Cabeçalho e 2 Colunas. Seu informativo pode ter mais ou menos componentes, dependendo de como você o configurou.

   >[!NOTE]
   >
   >Personalize informativos usando variáveis. No boletim informativo Geometrixx, as variáveis estão disponíveis no componente de Texto. Os valores das variáveis são herdados das informações no perfil do usuário.

   ![Editando conteúdo do informativo](assets/mcm_newsletter_content.png)

1. Para inserir variáveis, selecione a variável na lista e clique em **Inserir**. As variáveis são preenchidas no Perfil.

## Personalizar informativos {#personalizing-newsletters}

Personalize informativos inserindo variáveis predefinidas no componente Texto dos informativos no Geometrixx. Os valores das variáveis são herdados das informações no perfil do usuário.

Também é possível simular como um boletim informativo é personalizado usando o contexto do cliente e carregando um perfil.

Para personalizar um informativo e simular como ele será:

1. No MCM, abra o informativo cujas configurações você deseja personalizar.

1. Abra o componente de Texto que deseja personalizar.

1. Coloque o cursor onde deseja que a variável apareça, selecione uma variável na lista suspensa e clique em **Inserir**. Faça isso para quantas variáveis forem necessárias e clique em **OK**.

   ![Adicionando variáveis](assets/mcm_newsletter_variables.png)

1. Para simular a aparência da variável quando enviada, pressione CTRL+ALT+c para abrir o contexto do cliente e selecione **Carregar**. Selecione o usuário da lista cujo perfil você deseja carregar e clique em **OK**.

   As informações do perfil carregado preencheram as variáveis.

   ![Testando variáveis](assets/mc_newsletter_testvariables.png)

## Testando informativos em diferentes clientes de e-mail {#testing-newsletters-in-different-e-mail-clients}

>[!NOTE]
>
>Antes de enviar informativos, verifique a configuração do OSGi para o Day CQ Link Externalizer em `https://localhost:4502/system/console/configMgr`.
>
>Por padrão, o valor do parâmetro é `localhost:4502` e a operação não pode ser concluída se a porta da instância em execução for alterada.

Alternar entre clientes de e-mail comuns para ver como o informativo será exibido para seus clientes em potencial. Por padrão, o informativo é aberto sem nenhum dos clientes de e-mail selecionados.

Atualmente, você pode exibir informativos nos seguintes clientes de e-mail:

* E-mail do Yahoo
* Gmail
* Hotmail
* Thunderbird
* Microsoft Outlook 2007
* E-mail do Apple

Para alternar entre clientes, clique no ícone correspondente para exibir o informativo nesse cliente de e-mail:

1. No MCM, abra o informativo cujas configurações você deseja personalizar.

1. Clique em um cliente de e-mail na barra superior para ver como o informativo seria exibido nesse cliente.

   ![Alternando clientes de email](assets/chlimage_1-119.png)

1. Repita esta etapa para qualquer cliente de e-mail adicional que desejar ver.

   ![Alterando clientes de email](assets/chlimage_1-120.png)

## Personalizar configurações do informativo {#customizing-newsletter-settings}

Embora somente usuários autorizados possam enviar informativos, você deve personalizar o seguinte:

* A linha de assunto, para que os usuários queiram abrir seu email e também para garantir que seu informativo não acabe marcado como spam.
* O endereço De, por exemplo, `noreply@geometrixx.com`, para que os usuários recebam emails de um endereço especificado.

Para personalizar as configurações do informativo:

1. No MCM, abra o informativo cujas configurações você deseja personalizar.

   ![Abrindo um informativo](assets/mcm_newsletter_open.png)

1. Na parte superior do informativo, clique em **Configurações**.

   ![Editando configurações do informativo](assets/mcm_newsletter_settings.png)
1. Digite o endereço de email **De**

1. Modifique o **Assunto** do email, se necessário.

1. Selecione uma **Lista Padrão de Destinatários** na lista suspensa.

1. Clique em **OK**.

   Ao testar ou enviar o informativo, os destinatários receberão e-mails com o endereço de e-mail e o assunto especificados.

## Boletins informativos de testes de voo {#flight-testing-newsletters}

Embora o teste de voo não seja obrigatório, antes de enviar um informativo, talvez você queira testá-lo para ter certeza de que ele aparece da maneira desejada.

O teste de voo permite fazer o seguinte:

* Examine o informativo em [todos os clientes pretendidos](#testing-newsletters-in-different-e-mail-clients).
* Verifique se o servidor de e-mail está configurado corretamente.
* Determine se seu email está sendo sinalizado como spam. (Certifique-se de incluir a si mesmo na lista de recipients.)

>[!NOTE]
>
>Se você atualizar provedores de email, fazer um teste de voo ou enviar um boletim informativo, essas operações falharão se o boletim informativo não for publicado primeiro na instância de publicação ou se a instância de publicação não estiver disponível. Publique seu informativo e certifique-se de que a instância de publicação esteja em execução.

Para enviar boletins informativos de testes de voo:

1. No MCM, abra o informativo que deseja testar e enviar.

1. Na parte superior do informativo, clique em **Testar** para testar antes de enviar.

   ![Configurações para testar um informativo](assets/mcm_newsletter_testsettings.png)

1. Insira o endereço de email de teste para onde deseja enviar o informativo e clique em **Enviar**. Se quiser alterar o perfil, carregue outro perfil no contexto do cliente. Para fazer isso, pressione CTRL+ALT+c e selecione Carregar e carregue um perfil.

## Envio de informativos {#sending-newsletters}

>[!NOTE]
>
>A Adobe não pretende aprimorar ainda mais o rastreamento de e-mails de rejeições/aberturas (não entregues) enviadas pelo serviço SMTP da AEM.
>A recomendação é usar o [Adobe Campaign e a integração com o AEM](/help/sites-administering/campaign.md).

Você pode enviar um informativo do informativo ou da lista. Ambos os procedimentos são descritos.

>[!NOTE]
>
>Antes de enviar informativos, verifique a configuração do OSGi para o Day CQ Link Externalizer em `https://localhost:4502/system/console/configMgr`.
>
>Por padrão, o valor do parâmetro é `localhost:4502` e a operação não pode ser concluída se a porta da instância em execução for alterada.

>[!NOTE]
>
>Se você atualizar provedores de email, fazer um teste de voo ou enviar um boletim informativo, essas operações falharão se o boletim informativo não for publicado primeiro na instância de publicação ou se a instância de publicação não estiver disponível. Publique seu informativo e certifique-se de que a instância de publicação esteja em execução.

### Envio de informativos de uma campanha {#sending-newsletters-from-a-campaign}

Para enviar um informativo de dentro da campanha:

1. No MCM, abra o informativo que deseja enviar.

   >[!NOTE]
   >
   >Antes de enviar, verifique se você personalizou o assunto do seu informativo e o endereço de email de origem [personalizando as configurações](#customizing-newsletter-settings).
   >
   >
   >[Teste de voo](#flight-testing-newsletters) recomenda-se enviar o informativo antes.

1. Na parte superior do informativo, clique em **Enviar**. O assistente do informativo é aberto.

1. Na lista de destinatários, selecione a lista que deseja receber o informativo e clique em **Avançar**.

   ![Enviando informativo](assets/mcm_newslettersend.png)

1. A conclusão da configuração foi confirmada. Clique em **Enviar** para enviar o informativo.

   ![O informativo enviou a confirmação](assets/mcm_newslettersendconfirm.png)

   >[!NOTE]
   >
   >Certifique-se de que você é um dos destinatários para garantir que o informativo foi recebido.

### Envio de informativos de uma lista {#sending-newsletters-from-a-list}

Para enviar um informativo de uma lista:

1. No MCM, clique em **Listas** no painel esquerdo.

   >[!NOTE]
   >
   >Antes de enviar, verifique se você personalizou o assunto do seu informativo e o endereço de email de origem [personalizando as configurações](#customizing-newsletter-settings). Não é possível testar um informativo se você o enviar da lista; você pode [testar o voo](#flight-testing-newsletters) se enviá-lo do informativo.

1. Marque a caixa de seleção ao lado da lista de clientes potenciais para os quais você deseja enviar um informativo.

1. No menu **Ferramentas**, selecione **Enviar informativo**. A janela **Enviar Informativo** é aberta.

   ![Console do informativo](assets/mcm_newslettersendfromlist.png)

1. No campo **Informativo**, selecione o informativo que deseja enviar e clique em **Avançar**.

   ![Caixa de diálogo Enviar informativo](assets/mcm_newslettersenddialog.png)

1. A conclusão da configuração foi confirmada. Clique em **Enviar** para enviar o informativo selecionado para a lista especificada de clientes potenciais.

   ![Enviar confirmação](assets/mcm_newslettersenddialog_confirmation.png)

   Seu informativo é enviado aos destinatários selecionados.

## Assinatura de um informativo {#subscribing-to-a-newsletter}

Esta seção descreve como assinar um boletim informativo.

### Assinatura de um informativo {#subscribing-to-a-newsletter-1}

Para assinar um boletim informativo (usando o site da Geometrixx como exemplo):

1. Clique em **Sites**, navegue até a **Barra de Ferramentas** do Geometrixx e abra-a.

   ![Amostra de assinatura](assets/chlimage_1-121.png)

1. No campo **Inscrever-se** do informativo da Geometrixx, digite seu endereço de email e clique em **Inscrever-se**. Agora você está inscrito no informativo.
