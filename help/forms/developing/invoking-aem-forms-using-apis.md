---
title: Como chamar o AEM Forms usando APIs?
description: Saiba como chamar serviços da AEM Forms usando uma API Java&trade;, serviços da Web, Comunicação remota e REST.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: coding, development-tools
role: Developer
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
hide: true
hidefromtoc: true
exl-id: 8cf0c8ca-12ea-4094-97a6-1cf34042bc8a
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# Chamada do AEM Forms usando APIs {#invoking-aem-forms-using-apis}

**Exemplos e exemplos neste documento são somente para AEM Forms no ambiente JEE.**

O Adobe Experience Manager Forms é um software corporativo baseado em J2EE que consiste em serviços que operam em uma infraestrutura compartilhada. As operações de serviço normalmente consomem ou produzem documentos. Ao usar o AEM Forms, você pode combinar o Forms Workflow com formulários eletrônicos, segurança de documentos e geração de documentos em um conjunto integrado e coeso de serviços. Esses serviços podem ser acessados de dentro e de fora do firewall.

Os aplicativos clientes podem chamar serviços da AEM Forms programaticamente usando uma API Java™, serviços da Web, comunicação remota e REST. Usando o console de administração, você pode configurar um serviço para expor um endpoint que permite que os serviços do AEM Forms sejam chamados programaticamente. Por padrão, a maioria dos serviços é pré-configurada para expor pontos de extremidade de serviços da Web, Java™ e Comunicação remota.

Seus requisitos comerciais determinam qual método de invocação usar. Por exemplo, usando a API do Java™, você pode integrar a funcionalidade do AEM Forms em seus aplicativos corporativos Java™, como Entidade Java™ e Beans de mensagem. Da mesma forma, você pode integrar a funcionalidade do AEM Forms em projetos .NET (ou outros projetos desenvolvidos com ambientes de desenvolvimento que oferecem suporte aos padrões de serviço da Web) usando serviços da Web.

Os serviços exigem um contêiner de serviço para ser executado, de modo semelhante a como o Enterprise JavaBeans™ (EJBs) requer um contêiner J2EE. O AEM Forms inclui apenas uma implementação de um contêiner de serviço. O container de serviço é responsável por gerenciar a duração de um serviço, incluindo a implantação e a garantia de que todas as solicitações sejam enviadas ao serviço correto. Ele também gerencia documentos que um serviço consome ou produz.

>[!NOTE]
>
>A programação com o AEM Forms não inclui informações sobre como chamar o AEM Forms usando Pastas monitoradas ou email.
