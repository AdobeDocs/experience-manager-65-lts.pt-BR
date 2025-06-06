---
title: Notas de versão atuais do Adobe Experience Manager 6.5 LTS
description: Encontre informações sobre a versão atual do Adobe Experience Manager 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: b5a8f555-c061-4fe2-a100-cc01335959cb
source-git-commit: 2a83d6d4f25a866eacd87d6e2a4318b99c158ea0
workflow-type: tm+mt
source-wordcount: '1002'
ht-degree: 17%

---

# Notas de versão atuais do Adobe Experience Manager 6.5 LTS {#release-notes}

## Informações da versão {#release-information}

| Produto | [!DNL Adobe Experience Manager] |
|---|---|
| Versão | 6,5 LT |
| Tipo | Versão Principal |
| Data de disponibilidade geral | sábado, 7 de março de 2025 |

## Novidades {#what-s-new}

O [!DNL Adobe Experience Manager] 6.5 LTS é uma versão de atualização para a base de código [!DNL Adobe Experience Manager] 6.5. Ele fornece correções essenciais para o cliente, melhorias de alta prioridade para o cliente e correções gerais de bugs voltadas para a estabilização do produto. Também inclui versões do Service Pack do [!DNL Adobe Experience Manager] 6.5 até o SP22.

A lista abaixo fornece uma visão geral, enquanto as páginas subsequentes listam os detalhes completos.

### [!DNL Experience Manager Foundation] {#experience-manager-foundation}

A plataforma do [!DNL Adobe Experience Manager] 6.5 LTS se baseia nas versões atualizadas da estrutura baseada em OSGi (Apache Sling e Apache Felix) e do Repositório de Conteúdo Java™: Apache Jackrabbit Oak 1.68.x.

O Eclipse Jetty 11.0.x é usado como um mecanismo de servlet para o Quickstart.

#### Suporte para Java™  {#java-support}

* Suporte para Java™ 17 e Java™ 21.
* Para obter o desempenho ideal, substitua os valores de GC padrão por outros valores. Para obter mais informações, consulte a seção [instalar e atualizar](/help/sites-deploying/custom-standalone-install.md).
* A Adobe distribui atualizações de manutenção do Java™ 17 e do Java™ 21 para uso do cliente em projetos relacionados à AEM, quando não estão disponíveis publicamente na Oracle.

#### Empacotamento Uberjar {#uber-jar-packaging}

* Há uma pequena diferença na embalagem do Uberjar do AEM 6.5 LTS. Para obter mais informações, consulte [Atualizar a versão do AEM Uber Jar](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

#### Atualizar {#upgrade}

* Para obter detalhes sobre o procedimento de atualização, consulte a [documentação de atualização](/help/sites-deploying/upgrade.md).

## Instalar e atualizar {#install-update}

Para obter os requisitos de instalação, consulte [instruções de instalação](/help/sites-deploying/custom-standalone-install.md).

Para obter instruções detalhadas, consulte a [documentação de atualização](/help/sites-deploying/upgrade.md).

## Plataformas compatíveis {#supported-platforms}

Encontre a matriz completa de plataformas compatíveis, incluindo o nível de suporte em [requisitos técnicos do AEM 6.5 LTS](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Java™ 17/Java™ 21 são as versões recomendadas para usar com o AEM 6.5 LTS.

## Recursos obsoletos e removidos {#deprecated-and-removed-features}

A Adobe analisa continuamente os recursos do produto para melhorar o valor para o cliente, modernizando ou substituindo recursos mais antigos. Essas alterações são feitas com atenção especial à compatibilidade com versões anteriores.

Para comunicar a remoção ou substituição iminente dos recursos do Adobe Experience Manager (AEM), as seguintes regras de aplicam:

1. O anúncio sobre a descontinuidade é oferecido primeiro. Embora obsoletos, os recursos ainda estão disponíveis, mas não estão aprimorados.
1. A remoção de recursos obsoletos ocorre na versão principal a seguir, o mais tardar. A data de destino real para remoção está planejada para ser anunciada posteriormente.

Esse processo oferece ao usuário ao menos um ciclo de versão para adaptar sua implementação a uma nova versão ou sucessor de uma funcionalidade descontinuada, antes da remoção.

### Recursos obsoletos {#deprecated-features}

Esta seção lista os recursos e funcionalidades que o Adobe descontinuou no AEM 6.5 LTS. Normalmente, o Adobe descontinuará os recursos antes de removê-los em uma versão futura e fornece uma alternativa.


Os clientes são instruídos a analisar se usam o recurso/funcionalidade em sua implementação atual, bem como a planejar a alteração de sua implementação para usar a alternativa fornecida.

| Área | Destaque | Substituição | Versão (SP) |
|---|---|---|---|
| Sites | [Editor de SPA](/help/sites-developing/spa-overview.md) | Os editores preferidos para gerenciar conteúdo headless no AEM são:<br>- [O Editor Universal](/help/sites-developing/universal-editor/introduction.md) para edição visual.<br>- [O Editor de Fragmento de Conteúdo](/help/assets/content-fragments/content-fragments-managing.md) para edição baseada em formulário. | 6.5 LTS GA |

### Recursos removidos {#removed-features}

Esta seção lista os recursos e funcionalidades removidos do AEM 6.5 LTS. As versões anteriores tinham esses recursos marcados como obsoletos.

| Área | Destaque | Substituição | Versão (SP) |
|--- |--- |--- |--- |
| Commerce | O AEM CIF Classic não é compatível. | Migrar para o [AEM CIF](/help/commerce/cif/migration.md). | 6.5 LTS GA |
| Soluções | Social/Communities não são compatíveis. | Nenhuma substituição disponível. | 6.5 LTS GA |
| Screens | Screens não são compatíveis. | Nenhuma substituição disponível. | 6.5 LTS GA |
| Ativos | Não há suporte para `dam-pim` e `dam-rating`, pois os conjuntos são dependentes de redes sociais. | Nenhuma substituição disponível. | 6.5 LTS GA |
| Ativos | `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettings()` foi removido. | Use a api alternativa `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettingsList()` que foi adicionada. | 6.5 LTS GA |
| Portal | O AEM Portal Diretor não é compatível. | Nenhuma substituição disponível. | 6.5 LTS GA |
| Granite | O pacote `com.adobe.granite.socketio` foi removido. | Nenhuma substituição disponível. | 6.5 LTS GA |
| Granite | Não há suporte para `com.adobe.granite.crx-explorer`. | Nenhuma substituição disponível. | 6.5 LTS GA |
| Granite | Não há suporte para `crx2oak`. | Escolha a versão relevante de [oak-upgrade](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-upgrade) | 6.5 LTS GA |
| Adobe | Não há suporte para `com.adobe.cq.cq-searchpromote-integration`. | Nenhuma substituição disponível. | 6.5 LTS GA |
| Goiabas | Todas as dependências de guava agora são removidas no AEM e, portanto, o pacote `com.adobe.granite.osgi.wrapper.guava-15.0.0-0002` não faz parte do AEM. | Os clientes podem adicionar o guava por conta própria se dependerem dele ou substituir o código do guava por coleções do java ou outras alternativas, se possível. | 6.5 LTS GA |
| We.Retail | O site de exemplo We-retail não é compatível. | Nenhuma substituição disponível. | 6.5 LTS GA |
| Origem aberta | O conjunto `oak-solr-osgi` não é suportado. | Nenhuma substituição disponível. | 6.5 LTS GA |
| Origem aberta | Não há suporte para `org.apache.servicemix.bundles.abdera-parser`, `org.apache.servicemix.bundles.jdom` e `org.apache.sling.atom.taglib`. | Nenhuma substituição disponível. | 6.5 LTS GA |
| Origem aberta | `org.apache.commons.io` pacotes foram exportados de `org.apache.commons.commons-io`. | Nenhuma alteração necessária. | 6.5 LTS GA |
| Origem aberta | `javax.mail` pacotes estão sendo exportados do pacote `com.sun.javax.mail`. | Nenhuma alteração necessária. | 6.5 LTS GA |
| Origem aberta | `org.apache.jackrabbit.api` pacotes agora são exportados do pacote `org.apache.jackrabbit.oak-jackrabbit-api`. | Nenhuma alteração necessária. | 6.5 LTS GA |
| Origem aberta | Não há suporte para `com.github.jknack.handlebars` | Escolha a [versão](https://mvnrepository.com/artifact/com.github.jknack/handlebars) relevante | 6.5 LTS GA |

## Problemas conhecidos {#known-issues}

### Problema com o pacote de script JSP no AEM 6.5.21-6.5.23 e AEM 6.5 LTS GA

AEM 6.5.21, 6.5.22, 6.5.23 e AEM 6.5 LTS GA são fornecidos com o pacote `org.apache.sling.scripting.jsp:2.6.0`, que contém um problema conhecido. O problema normalmente ocorre em carga alta quando a instância do AEM lida com muitas solicitações simultâneas.

Quando esse problema ocorrer, uma das seguintes exceções poderá aparecer nos logs de erros junto com referências a `org.apache.sling.scripting.jsp:2.6.0`:

* `java.io.IOException: classFile.delete() failed`
* `java.io.IOException: tmpFile.renameTo(classFile) failed`
* `java.lang.ArrayIndexOutOfBoundsException: Index 0 out of bounds for length 0`
* `java.io.FileNotFoundException`

Um hotfix [cq-6.5.lts.0-hotfix-NPR-42640](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-NPR-42640-1.2.zip) está disponível para resolver esse problema.

### Falha de conexão do Dispatcher com recurso somente SSL {#ssl-only-feature}

Ao ativar o recurso somente SSL em implantações do AEM, há um problema conhecido que afeta a conectividade entre as instâncias do Dispatcher e do AEM. Após ativar esse recurso, as verificações de integridade podem falhar e a comunicação entre as instâncias do Dispatcher e do AEM pode ser interrompida.

**Impacto:**

* Falhas de verificação de integridade com códigos de resposta HTTP 500
* Tráfego interrompido entre instâncias do Dispatcher e do AEM
* O conteúdo não pode ser distribuído corretamente por meio do Dispatcher

**Ambientes Afetados:**

* Implantações do AEM com configurações do Dispatcher
* Sistemas em que o recurso somente SSL foi ativado

**Solução:**
Se você enfrentar esse problema, entre em contato com o Suporte ao cliente da Adobe. Um hotfix [cq-6.5.lts.0-hotfix-CQ-4359803](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-CQ-4359803-1.0.2.zip) está disponível para resolver esse problema. Não tente ativar recursos somente SSL até aplicar o hotfix necessário.

## Sites restritos{#restricted-sites}

Esses sites só estão disponíveis para clientes do. Se você for um cliente do e precisar de acesso, entre em contato com o gerente de conta da Adobe.

* [Download do produto em licensing.adobe.com](https://licensing.adobe.com/)
* [Contate o Suporte ao Cliente da Adobe](https://experienceleague.adobe.com/pt-br/docs/customer-one/using/home).

