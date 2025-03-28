---
title: Introdução ao Process Reporting
description: Introdução e principais recursos do AEM Forms no JEE Process Reporting
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 755df7e2-3603-4c0d-ad07-ec6f27de8c64
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Introdução ao Process Reporting{#introduction-to-process-reporting}

![relatório-processo](assets/process-reporting.png)

Relatórios de processos é uma ferramenta baseada em navegador usada para criar e exibir relatórios sobre processos e tarefas do AEM Forms.

O Process Reporting fornece um conjunto de relatórios prontos para uso que permitem filtrar, exibir informações sobre processos de longa execução, duração do processo e volume do fluxo de trabalho.

Além disso, o Process Reporting fornece uma interface para executar consultas adhoc e integrar exibições de relatórios personalizadas à interface do usuário do Process Reporting.

Para obter a lista de navegadores compatíveis, consulte [Plataformas compatíveis com AEM Forms](/help/sites-deploying/technical-requirements.md)

O Process Reporting é construído em módulos que:

* Ler dados do processo do Banco de Dados do AEM Forms
* Publicar dados do processo em um repositório incorporado do Process Reporting
* Fornece uma interface de usuário baseada em navegador para exibir relatórios

## Principais recursos {#key-capabilities}

### Relatório sempre ativo {#always-on-reporting}

![gerenciamento de sites](assets/site-management.png)

Visualize a lista de processos de longa execução, gráficos de duração do processo e executar consultas personalizadas usando filtros.

Process Reporting também oferece a opção de exportar o relatório e consultar dados no formato CSV.

### Relatórios Ad Hoc {#adhoc-reports}

![impressão-&amp;-cor](assets/print-&-colour.png)

Use filtros para obter uma visualização específica dos seus dados.

Você pode pesquisar processos ou tarefas por ID, duração, datas de início e término, iniciador do processo e assim por diante.

É possível combinar vários filtros para criar relatórios específicos.

É possível salvar os filtros de relatório para execução em uma data ou hora posterior.

### Histórico de Processos/Tarefas {#process-task-history}

![gerenciamento de arquivos](assets/file-management.png)

Os servidores da AEM Forms executam vários processos em paralelo. Esses processos continuam em transição de um estado para outro. Ao publicar dados do Forms no repositório do Process Reporting em intervalos regulares, o Process Reporting retém as informações de transição sobre os processos em execução no AEM Forms.

### Controle de acesso {#access-control-br}

![sem título](assets/untitled.png)

O Process Reporting fornece acesso baseado em permissão à interface do usuário.

Isso significa que somente os usuários com permissões de relatório têm acesso à interface do usuário do Process Reporting.
