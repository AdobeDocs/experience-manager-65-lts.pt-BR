---
title: Etapas de atualização para instalações do servidor de aplicativos (WLP)
description: Saiba como atualizar instâncias do AEM que são implantadas pelo Websphere Liberty.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 2a5d9026-49bc-4766-bcbe-38d834c14f72
source-git-commit: 82af7ee5b3665dcc33b47e05c8580e9981728888
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# Etapas de atualização para instalações do servidor de aplicativos (WLP) {#upgrade-steps-for-application-server-installations-wlp}

>[!NOTE]
>
>Esta página descreve o procedimento de atualização do AEM 6.5 LTS no WLP (WebSphere® Liberty).

## Etapas de pré-atualização {#pre-upgrade-steps}

Antes de executar a atualização, há várias etapas que devem ser concluídas. Consulte [Atualizando Código e Personalizações](/help/sites-deploying/upgrading-code-and-customizations.md) e [Tarefas de Manutenção de Pré-Atualização](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) para obter mais informações. Além disso, verifique se o seu sistema atende aos [requisitos para o AEM 6.5 LTS](/help/sites-deploying/technical-requirements.md).

Verifique [Planejando sua atualização](/help/sites-deploying/upgrade-planning.md) e como o [AEM Analyzer](/help/sites-deploying/aem-analyzer.md) pode ajudá-lo a estimar a complexidade da atualização do AEM.

### Pré-requisitos de migração {#migration-prerequisites}

* **Versão mínima exigida do Java**: certifique-se de ter instalado o IBM® Sumeru JRE 17 no servidor WLP.

### Execução da atualização {#performing-the-upgrade}

1. Verifique se você concluiu as etapas de [pré-atualização](#pre-upgrade-steps), como fazer backup do servidor AEM 6.5, antes de executar qualquer atividade de atualização
1. Dependendo dos seus requisitos, escolha um dos seguintes caminhos de atualização:
   1. **Atualização no Local**: se o servidor WLP atual der suporte ao Servlet 6, você poderá executar uma atualização no local e continuar com a etapa 3.
   1. **Sidegrade**: se você preferir uma nova configuração ou se o servidor WLP não oferecer suporte ao Servlet 6, configure uma nova instância do WLP com o AEM 6.5 LTS e migre o conteúdo seguindo o guia [AEM 6.5 para AEM 6.5 LTS Content Migration Using Oak-upgrade](/help/sites-deploying/aem-65-to-aem-65lts-content-migration-using-oak-upgrade.md) e pule para a seção [Implantar Base de Código Atualizado](#deploy-upgraded-codebase)

1. Pare a instância do AEM. Normalmente, isso pode ser feito usando este comando:

   ```shell
   <path-to-wlp-directory>/bin/server stop server_name
   ```

1. Remova os arquivos e as pastas que não são mais necessários. Os itens que você precisa remover especificamente são:

   * O **cq-quickstart-65.war** da pasta `dropins` e da pasta `expanded` geralmente localizados em `<path-to-aem-server>/dropins/cq-quickstart-65.war` e `<path-to-aem-server>/apps/expanded/cq-quickstart-65.war`, respectivamente
   * A pasta `launchpad/startup`. Você pode excluí-lo executando o seguinte comando no terminal, supondo que você esteja na pasta do servidor:

     ```shell
     rm -rf crx-quickstart/launchpad/startup
     ```

   * O arquivo `base.jar`. Você pode fazer isso executando os seguintes comandos:

     ```shell
     find crx-quickstart/launchpad -type f -name "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \;
     ```

   * O arquivo `BootstrapCommandFile_timestamp.txt`:

     ```shell
     rm -f crx-quickstart/launchpad/felix/bundle0/BootstrapCommandFile_timestamp.txt
     ```

   * Remova o arquivo `sling.options` executando:

     ```shell
     find crx-quickstart/launchpad -type f -name "sling.options.file" -exec rm -rf {} \; 
     ```

   * Remover o arquivo `sling.bootstrap.txt`:

     ```shell
     rm -rf crx-quickstart/launchpad/sling_bootstrap.txt
     ```

1. Faça um backup do arquivo `sling.properties` (geralmente presente em `crx-quickstart/conf/`) e exclua-o
1. Alterar a versão do servlet para **6.0** no arquivo `server.xml`
1. Instale o Java 17 e verifique se ele está instalado corretamente executando:

   ```shell
   java -version
   ```

1. Revise os parâmetros de início do servidor do AEM e atualize os parâmetros de acordo com suas necessidades. Consulte [Considerações sobre o Java 17](/help/sites-deploying/custom-standalone-install.md#java-considerations) para obter mais informações.
1. Baixe o novo 6.5 LTS WAR e copie-o para a pasta de recados localizada em: `/<path-to-aem-server>/dropins/`
1. Iniciar instância do AEM: geralmente pode ser feito usando este comando:

   ```shell
   <path-to-wlp-directory>/bin/server start server_name
   ```

1. Caso você tenha alterações personalizadas em `sling.properties`, siga as instruções abaixo:

   1. Parar a instância do AEM executando `<path-to-wlp-directory>/bin/server stop server_name`
   1. Aplicar as alterações personalizadas de `sling.properties` ao arquivo `sling.properties` recém-gerado (consultando o arquivo de backup criado na etapa 5)
   1. Inicie a instância do AEM. Geralmente, isso pode ser feito executando: `<path-to-wlp-directory>/bin/server start server_name`

## Implantar Base De Código Atualizada {#deploy-upgraded-codebase}

Depois que o processo de atualização for concluído, a base de código atualizada deverá ser implantada. As etapas para atualizar a base de código para funcionar na versão de destino do AEM podem ser encontradas na [página Atualizar Código e Personalizações](/help/sites-deploying/upgrading-code-and-customizations.md).

## Executar Verificações E Solução De Problemas Após A Atualização {#perform-post-upgrade-checks-and-troubleshooting}

Consulte [Solução de problemas e verificações pós-atualização](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md).
