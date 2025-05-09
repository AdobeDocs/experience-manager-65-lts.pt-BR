---
title: Atualização para o AEM 6.5 Forms LTS no OSGi
description: Você pode executar uma atualização direta do AEM 6.5.22.0 Forms para o AEM 6.5 Forms LTS.
content-type: reference
role: Admin, User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms, AEM Forms on OSGi, AEM Forms Upgrade
exl-id: 9233d4b7-441c-4cbd-86f8-2c52b99c3330
source-git-commit: dd45dfe953a111ccbbc71e8e25a8a2577037587a
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 1%

---

# Atualização para o AEM 6.5 Forms LTS no OSGi {#upgrade-to-aem-forms-osgi}

Para [atualizar do AEM 6.5 para o AEM 6.5 LTS](/help/sites-deploying/upgrade.md), atualize para o AEM 6.5.22.0 Forms ou posterior. Há suporte para uma atualização direta do AEM 6.5.22.0 para o AEM 6.5 Forms LTS.

Se você estiver usando AEM 6.0 Forms, AEM 6.1 Forms, AEM 6.2 Forms, AEM 6.3 Forms, AEM 6.4 Forms ou AEM 6.5 Forms, uma atualização direta para AEM 6.5 Forms LTS não estará disponível. Para obter caminhos de atualização detalhados, consulte a documentação [Caminhos de Atualização](/help/forms/using/upgrade.md).

Depois de atualizar para o service pack AEM Forms 6.5.22.0, siga estas etapas para atualizar para o AEM 6.5 LTS Forms:

1. Instale o pacote complementar do AEM Forms. As etapas estão listadas abaixo:

   1. Abra a [Distribuição de softwares](https://experience.adobe.com/downloads). Você precisa de uma Adobe ID para fazer logon na Distribuição de softwares.
   1. Selecione **[!UICONTROL Adobe Experience Manager]**, disponível no menu de cabeçalho.
   1. Na seção **[!UICONTROL Filtros]**:
      1. Selecione **[!UICONTROL Forms]** na lista suspensa **[!UICONTROL Solução]**.
      1. Selecione a versão e o tipo do pacote. Você também pode usar a opção **[!UICONTROL Downloads de Pesquisa]** para filtrar os resultados.
   1. Selecione o nome do pacote aplicável ao seu sistema operacional, selecione **[!UICONTROL Aceitar termos do EULA]** e selecione **[!UICONTROL Baixar]**.
   1. Abra o [Gerenciador de Pacotes](/help/sites-administering/package-manager.md) e clique em **[!UICONTROL Carregar Pacote]** para carregar o pacote.
   1. Selecione o pacote e clique em **[!UICONTROL Instalar]**.

      Você também pode baixar o pacote usando o link direto listado no artigo [versões do AEM Forms](https://experienceleague.adobe.com/pt-br/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases).

      Depois que o pacote for instalado, você será solicitado a reiniciar a instância do AEM. **Não interromper imediatamente o servidor.** Antes de interromper o servidor do AEM Forms, aguarde até que as mensagens ServiceEvent REGISTERED e ServiceEvent UNREGISTERED parem de aparecer no arquivo &lt;crx-repository>/error.log e o log fique estável. Observe também que alguns pacotes podem permanecer no estado instalado. Você pode ignorar com segurança o estado desses pacotes.


      **Reinicie a instância do AEM com os seguintes parâmetros de linha de comando JVM adicionais**:
      `--add-opens java.base/java.util=ALL-UNNAMED --add-exports=java.xml/com.sun.org.apache.xml.internal.serialize=ALL-UNNAMED`

      Se o servidor for iniciado por meio de um script ou serviço, atualize-o de acordo para incluir os itens acima, de modo que eles também sejam efetivos após as reinicializações subsequentes.

      >[!NOTE]
      >
      > É recomendável usar o comando &#39;Ctrl + C&#39; para reiniciar o SDK. Reiniciar o AEM SDK usando métodos alternativos, por exemplo, parar processos Java, pode levar a inconsistências no ambiente de desenvolvimento do AEM.

1. Executar atividades de pós-instalação.

   * **Executar Utilitário de Migração**

     O utilitário de migração torna os formulários adaptáveis e os ativos de gerenciamento de correspondência das versões anteriores compatíveis com os formulários do AEM 6.5. Você pode baixar o utilitário da Distribuição de software da AEM. Para obter informações detalhadas sobre como configurar e usar o utilitário de migração, consulte [utilitário de migração](../../forms/using/migration-utility.md).

     Se você estiver usando a [Amostra para integrar o componente de rascunhos e envios](https://helpx.adobe.com/br/experience-manager/6-3/forms/using/integrate-draft-submission-database.html) ao banco de dados e atualizar de uma versão anterior, execute as seguintes consultas SQL após executar a atualização:

     ```sql
     UPDATE metadata m, additionalmetadatatable am
     SET m.dataType = am.value
     WHERE m.id = am.id
     AND am.key = 'dataType'
     ```

     ```sql
     DELETE from additionalmetadatatable
     WHERE `key` = 'dataType'
     ```

   * **(Se estiver atualizando a partir do AEM 6.2 Forms ou apenas de versões anteriores) Reconfigure o Adobe Sign**

     Se você tiver o Adobe Sign configurado na versão anterior do AEM Forms, reconfigure-o a partir dos serviços em nuvem da AEM. Para obter mais detalhes, consulte [Integrar o Adobe Sign com o AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md).

   * **Suporte para jQuery**

     No AEM 6.5 Forms, a versão do jQuery foi atualizada para 3.2.1 e a versão da interface do usuário do jQuery foi atualizada para 1.12.1. O AEM Form usa JQuery no modo **noConflict**. Portanto, se você estiver usando qualquer outra versão do jQuery, nenhum problema será exibido ao executar um upgrade. No entanto, ao atualizar para o AEM 6.5 Forms:

      * Certifique-se de que os componentes personalizados, se houver, sejam compatíveis com as versões do jQuery compatíveis.
      * Remova APIs não compatíveis dos componentes personalizados. Consulte o [guia de atualização](https://jquery.com/upgrade-guide/3.0/) para obter a lista de APIs removidas. Por exemplo, o suporte para as APIs load(), .unload() e .error() é removido. Use o método .on() no lugar das APIs mencionadas anteriormente. Por exemplo, altere $(&quot;img&quot;).load(fn) para $(&quot;img&quot;).on(&quot;load&quot;, fn).

   * **(Se estiver atualizando a partir do AEM 6.2 Forms ou somente versões anteriores) Reconfigure a análise e os relatórios**

     No AEM 6.4 Forms, a variável de tráfego para origem e o evento bem-sucedido para impressão não estão disponíveis. Assim, ao atualizar do AEM 6.2 Forms ou de versões anteriores, o AEM Forms para de enviar dados para o servidor do Adobe Analytics e os relatórios do Analytics para formulários adaptáveis não estão disponíveis. Além disso, o AEM 6.4 Forms introduz a variável de tráfego para a versão da análise de formulário e o evento bem-sucedido para o tempo gasto em um campo. Portanto, reconfigure as análises e os relatórios para o ambiente do AEM Forms. Para obter etapas detalhadas, consulte [Configuração de análises e relatórios](../../forms/using/configure-analytics-forms-documents.md).

1. Verifique se o servidor foi atualizado com êxito, se todos os dados também foram migrados com êxito e se ele pode funcionar normalmente.

   * **Verifique o status dos pacotes:** Verifique se todos os pacotes estão no estado ativo.
   * **Verifique a replicação e a replicação inversa:** Publique, preencha e envie alguns formulários migrados. Verifique também os dados enviados.
   * **Verifique o acesso às interfaces de usuário do administrador e do desenvolvedor:** Faça logon na instância do AEM a partir de uma conta de administrador e verifique se você tem acesso às seguintes URLs:

      * `https://'[server]:[port]'/crx/packmgr`
      * `https://'[server]:[port]'/crx/de`
      * `https://'[server]:[port]'/aem/forms.html/content/dam/formsanddocuments`

   >[!NOTE]
   >
   >No AEM 6.4 Forms, a estrutura do repositório crx foi alterada. Se você atualizar do Forms 6.3 para o Forms do AEM 6.5, use os caminhos alterados para a personalização que você cria novamente. Para obter a lista completa de caminhos alterados, consulte [Reestruturação do repositório do Forms no AEM](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/implementing/deploying/restructuring/forms-repository-restructuring-in-aem-6-5).
