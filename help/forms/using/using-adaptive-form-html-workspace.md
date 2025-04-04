---
title: Uso de um formulário adaptável no HTML Workspace
description: Saiba como usar um Formulário adaptável no HTML Workspace que permite que os trabalhadores de campo acessem o formulário em seus dispositivos.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Workbench
role: User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 0%

---

# Uso de um formulário adaptável no HTML Workspace{#using-an-adaptive-form-in-html-workspace}

O AEM Forms no JEE fornece a capacidade de usar um formulário adaptável no HTML Workspace.

Como é possível selecionar um XDP durante o design do processo, a capacidade de navegar de um repositório existente de AEM de formulário adaptável foi adicionada. O recurso oferece ao Process Designer a capacidade de configurar um formulário adaptável no Ponto inicial e na Tarefa.

## Experiência de design de processos {#process-design-experience}

Execute o seguinte para ativar os formulários adaptáveis a serem usados no design do processo:

* Em Atribuir tarefa e ponto inicial, você pode navegar para um ativo de formulário adaptável no repositório do CRX ao atribuir um ativo de formulário a uma tarefa.
* Na folha de propriedades Atribuir Tarefa/Bancada do Ponto Inicial, você pode ocultar a barra de ferramentas de nível superior/global de um formulário adaptável.
* Você pode usar novos perfis de Ação para Renderizar e Enviar ações em formulários adaptáveis.

### Exportação e importação do aplicativo LiveCycle {#livecycle-application-export-and-import}

Como os formulários adaptáveis estão no repositório do AEM, a exportação do aplicativo LiveCycle contém somente as referências aos formulários adaptáveis usados. Portanto, a exportação e a importação do aplicativo LiveCycle são um processo de duas etapas. O aplicativo LiveCycle inclui definições de processo, e assim por diante. Um pacote separado contendo formulários adaptáveis é exportado como um arquivo ZIP do AEM. Durante a importação, o aplicativo LiveCycle é importado por meio do Workbench e os formulários adaptáveis são importados por meio do AEM.

## Experiência do usuário de formulários adaptáveis no HTML Workspace {#user-experience-of-adaptive-form-in-html-workspace}

O HTML Workspace fornece alguns controles específicos para formulários adaptáveis, além dos controles disponíveis para formulários móveis. Um usuário pode adicionar anexos, salvar, assinar, enviar e navegar pelos formulários adaptáveis no HTML Workspace quando abrir uma Tarefa ou Ponto de início. Veja a seguir as especificidades:

1. Para anexar arquivos, use Anexos de tarefa, como no Mobile Forms. Qualquer botão do tipo Anexo de arquivo do formulário adaptável está oculto.

1. Para salvar um formulário adaptável, clique em **Salvar**, como no Mobile Forms. Qualquer botão Salvar tipo de formulário adaptável fica oculto.

1. Para enviar um formulário adaptável, use o botão **Enviar** ou encaminhe as ações disponíveis, como no Mobile Forms. Qualquer botão Enviar tipo de formulário adaptável fica oculto.

1. **Visibilidade da barra de ferramentas global do formulário adaptável**: se Processar Designer ocultar a barra de ferramentas global/de nível superior, a barra de ferramentas e os botões não aparecerão nos formulários adaptáveis.

1. **Controles de navegação do Workspace para o Adaptive Forms**: os botões Próximo/Anterior estão disponíveis junto com os botões Salvar, Enviar e Rotear Ação para um formulário adaptável no HTML Workspace. Clique em Botões Avançar/Anterior para navegar pelos painéis de formulários adaptáveis no HTML Workspace. Os botões Próximo/Anterior fornecem navegação profunda, semelhante aos controles de navegação na exibição Móvel de formulários adaptáveis.

1. **Serviços eSign e Componente de Resumo do Formulário Adaptável**: o componente de Resumo não está operacional no HTML Workspace. Em outras palavras, se um formulário adaptável tiver um componente Resumo, ele não estará visível no espaço de trabalho. Em vez de Enviar automaticamente no componente E-sign, o usuário do espaço de trabalho clica na ação Enviar ou em uma ação de rota no HTML Workspace. Depois que um documento é assinado, ele fica visível como um documento simples assinado. Clique em **Enviar** ou em uma ação de rota para que você possa fechar/concluir a tarefa ou o Ponto de Início.\
   O documento assinado é coletado do servidor de serviços do eSign e o arquivo xml de dados é encaminhado para a próxima etapa do processo.

## Etapas para usar formulários adaptáveis no design do processo {#steps-to-use-adaptive-forms-in-process-design}

1. Abra o Adobe Experience Manager Forms Workbench.

1. Vá para **Arquivo > Novo > Aplicativo** ou use o aplicativo existente para criar um aplicativo.

   ![Criar novo aplicativo](assets/create_new_appl.png)

   Criar aplicativo

1. Crie um processo ou use um processo existente no aplicativo.

   ![Criar novo processo](assets/create_new_process.png)

   Criar processo

1. Crie um Ponto de Início ou Atribuir Tarefa e clique duas vezes nele.
1. Na seção **[!UICONTROL Apresentação e dados]**, selecione **[!UICONTROL usar um ativo do CRX]** e clique nas reticências antes do ativo.

   ![Usar um ativo do CRX](assets/use_crx_asset.png)

   Usar um ativo do CRX

1. Selecione o formulário adaptável criado por meio da interface do usuário Gerenciar Assets e clique em **[!UICONTROL OK]**.

   ![Selecione um formulário adaptável](assets/selecting_form.png)

   Selecione um formulário adaptável

   >[!NOTE]
   >
   >Para obter detalhes sobre como criar um formulário adaptável, consulte [Criação de um formulário adaptável](../../forms/using/creating-adaptive-form.md).
   >
   >
   >Para obter detalhes sobre como criar um processo, consulte [Criação e gerenciamento de processos](https://help.adobe.com/en_US/AEMForms/6.1/WorkbenchHelp/WS92d06802c76abadb-1cc35bda128261a20dd-7ff7.2.html).
