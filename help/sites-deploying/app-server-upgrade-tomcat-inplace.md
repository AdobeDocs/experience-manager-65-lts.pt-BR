---
title: Etapas de atualização para instalações do servidor de aplicativos (Tomcat)
description: Saiba como atualizar instâncias do AEM que são implantadas via Tomcat.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: b3c4e946a3f235fa0e3a0945f1ad692ee195e3ef
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# Etapas de atualização para instalações do servidor de aplicativos (Tomcat - Atualização no local) {#upgrade-steps-for-application-server-installations-tomcat-inplace}

>[!NOTE]
>
>Esta página descreve o procedimento de atualização (atualização local) do AEM 6.5 LTS para o AEM 6.5 LTS Servicepack no Tomcat. Para atualizar do AEM 6.5 para o 6.5 LTS, [consulte aqui](/help/sites-deploying/app-server-upgrade-tomcat.md).

## Etapas de pré-atualização {#pre-upgrade-steps}

Antes de executar a atualização, há várias etapas que devem ser concluídas. Consulte [Tarefas de Manutenção de Pré-Atualização](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) para obter mais informações. Além disso, verifique se o seu sistema atende aos [requisitos do AEM 6.5 LTS Servicepack](/help/sites-deploying/technical-requirements.md) e veja as [considerações de planejamento de atualização](/help/sites-deploying/upgrade-planning.md).


### Pré-requisitos de migração {#migration-prerequisites}

* **Versão mínima exigida do Java**: verifique se você instalou o Oracle® JRE 17/21 no servidor Tomcat.
* **Servidor Tomcat**: as versões do servidor Tomcat com suporte para o AEM 6.5 LTS e seus ServicePacks são **10.0.x** e **10.1.x**.

### Execução da atualização {#performing-the-upgrade}

Todos os exemplos neste procedimento usam o Tomcat como o servidor da aplicação e implicam que você tem uma versão funcional do AEM 6.5 LTS já implantada. O procedimento destina-se a documentar atualizações executadas do AEM versão **6.5** LTS para o **6.5 LTS** Servicepack.

1. Se o AEM 6.5 LTS já estiver implantado, verifique se os pacotes estão funcionando corretamente acessando: *`https://<serveraddress:port>/system/console/bundles`*
1. Em seguida, pare o AEM 6.5 LTS. Isso pode ser feito no Gerenciador de aplicativos Tomcat em: *`https://<serveraddress:port>/manager/html`*
1. Verifique se você concluiu as atividades de [pré-atualização](#pre-upgrade-steps), como o backup do servidor AEM 6.5 LTS, antes de executar qualquer atividade de atualização
1. Pare o servidor AEM 6.5 LTS Tomcat. Na maioria das situações, você pode fazer isso executando o script `./catalina.sh`, executando esse comando no terminal:

   ```
   $CATALINA_HOME/bin/catalina.sh stop
   ```

1. Remova os arquivos e as pastas que não são mais necessários. Os itens que você precisa remover especificamente são:

   * O arquivo **cq-quickstart-65.war** e a pasta `cq-quickstart-65` da pasta `webapps` geralmente estão localizados em `<path-to-aem-server>/webapps`
   * A pasta `launchpad/startup`. Você pode excluí-lo executando o seguinte comando no terminal, supondo que você esteja na pasta do servidor:

     ```shell
     rm -rf <path-to-aem-server>/bin/crx-quickstart/launchpad/startup
     ```

   * O arquivo `base.jar`. Você pode fazer isso executando os seguintes comandos:

     ```shell
     find <path-to-aem-server>/bin/crx-quickstart/launchpad -type f -name "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \;
     ```

   * O arquivo `BootstrapCommandFile_timestamp.txt`:

     ```shell
     rm -f <path-to-aem-server>/bin/crx-quickstart/launchpad/felix/bundle0/BootstrapCommandFile_timestamp.txt
     ```

   * Remova o arquivo `sling.options` executando:

     ```shell
     find <path-to-aem-server>/bin/crx-quickstart/launchpad -type f -name "sling.options.file" -exec rm -rf {} \; 
     ```

   * Remover o arquivo `sling.bootstrap.txt`:

     ```shell
     rm -rf <path-to-aem-server>/bin/crx-quickstart/launchpad/sling_bootstrap.txt
     ```

1. Faça um backup do arquivo `sling.properties` (geralmente presente em `<path-to-aem-server>/bin/crx-quickstart/launchpad/`) e exclua-o
1. Copie o arquivo WAR do AEM 6.5 LTS Servicepack para a pasta `<path-to-aem-server>/webapps`
1. Inicie o servidor AEM 6.5 LTS Tomcat executando:

   ```
   $CATALINA_HOME/bin/catalina.sh start
   ```

1. Monitore os logs de erro enquanto o AEM é inicializado para verificar se não há erros e se o AEM está funcionando sem problemas
1. Depois que o AEM 6.5 LTS for iniciado, verifique se os pacotes estão funcionando corretamente acessando: *`https://<serveraddress:port>/cq/system/console/bundles`*

## Executar Verificações E Solução De Problemas Após A Atualização {#perform-post-upgrade-checks-and-troubleshooting}

Consulte [Solução de problemas e verificações pós-atualização](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md) para obter mais informações.
