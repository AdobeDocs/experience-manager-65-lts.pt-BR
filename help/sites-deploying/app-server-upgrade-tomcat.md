---
title: Etapas de atualização para instalações do servidor de aplicativos (Tomcat)
description: Saiba como atualizar instâncias do AEM que são implantadas via Tomcat.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: a8367ff25591c6ea7916aab17e733605ec3f59c8
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# Etapas de atualização para instalações do servidor de aplicativos (Tomcat) {#upgrade-steps-for-application-server-installations-tomcat}

>[!NOTE]
>
>Esta página descreve o procedimento de atualização do AEM 6.5 LTS no Tomcat.

## Etapas de pré-atualização {#pre-upgrade-steps}

Antes de executar a atualização, há várias etapas que devem ser concluídas. Consulte [Atualizando Código e Personalizações](/help/sites-deploying/upgrading-code-and-customizations.md) e [Tarefas de Manutenção de Pré-Atualização](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) para obter mais informações. Além disso, verifique se o seu sistema atende aos [requisitos do AEM 6.5 LTS](/help/sites-deploying/technical-requirements.md) e veja as [considerações de planejamento de atualização](/help/sites-deploying/upgrade-planning.md) e como o [Analyzer](/help/sites-deploying/pattern-detector.md) pode ajudá-lo a estimar a complexidade.


### Pré-requisitos de migração {#migration-prerequisites}

* **Versão mínima exigida do Java**: verifique se você instalou o Oracle® JRE 17 no servidor Tomcat.
* **Servidor Tomcat**: a versão do servidor Tomcat necessária para o 6.5 LTS é **11.0.x**.

### Execução da atualização {#performing-the-upgrade}

Todos os exemplos neste procedimento usam o Tomcat como o servidor da aplicação e implicam que você tem uma versão funcional do AEM já implantada. O procedimento destina-se a documentar atualizações executadas do AEM versão **6.5** para o **6.5 LTS**.

1. Se o AEM 6.5 já estiver implantado, verifique se os pacotes estão funcionando corretamente acessando: *`https://<serveraddress:port>/system/console/bundles`*
1. Em seguida, pare o AEM 6.5. Isso pode ser feito no Gerenciador de aplicativos Tomcat em: *`https://<serveraddress:port>/manager/html`*
1. Verifique se você concluiu as atividades de [pré-atualização](#pre-upgrade-steps), como o backup do servidor do AEM 6.5, antes de executar qualquer atividade de atualização
1. Instale o Java 17 e verifique se ele está instalado corretamente executando o comando:

   ```
   java –version
   ```

1. Configurar um servidor Tomcat compatível com AEM 6.5 LTS
1. Revise os parâmetros de início do servidor do AEM e atualize os parâmetros de acordo com os requisitos do sistema. Consulte [Considerações sobre o Java 17](/help/sites-deploying/custom-standalone-install.md#java-17-considerations-java-considerations) para obter mais informações
1. Implante o recém-baixado 6.5 LTS WAR no servidor Tomcat usando o Java 17 e inicie o servidor AEM 6.5 LTS Tomcat executando:

   ```
   $CATALINA_HOME/bin/catalina.sh start
   ```

1. Quando o AEM estiver funcionando, verifique se todos os pacotes estão em estado de execução acessando: *`https://<serveraddress:port>/cq/system/console/bundles`*
1. Pare o servidor AEM 6.5 LTS Tomcat. Na maioria das situações, você pode fazer isso executando o script `./catalina.sh`, executando esse comando no terminal:

   ```
   $CATALINA_HOME/bin/catalina.sh stop
   ```

1. Agora migre seu conteúdo do AEM 6.5 para o AEM 6.5 LTS seguindo estas etapas: [Migração de conteúdo do AEM 6.5 para o AEM 6.5 LTS usando a atualização do Oak](/help/sites-deploying/aem-65-to-aem-65lts-content-migration-using-oak-upgrade.md)
1. Após a migração do conteúdo, aplique as alterações personalizadas necessárias no arquivo `sling.properties`
1. Inicie o servidor AEM 6.5 LTS Tomcat executando:

   ```
   $CATALINA_HOME/bin/catalina.sh start
   ```

1. Monitore os logs de erro enquanto o AEM é inicializado para verificar se não há erros e se o AEM está funcionando sem problemas
1. Depois que o AEM 6.5 LTS for iniciado, verifique se os pacotes estão funcionando corretamente acessando: *`https://<serveraddress:port>/cq/system/console/bundles`*

## Implantar Base De Código Atualizada {#deploy-upgraded-codebase}

Depois que o processo de atualização for concluído, a base de código atualizada deverá ser implantada. As etapas para atualizar a base de código para funcionar na versão de destino do AEM podem ser encontradas na [página Atualizar Código e Personalizações](/help/sites-deploying/upgrading-code-and-customizations.md).

## Executar Verificações E Solução De Problemas Após A Atualização {#perform-post-upgrade-checks-and-troubleshooting}

Consulte [Solução de problemas e verificações pós-atualização](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md) para obter mais informações.
