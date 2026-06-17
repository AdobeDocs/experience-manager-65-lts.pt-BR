---
title: Plataformas compatíveis com AEM Forms no JEE
description: Lista de componentes de infraestrutura necessários e compatíveis para a instalação do AEM Forms no JEE
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
geptopics: SG_AEMFORMS/categories/jee
docset: aem65
role: Admin
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,AEM Forms on JEE,Platform Matrix
exl-id: 63d0d345-a80b-4bfb-baab-c7f7aa648695
source-git-commit: 6795f085b5a4d1ac2836b6c6f2f4d09a5739e639
workflow-type: tm+mt
source-wordcount: '2893'
ht-degree: 1%

---


# Plataformas compatíveis com AEM Forms no JEE {#supported-platforms-for-aem-forms-on-jee}

## Níveis de suporte {#support-levels}

O AEM Forms no servidor JEE pode ser configurado usando qualquer combinação de sistemas operacionais, servidores de aplicativos, bancos de dados, drivers de banco de dados, JDK, servidores LDAP e servidores de email compatíveis.

Este documento lista as plataformas de cliente e servidor compatíveis com o AEM Forms no JEE. O Adobe fornece vários níveis de suporte, tanto para configurações recomendadas do Adobe quanto para outras configurações. O documento também lista outros softwares compatíveis e suas versões, exceções, definições de patch e política de suporte a patches de software de terceiros.

>[!NOTE]
>
>- O AEM Forms no JEE é compatível apenas com as versões em inglês, francês, alemão e japonês dos sistemas operacionais e aplicativos compatíveis.

### Política de atualização e suporte

#### Instalador completo

- **Suporte de atualização para instaladores completos**: só há suporte para atualizações completas baseadas em instalador a partir do AEM 6.5.23.0.

- **Descontinuação e remoção**: o suporte à plataforma é atualizado com cada versão completa do instalador. Qualquer software marcado como obsoleto na matriz de plataforma durante uma versão completa do instalador tem direito a ser removido da matriz de plataforma suportada em uma versão subsequente do instalador completo, indicando o fim do suporte para o software.


<!--
#### Service Packs

- **Service Pack Coverage**: Adobe provides technical support for AEM Forms environments using any of the latest six service packs. If your current version predates the last six service packs, Adobe strongly recommends upgrading to the latest version for optimal performance, security, and continuous support. 

- **Patch Installer Guidelines**: While using the patch installers to update, it's crucial to verify that the underlying full installer version is not more than two releases old. For instance, during the installation of service pack 6.5.19.0, ensure the underlying full installer version is either 6.5.18.0 or 6.5.12.0. 

- **Patch Upgrade Support**: You can keep upgrading to the latest service pack, until you are upgrading to the most recent supported platforms also. For example, upgrading from service pack 6.5.12.0 to 6.5.19.0 is possible, provided that you transition to a platform combination supported for 6.5.19.0.
-->

### Configurações recomendadas {#recommendedconfigurations}

A Adobe recomenda essas configurações e fornece suporte total ou restrito como parte do contrato padrão de manutenção de software:

<table>
 <tbody>
  <tr>
   <th>Nível de compatibilidade</th>
   <th>Descrição</th>
  </tr>
  <tr>
   <td>A: Suportado<br /> </td>
   <td>A Adobe oferece suporte e manutenção completos para essa configuração. Essa configuração é coberta pelo processo de controle de qualidade da Adobe.</td>
  </tr>
  <tr>
   <td>R: Suporte restrito</td>
   <td>A Adobe fornece suporte total para essa configuração após o cumprimento de determinados pré-requisitos. Entre em contato com o suporte corporativo da Adobe para saber mais sobre os pré-requisitos e fazer uma solicitação para obter suporte.</td>
  </tr>
  <tr>
   <td>L: Suporte limitado</td>
   <td>A Adobe fornece suporte e manutenção completos para essa configuração após o cumprimento de determinados pré-requisitos. Nem todos os recursos estão disponíveis na configuração. Contate o suporte empresarial da Adobe para saber mais sobre os pré-requisitos e levantar uma solicitação de suporte.<br /> </td>
  </tr>
 </tbody>
</table>

### Configurações não suportadas {#unsupported-configurations}

| Nível de compatibilidade | Descrição |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| E: A expectativa é funcionar | Espera-se que a configuração funcione e não há relatórios em contrário. |
| Z: Não suportado | A configuração não é compatível. A Adobe não faz nenhuma declaração sobre se a configuração funciona e não oferece suporte a ela. |

>[!NOTE]
>
>Para ajudar os clientes da AEM Forms a reduzir o custo de propriedade, simplificar a arquitetura de implantação e modernizar a pilha de desenvolvimento, a plataforma corporativa da Adobe Experience Manager está se afastando das implantações baseadas em servidor de aplicativos em favor das implantações independentes baseadas em OSGi. A Adobe continua a oferecer suporte à pilha do AEM Forms JEE com uma matriz reduzida de componentes de infraestrutura.
>Para novas instalações, quando viável, é recomendável implantar o AEM Forms na pilha OSGi moderna para usar as inovações mais recentes em relação ao Adaptive Forms responsivo para comunicações interativas em vários canais, móveis e integrações de dados de back-end usando o Modelo de dados de formulário.

### Máquinas virtuais Java™ (JVM) {#java-virtual-machines-jvm}

O Adobe Experience Manager Forms requer uma máquina virtual Java™ para ser executada, que é fornecida pela distribuição Java™ Development Kit (JDK). O Adobe Experience Manager opera com as seguintes versões das Máquinas Virtuais Java™:

<table>
 <tbody>
  <tr>
   <th><p><strong>Platform</strong></p> </th>
   <th><p><strong>Nível de compatibilidade</strong></p> </th>
   <th><p><strong>Definições de patch compatíveis</strong></p> </th>
  </tr>
   <tr> 
   <td><p>Oracle Java™ SE 21 (64 bits) <sup> [8] </sup> </p>  </td>
   <td><p>A: Suportado</p> </td>
   <td><p>Versões e atualizações secundárias </p> </td>
  </tr>
  <tr> 
   <td><p>Oracle Java™ SE 17 (64 bits) <sup> [8] </sup> </p>  </td>
   <td><p>A: Suportado</p> </td>
   <td><p>Versões e atualizações secundárias </p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>- Rastreie os Boletins de segurança do fornecedor Java™ para garantir a segurança dos ambientes de produção e instalar as atualizações mais recentes do Java™.
>- O AEM Forms no JEE é compatível apenas com JVMs de 64 bits em ambientes de produção.

### Bancos de dados e persistência do CRX {#databases-and-crx-persistence}

<table>
 <tbody>
  <tr>
   <td><p><strong>Platform</strong></p> </td>
   <td><p><strong> Descrição</strong></p> </td>
   <td><p><strong>Nível de compatibilidade</strong></p> </td>
  </tr>
  <tr>
   <td><p>Sistema de arquivos</p> </td>
   <td><p>Microkernel do repositório (arquivos TAR MK)</p> </td>
   <td><p>Compatível</p> </td>
  </tr>
  <tr>
   <td><p> RDBMK </p> </td>
   <td><p></p> </td>
   <td><p>Compatível</p> </td>
  </tr>
  <tr>
   <td><p> MongoDB Enterprise 9.0 </p> </td>
   <td><p>Microkernel do repositório</p> </td>
   <td><p>Compatível</p> </td>
  </tr>
  <tr>
   <td><p> MongoDB Enterprise 8.0</p> </td>
   <td><p>Microkernel do repositório</p> </td>
   <td><p>Compatível</p> </td>
  </tr>
    <tr>
   <td><p> MongoDB Enterprise 7.0 </p> </td>
   <td><p>Microkernel do repositório</p> </td>
   <td><p>Compatível</p> </td>
  </tr>
   <tr>
   <td>Oracle Database 19c (edições Standard, Real Application Clusters (RAC) e Enterprise) </td>
   <td>-</td>
   <td>Compatível</td>
  </tr>
  <tr>
   <td><p>Microsoft® SQL Server 2022 </p> </td>
   <td><p>-</p> </td>
   <td><p>Compatível</p> </td>
  </tr>
  <tr>
   <td>MySQL 8.4</td>
   <td>-</td>
   <td>R: Suporte restrito</td>
  </tr>
 </tbody>
</table>

- MongoDB é um software de terceiros e não está incluído no pacote de licenciamento da AEM. Para obter mais informações, consulte [política de licenciamento do MongoDB](https://www.mongodb.org/about/licensing/).
- Para aproveitar ao máximo a implantação do AEM, a Adobe recomenda licenciar a versão MongoDB Enterprise para se beneficiar de suporte profissional.
- O Atendimento ao cliente da Adobe auxilia na qualificação de problemas relacionados ao uso do MongoDB com o AEM. Para obter mais informações, consulte a [página MongoDB para Adobe Experience Manager](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).
- &#39;Sistema de Arquivos&#39; inclui armazenamento em bloco compatível com POSIX. Isso inclui a tecnologia de armazenamento em rede. Lembre-se de que o desempenho do sistema de arquivos pode variar e influencia o desempenho geral. É recomendável carregar o AEM de teste com o sistema de arquivos remoto/de rede.
- Somente o WiredTiger do Mecanismo de Armazenamento MongoDB é compatível.
- A fragmentação MongoDB não é compatível com o AEM.
- O módulo de Segurança de documentos não usa o Repositório de conteúdo. Isso implica que, se você estiver usando somente a Segurança de documentos e não planeja usar o HTML Workspace, formulários HTML5 ou formulários adaptáveis, não instale o Repositório de conteúdo.

### Drivers de banco de dados {#database-drivers}

<table>
 <tbody>
  <tr>
   <th>Banco de dados </th>
   <th><p><strong>Platform</strong></p> </th>
   <th><p><strong>Definições de patch compatíveis</strong></p> </th>
  </tr>
  <tr>
   <td>MySQL</td>
   <td><p>Conector MySQL/J 8.4</p> </td>
   <td><p>Fornecido com o AEM Forms na instalação do JEE</p> </td>
  </tr>
  <tr>
   <td>Microsoft® SQL Server<br /> </td>
   <td><p>Driver JDBC do Microsoft® SQL Server 12.10.0<br /> </p> <p>sqljdbc12.10.0.jar</p> </td>
   <td><p>Download do site da Microsoft® na web.</p> </td>
  </tr>
  <tr>
   <td>Oracle</td>
   <td><p>Driver JDBC do Oracle Database 19.3.0.0.0</p> <p>ojdbc8.jar (versão 19.3.0.0.0)<br /> </p> </td>
   <td><p>Baixar de <a href="https://www.oracle.com/database/technologies/appdev/jdbc-ucp-19c-downloads.html">Site da Oracle</a>.</p> </td>
  </tr>
 </tbody>
</table>

### Servidores de aplicativos {#application-servers}

<table>
 <tbody>
  <tr>
   <td><p><strong> Platform</strong></p> </td>
   <td><p><strong>Nível de compatibilidade</strong></p> </td>
   <td><p><strong>Definições de patch compatíveis</strong></p> </td>
  </tr>
  <tr>
   <td><p>JBoss® Enterprise Application Platform (EAP) 8.0.6 <sup>[2] [3] [7]</sup> </p> </td>
   <td><p>A: Suportado</p> </td>
   <td><p>Patches e patches cumulativos para a versão de EAP compatível</p> </td>
  </tr>
  <tr>
   <td><p>Perfil do WebSphere® Liberty (WLP)</p> </td>
   <td><p>A: Suportado</p> </td>
   <td><p>Service pack e atualizações críticas</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>O WebSphere® Liberty Profile (WLP) é suportado somente com o Oracle Database e o IBM® Sumeru JDK 21.

### Sistemas operacionais de servidor {#server-operating-systems}

#### Ambientes de produção {#production-environments}

<table>
 <tbody>
  <tr>
   <th><p><strong> Platform</strong></p> </th>
   <th><p><strong>Nível de suporte</strong></p> </th>
   <th><p><strong>Definições de patch compatíveis</strong></p> </th>
  </tr>
     <tr>
   <td>Microsoft® Windows Server 2022 (64 bits)</td>
   <td>A: Suportado</td>
   <td>Service packs e atualizações críticas</td>
  </tr>
  <tr>
   <td>Ubuntu 20.04</td>
   <td>A: Suportado</td>
   <td>Service packs e atualizações críticas</td>
  </tr>
  <tr>
   <td><p>Red Hat® Enterprise Linux® 9 (Kernel 5.x) (64 bits)</p> </td>
   <td><p>A: Suportado</p> </td>
   <td><p>Versões secundárias, atualizações cumulativas e atualizações críticas</p> </td>
  </tr>
  <tr>
   <td><p>Red Hat® Enterprise Linux® 8 (Kernel 4.x) (64 bits)</td>
   <td><p>A: Suportado</p> </td>
   <td><p>Versões secundárias, atualizações cumulativas e atualizações críticas</p> </td>
  </tr>
  <tr>
   <td><p>SUSE® Linux® Enterprise Server 15 SP6 (64 bits)</p> </td>
   <td><p>A: Suportado</p> </td>
   <td><p>Service packs, patches cumulativos e atualizações críticas de segurança</p> </td>
  </tr>
 </tbody>
</table>

#### Ambiente virtualizado {#virtualized-environment}

Você pode executar o AEM Forms no JEE em uma máquina física ou em um ambiente virtual. No entanto, se você encontrar algum problema com o AEM Forms em um ambiente virtual, tente replicar o problema em uma máquina física. Se o problema persistir no computador físico, entre em contato com o Suporte da Adobe para obter uma resolução. Para os problemas que não podem ser replicados em uma máquina física, entre em contato com o fornecedor do ambiente virtual.

#### Ambientes de desenvolvimento {#development-environments}

<table>
 <tbody>
  <tr>
   <th><p><strong>Plataforma (Versão Base)</strong></p> </th>
   <th>Nível de compatibilidade</th>
   <th><p><strong>Definições de patch compatíveis</strong></p> </th>
  </tr>
  <tr>
   <td><p>Microsoft® Windows® 10 de 64 bits</p> </td>
   <td>E: A expectativa é funcionar</td>
   <td><p>Service pack e atualizações críticas</p> </td>
  </tr>
  <tr>
   <td><p>Microsoft® Windows® 11 de 64 bits</p> </td>
   <td>E: A expectativa é funcionar</td>
   <td><p>Service pack e atualizações críticas</p> </td>
  </tr>
 </tbody>
</table>

### Exceções às plataformas de servidor compatíveis {#exceptions-to-supported-server-platforms}

Considere as exceções a seguir ao escolher uma plataforma para configurar o AEM Forms no servidor JEE.

1. O repositório do CRX oferece suporte à persistência do tipo TarMK e MongoDB.
1. O AEM Forms no JEE não suporta o controle de acesso baseado em função (RBAC) JBoss®.
1. O AEM Forms no JEE suporta o WebSphere® Liberty Profile (WLP) somente com o Oracle Database e o IBM® Sumeru JDK 21.

<!--
1. [!DNL Microsoft&reg; Windows Server 2019] does not support [!DNL MySQL 5.7] and [!DNL JBoss&reg; EAP 7.1], [!DNL Microsoft&reg; Windows Server 2019] does not support turnkey installations for [!DNL Experience Manager Forms Service Pack 6.5.10.0 and later]. (CQDOC-18312) 
-->

Além disso, considere os seguintes pontos ao escolher o software para Adobe AEM Forms em implantações JEE:

- Atualizações de suporte e fix packs do AEM Forms no JEE sobre a versão principal e secundária do software compatível. No entanto, não há suporte para a atualização para a próxima versão principal ou secundária, a menos que especificado.
- Instalações baseadas em cluster não dão suporte à persistência TarMK. Para obter informações sobre a persistência com suporte, consulte [Escolha de um tipo de persistência para uma instalação do AEM Forms](/help/forms/using/choosing-persistence-type-for-aem-forms.md).
- O AEM Forms no JEE oferece suporte a vários softwares de terceiros de acordo com a [Política de suporte a software de terceiros](#third-party-patch-support-policy-third-party-patch-support-policy) da Adobe.
- AEM Forms em plataformas de suporte JEE de acordo com o suporte fornecido por fornecedores terceirizados. Algumas combinações podem não ser permitidas por fornecedores de terceiros. Por exemplo, muitos fornecedores não certificaram seus servidores de aplicativos com o Oracle. Como resultado, o AEM Forms no JEE também não é compatível com essas combinações. Para garantir que você escolha as versões de software compatíveis, verifique também a matriz de suporte para outros fornecedores.
- O AEM Forms no JEE não é compatível com TarMK Cold Standby.
- O AEM Forms no JEE não é compatível com clustering vertical.
- O AEM Forms no JEE não oferece suporte ao banco de dados MySQL em um ambiente clusterizado.

### Servidores LDAP (opcional) {#ldap-servers-optional}

<table>
 <tbody>
  <tr>
   <th><p><strong>Produto (Versão Base)</strong></p> </th>
   <th><p><strong>Definições de patch compatíveis</strong></p> </th>
  </tr>
  <tr>
   <td>Diretório ativo Microsoft® 2022</td>
   <td>Versão de manutenção e fix packs</td>
  </tr>
  <tr>
   <td><p>Servidor de Diretórios IBM® Tivoli 6.4</p> </td>
   <td><p>Pacotes de recursos e correções provisórias</p> </td>
  </tr>
 </tbody>
</table>

### Servidores de e-mail (opcional) {#email-servers-optional}

| Produto |
| ----------------------- |
| Microsoft® Exchange 2013 |
| Microsoft® Office 365 |

### Gerenciadores de conteúdo e conectores correspondentes {#content-managers-and-corresponding-connectors}

<table>
 <tbody>
  <tr>
   <td><strong>Produto<br /> </strong></td>
   <td><strong>Versão</strong></td>
  </tr>
  <tr>
   <td>EMC Documentum®</td>
   <td>7,3</td>
  </tr>
  <tr>
   <td>IBM® FileNet</td>
   <td>5.5.2</td>
  </tr>
  <tr>
   <td>IBM® Content Manager Server (obsoleto) </td>
   <td>8.5 Fix pack 2</td>
  </tr>
  <tr>
   <td> Cliente do gerenciador de conteúdo IBM®</td>
   <td>8.7 </td>
  </tr>
  <tr>
   <td> Cliente do gerenciador de conteúdo IBM® (obsoleto)</td>
   <td>8.5 </td>
  </tr>
   <td>Microsoft® Sharepoint </td>
   <td>2019<br /> </td>
  </tr>
 </tbody>
</table>

### Suporte para Cordova {#support-for-cordova}

O aplicativo AEM Forms agora é compatível com o Apache Cordova. A seguir estão as versões específicas da plataforma do Cordova que são compatíveis:

- Apache Cordova 6.4.0
- Cordova iOS 4.3.0
- Cordova Android™ 6.0.0
- Cordova Windows 4.4.3

### Suporte de software para PDF Generator {#software-support-for-pdf-generator}

<table>
 <tbody>
  <tr>
   <th><p><strong>Produto</strong></p> </th>
   <th><p><strong>Formatos compatíveis com a conversão para o PDF</strong></p> </th>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html">Acrobat Pro DC</a> versão mais recente</td>
   <td>XPS, formatos de imagem (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML e HTM</td>
  </tr>

<tr>
   <td>Microsoft® Office 2024 Professional Plus, licenças de varejo e por volume</td>
   <td>DOC, DOCX, XLS, XLSX, PPT, PPTX, RTF e TXT</td>
  </tr>
  <tr>
   <td>
   OpenOffice 4.1.15 </td>
   <td>
    ODT, ODP, ODS, ODG, ODF, SXW, SXI, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, formatos de imagem (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, RTF e TXT<br>

</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>- O PDF Generator suporta apenas as versões em inglês, francês, alemão e japonês dos sistemas operacionais e aplicativos compatíveis.
>- A PDF Generator requer o Adobe Acrobat Pro DC de 32 bits e o Microsoft® Office Professional Plus para executar a conversão.
>- A instalação do Microsoft® Office Professional Plus pode usar o licenciamento por volume baseado em Varejo ou MAK/KMS/AD.
>- Se a instalação do Microsoft® Office se tornar desativada ou não licenciada por qualquer motivo, como uma instalação com licença de volume que não consegue localizar um host KMS em um período especificado, as conversões podem falhar até que a instalação seja relicenciada e reativada.
>- A PDF Generator não oferece suporte ao Microsoft® Office 365.
>- As conversões do PDF Generator para OpenOffice são suportadas no Windows e no Linux®.
>- Os recursos OCR PDF, Otimizar PDF e Export PDF são suportados apenas no Windows.
>- A PDF Generator não oferece suporte ao Microsoft® Windows 11.
>- O suporte ao Microsoft® Office 2021 Professional Plus está obsoleto.
<!--
Removed lines: >- PDF Generator fails to convert files using Microsoft&reg; Visio 2019. You can continue to use Microsoft&reg; Visio 2016 to convert .VSD and .VSDX files.
>- PDF Generator fails to convert files using Microsoft&reg; Project 2019. You can continue to use Microsoft&reg; Project 2016 to convert .MPP files.
-->

### Exceções ao suporte de acessibilidade {#exceptions-to-accessibility-support}

Os seguintes subsistemas do AEM Forms não são compatíveis com [508](https://www.section508.gov/):

- Interface de criação adaptável do Forms
- Interface de criação do Forms Manager
- Interface de criação do gerenciamento de correspondência
- Interface do usuário do administrador (Interface do usuário do Console de administração)

## Requisitos do sistema para AEM Forms no JEE {#system-requirements-for-aem-forms-on-jee}

### Requisitos mínimos de hardware {#minimum-hardware-requirements}

<table>
 <tbody>
  <tr>
   <td>Platform</td>
   <td>Requisito mínimo de hardware</td>
  </tr>
  <tr>
   <td>Microsoft® Windows Server</td>
   <td>Processador Intel Xeon® E5-2680 de 2,4 GHz ou equivalente<br /> VMWare ESX 5.1 ou posterior<br /> RAM: 6 GB (SO de 64 bits com JVM de 64 bits)<br /> Espaço livre em disco: 15 GB de espaço temporário mais 22 GB<br /> para AEM Forms no JEE</td>
  </tr>
  <tr>
   <td>SUSE® Linux® Enterprise Server</td>
   <td>Intel Xeon® E5-2670v2, 1 vCPU, processador de 2,5 GHz<br /> AWS m3.medium (3 ECUs)<br /> RAM: 6 GB (SO de 64 bits com JVM de 64 bits)<br /> Espaço livre em disco: 6 GB de espaço temporário mais 22 GB<br /> para AEM Forms no JEE</td>
  </tr>
  <tr>
   <td>Red Hat® Enterprise Linux®</td>
   <td>Intel Xeon® E5-2670v2, 1 vCPU, processador de 2,5 GHz<br /> AWS m3.medium (3 ECUs)<br /> RAM: 6 GB (SO de 64 bits com JVM de 64 bits)<br /> Espaço livre em disco: 6 GB de espaço temporário mais 22 GB<br /> para AEM Forms no JEE<br /> </td>
  </tr>
  <tr>
   <td>Requisitos de hardware para um ambiente de produção pequeno</td>
   <td>
    <ul>
     <li><strong>Ambiente equipado com Intel®</strong>: Intel Xeon® E5-2680, 2,4 GHz ou superior. O uso de um processador dual core melhora ainda mais o desempenho</li>
     <li><strong>Memória: </strong>4 GB <br /> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Para obter requisitos adicionais, consulte [Requisitos do sistema para um AEM Forms de servidor único na implantação do JEE](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/prepare-install-single-server.pdf)

### Adobe Acrobat e Adobe Reader {#adobe-acrobat-and-adobe-reader}

<table>
 <tbody>
  <tr>
   <th><p><strong>Acrobat e Adobe Reader (Base)</strong></p> </th>
   <th><p><strong>Definições de patch compatíveis</strong></p> </th>
  </tr>
  <tr>
   <td>Acrobat 2020 (faixa clássica)</td>
   <td>Versão 20.004.30006 ou posterior<br /> </td>
  </tr>

</tbody>
</table>

>[!NOTE]
>
>A família de produtos do Acrobat DC apresenta duas faixas para o Acrobat e o Reader, que são produtos diferentes: &quot;Clássico&quot; e &quot;Contínuo&quot;.

## Clientes compatíveis com o AEM Forms no JEE {#supported-clients-for-aem-forms-on-jee}

### Workbench {#workbench}

<table>
 <tbody>
  <tr>
   <th><p><strong>Platform</strong></p> </th>
   <th><p><strong>Definições de patch compatíveis</strong></p> </th>
  </tr>
  <tr>
   <td><p>Microsoft® Windows® 10 (Enterprise, Pro, Basic)</p> <p>Versão de 32 bits ou 64 bits</p> <p> </p> </td>
   <td>Service packs e atualizações críticas</td>
  </tr>
  <tr>
   <td><p>Microsoft® Windows® 11 (Enterprise, Pro, Basic)</p> <p>Versão de 64 bits</p> <p> </p> </td>
   <td>Service packs e atualizações críticas</td>
  </tr>
  <tr>
   <td>Servidor Microsoft® Windows® 2022</td>
   <td>Service packs e atualizações críticas</td>
  </tr>
 </tbody>
</table>

- Espaço em disco para instalação: 1,7 GB apenas para o Workbench, 2,7 GB em uma única unidade para uma instalação completa do Workbench, Designer e a montagem de amostras 400 MB para diretórios de instalação temporários - 200 MB no diretório temporário do usuário e 200 MB no diretório temporário do Windows. Se todos esses locais residirem em uma única unidade, deverá haver 1,5 GB de espaço disponível durante a instalação. Os arquivos copiados para os diretórios temporários são excluídos quando a instalação é concluída.

- Memória para executar o Workbench: 2 GB de RAM
- Requisito de hardware: processador de 1 GHz Intel® Pentium® 4 ou AMD® equivalente
- Resolução mínima do monitor de 1024 X 768 pixels ou superior com cor de 16 bits ou superior
- Conexão de rede TCP/IPv4 ou TCP/IPv6 com o AEM Forms no servidor JEE
- Você deve ter privilégios Administrativos para instalar o Workbench no Windows. Se você estiver instalando usando uma conta de não administrador, o instalador solicitará as credenciais de uma conta apropriada.

### Designer {#designer}

- Microsoft® Windows® 2016 Server, Microsoft® Windows® 2019 Server, Microsoft® Windows® 10 ou Windows® 11
- 1 GHz ou mais rápido com suporte para PAE, NX e SSE2.
- 1 GB de RAM para 32 bits ou 2 GB de RAM para SO de 64 bits
- 16 GB de espaço em disco para 32 ou 20 GB de espaço em disco para SO de 64 bits
- Memória gráfica - 128 MB de GPU (recomenda-se 256 MB)
- 2,35 GB de espaço disponível em disco rígido
- Resolução do monitor de 1024 X 768 pixels ou superior
- Aceleração de hardware de vídeo (opcional)
- Acrobat Pro DC, Acrobat Standard DC ou Adobe Acrobat Reader DC
- Privilégios administrativos para instalar o Designer
- Microsoft® Visual C++ 2019 (VC 14.28 ou superior) tempo de execução de 32 bits

### Navegadores {#browsers}

#### Áreas de trabalho {#desktops}

<table>
 <tbody>
  <tr>
   <th><p><strong>Navegador (Base)</strong></p> </th>
   <th><p><strong>Nível de suporte</strong></p> </th>
   <th><p><strong>Definições de patch compatíveis</strong></p> </th>
  </tr>
  <tr>
   <td><p>Microsoft® Edge (Evergreen)</p> </td>
   <td><p>A: Suportado</p> </td>
   <td><p>Service packs e atualizações</p> </td>
  </tr>
  <tr>
   <td><p>Mozilla Firefox (Evergreen)</p> </td>
   <td><p>A: Suportado</p> </td>
   <td>Todas as atualizações</td>
  </tr>
  <tr>
   <td>Mozilla Firefox ESR</td>
   <td>E: A expectativa é funcionar</td>
   <td> Todas as atualizações</td>
  </tr>
  <tr>
   <td><p>Google Chrome (Evergreen)</p> </td>
   <td><p>A: Suportado</p> </td>
   <td>Todas as atualizações</td>
  </tr>
  <tr>
   <td>Apple Safari no macOS</td>
   <td>A: Suportado</td>
   <td>Todas as atualizações</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Algumas exceções relacionadas ao navegador para desktops são as seguintes:
>
>- O Safari é compatível somente com Macintosh OS X.
>- O Workspace é compatível com o Safari 5.1 no Macintosh OS X 10.6 e 10.7 com o Acrobat DC ou versões posteriores.
>- O Console de administração não é compatível com o Safari.
>- O Gerenciamento de correspondência não é compatível com o Windows® Internet Explorer 9.0 para formulários do AEM 6.1.
>- O Forms Portal oferece suporte ao software de leitor de tela JAWS 14.0 no Internet Explorer 11 para acessibilidade.

#### Clientes móveis {#mobile-clients}

<table>
 <tbody>
  <tr>
   <th><p><strong>Navegador (Base)</strong></p> </th>
   <th><p><strong>Definições de patch compatíveis</strong></p> </th>
  </tr>
  <tr>
   <td><p>Chrome no Android™ 4.1.2 e superior</p> </td>
   <td><p>Todas as atualizações</p> </td>
  </tr>
  <tr>
   <td>Safari no iOS 15.1 e posterior</td>
   <td>Todas as atualizações</td>
  </tr>
  <tr>
   <td>Microsoft® Edge<br /> </td>
   <td>Todas as atualizações<br /> </td>
  </tr>
  <tr>
   <td>Navegador Android™ nativo no Android™ 4.4 e superior</td>
   <td>Todas as atualizações</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>- O Forms Portal é compatível com o Safari somente no iPad.

### aplicativo AEM Forms {#aem-forms-workspace-app}

#### Suporte a dispositivo móvel {#mobile-device-support}

O aplicativo AEM Forms está disponível nas seguintes plataformas:

| **Plataforma** | **Dispositivos com suporte** |
| --- | --- |
| Apple iOS | Apple iPhone, iPad, iPad Air e iPad mini executando o iOS 15.1 e superior. |
| Google Android™ | Android™ 5.1 e superior. O aplicativo AEM Forms é certificado em tablets Samsung Galaxy de 7 e 10 polegadas e smartphones populares. |
| Microsoft® Windows | Dispositivos Microsoft® Surface, tablets, laptops e desktops com o sistema operacional Microsoft® Windows 10. |

### Adobe Document Security Extension for Microsoft® Office {#adobe-rights-management-extension-for-microsoft-office}

Clique [aqui](https://www.adobe.com/br/products/livecycle/rightsmanagement/extension/downloads.html) para ver os requisitos de sistema do Adobe Document Security Extension for Microsoft® Office.

### Exceções ao suporte ao cliente {#exceptions-to-client-support}

Atualizações de suporte, patches e fix packs do AEM Forms no JEE sobre a versão principal e secundária especificada do software compatível. No entanto, não há suporte para a atualização para a próxima versão principal ou secundária, a menos que especificado.

## Política de suporte a patches de terceiros {#third-party-patch-support-policy}

Os requisitos de software de terceiros para o AEM Forms no JEE estão documentados na seção &quot;Requisitos do sistema&quot; dos respectivos documentos do produto. Acesse toda a documentação do [AEM Forms 65 LTS](https://experienceleague.adobe.com/en/docs/experience-manager-65-lts/content/forms/getting-started/introduction-aem-forms).

A AEM Forms nas plataformas de referência de terceiros do JEE especifica o nível de patch específico da infraestrutura de terceiros que estava em vigor durante o desenvolvimento e o lançamento do AEM Forms no JEE e a partir do nível mínimo de patch/service pack da infraestrutura compatível com essa versão do AEM Forms no JEE.

A Adobe oferece suporte a patches urgentes ou recomendados emitidos por fornecedores terceirizados após o lançamento, supondo que esses fornecedores garantam compatibilidade com versões anteriores compatíveis com o AEM Forms no JEE. O Adobe só oferecerá suporte a patches lançados após o nível mínimo de patch declarado na documentação do AEM Forms no JEE.

Às vezes, o Adobe não é compatível com atualizações de terceiros que alteram a funcionalidade principal e, portanto, não é compatível com versões anteriores completas.

Em circunstâncias fora do controle da Adobe, patches de terceiros que alegam compatibilidade com versões anteriores podem ter impacto negativo nos produtos da Adobe ou nos ambientes dos clientes. Nesses casos, a Adobe recomenda que os clientes avaliem o impacto de qualquer patch urgente de terceiros antes de aplicá-los a sistemas críticos. A Adobe trabalha com terceiros usando esforços razoáveis dos negócios para resolver esses problemas, seja por meio de programas normais de suporte da Adobe ou por terceiros que corrijam o problema na correção. Isso não garante que um patch de terceiros recém-lançado compatível com o Adobe funcione conforme documentado pelo fornecedor ou com o AEM Forms no JEE.

A Adobe se reserva o direito de alterar as plataformas de referência de terceiros compatíveis com uma versão do AEM Forms no JEE e suas definições de patch compatíveis em qualquer ponto específico.

Informações adicionais sobre patches de terceiros também podem ser encontradas no site de suporte do Adobe Enterprise para obter artigos da base de conhecimento relacionados ao seu produto.

Para qualquer consulta relacionada a formatos ou versões de plataforma compatíveis, entre em contato com o [suporte da AEM Forms](https://business.adobe.com/in/support/main.html)

<!--

## Platform updates {#platform-updates}

The following platforms are marked as deprecated with AEM Forms 6.5.18.0 release on August 31, 2023:

- Microsoft&reg; Windows Server 2019 (64-bit)
- Microsoft&reg; Active Directory 2016

The following platforms are marked as deprecated with AEM Forms 6.5.13.0 release on June 2, 2022:
- Microsoft&reg; SharePoint 2016

The following platforms are marked as deprecated with AEM Forms 6.5.10.0 release on September 7, 2021:

- Adobe Acrobat 2017 - [Core support for Adobe Acrobat 2017 ends on June 6, 2022](https://helpx.adobe.com/support/programs/eol-matrix.html).
- Red Hat&reg; Enterprise Linux&reg; 7 (Kernel 3.x) (64-bit)
- Microsoft&reg; Windows Server 2016 (64-bit) 
- Microsoft&reg; Office 2016
- OpenOffice 4.1.2

-->


<!--## Revision History {#revision-history}-->

<!--

- 6.5.18.0 (Aug 31, 2023)
  - **Added support**: [!DNL Adobe Experience Manager Forms] on JEE has added support for the following platforms:
    - MongoDB Enterprise 4.4
    - Oracle WebLogic Server 14c
    - My SQL JDBC connector 8
    - Active Directory 2022
    - Microsoft&reg; Windows Server 2022 (64-bit)

  - **Removed support**: [!DNL Adobe Experience Manager Forms] on JEE has removed support for the following platforms:
    - Windows Server 2016 (64-bit)
    - MongoDB Enterprise 4.0
    - Oracle Database 12c Release 2 (12.2.0.1.0)
    - MySQL 5.7.35
    - Microsoft&reg; SQL Server 2016
    - JBoss&reg; EAP 7.1.4
    - My SQL JDBC connector 5.1.44
    - Microsoft&reg; SQL Server JDBC driver 6.2.1.0
    - Microsoft&reg; SQL Server JDBC driver 6.2.2.0
    - Microsoft&reg; JDBC Driver 8.x for SQL Server

    The release has also removed support for the following platforms for PDF Generator and in-general:
    - Microsoft&reg; Sharepoint 2016
    - Microsoft&reg; Office 2016
    - Microsoft&reg; Office Visio 2016 
    - Microsoft&reg; Publisher 2016
    - Microsoft&reg; Project 2016
    - OpenOffice 4.1.2
    - Acrobat 2017 (Classic track) Version 17.011.30078 or later

  - **Deprecated support**: [!DNL Adobe Experience Manager Forms] on JEE has deprecated the following platforms:
    - Microsoft&reg; Windows Server 2019 (64-bit)
    - Microsoft&reg; Active Directory 2016
    
- 6.5.13.0 (June 2, 2022)

  The following platforms are deprecated with AEM Forms 6.5.13.0 release on:
 
  - Microsoft&reg; SharePoint 2016

- 6.5.12.0 (March 3, 2022)

    - **Platform Updates**: [!DNL Adobe Experience Manager Forms] on JEE has removed support for the following platforms:
      - IBM&reg; J9 Virtual Machine (build 2.8, JRE 1.8.0)
      - Oracle Database 12c Release 1
      - Oracle Database 18c
      - Oracle Unified Directory (OUD) 11g Release 2
      - IBM&reg; Lotus Domino 9.0
      - IBM&reg; FileNet 5.2
      - Adobe Flash Player

    - **Platform Updates**: [!DNL Adobe Experience Manager Forms] on JEE has deprecated the following platforms:

      - MongoDB Enterprise 4.0
      - MongoDB Enterprise 4.2
      - IBM&reg; DB2&reg; 11.1
      - Oracle Database 12c Release 2
      - MySQL 5.7.35
      - Microsoft&reg; SQL Server JDBC driver 6.2.1.0
      - JBoss&reg; Enterprise Application Platform (EAP) 7.1.4
      - IBM&reg; Content Manager Server 8.5 Fix pack 2
      - IBM&reg; Content Manager Client 8.5
      - Microsoft&reg; SQL Server 2016

- 6.5.10.0 (Sep 01, 2022)

  - **Added support**: [!DNL Adobe Experience Manager Forms] on JEE has added support for the following platform:
  
    - Oracle Java&trade; SE 11 (64 bit) SDK for application server JBoss&reg; EAP 7.4.
  - **Deprecated support**: [!DNL Adobe Experience Manager Forms] on JEE has deprecated the following platforms:

    - Adobe Acrobat 2017 - [Core support for Adobe Acrobat 2017 ends on June 6, 2022](https://helpx.adobe.com/support/programs/eol-matrix.html).
    - Red Hat&reg; Enterprise Linux&reg; 7 (Kernel 3.x) (64-bit)
    - Microsoft&reg; Windows Server 2016 (64-bit) 
    - Microsoft&reg; Office 2016
    - OpenOffice 4.1.2


-->
<!--
### Release 6.5.19.1 (Dec 15, 2023)

| Added Support | Removed Support | Deprecated Support |
| -------------- | --------------- | ------------------- |
| MongoDB Enterprise 6.0 |MongoDB Enterprise 4.4   |  |
| MongoDB Enterprise 5.0 |  |  |
|  | |  |

### Release 6.5.18.0 (Aug 31, 2023)

| Added Support | Removed Support | Deprecated Support |
| -------------- | --------------- | ------------------- |
| MongoDB Enterprise 4.4 | Windows Server 2016 (64-bit) | Microsoft&reg; Windows Server 2019 (64-bit) |
| Oracle WebLogic Server 14c | MongoDB Enterprise 4.0 | Microsoft&reg; Active Directory 2016 |
| My SQL JDBC connector 8 | Oracle Database 12c Release 2 (12.2.0.1.0) |  |
| Active Directory 2022 | MySQL 5.7.35 |  |
| Microsoft&reg; Windows Server 2022 (64-bit) | Microsoft&reg; SQL Server 2016 |  |
|  | JBoss&reg; EAP 7.1.4 |  |
|  | My SQL JDBC connector 5.1.44 |  |
|  | Microsoft&reg; SQL Server JDBC driver 6.2.1.0 |  |
|  | Microsoft&reg; SQL Server JDBC driver 6.2.2.0 |  |
|  | Microsoft&reg; JDBC Driver 8.x for SQL Server |  |
|  |  |  |
|  | **Removed Support (PDF Generator and In-General):** |  |
|  | Microsoft&reg; Sharepoint 2016 |  |
|  | Microsoft&reg; Office 2016 |  |
|  | Microsoft&reg; Office Visio 2016 |  |
|  | Microsoft&reg; Publisher 2016 |  |
|  | Microsoft&reg; Project 2016 |  |
|  | OpenOffice 4.1.2 |  |
|  | Acrobat 2017 (Classic track) Version 17.011.30078 or later |  |


### Release 6.5.13.0 (June 2, 2022)

| Added Support | Removed Support | Deprecated Support |
| -------------- | --------------- | ------------------- |
|  |  | Microsoft&reg; SharePoint 2016 |


### Release 6.5.12.0 (March 3, 2022)

| Added Support | Removed Support | Deprecated Support |
| -------------- | --------------- | ------------------- |
|  | IBM&reg; J9 Virtual Machine (build 2.8, JRE 1.8.0) | MongoDB Enterprise 4.0 |
|  | Oracle Database 12c Release 1 | MongoDB Enterprise 4.2 |
|  | Oracle Database 18c | IBM&reg; DB2&reg; 11.1 |
|  | Oracle Unified Directory (OUD) 11g Release 2 | Oracle Database 12c Release 2 |
|  | IBM&reg; Lotus Domino 9.0 | MySQL 5.7.35 |
|  | IBM&reg; FileNet 5.2 | Microsoft&reg; SQL Server JDBC driver 6.2.1.0 |
|  | Adobe Flash Player | JBoss&reg; Enterprise Application Platform (EAP) 7.1.4 |
|  | | IBM&reg; Content Manager Server 8.5 Fix pack 2 |
|  | | IBM&reg; Content Manager Client 8.5 |
|  | | Microsoft&reg; SQL Server 2016 |
|  | | Microsoft&reg; Windows Server 2016 |

### Release 6.5.10.0 (September 01, 2022)

| Added Support | Removed Support | Deprecated Support |
| -------------- | --------------- | ------------------- |
| Oracle Java&trade; SE 11 (64 bit) SDK for application server JBoss&reg; EAP 7.4. | | [Adobe Acrobat 2017 - Core support for Adobe Acrobat 2017 ends on June 6, 2022.](https://helpx.adobe.com/support/programs/eol-matrix.html)|
|  | Red Hat&reg; Enterprise Linux&reg; 7 (Kernel 3.x) (64-bit)| |
|  | | Microsoft&reg; Windows Server 2016 (64-bit)|
|  | | Microsoft&reg; Office 2016 |
|  | | OpenOffice 4.1.2 |


>[!NOTE]
>
> A deprecated platform continue to receive support until the next full installer release or until third-party vendor support for the platform reaches its end-of-life, whichever is earlier.
-->
<!-- 
- Oct 10, 2021

  - Changed supported version of iOS for AEM Forms App to iOS 15.1. The previous version was iOS 12.

- Sep 07, 2021
  - **Platform Updates**: [!DNL Adobe Experience Manager Forms] on JEE has added support for the following platforms:
    - [!DNL Adobe Acrobat 2020]
    - [!DNL Ubuntu 20.04]
    - [!DNL Open Office 4.1.10]
    - [!DNL Microsoft&reg;&reg; Office 2016]
    - [!DNL Microsoft&reg;&reg; Windows Server 2016]
    - [!DNL RHEL8]

- Dec 03, 2020
  - Support added with AEM Forms 6.5.7.0 or later for the following platform:
    - [!DNL Microsoft&reg;&reg; SQL Server 2019]

- Sep 09, 2020

    - Changed supported version of iOS for AEM Forms App to iOS 12. The previous version was iOS 11.

-->
