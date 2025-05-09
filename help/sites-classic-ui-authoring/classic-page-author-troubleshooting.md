---
title: Solução de problemas do AEM durante a criação
description: A seção a seguir aborda alguns problemas que você poderá enfrentar ao usar o AEM, junto com sugestões sobre como resolvê-los.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 27%

---

# Solucionar problemas do AEM durante a criação  {#troubleshooting-aem-when-authoring}

A seção a seguir aborda alguns problemas que você poderá enfrentar ao usar o AEM, junto com sugestões sobre como resolvê-los.

>[!NOTE]
>
>Quando você tiver problemas, também vale a pena verificar a lista de [Problemas conhecidos](/help/release-notes/release-notes.md) para sua instância (versão e service packs).

>[!NOTE]
>
>Os usuários que têm privilégios de administrador e que desejam solucionar problemas com o AEM podem usar os métodos de solução de problemas descritos em [Solução de problemas do AEM (para Administradores)](/help/sites-administering/troubleshoot.md). Se você não tiver privilégios suficientes, consulte o administrador do sistema para obter informações sobre como solucionar problemas do AEM.

## A versão antiga da página ainda está no site publicado {#old-page-version-still-on-published-site}

* **Problema**:

   * Você fez alterações em uma página e a replicou para o site de publicação, mas a versão *antiga* da página ainda está sendo exibida no site de publicação.

* **Motivo**:

   * Isso pode ter várias causas, mais frequentemente o cache (o navegador local ou o Dispatcher), embora possa, às vezes, ser um problema com a fila de replicação.

* **Soluções**:

   * Há várias possibilidades aqui:
   * Confirme se a página foi replicada corretamente. Verifique o status da página e, se necessário, o estado da fila de replicação.
   * Limpar o cache no seu navegador local e acessar a página novamente.
   * Adicionar `?` ao final do URL da página. Por exemplo:

     `http://localhost:4502/sites.html/content?`

     Isso solicitará a página diretamente do AEM e ignorará o Dispatcher. Se você receber a página atualizada, isso será uma indicação de que é necessário limpar o cache do Dispatcher.

   * Entre em contato com o administrador do sistema se houver problemas com as filas de replicação.

## Sidekick não visível {#sidekick-not-visible}

* **Problema**:

   * O Sidekick não fica visível ao editar uma página de conteúdo no ambiente de criação.

* **Motivo**:

   * Em casos raros, você pode ter posicionado o cabeçalho do seu sidekick fora do escopo da sua janela atual. Isso significa que não é possível reposicioná-lo novamente.

* **Solução**:

   * Faça logout da sessão atual e login novamente. O Sidekick retornará à posição padrão.

## Localizar e substituir - nem todas as instâncias são substituídas {#find-replace-not-all-instances-are-replaced}

* **Problema:**

   * Ao usar a opção **Localizar e Substituir**, pode acontecer que nem todas as instâncias do termo `find` sejam substituídas em uma página.

* **Motivo**:

   * A capacidade de **Localizar e substituir** depende de como o conteúdo é salvo e se ele pode ser pesquisado. Por exemplo, um texto de blog é armazenado na propriedade `jcr:text`, que não está configurada para ser pesquisada. O escopo padrão para o servlet localizar e substituir abrange as seguintes propriedades:

      * `jcr:title`
      * `jcr:description`
      * `jcr:text`
      * `text`

* **Solução**:

   * Essas definições podem ser alteradas com a configuração para o **Day CQ WCM Find Replace Servlet** usando o **Console da Web**; por exemplo, em

     `http://localhost:4502/system/console/configMgr`
