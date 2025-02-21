---
title: Lista de pacotes obsoletos desinstalados após a atualização
description: Uma lista detalhando os pacotes que são desinstalados automaticamente ao atualizar para o AEM 6.3.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 34693070f2fcb5b468c72118cd5d5fc26d6d9dd0
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# Lista de pacotes obsoletos desinstalados após a atualização{#list-of-obsolete-bundles-uninstalled-after-the-upgrade}

Ao atualizar para o AEM 6.5.2025, os seguintes pacotes serão desinstalados automaticamente, dependendo da versão do service pack do AEM 6.5 que a atualização foi executada:

* com.adobe.cq.social.cq-social-activitystreams
* com.adobe.cq.social.cq-social-as-provider
* com.adobe.cq.social.cq-social-badging-api
* com.adobe.cq.social.cq-social-badging-basic-impl
* com.adobe.cq.social.cq-social-badging-impl
* com.adobe.cq.social.cq-social-calendar-api
* com.adobe.cq.social.cq-social-calendar-impl
* com.adobe.cq.social.cq-social-commons-oauth
* com.adobe.cq.social.cq-social-commons
* com.adobe.cq.social.cq-social-console
* com.adobe.cq.social.cq-social-content-fragments-impl
* com.adobe.cq.social.cq-social-enablement-api
* com.adobe.cq.social.cq-social-enablement-impl
* com.adobe.cq.social.cq-social-filelibrary
* com.adobe.cq.social.cq-social-forum
* com.adobe.cq.social.cq-social-gamification-api
* com.adobe.cq.social.cq-social-gamification-impl
* com.adobe.cq.social.cq-social-graph-api
* com.adobe.cq.social.cq-social-graph-impl
* com.adobe.cq.social.cq-social-group
* com.adobe.cq.social.cq-social-handlebars
* com.adobe.cq.social.cq-social-ideation-api
* com.adobe.cq.social.cq-social-ideation-impl
* com.adobe.cq.social.cq-social-jcr-provider-common
* com.adobe.cq.social.cq-social-jcr-provider
* com.adobe.cq.social.cq-social-journal
* com.adobe.cq.social.cq-social-livefyre
* com.adobe.cq.social.cq-social-members-api
* com.adobe.cq.social.cq-social-members-impl
* com.adobe.cq.social.cq-social-messaging-api
* com.adobe.cq.social.cq-social-messaging-impl
* com.adobe.cq.social.cq-social-moderation-spamdetector-core
* com.adobe.cq.social.cq-social-moderation
* com.adobe.cq.social.cq-social-ms-provider
* com.adobe.cq.social.cq-social-notifications-api
* com.adobe.cq.social.cq-social-notifications-channels-web
* com.adobe.cq.social.cq-social-notifications-impl
* com.adobe.cq.social.cq-social-qna
* com.adobe.cq.social.cq-social-rdb-provider
* com.adobe.cq.social.cq-social-reporting-management
* com.adobe.cq.social.cq-social-review
* com.adobe.cq.social.cq-social-scf-api
* com.adobe.cq.social.cq-social-scf-impl
* com.adobe.cq.social.cq-social-scoring-api
* com.adobe.cq.social.cq-social-scoring-basic-impl
* com.adobe.cq.social.cq-social-scoring-impl
* com.adobe.cq.social.cq-social-serviceusers-api
* com.adobe.cq.social.cq-social-serviceusers-impl
* com.adobe.cq.social.cq-social-srp-api
* com.adobe.cq.social.cq-social-srp-impl
* com.adobe.cq.social.cq-social-tally
* com.adobe.cq.social.cq-social-translation
* com.adobe.cq.social.cq-social-ugc-search-collections
* com.adobe.cq.social.cq-social-ugcbase-api
* com.adobe.cq.social.cq-social-ugcbase-impl
* com.adobe.cq.social.cq-social-user-ugc-management
* com.adobe.cq.sample.we.retail.core
* com.adobe.cq.screens.dcc
* com.adobe.cq.screens.mq.activemq
* com.adobe.cq.screens.mq.core
* com.adobe.cq.screens
* com.adobe.cq.screens.sessions
* com.adobe.granite.socketio
* org.apache.jackrabbit.jackrabbit-api (substituído pela versão mais recente org.apache.jackrabbit.oak-jackrabbit-api)
* com.adobe.cq.commerce.cq-commerce-core
* com.adobe.cq.commerce.cq-commerce-pim
* com.adobe.cq.commerce.cq-commerce-social
* org.apache.servicemix.bundles.abdera-parser
* org.apache.servicemix.bundles.jdom
* com.day.cq.dam.cq-dam-pim
* com.day.cq.dam.cq-dam-rating
* org.apache.commons.io (substituído pela versão mais recente org.apache.commons.commons-io)
* com.adobe.granite.crx-explorer
* org.apache.jackrabbit.oak-solr-osgi
* com.adobe.cq.cq-searchpromote-integration

Os pacotes a seguir não estão incluídos em uma nova instância do AEM 6.5.2025. Após a atualização, você pode encontrar esses pacotes em estados inativos. Eles podem ser removidos manualmente:

* org.apache.sling.atom.taglib
* com.github.jknack.handlebars
* com.adobe.granite.osgi.wrapper.guava
* com.adobe.cq.core.wcm.components.core (Pode ser substituído pela versão compatível com o AEM 6.5 LTS)
* com.adobe.cq.core.wcm.components.extension.contentfragment.bundle (pode ser substituído pela versão compatível com o AEM 6.5 LTS)