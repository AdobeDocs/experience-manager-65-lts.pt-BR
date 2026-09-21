---
title: Hotfixes do Adobe Experience Manager Forms 6.5 LTS SP1
description: Fornece informações sobre como baixar e instalar um hotfix do AEM Forms 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
exl-id: e485100f-3e16-4fd4-a8ce-af771d765dd1
source-git-commit: 0ce01150bd74eeea7edb6c6127003e1aefda97a9
workflow-type: tm+mt
source-wordcount: '1089'
ht-degree: 0%
---
# Hotfixes LTS do Adobe Experience Manager Forms 6.5{#aem-form-hotfix}

Este artigo lista as correções críticas implementadas para resolver problemas conhecidos, melhorar a estabilidade do sistema e aprimorar o desempenho geral do AEM Forms 6.5 LTS.


>[!NOTE]
>
> Os hotfixes foram projetados para serem cumulativos, abrangendo todas as correções anteriores. Ao aplicar a correção mais recente a uma versão do, ele não apenas aborda o problema mais recente, mas também incorpora todas as correções de erros e aprimoramentos anteriores.

## Hotfixes para o AEM Forms 6.5 LTS {#hotfix-for-aem-forms}

<table>
  <tbody>
  <tr>
    <td><strong>Data</strong></td>
    <td><strong>Link de download do Hotfix (link de Distribuição de software da AEM)</strong></td>
    <td><strong>Problemas corrigidos</strong></td>
  </tr>
  <tr>
    <td>
      <strong>21 de setembro de 2026</strong><br>
      <em>Aplica-se a:</em> implantações do AEM Forms 6.5 LTS Service Pack 2 JEE (JBoss, WebLogic, WebSphere)<br>
    </td>
    <td>
    <p><strong>Para instalar essa correção, conclua estas etapas na ordem:</strong></p>
    <p><strong>Etapa 1: Instalar o patch</strong></p>
    <ul>
    <strong>JBoss:</strong>
    <li>Windows- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/jboss/adobe-aem-forms-jee-hotfix-6.5.LTS.2-win-jboss.zip">Hotfix do AEM Forms 6.5 LTS SP2 no Windows para servidor JBoss JEE</a></li>
    <li>Linux- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/jboss/adobe-aem-forms-jee-hotfix-6.5.LTS.2-linux-jboss.tar.gz">Hotfix do AEM Forms 6.5 LTS SP2 no Linux para servidor JBoss JEE</a></li>
    <strong>WebLogic:</strong>
    <li>Windows- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/weblogic/adobe-aem-forms-jee-hotfix-6.5.LTS.2-win-weblogic.zip">Hotfix do AEM Forms 6.5 LTS SP2 no Windows para servidor Weblogic JEE</a></li>
    <li>Linux- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/weblogic/adobe-aem-forms-jee-hotfix-6.5.LTS.2-linux-weblogic.tar.gz">Hotfix do AEM Forms 6.5 LTS SP2 no Linux para servidor Weblogic JEE</a></li>
    <strong>WebSphere:</strong>
    <li>Windows- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/websphere/adobe-aem-forms-jee-hotfix-6.5.LTS.2-win-websphere.zip">Hotfix do AEM Forms 6.5 LTS SP2 no Windows para servidor Websphere JEE</a></li>
    <li>Linux- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/websphere/adobe-aem-forms-jee-hotfix-6.5.LTS.2-linux-websphere.tar.gz">Hotfix do AEM Forms 6.5 LTS SP2 no Linux para servidor Websphere JEE</a></li>
    </ul>
    <p>Instale o patch usando o procedimento padrão de instalação de patch do AEM Forms no JEE. <!-- TODO: link to the 6.5 LTS JEE patch installation instructions once available --></p>
    <p><strong>Etapa 2: instalar o pacote de correção de vulnerabilidade</strong></p>
    <ul>
    <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/SP2LTSBundles_VULN-36670.zip">Pacote de correção de vulnerabilidade para AEM Forms 6.5 LTS SP2</a></li>
    </ul>
    <ol>
    <li>Abra o console OSGi em <code>http://&lt;host&gt;:&lt;port&gt;/lc/system/console/bundles</code>.</li>
    <li>Clique em <strong>Instalar/Atualizar</strong>.</li>
    <li>Marque as caixas de seleção <strong>Iniciar pacote</strong> e <strong>Atualizar pacotes</strong>.</li>
    <li>Clique em <strong>Escolher Arquivo</strong> e carregue o pacote baixado.</li>
    <li>Aguarde até que o log seja definido e o conjunto seja exibido como <strong>Ativo</strong>.</li>
    </ol>
    <p><strong>Etapa 3: atualizar o instalador do AEM Forms Workbench</strong></p>
    <p>Você deve atualizar para o instalador mais recente do AEM Forms Workbench. Baixe-o do <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/fd/workbench/6-5-0-20260902-1-45/Workbench_DVD.zip">instalador do AEM Forms Workbench</a>.</p>
    <p><strong>Etapa 4: atualizar arquivos da biblioteca do cliente (desenvolvedores)</strong></p>
    <p>Este patch inclui uma atualização importante na biblioteca do cliente SDK <code>adobe-livecycle-client.jar</code> (consulte <a href="/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files">Incluindo arquivos da biblioteca AEM Forms Java</a>). Se o seu projeto usa esse arquivo JAR, atualize <code>adobe-livecycle-client.jar</code> no classpath do projeto depois de instalar o hotfix. A última versão está disponível em <code>&lt;AEM_Forms_Installation_dir&gt;\sdk\client-libs\common\adobe-livecycle-client.jar</code>.</p>
    <p>A correção é cumulativa, portanto, você pode aplicá-la no AEM Forms 6.5 LTS Service Pack 2 ou em um Service Pack anterior sem instalar o Service Pack 2 primeiro.</p>
    </td>
    <td>
    <ul>
    <li><b>FORMS-26818</b> Depois que o Apache Shiro é atualizado para a versão 2.1.0, o AEM Forms no JEE falha ao inicializar com um <code>NoClassDefFoundError</code> para o gerenciador de segurança Shiro. Este hotfix restaura o bootstrapping bem-sucedido.</li>
    <li><b>FORMS-26819</b> O AEM Forms no JEE falha com um erro "nenhuma classe encontrada" para <code>org.owasp.esapi.reference.JavaLogFactory</code>. Esse hotfix resolve a classe ausente.</li>
    <li><b>FORMS-26584, FORMS-26589</b> Depois de atualizar para o AEM Forms 6.5 LTS, os pontos de extremidade do TaskManager são removidos. Este hotfix restaura os pontos de extremidade do TaskManager.</li>
    <li><b>FORMS-26569</b> Em JEE, a etapa MergeEars do Configuration Manager falha com um erro de declaração DOCTYPE (<code>ALC-LCM-010-200</code>) devido ao construtor de XML seguro. Essa correção permite que a etapa MergeEars seja concluída.</li>
    <li><b>FORMS-25063</b> Os logs no nível do aplicativo estão ausentes nas implantações do IBM WebSphere Liberty. Este hotfix restaura o registro em nível de aplicativo.</li>
    <li><b>FORMS-24892</b> No JBoss, o email falha com "IMAPProvider não é um subtipo". Este hotfix restaura a funcionalidade de email no JBoss.</li>
    <li><b>FORMS-24692</b> No Perfil do WebSphere Liberty (WLP), o email falha com "Não foi possível converter o soquete em TLS". Esta correção restaura o email por TLS no WLP.</li>
    <li><b>FORMS-26688</b> Atualiza a biblioteca Gibson para a versão 6.0.29665850.</li>
    <li><b>FORMS-25222</b> Melhorias na validação de asserção SAML do Backports.</li>
    <li><b>FORMS-26733, FORMS-26734</b> Atualizou o Apache Log4j para a versão 2.25.5.</li>
    <li>Essa correção também inclui correções de segurança.</li>
    </ul>
    </td>
  </tr>
  <tr>
    <td>
      <strong>9 de setembro de 2025</strong><br>
    <td>
    <ul>
    <li>Windows- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[...]1-hotfix-on-add-on/adobe-aemfd-win-pkg-6.1.176-RHF-002.zip">Hotfix2 para AEM Service Pack 6.5 LTS no Windows</a></li>
    <li>Linux- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[...]hotfix-on-add-on/adobe-aemfd-linux-pkg-6.1.176-RHF-002.zip">Hotfix2 para AEM Service Pack 6.5 LTS no Linux</a></li>
     <li>MacOS- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[...]1-hotfix-on-add-on/adobe-aemfd-osx-pkg-6.1.176-RHF-002.zip">Hotfix2 para AEM Service Pack 6.5 LTS no MacOS</a></li>
    <td>
    <ul>
    <li>Maior confiabilidade no envio de formulários, solucionando um problema em que os envios podem falhar quando a Validação no lado do servidor (SSV) foi ativada. Se encontrar problemas, entre em contato com o [Suporte da Adobe Experience Manager Forms](https://business.adobe.com/in/support/main.html)
    </li>
    </ul>
    </td>    
  </tr>
    </ul>
    </td>    
  </tr>
  <tbody>
</table>

## Baixe e instale um Hotfix OSGi {#download-install-hotfix}

Execute as seguintes etapas para baixar e instalar o Hotfix:

1. Baixar [Hotfix](#hotfix-for-adaptive-forms) do link de Distribuição de Software.
1. Extraia o arquivo de Hotfix para obter um pacote do Experience Manager (.zip) e arquivos de pacote (.jar).
1. Carregue e instale o pacote (.zip) por meio do [Gerenciador de Pacotes](https://experienceleague.adobe.com/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager.html?lang=es#accessing).
1. Abra os pacotes do gerenciador de configurações `https://server:host/system/console/bundles`, carregue e instale o pacote (.jar). O hotfix do está instalado.
