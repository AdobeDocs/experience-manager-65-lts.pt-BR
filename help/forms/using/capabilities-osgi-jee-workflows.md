---
title: Ações e recursos de workflows do AEM centrados em formulários em workflows OSGi e AEM Forms JEE
description: Ações e recursos de workflows do AEM centrados em formulários em workflows OSGi e AEM Forms JEE
contentOwner: khsingh
solution: Experience Manager, Experience Manager Forms
hide: true
hidefromtoc: true
feature: Adaptive Forms,AEM Forms on OSGi
role: User, Developer
exl-id: d0f54236-5dc2-4c64-87c5-85e5e85e8cf7
source-git-commit: 060bb23d64a90f0b2da487ead4c672cbf471c9a8
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 20%

---

# Ações e recursos de workflows do AEM centrados em formulários em workflows OSGi e AEM Forms JEE {#actions-and-capabilities-of-form-centric-aem-workflows-on-osgi-and-aem-forms-jee-workflows}

## Caixa de entrada do AEM e HTML Workspace {#aem-inbox-and-html-workspace}

Você pode usar a Caixa de entrada do AEM para executar e monitorar fluxos de trabalho do AEM centrados na Forms no OSGi. Por outro lado, o HTML Workspace permite executar e monitorar Workflows do AEM Forms JEE. A tabela a seguir ajuda você a entender várias ações importantes disponíveis na Caixa de entrada do AEM para fluxos de trabalho do AEM centrados no Forms no OSGi e no HTML Workspace para fluxos de trabalho do AEM Forms JEE.

<table>
 <tbody>
  <tr>
   <td>Ações</td>
   <td>Caixa de entrada AEM</td>
   <td>HTML Workspace</td>
  </tr>
  <tr>
   <td>Iniciando um processo, tarefa ou aplicativo de formulário<br /> </td>
   <td>Com suporte<br /> </td>
   <td>Com suporte<br /> </td>
  </tr>
  <tr>
   <td>Envio de tarefas</td>
   <td>Com suporte<br /> </td>
   <td>Com suporte<br /> </td>
  </tr>
  <tr>
   <td>Atribuir uma tarefa a um grupo</td>
   <td>Com suporte<br /> </td>
   <td>Com suporte<br /> </td>
  </tr>
  <tr>
   <td>Enviando para vários roteiros</td>
   <td>Com suporte<br /> </td>
   <td>Com suporte<br /> </td>
  </tr>
  <tr>
   <td>Rastreamento do histórico e do resumo das tarefas</td>
   <td>Com suporte<br /> </td>
   <td>Com suporte<br /> </td>
  </tr>
  <tr>
   <td>Notificações por email</td>
   <td>Com suporte<br /> </td>
   <td>Com suporte<br /> </td>
  </tr>
  <tr>
   <td>Reatribuindo tarefas</td>
   <td>Compatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Anexos de nível de campo para formulários adaptáveis</td>
   <td>Compatível</td>
   <td>Incompatível</td>
  </tr>
  <tr>
   <td>Exibição de calendário</td>
   <td>Compatível</td>
   <td>Incompatível</td>
  </tr>
  <tr>
   <td>Comentários no nível da tarefa</td>
   <td>Compatível</td>
   <td>Incompatível</td>
  </tr>
  <tr>
   <td>Filas (fila pessoal compartilhada, tarefas de reclamação da fila)</td>
   <td>Compatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Notificação de ausência temporária</td>
   <td>Compatível</td>
   <td>Compatível</td>
  </tr>
    <tr>
   <td>Personalização de elementos da interface</td>
   <td>Compatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Atribuir uma tarefa a vários usuários</td>
   <td>Incompatível</td>
   <td>Compatível</td>
  </tr>
 </tbody>
</table>

## Fluxos de trabalho do AEM centrados em formulários em fluxos de trabalho OSGi e AEM Forms JEE {#form-centric-aem-workflows-on-osgi-and-aem-forms-jee-workflows}

Os fluxos de trabalho do AEM centrados em formulários no OSGi e os fluxos de trabalho do AEM Forms JEE (AEM Forms no Gerenciamento de processos do JEE) têm um conjunto diferente de recursos. A tabela a seguir ajuda você a entender recursos importantes disponíveis em Workflows do AEM centrados em formulário no OSGi e em Workflows do AEM Forms no JEE:

<table>
 <tbody>
  <tr>
   <td>Recursos</td>
   <td>Fluxos de trabalho do AEM centrados em formulário no OSGi<br /> </td>
   <td>Fluxos de trabalho do AEM Forms JEE</td>
  </tr>
  <tr>
   <td>Formulários adaptáveis</td>
   <td>Compatível</td>
   <td>Com suporte<br /> </td>
  </tr>
  <tr>
   <td>Integração com outras soluções da AEM</td>
   <td>Compatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Rabiscar a assinatura</td>
   <td>Compatível</td>
   <td>Com suporte<br /> </td>
  </tr>
  <tr>
   <td>Modelos de email personalizados</td>
   <td>Compatível</td>
   <td>Com suporte<br /> </td>
  </tr>
  <tr>
   <td>Definindo a prioridade da tarefa</td>
   <td>Compatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Tempo limite de uma tarefa após a data de vencimento</td>
   <td>Compatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Loops no fluxo de trabalho</td>
   <td>Compatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Escolher dinamicamente um destinatário </td>
   <td>Compatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Uso de metadados personalizados</td>
   <td>Compatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Assinatura eletrônica (Adobe Sign)</td>
   <td>Com suporte <sup>[1]</sup></td>
   <td>Suportado <sup>[5]</sup></td>
  </tr>
  <tr>
   <td>Gerenciar aplicativos de formulários e tarefas</td>
   <td>Com suporte <sup>[2]</sup><br /> </td>
   <td>Com suporte <sup>[2]</sup></td>
  </tr>
  <tr>
   <td>Serviços de documento</td>
   <td>Suportado <sup>[3]</sup></td>
   <td>Suportado <sup>[3]</sup></td>
  </tr>
  <tr>
   <td>Renderizar tarefa concluída como formulário adaptável ou documento do PDF</td>
   <td>Compatível</td>
   <td>Suportado [4]</td>
  </tr>
  <tr>
   <td>Integração com o Gerenciamento de correspondência</td>
   <td>Compatível</td>
   <td>Compatível</td>
  </tr>
   <tr>
   <td>Gateways, SEM ESPERA </td>
   <td>Compatível</td>
   <td>Compatível</td>
  </tr>
   <tr>
   <td>Variáveis para armazenar dados </td>
   <td>Compatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>OU E dividir</td>
   <td>Compatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Avatar do usuário</td>
   <td>Compatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Enviar um email ao final do fluxo de trabalho</td>
   <td>Suportado <sup>[7]</sup></td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Chamar um serviço Web a partir de um fluxo de trabalho</td>
   <td>Compatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Assinatura digital</td>
   <td>Com suporte<br /> </td>
   <td>Com suporte<br /> </td>
  </tr>
  <tr>
   <td>Botão de redefinição</td>
   <td>Compatível</td>
   <td>Incompatível</td>
  </tr>
  <tr>
   <td>Estágios do fluxo de trabalho</td>
   <td>Compatível</td>
   <td>Incompatível</td>
  </tr>
  <tr>
   <td>Formulários adaptáveis somente leitura</td>
   <td>Compatível</td>
   <td>Incompatível</td>
  </tr>
  <tr>
   <td>Ocultando o botão de salvamento padrão</td>
   <td>Compatível</td>
   <td>Incompatível</td>
  </tr>
  <tr>
   <td>Controle granular da seção de detalhes do fluxo de trabalho</td>
   <td>Compatível</td>
   <td>Incompatível</td>
  </tr>
  <tr>
   <td>Serviço de pesquisa/agendamento</td>
   <td>Disponível imediatamente</td>
   <td>É necessária uma implementação personalizada</td>
  </tr>
  <tr>
   <td>Aplicativo Forms adaptável</td>
   <td>Compatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Serviço de Assembler</td>
   <td>Compatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Serviço PDF Generator</td>
   <td>Compatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Serviço do Forms</td>
   <td>Compatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Serviço de saída</td>
   <td>Compatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Assurance do documento</td>
   <td>Compatível</td>
   <td>Compatível </td>
  </tr>
  <tr>
   <td>Executar script</td>
   <td>Compatível com ECMAScript</td>
   <td>Suporta trechos de código Java</td>
  </tr>
  <tr>
   <td>Assembler</td>
   <td>Compatível</td>
   <td>Compatível</td>
  </tr>  
  <tr>
   <td>HTML5 Forms, PDF forms interativo, Conjunto de formulários</td>
   <td>Incompatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Relatório de processo</td>
   <td>Incompatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Assinatura digital</td>
   <td>Compatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Categorias de ponto inicial</td>
   <td>Incompatível </td>
   <td>Compatível </td>
  </tr>
  <tr>
   <td>Aprovação de tarefas em massa </td>
   <td>Incompatível </td>
   <td>Compatível </td>
  </tr>
  <tr>
   <td>Salvar rascunho com um nome personalizado</td>
   <td>Incompatível </td>
   <td>Compatível </td>
  </tr>
  <tr>
   <td>Iniciar um processo com dados de processo existentes<br /> </td>
   <td>Incompatível</td>
   <td>Compatível </td>
  </tr>
  <tr>
   <td>Salvar um ponto de partida como rascunho</td>
   <td>Incompatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Visualização do gerente</td>
   <td>Incompatível</td>
   <td>Com suporte<br /> </td>
  </tr>
  <tr>
   <td>Pesquisar modelos</td>
   <td>Incompatível</td>
   <td>Com suporte<br /> </td>
  </tr>
  <tr>
   <td>Integração com aplicativos de terceiros</td>
   <td>Sem Suporte <sup>[6]</sup></td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Anexos de nível de tarefa para aplicativo de fluxo de trabalho ou ponto inicial</td>
   <td>Incompatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Email de lembrete</td>
   <td>Incompatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Alterar título no tempo limite da tarefa</td>
   <td>Incompatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Enviar email sobre delegação de tarefas e declaração de tarefa</td>
   <td>Incompatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Delegar entre grupos separados</td>
   <td>Incompatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Transformação XSLT</td>
   <td>Incompatível</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td>Prioridade de tarefa dinâmica</td>
   <td>Incompatível</td>
   <td>Incompatível</td>
  </tr>
  <tr>
   <td>Título dinâmico</td>
   <td>Incompatível</td>
   <td>Incompatível</td>
  </tr>
    <tr>
   <td>Descrição dinâmica</td>
   <td>Incompatível</td>
   <td>Incompatível</td>
  </tr>
 </tbody>
</table>

1. Você pode usar Workflows da AEM centrados em formulários no OSGi para assinar um formulário adaptável preenchido. Workflows da AEM centrados em formulários no OSGi são compatíveis com a assinatura fora do formulário. A experiência de [assinatura no formulário](../../forms/using/working-with-adobe-sign.md#create-in-form-signing-experience) não é suportada.

1. Você precisa de acesso à Caixa de entrada do AEM para executar e monitorar fluxos de trabalho centrados em formulários no AEM Forms OSGi e no HTML Workspace para executar e monitorar fluxos de trabalho do AEM Forms JEE.
1. Os serviços de documento nativos do AEM Forms estão disponíveis para fluxos de trabalho do AEM centrados em formulário no OSGi e para fluxos de trabalho do AEM Forms no JEE. O fluxo de trabalho do AEM usa serviços de documento nativos para fluxos de trabalho do AEM centrados em formulários em fluxos de trabalho OSGi e AEM Forms JEE (Gerenciamento de processos).
1. Os fluxos de trabalho do AEM Forms JEE só podem renderizar um formulário adaptável. Não há suporte para a renderização de um formulário adaptável como um documento do PDF.
1. Os fluxos de trabalho do AEM Forms JEE não têm uma etapa separada para o Adobe Sign. Você precisa de um formulário adaptável habilitado para o Adobe Sign para os Workflows JEE de formulários do AEM. Para obter mais detalhes, consulte [Documentação do Adobe Sign](../../forms/using/working-with-adobe-sign.md#add-and-configure-the-signature-step-component).
1. Você pode usar a etapa [Invocar Serviço de Modelo de Dados de Formulário](../../forms/using/aem-forms-workflow-step-reference.md#p-invoke-form-data-model-service-step-p) para invocar um serviço Web e postar ou recuperar dados de um aplicativo de terceiros.
1. Você pode usar a etapa [Enviar Email](../../forms/using/aem-forms-workflow-step-reference.md#send-email-step) para enviar emails.

## Diferenças entre a Caixa de entrada do AEM e os recursos do aplicativo AEM Forms {#differences-between-aem-inbox-and-aem-forms-app-features}

Duas das principais maneiras de iniciar um fluxo de trabalho centrado no Forms são usando a [Caixa de Entrada do AEM](../../forms/using/manage-applications-inbox.md) e o aplicativo AEM Forms. No entanto, os recursos da Caixa de entrada do AEM e do aplicativo AEM Forms são diferentes. A Caixa de entrada do AEM funciona somente com [fluxos de trabalho centrados no Forms](../../forms/using/aem-forms-workflow.md), enquanto o aplicativo AEM Forms funciona com fluxos de trabalho centrados no Forms e gerenciamento de processos.

A tabela a seguir lista os recursos da Caixa de entrada do AEM e do aplicativo AEM Forms:

<table>
 <tbody>
  <tr>
   <td><p><strong>Ações</strong></p> </td>
   <td><p><strong>Caixa de entrada AEM</strong></p> </td>
   <td><p><strong>Aplicativo AEM Forms</strong></p> </td>
  </tr>
  <tr>
   <td><p>Iniciando um aplicativo de formulário</p> </td>
   <td><p>Compatível</p> </td>
   <td><p>Compatível</p> </td>
  </tr>
  <tr>
   <td><p>Envio de tarefas</p> </td>
   <td><p>Compatível</p> </td>
   <td><p>Compatível</p> </td>
  </tr>
  <tr>
   <td><p>Delegar tarefas</p> </td>
   <td><p>Compatível</p> </td>
   <td><p>Incompatível</p> </td>
  </tr>
  <tr>
   <td><p>Rastreamento do histórico e do resumo das tarefas</p> </td>
   <td><p>Compatível</p> </td>
   <td><p>Incompatível</p> </td>
  </tr>
  <tr>
   <td><p>Adicionando anexos no nível da tarefa</p> </td>
   <td><p>Compatível</p> </td>
   <td><p>Compatível</p> </td>
  </tr>
  <tr>
   <td><p>Exibindo anexos no nível da tarefa</p> </td>
   <td><p>Compatível</p> </td>
   <td><p>Compatível</p> </td>
  </tr>
  <tr>
   <td><p>Adição de anexos em nível de campo</p> </td>
   <td><p>Compatível</p> </td>
   <td><p>Compatível</p> </td>
  </tr>
  <tr>
   <td><p>Exibição da exibição de calendário</p> </td>
   <td><p>Compatível</p> </td>
   <td><p>Incompatível</p> </td>
  </tr>
  <tr>
   <td><p>Adição de comentários</p> </td>
   <td><p>Compatível</p> </td>
   <td><p>Compatível</p> </td>
  </tr>
 </tbody>
</table>
