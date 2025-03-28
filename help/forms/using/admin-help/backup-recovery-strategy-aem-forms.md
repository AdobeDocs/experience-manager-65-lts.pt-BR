---
title: Estratégia de backup e recuperação para formulários AEM
description: Saiba como implementar uma estratégia para fazer backup de dados e garantir que eles permaneçam em sincronia com os dados de formulários do AEM.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 2f34b48a-0b95-4994-ac4f-616620a5b211
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '1518'
ht-degree: 0%

---

# Estratégia de backup e recuperação para formulários AEM{#backup-and-recovery-strategy-for-aem-forms}

Se sua implementação do AEM Forms armazenar dados personalizados adicionais em um banco de dados diferente, você será responsável por implementar uma estratégia para fazer backup desses dados e garantir que eles permaneçam sincronizados com os dados do AEM Forms. Além disso, o aplicativo deve ser projetado de modo que seja robusto o suficiente para lidar com um cenário em que os bancos de dados adicionais fiquem fora de sincronia. É altamente recomendável que qualquer operação de banco de dados executada seja feita no contexto de uma transação para ajudar a manter um estado consistente.

Depois de identificar como o AEM Forms é usado, determine quais arquivos devem ser incluídos no backup, com que frequência e a janela de backup a ser disponibilizada.

>[!NOTE]
>
>Assim como em qualquer outro aspecto da implementação de formulários AEM, sua estratégia de backup e recuperação deve ser desenvolvida e testada em um ambiente de desenvolvimento ou de preparo antes de ser usada na produção, para garantir que toda a solução funcione como esperado sem perda de dados.

O Adobe Experience Manager (AEM) é parte integrante do AEM Forms. Portanto, é necessário fazer backup do AEM em sincronia com o backup do AEM Forms, pois a Solução de Gerenciamento de Correspondência e serviços, como o gerenciador de formulários, são baseados em dados armazenados na parte AEM dos formulários do AEM.Para evitar perda de dados, o backup dos dados específicos dos formulários do AEM deve ser feito de forma a garantir que o GDS e o AEM (repositório) estejam correlacionados com as referências do banco de dados.O banco de dados, o GDS, o AEM e os diretórios raiz de armazenamento de conteúdo devem ser restaurados para um computador com o mesmo nome DNS do original.

## Tipos de backups {#types-of-backups}

A estratégia de backup do AEM Forms envolve dois tipos de backups:

**Imagem do sistema:** um backup completo do sistema que você pode usar para restaurar o conteúdo do computador se o disco rígido ou o computador inteiro parar de funcionar. Um backup de imagem do sistema é necessário somente antes da implantação em produção dos formulários do AEM. As políticas corporativas internas determinam a frequência com que os backups de imagem do sistema são necessários.

**Dados específicos de formulários do AEM:** Os dados de aplicativo existem no banco de dados, no Armazenamento Global de Documentos (GDS) e no repositório do AEM e devem ser copiados em backup em tempo real. O GDS é um diretório usado para armazenar arquivos de longa vida usados em um processo. Esses arquivos podem incluir PDFs, políticas ou modelos de formulário.

>[!NOTE]
>
>Se o Content Services (Obsoleto) estiver instalado, faça também o backup do diretório raiz do armazenamento de conteúdo. Consulte [Diretório raiz do armazenamento de conteúdo (somente Content Services)](/help/forms/using/admin-help/files-back-recover.md#content-storage-root-directory-content-services-only).

O banco de dados é usado para armazenar artefatos de formulário, configurações de serviço, estado do processo e referências de banco de dados para arquivos GDS. Se você ativou o armazenamento de documentos no banco de dados, os dados e documentos persistentes no GDS também serão armazenados no banco de dados. O backup e a recuperação do banco de dados podem ser feitos usando os seguintes métodos:

* O modo **Backup de instantâneo** indica que o sistema de formulários do AEM está no modo de backup indefinidamente ou por um número especificado de minutos, após o qual o modo de backup não será mais habilitado. Para entrar ou sair do modo de backup de snapshot, você pode usar uma das opções a seguir. Após um cenário de recuperação, o modo de backup de snapshot não deve ser ativado.

   * Use a página Definições de Backup no Console de Administração. Para entrar no modo de instantâneo, marque a caixa de seleção Operar no modo de backup seguro. Desmarque a caixa de seleção para sair do modo de instantâneo.
   * Use o script LCBackupMode (consulte [Fazer backup do banco de dados, do GDS e dos diretórios Raiz de Armazenamento de Conteúdo](/help/forms/using/admin-help/backing-aem-forms-data.md#back-up-the-database-gds-aem-repository-and-content-storage-root-directories)). Para sair do modo de backup de instantâneo, no argumento de script, defina o parâmetro `continuousCoverage` como `false` ou use a opção `leaveContinuousCoverage`.
   * Use a API de Backup/Recuperação fornecida. <!-- Fix broken link(see AEM forms API Reference section on AEM Forms Help and Tutorials page).-->

* **O modo de backup contínuo** indica que o sistema está sempre no modo de backup, com uma nova sessão de modo de backup sendo iniciada assim que a sessão anterior é lançada. Não há tempo limite associado ao modo de backup contínuo. Quando o script ou as APIs LCBackupMode são chamados para deixar o modo de backup contínuo, uma nova sessão de modo de backup contínuo é iniciada. Esse modo é útil para oferecer suporte a backups contínuos, mas ainda permitir que documentos antigos e desnecessários sejam removidos do diretório GDS. O modo de backup contínuo não é suportado pela página Backup e Recuperação. Após um cenário de recuperação, o modo de backup contínuo ainda é ativado. Você pode sair do modo de backup contínuo (modo de backup contínuo) usando o script LCBackupMode com a opção `leaveContinuousCoverage`.

>[!NOTE]
>
>Sair do modo de backup contínuo faz com que uma nova sessão de modo de backup comece imediatamente. Para desabilitar completamente o modo de backup acumulado, use a opção `leaveContinuousCoverage` no script, que substitui a sessão de backup acumulado existente. Quando estiver no modo de backup de snapshot, você poderá deixar o modo de backup como costuma fazer.

Para evitar a perda de dados, o backup dos dados específicos dos formulários AEM deve ser feito de forma a garantir que os documentos do GDS e do diretório raiz de armazenamento de conteúdo estejam correlacionados com as referências do banco de dados.

>[!NOTE]
>
>Quando o GDS estiver armazenado no sistema de arquivos e não no banco de dados, execute o backup do banco de dados antes do backup do GDS.

## Considerações especiais para backup e recuperação {#special-considerations-for-backup-and-recovery}

Use as diretrizes a seguir se precisar recuperar formulários do AEM em um ambiente diferente devido às seguintes alterações:

* Alteração no endereço IP, no nome do host ou na porta do AEM Forms Server
* Alteração nas letras de unidade ou no caminho do diretório
* Alterar para outro host de banco de dados, porta ou nome

Normalmente, esses cenários de recuperação são causados por falha de hardware do servidor que hospeda o servidor de aplicativos, o servidor de banco de dados ou o Forms Server. Além das configurações específicas dos formulários do AEM descritas nesta seção, você também deve fazer as alterações necessárias para outras partes da implantação dos formulários do AEM, como balanceadores de carga e firewalls, se o nome do host ou endereço IP de um servidor do AEM Forms for alterado.

### O que não pode ser alterado {#what-cannot-be-changed}

Mesmo que você possa alterar o servidor de banco de dados e muitos outros parâmetros, não será possível alterar o tipo de servidor de aplicativos ou o tipo de banco de dados ao recuperar formulários AEM de um backup. Por exemplo, se estiver recuperando um backup de formulários do AEM, você não poderá alterar o servidor de aplicativos de JBoss para WebLogic ou o banco de dados de Oracle para DB2. Além disso, os formulários recuperados do AEM devem usar os mesmos caminhos do sistema de arquivos, como o diretório de fontes.

### Reiniciando após uma recuperação {#restarting-after-a-recovery}

Antes de reiniciar o Forms Server após uma recuperação, faça o seguinte:

1. Inicie o sistema no modo de manutenção.
1. Faça o seguinte para garantir que o Gerenciador de formulários seja sincronizado com o AEM Forms no modo de manutenção:

   1. Acesse https://&lt;*server*>:&lt;*port*>/lc/fm e faça logon usando as credenciais de administrador/senha.
   1. Clique no nome do usuário (neste caso, Super Administrator) no canto superior direito.
   1. Clique em **Opções de Administração**.
   1. Clique em **Iniciar** para sincronizar ativos do repositório.

1. Em um ambiente em cluster, o nó primário (em relação ao AEM) deve estar ativo antes dos nós secundários.
1. Certifique-se de que nenhum processo seja iniciado a partir de fontes internas ou externas, como iniciadores de processos da Web, SOAP ou EJB, até que a operação normal do sistema seja validada.

Se o banco de dados principal do AEM Forms for movido ou alterado, consulte os Guias de instalação relevantes para o servidor de aplicativos para obter informações sobre como atualizar as informações de conexão do banco de dados para as fontes de dados do AEM Forms IDP_DS e EDC_DS.

>[!NOTE]
> 
> É recomendável usar o comando &#39;Ctrl + C&#39; para reiniciar o SDK. Reiniciar o AEM SDK usando métodos alternativos, por exemplo, parar processos Java, pode levar a inconsistências no ambiente de desenvolvimento do AEM.

### Alteração do nome do host ou endereço IP dos formulários do AEM {#changing-the-aem-forms-hostname-or-ip-address}

Em um cluster, se você usar o cache TCP em vez de UDP, atualize a configuração do localizador de cache. Consulte &quot;Configurar os localizadores de cache (armazenamento em cache usando apenas TCP)&quot; no guia de configuração relevante para o servidor de aplicativos.

### Alteração dos caminhos do sistema de arquivos do nó dos formulários do AEM {#changing-the-aem-forms-node-file-system-paths}

Se você alterar os caminhos do sistema de arquivos para um nó independente, deverá atualizar as referências apropriadas nas preferências, em outras configurações do sistema, em aplicativos personalizados e em aplicativos AEM forms implantados. Por outro lado, para um cluster, todos os nós devem usar a mesma configuração de caminho do sistema de arquivos. Defina o diretório raiz do Armazenamento de Documentos Globais (GDS) e verifique se ele aponta para uma cópia do GDS recuperado que esteja sincronizada com o banco de dados recuperado. A definição do caminho GDS é importante porque o GDS pode conter dados destinados a persistir durante reinicializações do servidor de aplicativos.

Em um ambiente em cluster, a configuração do caminho do sistema de arquivos do repositório deve ser a mesma para todos os nós de cluster antes do backup e depois da recuperação.

Use o script `LCSetGDS` na pasta `[*aem-forms root]*\sdk\misc\Foundation\SetGDSCommandline` para definir o caminho GDS depois de alterar os caminhos do sistema de arquivos. Consulte o arquivo `ReadMe.txt` na mesma pasta para obter detalhes. Se o caminho de diretório GDS antigo não puder ser usado, o script `LCSetGDS` deverá ser usado para definir o novo caminho para o GDS antes de você iniciar os formulários do AEM.

>[!NOTE]
>
>Essa circunstância é a única sob a qual você deve usar esse script para alterar a localização do GDS. Para alterar a localização do GDS enquanto o AEM Forms estiver em execução, use o Console de Administração. (Consulte [Definir configurações gerais de formulários do AEM](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings)*.) *

Depois de definir o caminho GDS, inicie o Forms Server no modo de manutenção e use o console de administração para atualizar os caminhos restantes do sistema de arquivos para o novo nó. Depois de verificar se todas as configurações necessárias foram atualizadas, reinicie e teste o AEM Forms.
