---
title: Notas de versão do  [!DNL Adobe Experience Manager] 6.5 LTS
description: Encontre informações sobre a versão atual do Adobe Experience Manager 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: 70436606-d95c-4208-94f6-e33f3eefdf66
source-git-commit: 7f9f24f173604640b454449b389da9fcdcf7017d
workflow-type: tm+mt
source-wordcount: '1068'
ht-degree: 94%

---

# Notas de versão atuais do Adobe Experience Manager 6.5 LTS {#release-notes}

## Informações da versão {#release-information}

| Produto | [!DNL Adobe Experience Manager] |
|---|---|
| Versão | 6.5 LTS |
| Tipo | Versão Principal |
| Disponibilidade geral | 7 de março de 2025 |

## Novidades {#what-s-new}

O [!DNL Adobe Experience Manager] 6.5 LTS é uma versão de upgrade da base de código [!DNL Adobe Experience Manager] 6.5. Ele fornece correções essenciais para o cliente, melhorias de alta prioridade para o cliente e correções gerais de bugs voltadas para a estabilização do produto. Também inclui as versões do pacote de serviços do [!DNL Adobe Experience Manager] 6.5 até o SP22.

A lista abaixo fornece uma visão geral, enquanto as páginas seguintes listam todos os detalhes.

### [!DNL Experience Manager Foundation] {#experience-manager-foundation}

A plataforma do [!DNL Adobe Experience Manager] 6.5 LTS baseia-se nas versões atualizadas da estrutura baseada em OSGi (Apache Sling e Apache Felix) e do repositório de conteúdo Java™: Apache Jackrabbit Oak 1.68.x.

O Eclipse Jetty 11.0.x é usado como um mecanismo de servlet para o início rápido.

#### Suporte a Java™  {#java-support}

* Compatibilidade com Java™ 17 e Java™ 21.
* Para atingir o desempenho ideal, substitua os valores de GC padrão por outros valores. Para obter mais informações, consulte a seção [instalar e atualizar](/help/sites-deploying/custom-standalone-install.md).
* A Adobe distribui atualizações de manutenção do Java™ 17 e do Java™ 21 para uso dos clientes em projetos relacionados ao AEM, quando não estão disponíveis publicamente na Oracle.

#### Embalagem de Uberjar {#uber-jar-packaging}

* Há uma pequena diferença no empacotamento do Uberjar do AEM 6.5 LTS. Para mais informações, consulte [Atualizar a versão Uber Jar do do AEM](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

#### Atualizar {#upgrade}

* Para mais detalhes sobre o procedimento de upgrade, consulte a [documentação de upgrade](/help/sites-deploying/upgrade.md).

## Instalar e atualizar {#install-update}

Para conferir os requisitos de instalação, consulte as [instruções de instalação](/help/sites-deploying/custom-standalone-install.md).

Para instruções mais detalhadas, consulte a [documentação de upgrade](/help/sites-deploying/upgrade.md).

>[!NOTE]
>
> Para novas instalações do AEM 6.5 LTS, as definições de índice precisam ser instaladas separadamente. Para obter mais informações, consulte [este artigo](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#index-definitions).

## Plataformas compatíveis {#supported-platforms}

Encontre o conjunto completo de plataformas compatíveis, incluindo em relação ao suporte, nos [requisitos técnicos do AEM 6.5 LTS](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Java™ 17/Java™ 21 são as versões recomendadas para usar com o AEM 6.5 LTS.

## Recursos obsoletos e removidos {#deprecated-and-removed-features}

A Adobe analisa continuamente os recursos do produto para melhorar o valor para o cliente, modernizando ou substituindo recursos mais antigos. Essas alterações são feitas com atenção especial à compatibilidade com versões anteriores.

Para comunicar a remoção ou substituição iminente dos recursos do Adobe Experience Manager (AEM), as seguintes regras aplicam-se:

1. O anúncio sobre a descontinuidade é oferecido primeiro. Embora descontinuados, os recursos continuam disponíveis, mas não são mais aprimorados.
1. A remoção de recursos descontinuados ocorre na versão principal a seguir, no mais tardar. A data real da remoção está planejada para ser anunciada posteriormente.

Esse processo oferece a clientes ao menos um ciclo de versão para adaptar sua implementação a uma nova versão ou sucessor de uma funcionalidade descontinuada, antes da remoção.

### Recursos descontinuados {#deprecated-features}

Esta seção lista os recursos e funcionalidades que a Adobe descontinuou no AEM 6.5 LTS. Normalmente, a Adobe descontinua recursos antes de os remover em uma versão futura e fornece uma alternativa.


Clientes devem analisar se usam o recurso/funcionalidade em sua implementação atual, bem como planejar a alteração de sua implementação para usar a alternativa fornecida.

| Área | Destaque | Substituição | Versão (SP) |
|---|---|---|---|
| Sites | [Editor SPA](/help/sites-developing/spa-overview.md) | Os editores preferidos para gerenciar conteúdo headless no AEM são:<br>- [O editor universal](/help/sites-developing/universal-editor/introduction.md) para edição visual.<br>- [O editor de fragmentos de conteúdo](/help/assets/content-fragments/content-fragments-managing.md) para editar com base em formulários. | 6.5 LTS GA |

### Recursos removidos {#removed-features}

Esta seção lista os recursos e funcionalidades que foram removidas do AEM 6.5 LTS. Nas versões anteriores, esses recursos estavam marcados como descontinuados.

| Área | Destaque | Substituição | Versão (SP) |
|--- |--- |--- |--- |
| Commerce | O AEM CIF Classic não é compatível. | Migre para o [AEM CIF](/help/commerce/cif/migration.md). | 6.5 LTS GA |
| Soluções | Redes sociais/comunidades não são compatíveis. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Screens | Telas não são compatíveis. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Ativos | `dam-pim` e `dam-rating` não são compatíveis, pois esses conjuntos dependem de redes sociais. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Ativos | `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettings()` foi removido. | Use a API alternativa `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettingsList()` que foi adicionada. | 6.5 LTS GA |
| Portal | O AEM Portal Diretor não é compatível. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Granite | O pacote `com.adobe.granite.socketio` foi removido. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Granite | `com.adobe.granite.crx-explorer` não é compatível. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Granite | `crx2oak` não é compatível. | Escolha a versão relevante do [Oak-upgrade](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-upgrade) | 6.5 LTS GA |
| Adobe | `com.adobe.cq.cq-searchpromote-integration` não é compatível. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Guava | Todas as dependências do Guava foram removidas do AEM; portanto, o pacote `com.adobe.granite.osgi.wrapper.guava-15.0.0-0002` não faz parte do AEM. | Os clientes podem adicionar o Guava por conta própria se dependerem dele ou substituir o código do Guava por coleções de Java ou outras alternativas, se possível. | 6.5 LTS GA |
| `We.Retail` | Não há suporte para o site de exemplo `We-retail`. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Fonte aberta | O pacote `oak-solr-osgi` não é compatível. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Fonte aberta | `org.apache.servicemix.bundles.abdera-parser`, `org.apache.servicemix.bundles.jdom` e `org.apache.sling.atom.taglib` não são compatíveis. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Fonte aberta | Os pacotes `org.apache.commons.io` foram exportados de `org.apache.commons.commons-io`. | Nenhuma alteração necessária. | 6.5 LTS GA |
| Fonte aberta | Os pacotes `javax.mail` estão sendo exportados do pacote `com.sun.javax.mail`. | Nenhuma alteração necessária. | 6.5 LTS GA |
| Fonte aberta | Os pacotes `org.apache.jackrabbit.api` agora são exportados do pacote `org.apache.jackrabbit.oak-jackrabbit-api`. | Nenhuma alteração necessária. | 6.5 LTS GA |
| Fonte aberta | `com.github.jknack.handlebars` não é compatível. | Escolha a [versão](https://mvnrepository.com/artifact/com.github.jknack/handlebars) adequada | 6.5 LTS GA |

## Problemas conhecidos {#known-issues}

### Problema com o pacote de script JSP no AEM 6.5.21-6.5.23 e AEM 6.5 LTS GA

O AEM 6.5.21, 6.5.22, 6.5.23 e o AEM 6.5 LTS GA são fornecidos com o pacote `org.apache.sling.scripting.jsp:2.6.0`, que contém um problema conhecido. O problema normalmente ocorre com cargas altas, quando a instância do AEM trata muitas solicitações simultâneas.

Quando esse problema ocorre, uma das seguintes exceções pode aparecer nos logs de erros, junto com referências a `org.apache.sling.scripting.jsp:2.6.0`:

* `java.io.IOException: classFile.delete() failed`
* `java.io.IOException: tmpFile.renameTo(classFile) failed`
* `java.lang.ArrayIndexOutOfBoundsException: Index 0 out of bounds for length 0`
* `java.io.FileNotFoundException`

Uma hotfix [cq-6.5.lts.0-hotfix-NPR-42640](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-NPR-42640-1.2.zip) está disponível para resolver esse problema.

### Falha de conexão do Dispatcher com o recurso de somente SSL {#ssl-only-feature}

Ao habilitar o recurso de somente SSL em implantações do AEM, há um problema conhecido que afeta a conectividade entre as instâncias do Dispatcher e do AEM. Após habilitar esse recurso, as verificações de integridade podem falhar, e a comunicação entre as instâncias do Dispatcher e do AEM pode ser interrompida. Esse problema ocorre especificamente quando os clientes tentam se conectar por meio do `https + IP` a partir da Dispatcher com instâncias do AEM. Ela está relacionada a problemas de validação de SNI (Server Name Indication, Indicação de nome do servidor).

**Impacto:**

* Falhas de verificação da integridade com códigos de resposta HTTP 400
* Tráfego interrompido entre as instâncias do Dispatcher e do AEM
* O conteúdo não pode ser distribuído corretamente por meio do Dispatcher
* Falhas de conexão ao usar HTTPS com endereços IP na configuração do Dispatcher
* Erros HTTP 400 “SNI inválida” ao conectar-se via HTTPS + IP

**Ambientes afetados:**

* Implantações do AEM com configurações do Dispatcher
* Sistemas em que o recurso de somente SSL foi habilitado
* Configurações do Dispatcher, usando-se o método de conexão `https + IP` com instâncias do AEM

**Solução:**
Se você se deparar com esse problema, entre em contato com o suporte ao cliente da Adobe. Uma hotfix [cq-6.5.lts.0-hotfix-CQ-4359803](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-CQ-4359803-1.0.2.zip) está disponível para resolver esse problema. Não tente habilitar recursos de somente SSL até aplicar a hotfix necessária.

## Sites restritos{#restricted-sites}

Estes sites só estão disponíveis para clientes. Se você for cliente e precisar de acesso, entre em contato com o seu gerente de conta da Adobe.

* [Download do produto em licensing.adobe.com](https://licensing.adobe.com/)
* [Fale com o suporte ao cliente da Adobe](https://experienceleague.adobe.com/pt-br/docs/customer-one/using/home).