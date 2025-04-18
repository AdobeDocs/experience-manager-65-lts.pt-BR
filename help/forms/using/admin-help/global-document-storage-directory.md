---
title: Diretório de armazenamento de documentos global
description: O diretório de armazenamento global de documentos (GDS) é um diretório usado para armazenar arquivos de longa duração que são usados em um processo.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 9a93b8f9-33cb-4aec-81e0-a1146bba955a
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 1%

---

# Diretório de armazenamento de documentos global{#global-document-storage-directory}

O diretório *GDS (armazenamento global de documentos)* é um diretório usado para armazenar arquivos de longa duração que são usados em um processo. Esses arquivos incluem PDFs, políticas e modelos de formulário. Arquivos de longa duração são uma parte essencial do estado geral de muitas implantações de formulários AEM. Se alguns ou todos os documentos de longa duração forem perdidos ou corrompidos, o Forms Server poderá se tornar instável. Os documentos de entrada para invocações de trabalho assíncrono também são armazenados no diretório GDS e devem estar disponíveis para processar solicitações. É importante considerar a confiabilidade do sistema de arquivos que hospeda o diretório GDS. Use um storage redundante de discos independentes (RAID) ou outra tecnologia, conforme apropriado para suas necessidades de qualidade e nível de serviço.

Arquivos de longa duração podem conter informações confidenciais do usuário. Essas informações podem exigir credenciais especiais quando acessadas usando as APIs de formulários do AEM ou as interfaces do usuário. É importante que o diretório GDS seja adequadamente protegido pelo sistema operacional. Somente a conta de administrador usada para executar o servidor de aplicativos deve ter acesso de leitura/gravação ao diretório GDS.

Além de selecionar um diretório seguro e altamente disponível para GDS, você também pode optar por habilitar o armazenamento de documentos no banco de dados. Observe que mesmo com o uso do banco de dados do AEM Forms para armazenamento de documentos, o AEM Forms ainda exige o diretório GDS. (Consulte [Opções de backup quando o banco de dados for usado para armazenamento de documentos](/help/forms/using/admin-help/files-back-recover.md#backup-options-when-database-is-used-for-document-storage).)

Os dados do aplicativo do AEM Forms residem no diretório GDS e no banco de dados do AEM Forms. A tabela a seguir descreve os dados e seus locais.

<table>
 <thead>
  <tr>
   <th><p>Dados de formulários do AEM</p></th>
   <th><p>Banco de dados</p></th>
   <th><p>GDS</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>Dados de aplicativos (usuários, funções, processos, políticas, endpoints, eventos etc.)</p></td>
   <td><p>Sim</p></td>
   <td><p>Não</p></td>
  </tr>
  <tr>
   <td><p>Contêineres de serviço implantados</p></td>
   <td><p>Sim</p></td>
   <td><p>Não</p></td>
  </tr>
  <tr>
   <td><p>Gerenciador de documentos </p></td>
   <td><p>Não</p></td>
   <td><p>Sim</p></td>
  </tr>
  <tr>
   <td><p>Repositório do Forms</p></td>
   <td><p>Sim</p></td>
   <td><p>Não</p></td>
  </tr>
  <tr>
   <td><p>Configuração do sistema</p></td>
   <td><p>Sim</p></td>
   <td><p>Não</p></td>
  </tr>
  <tr>
   <td><p>Pastas monitoradas</p></td>
   <td><p>Não</p></td>
   <td><p>Sim</p></td>
  </tr>
 </tbody>
</table>

## Configuração do diretório GDS {#configuring-the-gds-directory}

A localização do diretório GDS pode ser configurada manualmente durante o processo de instalação dos formulários AEM. Se a configuração de local permanecer vazia durante a instalação, o local assumirá como padrão um diretório na instalação do servidor de aplicativos da seguinte maneira:

* (JBoss) `[appserver root]/server/[type]/svcnative/DocumentStorage`
* (WebLogic) `[appserverdomain]/'server'/adobe/DocumentServer/DocumentStorage`
* (WebSphere) `[appserver root]/installedApps/adobe/'server'/DocumentStorage`

## Alterar a localização padrão do GDS {#change-the-default-gds-location}

Você poderá alterar a localização do GDS no console de administração após a conclusão da instalação dos formulários do AEM. Realoque manualmente os dados para concluir o processo.

>[!NOTE]
>
>* Migre os dados da seguinte maneira ou ocorrerá perda de dados.
>* Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

1. Faça logon no console de administração e clique em Configurações > Configurações do sistema principal > Configurações.
1. Na caixa Diretório de armazenamento de documentos global, digite o caminho completo para o novo diretório GDS e clique em OK.
1. Desative imediatamente o servidor de aplicativos.
1. Mova todos os arquivos do diretório GDS antigo para o novo local, mantendo a estrutura do diretório interno.
1. Reinicie o servidor de aplicativos.

## Sobre Arquivos de Implantação {#about-deployment-files}

Os formulários do AEM consistem em dois tipos de arquivos de implantação, os contêineres de serviço e os arquivos EAR da Plataforma Java 2, Enterprise Edition (J2EE). Os arquivos EAR consistem em pacotes de aplicativos J2EE padrão que contêm a funcionalidade principal dos formulários AEM. Os arquivos EAR específicos do servidor de aplicativos são os seguintes:

* adobe-core-*[appserver]*.ear
* adobe-core-*[appserver]*-*[OS]*.ear

A implementação do AEM Forms envolve a implantação dos arquivos EAR montados e dos arquivos de suporte no servidor de aplicativos em que você planeja executar a solução AEM Forms. Se você configurou e montou vários módulos, os módulos implantáveis são empacotados dentro dos arquivos EAR implantáveis. Para implantar esses arquivos, copie-os no diretório *[home do appserver]*\server\all\deploy.

Módulos e arquivos de arquivamento de formulários do AEM são empacotados em arquivos JAR. Como não são arquivos do tipo J2EE, eles não são implantados no servidor de aplicativos. Em vez disso, eles são copiados para o diretório GDS e uma referência a seu local é armazenada no banco de dados do AEM Forms. Por esse motivo, o diretório GDS deve ser compartilhado entre todos os nós do cluster. Todos os nós devem ter acesso ao diretório de armazenamento central para os DSCs.

>[!NOTE]
>
>Antes de disponibilizar os contêineres de serviço, certifique-se de ter criado e configurado o diretório GDS. (Consulte [Configurando o diretório GDS](global-document-storage-directory.md#configuring-the-gds-directory))
