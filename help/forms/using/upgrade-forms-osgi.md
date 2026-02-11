---
title: Atualização para o AEM 6.5 Forms LTS no OSGi
description: Você pode executar uma atualização direta do AEM 6.5.22.0 Forms para o AEM 6.5 Forms LTS.
content-type: reference
role: Admin, User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms, AEM Forms on OSGi, AEM Forms Upgrade
exl-id: 9233d4b7-441c-4cbd-86f8-2c52b99c3330
source-git-commit: b7aa877f9e782b0568adc7baa440dc630c690454
workflow-type: tm+mt
source-wordcount: '1527'
ht-degree: 2%

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


## Implantação do AEM no JBoss EAP 8 (Windows)

### Visão geral

Este guia fornece instruções passo a passo para implantar o Adobe Experience Manager (AEM) como um arquivo OSGi WAR independente no JBoss Enterprise Application Platform (EAP) 8 em um ambiente Windows usando o JDK 21.

### Requisitos do sistema

Antes de iniciar o processo de implantação, verifique se seu ambiente atende aos seguintes requisitos:

| Componente | Requisito |
|-----------|-------------|
| Sistema Operacional | Windows Server 2016 ou posterior (64 bits) |
| Java Development Kit | JDK 21 (Oracle ou OpenJDK) |
| Servidor de aplicativos | JBoss EAP 8.x |
| Distribuição do AEM | Arquivo WAR do AEM (obtido do Adobe) |

>[!NOTE]
>
> Verifique se a variável de ambiente `JAVA_HOME` aponta para o diretório de instalação do JDK 21.

### Etapa 1: instalar o JBoss EAP 8

#### Baixar JBoss EAP

1. Navegue até o portal Desenvolvedor Red Hat:\
   [https://developers.redhat.com/products/eap/download](https://developers.redhat.com/products/eap/download)

2. Baixe a distribuição ZIP JBoss EAP 8 para Windows.

#### Extrair JBoss EAP

1. Extraia o arquivo ZIP baixado para o diretório de instalação de sua preferência.

2. Anote este caminho de diretório como `<JBOSS_HOME>` para uso neste guia.

   **Exemplo:**\
   ```C:\jboss-eap-8.0```

### Etapa 2: Preparar o arquivo WAR do AEM

#### Obter o AEM WAR

Adquira o arquivo AEM WAR da Distribuição de software da Adobe ou do representante da Adobe.

#### Renomear arquivo WAR

Renomeie o arquivo WAR para refletir o caminho de contexto do URL desejado:

```
cq-quickstart.war
```

>[!IMPORTANT]
>
> O nome de arquivo WAR determina o contexto do URL do aplicativo. Por exemplo, `cq-quickstart.war` estará acessível em `/cq-quickstart`.


### Etapa 3: configurar o AEM WAR

Todas as modificações de configuração devem ser concluídas **antes** de implantar no JBoss.

#### Criar Diretório de Trabalho

1. Crie um diretório de trabalho temporário:

   ```
   C:\aem\war-config
   ```

2. Copie `cq-quickstart.war` para este diretório.

#### Extrair conteúdo WAR

1. Abra o **Prompt de Comando** e navegue até o seu diretório de trabalho:

   ```cmd
   cd C:\aem\war-config
   ```

2. Extraia o arquivo WAR:

   ```cmd
   jar -xvf cq-quickstart.war
   ```

   Isso cria uma estrutura de diretório com `WEB-INF` e outros arquivos de aplicativo.

### Etapa 4: Configurar o descritor de deployment JBoss

#### Criar arquivo de estrutura de implantação

1. Navegue até o diretório `WEB-INF` dentro do WAR extraído:

   ```cmd
   cd WEB-INF
   ```

2. Crie um novo arquivo chamado `jboss-deployment-structure.xml`.

3. Adicione o seguinte conteúdo XML:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jboss-deployment-structure xmlns="urn:jboss:deployment-structure:1.2">
       <deployment>
           <dependencies>
               <module name="jdk.unsupported" />
           </dependencies>
       </deployment>
   </jboss-deployment-structure>
   ```

4. Salvar e fechar o arquivo.

**Propósito:** essa configuração fornece acesso aos módulos internos do JDK exigidos pelo AEM.

### Etapa 5: definir configurações de upload de várias partes

>[!NOTE]
>
> A etapa 5 é aplicável somente a **AEM Forms**. Se você estiver configurando apenas o **AEM**, ignore esta etapa.


#### Modificar web.xml

1. Abra `WEB-INF\web.xml` em um editor de texto.

2. Localize a seção `<servlet>` que contém a configuração do modo de execução:

   ```xml
   <!-- Set the runmode per default to author -->
   <init-param>
       <param-name>sling.run.modes</param-name>
       <param-value>author</param-value>
   </init-param>
   <load-on-startup>100</load-on-startup>
   </servlet>
   ```

3. Substituir a marca de fechamento `</servlet>` e a linha anterior por:

   ```xml
   <init-param>
       <param-name>sling.run.modes</param-name>
       <param-value>author</param-value>
   </init-param>
   <multipart-config>
       <max-file-size>1048576000</max-file-size>
       <max-request-size>1048576000</max-request-size>
       <file-size-threshold>0</file-size-threshold>
   </multipart-config>
   <load-on-startup>100</load-on-startup>
   </servlet>
   ```

4. Salvar e fechar `web.xml`.

**Propósito:** essas configurações permitem uploads de arquivos grandes (até 1 GB) para o AEM Forms e o Digital Asset Management.

### Etapa 6: reempacotar o arquivo WAR

Após concluir todas as alterações de configuração, reempacote o arquivo WAR.

1. Volte para o diretório de trabalho que contém o conteúdo extraído:

   ```cmd
   cd C:\aem\war-config
   ```

2. Crie o novo arquivo WAR:

   ```cmd
   jar -cvf cq-quickstart.war *
   ```

>[!IMPORTANT]
>
> Execute essa etapa apenas uma vez, após a conclusão de todas as configurações.

### Etapa 7: implantar e iniciar o AEM

#### Implantar WAR no JBoss

1. Copie o `cq-quickstart.war` reempacotado para o diretório de implantações do JBoss:

   ```
   <JBOSS_HOME>\standalone\deployments
   ```

   **Exemplo:**
   ```C:\jboss-eap-8.0\standalone\deployments```

#### Definir configurações de JVM (opcional, mas recomendado)

Antes de iniciar o JBoss, defina as configurações de memória JVM:

1. Abra `<JBOSS_HOME>\bin\standalone.conf.bat` em um editor de texto.

1. Modifique ou adicione a seguinte linha para definir a memória heap:

   ```batch
   set "JAVA_OPTS=-Xms4096m -Xmx4096m -XX:MaxMetaspaceSize=512m"
   ```

>[!NOTE]
>
> Ajuste os valores de memória com base na capacidade do servidor e nos requisitos de AEM.

1. Salvar e fechar o arquivo.

#### Iniciar EAP JBoss

1. Abra o **Prompt de Comando** como **Administrador**.

1. Navegue até o diretório bin JBoss:

   ```cmd
   cd <JBOSS_HOME>\bin
   ```

   **Exemplo:**
   ```cmd cd C:\jboss-eap-8.0\bin```

1. Inicie o servidor JBoss:

   ```cmd
   standalone.bat -b 0.0.0.0 -bmanagement 0.0.0.0
   ```

   **Parâmetros:**
   * `-b 0.0.0.0` — Associa o servidor a todas as interfaces de rede
   * `-bmanagement 0.0.0.0` — Associa a interface de gerenciamento a todas as interfaces de rede

#### Monitorar implantação

Observe as mensagens de implantação na saída do console. A implantação bem-sucedida é indicada por:

```
Deployed "cq-quickstart.war" (runtime-name : "cq-quickstart.war")
```

### Etapa 8: acessar o AEM

Quando a implantação for concluída e o AEM for totalmente iniciado:

**URL do Autor do AEM:**
```http://<server-ip>:8080/cq-quickstart```

**Credenciais Padrão:**

* Nome de Usuário: `admin`
* Senha: `admin`

**Importante:** altere a senha padrão imediatamente após o primeiro logon.

### Resolução de problemas

#### Problemas comuns

| Problema | Solução |
|-------|----------|
| Falha na implantação com ClassNotFoundException | Verifique se `jboss-deployment-structure.xml` está configurado corretamente |
| OutOfMemoryError durante a inicialização | Aumentar memória de heap em `standalone.conf.bat` |
| O AEM não é iniciado após a implantação | Verificar logs JBoss em `<JBOSS_HOME>\standalone\log\server.log` |
| Não é possível acessar o AEM no navegador | Verifique se as configurações do firewall permitem a porta 8080 |

#### Arquivos de registro

* **Log do JBoss Server:** `<JBOSS_HOME>\standalone\log\server.log`
* **Log de Erros do AEM:** Disponível pelo Console da Web da AEM após inicialização em\
  `http://<server-ip>:8080/cq-quickstart/system/console`

### Configuração adicional

#### Configurando Modos de Execução

Para alterar os modos de execução do AEM (autor/publicação), modifique o parâmetro `sling.run.modes` em `WEB-INF\web.xml` antes de reempacotar o WAR:

```xml
<init-param>
    <param-name>sling.run.modes</param-name>
    <param-value>publish</param-value>
</init-param>
```

#### Recomendações de produção

Para ambientes de produção:

* Configurar certificados SSL/TLS no JBoss
* Configurar agentes de replicação do AEM
* Configurar o dispatcher para balanceamento de carga
* Ativar backups automatizados
* Implementar monitoramento e alertas

### Documentação relacionada

* [Documentação do JBoss EAP 8](https://access.redhat.com/documentation/en-us/red_hat_jboss_enterprise_application_platform/8.0)
* [Documentação do Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=pt-BR)
* [Guia de Instalação e Implantação do AEM](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html?lang=pt-BR)

### Informações do documento

| Texto | Valor |
|-------|-------|
| Última atualização | Fevereiro de 2026 |
| Versão do AEM | 6.5+ (LTS) |
| Versão do JBoss | EAP 8.x |
| Versão do JDK | 21 |
| Platform | Windows |


