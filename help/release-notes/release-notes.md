---
title: Notas de versão atuais do Adobe Experience Manager 6.5 LTS
description: Estas são as Notas de versão atuais do Adobe Experience Manager 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: b5a8f555-c061-4fe2-a100-cc01335959cb
source-git-commit: 0afd255ec5c9d3db37f2f059782b35052761b1cf
workflow-type: tm+mt
source-wordcount: '801'
ht-degree: 19%

---

# Notas de versão atuais do Adobe Experience Manager 6.5 LTS {#release-notes}

## Informações da versão {#release-information}

| Produto | [!DNL Adobe Experience Manager] |
|---|---|
| Versão | 6,5 LT |
| Tipo | Versão Principal |
| Data de disponibilidade geral | sábado, 7 de março de 2025 |

## Novidades {#what-s-new}

O [!DNL Adobe Experience Manager] 6.5 LTS é uma versão de atualização para a base de código [!DNL Adobe Experience Manager] 6.5. Ele fornece funcionalidades novas e aprimoradas, correções essenciais para o cliente, melhorias de alta prioridade para o cliente e correções gerais de erros voltadas para a estabilização do produto. Também inclui versões do Service Pack do [!DNL Adobe Experience Manager] 6.5 até o SP22.

A lista abaixo fornece uma visão geral, enquanto as páginas subsequentes listam os detalhes completos.

### [!DNL Experience Manager Foundation] {#experience-manager-foundation}

A plataforma do [!DNL Adobe Experience Manager] 6.5 LTS se baseia nas versões atualizadas da estrutura baseada em OSGi (Apache Sling e Apache Felix) e do Repositório de Conteúdo Java™: Apache Jackrabbit Oak 1.68.x.

O Quickstart usa o Eclipse Jetty 11.0.x como mecanismo de servlet.

#### Suporte para Java™  {#java-support}

* Suporte para Java™ 17.
* Para obter o desempenho ideal, substitua os valores de GC padrão por outros valores. Para obter mais informações, consulte a seção [instalar e atualizar](/help/sites-deploying/custom-standalone-install.md).
* As atualizações de manutenção do Java™ 17 são distribuídas pela Adobe para uso do cliente em projetos relacionados à AEM, quando não estão disponíveis publicamente na Oracle.

#### Empacotamento Uberjar {#uber-jar-packaging}

* Há uma pequena diferença na embalagem do Uberjar do AEM 6.5 LTS. Para obter mais informações, consulte [Atualizar a versão do AEM Uber Jar](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

#### Atualizar {#upgrade}

* Para obter detalhes sobre o procedimento de atualização, consulte a [documentação de atualização](/help/sites-deploying/upgrade.md).

## Instalar e atualizar {#install-update}

Para obter os requisitos de instalação, consulte [instruções de instalação](/help/sites-deploying/custom-standalone-install.md).

Para obter instruções detalhadas, consulte [documentação de atualização](/help/sites-deploying/upgrade.md).

## Plataformas compatíveis {#supported-platforms}

Encontre a matriz completa de plataformas compatíveis, incluindo o nível de suporte em [requisitos técnicos do AEM 6.5 LTS](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>O Java™ 17 é a versão recomendada para usar com o AEM 6.5 LTS.

## Recursos obsoletos e removidos {#deprecated-and-removed-features}

A Adobe avalia as funcionalidades do produto constantemente, para reinventar ou substituir recursos mais antigos por alternativas mais modernas, de forma a melhorar o valor do cliente em geral, sempre sob considerações cuidadosas de compatibilidade com versões anteriores.

Para comunicar a remoção ou substituição iminente dos recursos do Adobe Experience Manager (AEM), as seguintes regras de aplicam:

1. O anúncio sobre a descontinuidade é oferecido primeiro. Embora obsoletos, os recursos ainda estão disponíveis, mas não estão aprimorados.
1. A remoção de recursos obsoletos ocorre na versão principal a seguir, o mais tardar. A data de destino real para remoção será anunciada posteriormente.

Esse processo oferece ao usuário ao menos um ciclo de versão para adaptar sua implementação a uma nova versão ou sucessor de uma funcionalidade descontinuada, antes da remoção.

### Recursos obsoletos {#deprecated-features}

Esta seção lista os recursos e funcionalidades marcados como obsoletos no AEM 6.5 LTS. Geralmente, os recursos planejados para remoção em uma versão futura são definidos como obsoletos primeiro, com uma alternativa fornecida.

Os clientes são instruídos a analisar se usam o recurso/funcionalidade em sua implementação atual, bem como a planejar a alteração de sua implementação para usar a alternativa fornecida.

| Área | Destaque | Substituição | Versão (SP) |
|---|---|---|---|
| Sites | [Editor de SPA](/help/sites-developing/spa-overview.md) | Os editores preferidos para gerenciar conteúdo headless no AEM são:<br>- [O Editor Universal](/help/sites-developing/universal-editor/introduction.md) para edição visual.<br>- [O Editor de Fragmento de Conteúdo](/help/assets/content-fragments/content-fragments-managing.md) para edição baseada em formulário. | 6,5 LTS GA |

### Recursos removidos {#removed-features}

Esta seção lista os recursos e funcionalidades removidos do AEM 6.5 LTS. As versões anteriores tinham esses recursos marcados como obsoletos.

| Área | Destaque | Substituição | Versão (SP) |
|--- |--- |--- |--- |
| Commerce | O AEM CIF Classic não é compatível. | Você deve migrar para o [AEM CIF](/help/commerce/cif/migration.md). | 6,5 LTS GA |
| Soluções | Social/Communities não são compatíveis. | Nenhuma substituição disponível. | 6,5 LTS GA |
| Screens | O Screens não é compatível. | Nenhuma substituição disponível. | 6,5 LTS GA |
| Ativos | Não há suporte para `dam-pim` e `dam-rating`, pois os conjuntos são dependentes de redes sociais. | Nenhuma substituição disponível. | 6,5 LTS GA |
| Ativos | `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettings()` foi removido. | Use a api alternativa `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettingsList()` que foi adicionada. | 6,5 LTS GA |
| Portal | O AEM Portal Diretor não é compatível. | Nenhuma substituição disponível. | 6,5 LTS GA |
| Granite | O pacote `com.adobe.granite.socketio` foi removido. | Nenhuma substituição disponível. | 6,5 LTS GA |
| Granite | Não há suporte para `com.adobe.granite.crx-explorer`. | Nenhuma substituição disponível. | 6,5 LTS GA |
| Granite | Não há suporte para `crx2oak`. | Escolha a versão relevante de [oak-upgrade](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-upgrade) | 6,5 LTS GA |
| Adobe | Não há suporte para `com.adobe.cq.cq-searchpromote-integration`. | Nenhuma substituição disponível. | 6,5 LTS GA |
| Goiabas | Todas as dependências de guava agora são removidas no AEM e, portanto, o pacote `com.adobe.granite.osgi.wrapper.guava-15.0.0-0002` não faz parte do AEM. | Os clientes podem adicionar o guava por conta própria se dependerem dele ou substituir o código do guava por coleções do java ou outras alternativas, se possível. | 6,5 LTS GA |
| We.Retail | O site de exemplo We-retail não é compatível. | Nenhuma substituição disponível. | 6,5 LTS GA |
| Origem aberta | O conjunto `oak-solr-osgi` não é suportado. | Nenhuma substituição disponível. | 6,5 LTS GA |
| Origem aberta | Não há suporte para `org.apache.servicemix.bundles.abdera-parser`, `org.apache.servicemix.bundles.jdom` e `org.apache.sling.atom.taglib`. | Nenhuma substituição disponível. | 6,5 LTS GA |
| Origem aberta | `org.apache.commons.io` pacotes foram exportados de `org.apache.commons.commons-io`. | Nenhuma alteração necessária. | 6,5 LTS GA |
| Origem aberta | `javax.mail` pacotes estão sendo exportados do pacote `com.sun.javax.mail`. | Nenhuma alteração necessária. | 6,5 LTS GA |
| Origem aberta | `org.apache.jackrabbit.api` pacotes agora são exportados do pacote `org.apache.jackrabbit.oak-jackrabbit-api`. | Nenhuma alteração necessária. | 6,5 LTS GA |
| Origem aberta | Não há suporte para `com.github.jknack.handlebars` | Escolher a [versão](https://mvnrepository.com/artifact/com.github.jknack/handlebars) relevante | 6,5 LTS GA |

## Sites restritos{#restricted-sites}

Esses sites só estão disponíveis para clientes do. Se você for um cliente do e precisar de acesso, entre em contato com o gerente de conta da Adobe.

* [Download do produto em licensing.adobe.com](https://licensing.adobe.com/)
* [Contate o Suporte ao Cliente da Adobe](https://experienceleague.adobe.com/pt-br/docs/customer-one/using/home).

