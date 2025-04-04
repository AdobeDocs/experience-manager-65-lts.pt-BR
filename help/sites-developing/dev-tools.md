---
title: Ferramentas de desenvolvimento
description: Para desenvolver aplicativos JCR, Apache Sling ou Adobe Experience Manager, vários conjuntos de ferramentas estão disponíveis.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing,Developer Tools
role: Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 2%

---

# Ferramentas de desenvolvimento{#development-tools}

Para desenvolver aplicativos JCR, Apache Sling ou Adobe Experience Manager (AEM), os seguintes conjuntos de ferramentas estão disponíveis:

* um conjunto formado por [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) e WebDAV. O CRXDE Lite está incorporado ao CRX/AEM e permite executar tarefas de desenvolvimento padrão no navegador. Com o CRXDE Lite, você pode criar e editar arquivos (como .jsp e .java), pastas, modelos, componentes, caixas de diálogo, nós, propriedades e pacotes, ao fazer logon e integrar com o SVN.

  O CRXDE Lite é recomendado quando você não tem acesso direto ao servidor CRX/AEM, quando desenvolve um aplicativo estendendo ou modificando os componentes prontos para uso e pacotes Java™ ou quando não precisa de um depurador dedicado, autocompletar de código e realce de sintaxe.

* Um conjunto constituído pelo seguinte:
   * Um ambiente de desenvolvimento integrado. Por exemplo, [Eclipse](/help/sites-developing/howto-projects-eclipse.md) ou [IntelliJ](/help/sites-developing/ht-intellij.md).
   * Uma ferramenta de criação. Por exemplo, [Apache Maven](/help/sites-developing/ht-projects-maven.md).
   * FileVault, que foi desenvolvido pela Adobe para mapear um repositório em um sistema de arquivos, um sistema de controle de versão. Por exemplo, Subversion.
   * Um sistema de rastreio de erros. Por exemplo, Jira.
   * Um sistema central de gerenciamento de dependências. Por exemplo, Apache Archiva.
   * E um sistema de automação de construção. Por exemplo, Apache Continuum.

  Essa configuração permite integrar totalmente o aplicativo (conteúdo, código, configuração) em qualquer ambiente e processo de desenvolvimento. O link entre os diferentes elementos é a representação do repositório no sistema de arquivos por meio do FileVault, já que todas as ferramentas de desenvolvimento mencionadas anteriormente podem funcionar com arquivos.

## Extensões para ambientes de desenvolvimento integrados {#extensions-for-integrated-development-environments}

A Adobe lançou as seguintes extensões:

* [Extensão do AEM Eclipse](/help/sites-developing/aem-eclipse.md)
* [Extensão AEM Brackets](/help/sites-developing/aem-brackets.md)

### Outras ferramentas {#other-tools}

O AEM é fornecido com outras ferramentas que facilitam o desenvolvimento:

* [Editor de caixa de diálogo](/help/sites-developing/dialog-editor.md)
* [Usar o Translator para gerenciar dicionários](/help/sites-developing/i18n-translator.md)
* [Gerenciamento de pacotes usando o Maven](/help/sites-developing/vlt-mavenplugin.md)
* [Como desenvolver projetos do AEM usando o Eclipse](/help/sites-developing/howto-projects-eclipse.md)
* [Como criar projetos do AEM usando o Apache Maven](/help/sites-developing/ht-projects-maven.md)
* [Como desenvolver projetos do AEM usando o IntelliJ IDEA](/help/sites-developing/ht-intellij.md)
* [Como usar a ferramenta VLT](/help/sites-developing/ht-vlttool.md)
* [Como usar a ferramenta Servidor proxy](/help/sites-developing/ht-proxy-server.md)
* [Ferramentas de Modernização do AEM](/help/sites-developing/modernization-tools.md)
* [Ferramenta AEM Repo](/help/sites-developing/aem-repo-tool.md)

Ferramentas que facilitam a criação de novos projetos:

* [Arquétipo de projeto do AEM](https://github.com/adobe/aem-project-archetype)
* [Modelos de AEM Lazybones](https://github.com/Adobe-Consulting-Services/lazybones-aem-templates)

>[!NOTE]
>
>O tutorial a seguir pode ser de interesse para iniciar um novo projeto do AEM:
>[Introdução ao AEM Sites Parte 1 - Configuração do projeto](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part1.html)
