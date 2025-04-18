---
title: Gerenciamento de credenciais HSM
description: Saiba como gerenciar credenciais HSM. Você pode gerenciar o HSM na página Gerenciamento de armazenamento de confiança. Você pode exibir, verificar, atualizar, redefinir e excluir componentes HSM.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Security
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 5e9e0371-018a-496f-aad4-04ff21391d51
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '1334'
ht-degree: 0%

---

# Gerenciamento de credenciais HSM {#managing-hsm-credentials}

Na página Gerenciamento de armazenamento de confiança, você pode gerenciar credenciais do Módulo de segurança de hardware (HSM). Um HSM é um dispositivo PKCS#11 de terceiros que você pode usar para gerar e armazenar chaves privadas com segurança. O HSM protege fisicamente o acesso e o uso das chaves privadas.

O software cliente é necessário para se comunicar com o HSM. O software cliente HSM deve ser instalado e configurado no mesmo computador que o AEM Forms.

O AEM Forms Digital Signatures pode usar credenciais armazenadas em um HSM para aplicar assinaturas digitais do lado do servidor. Siga as instruções nesta seção para criar um alias para cada credencial HSM que as assinaturas digitais usarão. O alias contém todos os parâmetros exigidos pelo HSM.

>[!NOTE]
>
>Depois de alterar a configuração do HSM, reinicie o AEM Forms Server.

## Criar um alias para uma credencial HSM quando o dispositivo HSM estiver online {#create-an-alias-for-an-hsm-credential-when-the-hsm-device-is-online}

>[!NOTE]
> 
> Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

1. No console de administração, clique em Configurações > Gerenciamento de armazenamento de confiança > Credenciais HSM e clique em Adicionar.
1. Na caixa Nome do perfil, digite uma string usada para identificar o alias. Esse valor é usado como uma propriedade para algumas operações de Assinaturas digitais, como a operação Assinar campo de assinatura.
1. Na caixa Biblioteca PKCS11, digite o caminho totalmente qualificado da biblioteca do cliente HSM no servidor. Por exemplo, `c:\Program Files\LunaSA\cryptoki.dll`. Em um ambiente de cluster, esse caminho deve ser idêntico para todos os servidores do cluster.
1. Clique em Test HSM Connectivity (Testar conectividade HSM). Se o AEM Forms puder se conectar ao dispositivo HSM, uma mensagem será exibida informando que o HSM está disponível. Clique em Avançar.
1. Use o Nome do token, a ID do slot ou o Índice da lista de slots para identificar onde as credenciais são armazenadas no HSM.

   * **Nome do Token:** Corresponde ao nome da partição HSM a ser usada (por exemplo, HSMPART1).
   * **ID do Slot:** A ID do Slot é um identificador de slot do tipo de dados long.
   * **Índice da Lista de Slots:** Se você selecionar Índice da Lista de Slots, defina as Informações de Slot para um número inteiro que corresponda ao slot. Este é um índice baseado em 0, o que significa que se o cliente for registrado primeiro com a partição HSMPART1, HSMPART1 será consultado usando o valor 0 de SlotListIndex.

1. Na caixa Token Pin, digite a senha necessária para acessar a chave HSM e clique em Next.
1. Na caixa Credenciais, selecione uma credencial. Clique em Salvar.

## Criar um alias para uma credencial HSM quando o dispositivo HSM estiver offline {#create-an-alias-for-an-hsm-credential-when-the-hsm-device-is-offline}

1. No console de administração, clique em Configurações > Gerenciamento de armazenamento de confiança > Credenciais HSM e clique em Adicionar.
1. Na caixa Nome do perfil, digite uma string usada para identificar o alias. Esse valor é usado como uma propriedade para algumas operações de Assinaturas digitais, como a operação Assinar campo de assinatura.
1. Na caixa Biblioteca PKCS11, digite o caminho totalmente qualificado da biblioteca do cliente HSM no servidor. Por exemplo, `c:\Program Files\LunaSA\cryptoki.dll`. Em um ambiente de cluster, esse caminho deve ser idêntico para todos os servidores do cluster.
1. Marque a caixa de seleção Criação de perfil offline. Clique em Avançar.
1. Na lista Dispositivo HSM, selecione o fabricante do dispositivo HSM onde a credencial está armazenada.
1. Na lista Tipo de slot, selecione ID do slot, Índice do slot ou Nome do token e especifique um valor na caixa Informações do slot. O AEM Forms usa essas configurações para determinar onde as credenciais são armazenadas no HSM.

   * **Nome do Token:** Corresponde a um nome de partição (por exemplo, HSMPART1).
   * **ID do Slot:** A ID do Slot é um número inteiro que corresponde ao slot, que por sua vez corresponde a uma partição. Por exemplo, o cliente (Forms Server) registrou-se primeiro com a partição HSMPART1. Isso mapeia o slot 1 para a partição HSMPART1 deste cliente. Como HSMPART1 é a primeira partição registrada, a ID do Slot é 1 e você definiria Informações do Slot como 1.

     A ID do slot é definida cliente por cliente. Se você registrou uma segunda máquina em uma partição diferente (por exemplo, HSMPART2 no mesmo dispositivo HSM), o slot 1 seria associado à partição HSMPART2 desse cliente.

   * **Índice de Slot:** Se você selecionar Índice de Slot, defina as Informações de Slot para um número inteiro que corresponda ao slot. Este é um índice baseado em 0, o que significa que se o cliente for registrado primeiro com a partição HSMPART1, o slot 1 será mapeado para o HSMPART1 deste cliente. Como HSMPART1 é a primeira partição registrada, o Índice de Slot é 0.

1. Selecione uma dessas opções e forneça o caminho:

   * **Certificado**: (Não é necessário se você estiver usando o SHA1) Clique em Procurar e localize o caminho para a chave pública da credencial que você está usando.
   * **SHA1 do certificado:** (Não é necessário se estiver usando um certificado físico) Digite o valor SHA1 (impressão digital) do arquivo de chave pública (.cer) da credencial que você está usando. Verifique se não há espaços usados no valor SHA1.

1. Na caixa Senha, digite a senha necessária para acessar a chave HSM para as informações de slot fornecidas e, em seguida, clique em Salvar.

## Exibir propriedades de alias de credencial HSM {#view-hsm-credential-alias-properties}

1. No console de administração, clique em Configurações > Gerenciamento de armazenamento de confiança > Credenciais HSM.
1. Clique no nome do alias da credencial para exibir as propriedades e clique em OK.

## Verificar o status de uma credencial HSM {#check-the-status-of-an-hsm-credential}

1. No console de administração, clique em Configurações > Gerenciamento de armazenamento de confiança > Credenciais HSM.
1. Clique na caixa de seleção ao lado da credencial que você deseja verificar e clique em Verificar status.

A coluna Status reflete o status atual da credencial. Se houver uma falha, um X vermelho será exibido na coluna Status. Passe o mouse sobre o X para exibir uma dica de ferramenta contendo o motivo da falha.

## Atualizar propriedades de alias de credencial HSM {#update-hsm-credential-alias-properties}

1. No console de administração, clique em Configurações > Gerenciamento de armazenamento de confiança > Credenciais HSM.
1. Clique no nome do alias da credencial.
1. Clique em Atualizar credencial e atualize as configurações conforme necessário.

## Redefinir todas as conexões HSM {#reset-all-hsm-connections}

Redefina as conexões abertas para um dispositivo HSM após qualquer interrupção na sessão de rede entre o servidor Forms e o dispositivo HSM. Por exemplo, podem ocorrer interrupções devido a uma interrupção da rede ou ao dispositivo HSM ser colocado off-line para uma atualização de software. Após uma interrupção, as conexões existentes ficam obsoletas e qualquer solicitação de assinatura nessas conexões falha. Usar a opção Redefinir todas as conexões HSM apaga as conexões antigas.

1. No console de administração, clique em Configurações > Gerenciamento de armazenamento de confiança > Credenciais HSM.
1. Clique em Redefinir todas as conexões HSM.

## Excluir um alias de credencial HSM {#delete-an-hsm-credential-alias}

1. No console de administração, clique em Configurações > Gerenciamento de armazenamento de confiança > Credenciais HSM.
1. Marque as caixas de seleção das credenciais HSM que deseja excluir, clique em Excluir e, em seguida, em OK.

## Configurar o suporte a HSM remoto {#configure-remote-hsm-support}

O AEM Forms usa um mecanismo IPC/RPC baseado em serviços da Web. Esse mecanismo permite que o AEM Forms use um HSM instalado em um computador remoto. Para usar essa funcionalidade, instale o serviço Web no computador remoto onde o HSM está instalado. Consulte [Configurando o suporte HSM para AEM Forms ES usando Sun JDK na plataforma Windows de 64 bits](https://kb2.adobe.com/cps/808/cpsid_80835.html)para obter mais informações.

Esse mecanismo não oferece suporte à criação online de perfis HSM ou verificações de status. No entanto, há duas maneiras de criar perfis HSM e executar verificações de status:

* Crie uma credencial de cliente do AEM Forms transmitindo-a ao Certificado do signatário. Siga as etapas em [Configurando o suporte HSM para o AEM Forms ES usando o Sun JDK na plataforma Windows de 64 bits](https://kb2.adobe.com/cps/808/cpsid_80835.html). O local do serviço Web é passado como uma propriedade de credencial. Perfis HSM offline criados usando o certificado der ou o certificado SHA-1 hex também são compatíveis. No entanto, se você tiver atualizado para o AEM Forms de uma versão anterior do AEM Forms, faça alterações no cliente, pois a credencial continha informações de certificado e serviço da Web.
* O local do Serviço Web está especificado no console de administração para o serviço de Assinatura. (Consulte [Configurações do serviço de assinatura](/help/forms/using/admin-help/configure-service-settings.md#signature-service-settings).) Aqui, o cliente carregou apenas o alias do perfil HSM no armazenamento de confiança. Você pode usar essa opção facilmente sem fazer alterações no cliente, mesmo se tiver atualizado para o AEM Forms de uma versão anterior do AEM Forms. Essa opção não é compatível com perfis HSM que usam o certificado SHA-1.
