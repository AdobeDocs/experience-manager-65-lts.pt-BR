---
title: Expurgar registros do banco de dados do Gerenciador de Jobs
description: Dados de processos grandes podem resultar em menor desempenho dos formulários AEM. É uma boa prática limpar os dados do processo quando os registros não são mais necessários.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: 92609575368de96d07ce7f67fef4301fa838213e
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 0%

---

# Expurgar registros do banco de dados do Gerenciador de Jobs {#purge-records-from-the-job-manager-database}

>[!NOTE]
> 
> Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

Os dados de processo gerados quando um processo de longa duração é chamado podem se tornar muito grandes, resultando em menor desempenho dos formulários AEM e no uso de espaço em disco desnecessário. É uma boa prática limpar os dados do processo quando os registros não são mais necessários.

Você pode usar a console de administração para executar uma expurgação única de registros obsoletos ou para programar expurgações automáticas regulares. Outros métodos para limpar registros obsoletos são discutidos em [Limpando dados do processo](/help/forms/using/admin-help/purging-process-data.md#purging-process-data).

**Acessar a página Agendador de Limpeza de Trabalho**

1. No Console de administração, clique em Monitor de integridade no canto superior direito da página.
1. Clique na guia Agendador de Expurgação de Job.

As informações sobre expurgações programadas no momento são exibidas na caixa Informações do Agendador de Expurgação de Job.

>[!NOTE]
>
>Clicar em Interromper Scheduler interrompe todas as expurgações programadas no futuro, mas não interrompe um job de expurgação que já esteja em andamento.

**Agendar uma limpeza única**

1. Selecione Somente Uma Vez.
1. Na área Filtro de Registros de Expurgação Concluída, especifique o número de dias ou semanas após os quais um registro será considerado obsoleto e pronto para expurgação.

   >[!NOTE]
   >
   >Os registros relacionados a processos que não foram concluídos não serão removidos, mesmo se forem mais antigos que a idade especificada.

1. Especifique quando a limpeza ocorrerá. Marque a caixa de seleção Usar data e hora atuais ou desmarque a caixa de seleção e clique nos ícones de calendário e relógio para especificar a data e a hora em que a limpeza será realizada.

   >[!NOTE]
   >
   >Se você especificar uma data e hora iniciais que estejam no passado, a expurgação ocorrerá imediatamente quando você clicar em Iniciar Scheduler.

1. Clique em Iniciar Scheduler. Todas as configurações do scheduler previamente agendadas são substituídas pelas novas configurações.

**Configurar um agendamento de limpeza automática**

1. Selecione Repetir a Cada e especifique o número de dias ou semanas entre expurgações.
1. Na área Filtro de Registros de Expurgação Concluída, especifique o número de dias ou semanas após os quais um registro será considerado obsoleto e pronto para expurgação. Você não pode definir o valor como `0`.

   >[!NOTE]
   >
   >Os registros relacionados a processos que não foram concluídos não serão removidos, mesmo se forem mais antigos que a idade especificada.

1. Especifique quando as limpezas começarão. Marque a caixa de seleção Usar data e hora atuais ou desmarque a caixa de seleção e clique nos ícones de calendário e relógio para especificar a data e a hora em que a limpeza será realizada.

   >[!NOTE]
   >
   >Se você especificar uma data e hora de início que esteja no passado, o AEM Forms calculará a próxima data de início lógica com base na data especificada. Por exemplo, se você programar que as expurgações de job ocorram semanalmente a partir de 7 de abril e agora for 9 de abril, a primeira expurgação ocorrerá em 14 de abril.

1. Clique em Iniciar Scheduler. Todas as configurações do scheduler previamente agendadas são substituídas pelas novas configurações.
