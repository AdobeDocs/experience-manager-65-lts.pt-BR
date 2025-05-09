---
title: Uso do salvamento automático no aplicativo AEM Forms
description: Saiba como usar o recurso de salvamento automático no aplicativo AEM Forms que permite evitar perda de dados.
contentOwner: sashanka
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
docset: aem65
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Uso do salvamento automático no aplicativo AEM Forms{#using-autosave-in-aem-forms-app}

Quando um usuário insere dados no aplicativo Adobe Experience Manager Forms, o recurso de salvamento automático os salva em intervalos regulares. O recurso de salvamento automático no aplicativo AEM Forms ajuda a evitar a perda de dados se o aplicativo for fechado acidentalmente.

Seu aplicativo pode fechar acidentalmente:

* Se o dispositivo for desligado devido à bateria fraca
* Se o usuário matar o aplicativo
* Se ocorrer uma falha inesperada

Você pode especificar os intervalos após os quais o aplicativo salva os dados inseridos.

>[!NOTE]
>
>Selecione a frequência de salvamento automático criteriosamente. Operações frequentes de salvamento automático podem ter um impacto notável no desempenho do dispositivo.

Execute as seguintes etapas para usar o recurso de salvamento automático no aplicativo AEM Forms:

1. Faça logon no aplicativo e navegue até **Configurações > Geral**.
1. Na tela Geral, use a opção **Frequência de salvamento automático** para selecionar os intervalos em que deseja que o aplicativo salve os dados inseridos.
   [![Definindo frequência de salvamento automático](assets/using-autosave-freq-07.png)](assets/using-autosave-freq-07-1.png)

1. Ao reiniciar o aplicativo e fazer logon com o mesmo usuário, você será solicitado a restaurar a tarefa com a caixa de diálogo Recuperar tarefa não salva. Clique em **OK** na caixa de diálogo Recuperar tarefa não salva para continuar a trabalhar com a tarefa salva. Você pode clicar em **Cancelar** para excluir os dados salvos correspondentes ao último salvamento automático acionado e começar a trabalhar com uma nova tarefa.

   Ao clicar em **OK**, a tarefa é restaurada com os dados correspondentes ao salvamento automático mais recente acionados antes da falha do aplicativo. Inclui os dados de formulário e todos os anexos associados à tarefa.
   [![Recuperando uma tarefa ](assets/autosave-flow.png)](assets/using-autosave-freq-06.png)**A.** Um formulário de trabalho em andamento **B.** Aplicativo fechado à força **C.** Aplicativo reiniciado com caixa de diálogo Recuperar Tarefa Não Salva **D.** Formulário restaurado com dados originais
