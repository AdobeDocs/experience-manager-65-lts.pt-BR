---
title: Personalizando a página de detalhes da tarefa
description: Como personalizar a página de detalhes da tarefa no espaço de trabalho do AEM Forms para modificar as informações padrão exibidas sobre uma tarefa.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Personalizando a página de detalhes da tarefa {#customizing-the-task-details-page}

A página de detalhes da tarefa contém informações sobre uma tarefa e seus processos. No entanto, você pode personalizar a página de detalhes da tarefa para adicionar ou excluir informações.

Você pode adicionar as seguintes informações à página de detalhes da tarefa:

* Informações disponíveis no objeto JSON de uma tarefa (seção Tarefa em [Descrição de Objeto JSON do espaço de trabalho do AEM Forms](/help/forms/using/html-workspace-json-object-description.md))
* Informações disponíveis no objeto JSON de uma instância do processo (seção Instância do processo na [Descrição do objeto JSON do espaço de trabalho do AEM Forms](/help/forms/using/html-workspace-json-object-description.md))

Para personalizar a página de detalhes da tarefa:

1. Siga [Etapas genéricas para personalização do espaço de trabalho do AEM Forms.](/help/forms/using/generic-steps-html-workspace-customization.md)
1. Para mostrar mais informações, adicione os pares de valores chave correspondentes ao arquivo `translation.json` em `todo`bloco > `details`bloco > `app`bloco > [`required`bloco].

   O [`required`bloco] se refere aos blocos disponíveis, como o bloco de tarefas para informações de tarefas, o bloco de processos para informações de processos e o bloco de tarefas pendentes atual para informações de tarefas pendentes.

   Por exemplo, para adicionar informações sobre Seleção de Rota Necessária na página de detalhes da tarefa, você pode adicionar o seguinte par de valores-chave no bloco de tarefas:

   ```json
   "todo" : {
       .
       .
       .
       "details" : {
           .
           .
           "task" : {
               .
               .
               "RouteSelectionRequired" : "Route Selection Required"
           }
       }
   }
   ```

   >[!NOTE]
   >
   >Adicione pares de valores chave correspondentes para todos os idiomas compatíveis.

1. Copiar `/libs/ws/js/runtime/templates/taskdetails.html` para `/apps/ws/js/runtime/templates/taskdetails.html`.

   Adicionar as novas informações a `/apps/ws/js/runtime/templates/taskdetails.html`. Por exemplo:

   ```css
   <div class="detailsContainer">
       .
       .
       <ul>
           .
           .
           <li>
               <label for="routeSelectionRequired" title="<%= $.t('todo.details.task.RouteSelectionRequired')%>"><%= $.t('todo.details.task.RouteSelectionRequired')%></label>
               <div>
                   <span id="routeSelectionRequired"><%= isRouteSelectionRequired != null ? isRouteSelectionRequired : ''%></span>
               </div>
           </li>
           .
           .
       </ul>
   </div>
   ```

1. Abra /apps/ws/js/registry.js para edição.

   Pesquisar e substituir `text!/lc/libs/ws/js/runtime/templates/taskdetails.html` por `text!/lc/apps/ws/js/runtime/templates/taskdetails.html`.

>[!NOTE]
>
>Para personalizar a página de detalhes da tarefa com tarefas criadas na guia **Iniciar Processo** do espaço de trabalho do AEM Forms, adicione as novas informações a `/apps/ws/js/runtime/templates/startprocess.html`.
>
>Para adicionar novos estilos às informações adicionadas na página de detalhes, modifique o arquivo CSS usando a seção *Alterações na interface do usuário* em [Personalização do Workspace](changing-locale-user-interface.md).
