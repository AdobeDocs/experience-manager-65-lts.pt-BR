---
title: Regulamentos de proteção e privacidade de dados - Disponibilidade do Adobe Experience Manager
description: Saiba mais sobre o suporte do Adobe Experience Manager para os vários Regulamentos de proteção e privacidade de dados. Ele inclui o Regulamento Geral sobre a Proteção de Dados da UE (GDPR), a Lei de Privacidade do Consumidor da Califórnia e como estar em conformidade ao implementar um novo projeto do AEM.
contentOwner: AEM Docs
topic-tags: introduction, grdp
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MANAGING
docset: aem65
solution: Experience Manager, Experience Manager 6.5
feature: Compliance
role: Developer,Leader,Architect,Data Architect,User
source-git-commit: d1297182b801ff4db163b8ae91332f5aebb94b9b
workflow-type: tm+mt
source-wordcount: '745'
ht-degree: 43%

---

# Regulamentos de disponibilidade para proteção e privacidade de dados do Adobe Experience Manager {#aem-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>O conteúdo deste documento não constitui um aconselhamento jurídico e não se destina a substituir tal aconselhamento.
>
>Consulte o departamento jurídico da sua empresa para obter aconselhamento sobre os regulamentos de proteção e privacidade de dados.

>[!NOTE]
>
>Para obter mais informações sobre a resposta da Adobe a questões de privacidade, e o que isso significa para você como cliente da Adobe, consulte o [Centro de privacidade da Adobe](https://www.adobe.com/br/privacy.html).

A Adobe está fornecendo documentação e procedimentos (com APIs, quando disponíveis), para o administrador de privacidade do cliente ou o administrador do AEM lidar com solicitações de proteção e privacidade de dados. Ela pode ajudá-lo a cumprir esses regulamentos. Os procedimentos documentados permitem que os clientes executem as solicitações normativas manualmente ou chamando APIs, quando disponíveis, de um portal ou serviço externo.

>[!CAUTION]
>
>Os detalhes documentados aqui são restritos ao Adobe Experience Manager.
>
>Dados de outro Serviço sob demanda da Adobe, juntamente com quaisquer solicitações de privacidade relacionadas, exigirão que ações sejam tomadas nesse serviço.
>
>Para mais informações, consulte a [Central de privacidade da Adobe](https://www.adobe.com/br/privacy.html).

## Introdução {#introduction}

As instâncias do Adobe Experience Manager e os aplicativos executados nelas pertencem e são operadas por clientes do Adobe.

Como consequência, as regulamentações de proteção de dados, como GDPR, CCPA e outras, são em grande parte de responsabilidade dos clientes.

Como uma breve introdução, os regulamentos relativos à privacidade e proteção de dados incluem novas regras que devem ser seguidas pelas funções de:

* Entidades de Negócios (CCPA) e/ou Controladores de Dados (GDPR)

* Fornecedores de serviços (CCPA) e/ou Processadores de dados (GDPR)

As principais disposições desses regulamentos são as seguintes:

1. Definição ampliada de dados pessoais para incluir todas as IDs exclusivas; como nos dados direta e indiretamente identificáveis.

2. Requisitos de consentimento reforçados.

3. Aumento do foco nos direitos de exclusão (eliminação de dados).

4. Recusar a venda de dados.

Para o Adobe Experience Manager:

* As instâncias e os aplicativos que são executados nelas pertencem e são operadas pelo cliente.

   * O cliente gerencia as funções normativas, incluindo Entidades de negócios e Provedor de serviços, Controlador de dados e Processador de dados, entre outras.

   * O Adobe Experience Platform Privacy Service não faz parte do fluxo de trabalho do AEM, conforme ilustrado no diagrama abaixo.

* O AEM inclui documentação e procedimentos para o administrador de privacidade do cliente e/ou o administrador AEM executarem as solicitações de regulamento de privacidade, seja manualmente ou por meio de APIs, quando disponível.

* Nenhum novo serviço ou interface foi adicionado.

   * Em vez disso, os procedimentos e as APIs estão documentados para uso pelas interfaces/portais do cliente que lidam com solicitações de regulamento de privacidade.

* O AEM não inclui nenhuma ferramenta pronta para uso para dar suporte a fluxos de trabalho de solicitações de privacidade.

   * A Adobe fornece documentação e procedimentos para o administrador de privacidade do cliente e o administrador do AEM, permitindo que eles executem manualmente solicitações relacionadas a regulamentos de privacidade.

A Adobe está fornecendo procedimentos para lidar com solicitações de privacidade relacionadas ao Acesso, Exclusão e Não participação no Adobe Experience Manager. Às vezes, há APIs disponíveis que podem ser chamadas de um portal desenvolvido pelo cliente ou scripts para ajudar na automação.

O diagrama a seguir ilustra um fluxo de trabalho de solicitação de privacidade (ilustrado com o Adobe Experience Manager 6.5):

![Proteção e privacidade de dados](assets/data-protection-and-privacy-01.png)

## Adobe Experience Manager e Disponibilidade regulamentar {#aem-and-regulatory-readiness}

Consulte as seções abaixo para obter a documentação regulamentar para as áreas de produtos do AEM.

## AEM Foundation {#aem-foundation}

Consulte [Lidar com solicitações de proteção e privacidade de dados para o AEM Foundation](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md).

## AEM Optando Pela Coleta De Estatísticas De Uso Agregado {#aem-opting-into-aggregate-usage-statistics-collection}

Consulte [Coleção de Estatísticas de Uso Agregado](/help/sites-deploying/opt-in-aggregated-usage-statistics.md).

## AEM Sites {#aem-sites}

Consulte [AEM Sites - Disponibilidade para proteção e privacidade de dados.](/help/sites-administering/gdpr-compliance-sites.md)

## Integração do AEM com o Adobe Target e o Adobe Analytics {#aem-integration-with-adobe-target-adobe-analytics}

Essas integrações da Adobe Experience Manager incluem os serviços prontos de proteção e privacidade de dados (por exemplo, GDPR ou CCPA). Nenhum dado pessoal do Adobe Target ou do Adobe Analytics é armazenado no AEM em relação às integrações.

Para obter mais informações, consulte o seguinte:

* [Adobe Target - Visão geral sobre a privacidade](https://developer.adobe.com/target/before-implement/privacy/cmp-privacy-and-general-data-protection-regulation/?lang=en)

* [Fluxo de trabalho da Privacidade de dados do Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/data-governance/an-gdpr-workflow.html?lang=pt-BR)

## AEM Forms {#aem-forms}

O AEM Forms inclui componentes e fluxos de trabalho que capturam, processam e armazenam dados para orquestrar processos de negócios e concluir transações digitais. Componentes diferentes usam armazenamentos de dados diferentes e permitem a integração com armazenamentos de dados personalizados também. A documentação a seguir explica os procedimentos e as diretrizes para acessar e manusear dados do usuário para oferecer suporte aos fluxos de trabalho de proteção e privacidade de dados (por exemplo, GDPR ou CCPA) de um componente.

* [Portal Forms](/help/forms/using/forms-portal-handling-user-data.md)
* [Gerenciamento de correspondência](/help/forms/using/correspondence-management-handling-user-data.md)
* [Integração com o Adobe Sign](/help/forms/using/integration-adobe-sign-handling-user-data.md)
* [Fluxos de trabalho centrados no Forms no OSGi](/help/forms/using/forms-workflow-osgi-handling-user-data.md)
* [Fluxos de trabalho do Forms JEE](/help/forms/using/forms-workflow-jee-handling-user-data.md) (somente AEM Forms JEE)
* [Segurança de documentos](/help/forms/using/document-security-handling-user-data.md) (somente AEM Forms JEE)
* [Gerenciamento de usuários](/help/forms/using/user-management-handling-user-data.md) (somente AEM Forms JEE)
