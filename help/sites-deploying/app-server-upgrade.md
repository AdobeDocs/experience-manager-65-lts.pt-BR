---
title: Etapas de Atualização para Instalações de Servidor de Aplicativos
description: Saiba como atualizar instâncias do AEM implantadas por meio de servidores de aplicativos.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 28701105452c347c5470fdb582d783e7aef1adb0
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# Etapas de Atualização para Instalações de Servidor de Aplicativos {#upgrade-steps-for-application-server-installations}

>[!NOTE]
>
>Esta página descreve o procedimento de atualização da guerra do AEM 6.5 LTS com o WLP (WebSphere Liberty).

## Etapas de pré-atualização {#pre-upgrade-steps}

Antes de executar a atualização, há várias etapas que devem ser concluídas. Consulte [Atualizando Código e Personalizações](/help/sites-deploying/upgrading-code-and-customizations.md) e [Tarefas de Manutenção de Pré-Atualização](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) para obter mais informações. Além disso, verifique se o seu sistema atende aos requisitos do AEM 6.5 LTS. Veja como o Analyzer pode ajudá-lo a estimar a complexidade da sua atualização e também fazer um plano para a atualização (consulte [Planejando sua atualização](/help/sites-deploying/upgrade-planning.md) para obter mais informações).

### Pré-requisitos de migração {#migration-prerequisites}

* **Versão mínima necessária do Java**: verifique se você instalou o IBM Sumeru JRE 17 no servidor WLP.

### Execução da atualização {#performing-the-upgrade}

1. Faça um backup da sua instância antes de iniciar qualquer atividade de atualização.
1. Identifique se você precisa de uma atualização no local ou de um sidegrade dependendo da versão do servidor WLP que você está usando. Se o seu servidor WLP atual suportar o Servlet 6, você poderá executar uma atualização no local e continuar com esta documentação. Caso contrário, você precisa executar sidegrade. Para a descontinuação, siga a documentação de Migração de conteúdo com o Oak-Upgrade - [Link a ser adicionado]
1. Pare a instância do AEM. Normalmente, isso pode ser feito usando este comando:

   ```shell
   <path-to-wlp-directory>/bin/server stop server_name
   ```

1. Remova os arquivos e as pastas que não são mais necessários. Os itens que você precisa remover especificamente são:

   * O `cq-quickstart-65.war` da pasta `dropins` e da pasta expandida normalmente estão localizados em `<path-to-aem-server>/dropins/cq-quickstart-65.war` e `<path-to-aem-server>/apps/expanded/cq-quickstart-65.war`, respectivamente
   * A pasta `launchpad/startup`. Você pode excluí-lo executando o seguinte comando no terminal, supondo que você esteja na pasta do servidor:

     ```shell
     rm -rf crx-quickstart/launchpad/startup
     ```

   * O arquivo `base.jar`. Você pode fazer isso executando os seguintes comandos:

     ```shell
     find crx-quickstart/launchpad -type f -name 
     "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \;
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
1. Revise os parâmetros de início do servidor do AEM e atualize os parâmetros de acordo com os requisitos do sistema. Consulte [Instalação autônoma personalizada](/help/sites-deploying/custom-standalone-install.md) para obter mais informações
1. Instale o Java 17 e verifique se ele está instalado corretamente executando:

   ```shell
   java -version
   ```

1. Baixe o novo WAR 6.5 LTS da Distribuição de software e copie-o para a pasta de recados localizada em: `/<path-to-aem-server>/dropins/`
1. Iniciar instância do AEM: geralmente pode ser feito usando este comando:

   ```shell
   <path-to-wlp-directory>/bin/server start server_name
   ```

1. Caso você tenha alterações personalizadas em `sling.properties`, siga as instruções abaixo:

   1. Parar a instância do AEM executando `<path-to-wlp-directory>/bin/server stop server_name`
   1. Aplicar as alterações personalizadas de `sling.properties` ao arquivo `sling.properties` recém-gerado (consultando o arquivo de backup criado na etapa 6)
   1. Inicie a instância do AEM. Geralmente, isso pode ser feito executando: `<path-to-wlp-directory>/bin/server start server_name`

## Implantar Base De Código Atualizada {#deploy-upgraded-codebase}

Depois que o processo de atualização no local for concluído, a base de código atualizada deverá ser implantada. As etapas para atualizar a base de código para funcionar na versão de destino do AEM podem ser encontradas na página [Atualizar Código e Personalizações](/help/sites-deploying/upgrading-code-and-customizations.md).

## Executar Verificações E Solução De Problemas Após A Atualização {#perform-post-upgrade-checks-and-troubleshooting}

Consulte [Solução de problemas e verificações pós-atualização](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md) para obter mais informações.