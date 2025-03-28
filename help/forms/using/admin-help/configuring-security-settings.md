---
title: Definição das configurações de segurança
description: Saiba como definir configurações de segurança. Você pode proteger documentos do PDF limitando o acesso. Você pode criptografar, certificar ou proteger o documento por senha.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: PDF Generator,Document Security
solution: Experience Manager, Experience Manager Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: fee34d9e-6606-40c1-bbbe-e7975ad90a22
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '1430'
ht-degree: 0%

---

# Definição das configurações de segurança{#configuring-security-settings}

É possível limitar o acesso a documentos do PDF definindo senhas e restringindo determinados recursos, como impressão e edição. Quando um documento do PDF tem recursos restritos, as ferramentas e os itens de menu relacionados a esses recursos ficam esmaecidos. Você também pode usar outros métodos para criar documentos seguros, como criptografar ou certificar um documento. Uma configuração de segurança contém a senha e as opções específicas a serem usadas para determinadas conversões do PDF.

Na página Configurações de segurança, é possível executar as seguintes tarefas:

## Criar ou editar uma configuração de segurança {#create-or-edit-a-security-setting}

>[!NOTE]
> 
> Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

Uma *configuração de segurança* controla a segurança e as permissões para arquivos convertidos com essa configuração de segurança.

1. No console de administração, clique em Serviços > PDF Generator > Configurações de segurança.
1. Clique em Novo ou clique no nome de uma configuração de segurança.
1. Na página Novo/Editar configuração de segurança, preencha as informações necessárias para a configuração de segurança. (Consulte [Definir configurações de tipo de arquivo](/help/forms/using/admin-help/configuring-file-type-settings.md#configuring-file-type-settings).)
1. Clique em Salvar e, na caixa de diálogo exibida, digite um nome para a configuração e clique em OK.

### Configurações de segurança {#security-settings}

Essas configurações definem a compatibilidade e a criptografia. Para obter instruções sobre como acessar as configurações de fontes, consulte [Criar ou editar uma configuração de segurança](configuring-security-settings.md#create-or-edit-a-security-setting).

**Compatibilidade:** define o tipo de criptografia para abrir um documento protegido por senha. A opção Acrobat 3.0 e posterior usa um nível de criptografia baixo, mas as outras opções usam um nível de criptografia alto:

**Acrobat 3.0 E Posterior:** Usa baixa criptografia (RC4 de 40 bits).

**Acrobat 5.0 E Posterior:** Usa criptografia alta (RC4 de 128 bits).

**Acrobat 6.0 E Posterior:** Usa criptografia alta (RC4 de 128 bits). Essa opção permite ativar metadados para pesquisa.

**Acrobat 7.0 E Posterior:** Usa criptografia alta (AES de 128 bits). Essa opção permite ativar metadados para pesquisar e criptografar apenas anexos de arquivo.

**Acrobat 9.0 E Posterior:** Usa criptografia alta (AES de 256 bits). Essa opção permite ativar metadados para pesquisar e criptografar apenas anexos de arquivo.

Uma versão anterior do Acrobat não pode abrir um documento do PDF com uma configuração de compatibilidade mais alta. Por exemplo, se você selecionar a opção Acrobat 7.0 e posterior, não será possível abrir o documento no Acrobat 6.0 ou anterior.

Verifique se o nível de compatibilidade é consistente com o nível de compatibilidade do PDF para a mesma origem. Por exemplo, se você tiver uma pasta monitorada configurada para usar a configuração Padrão do PDF, que é compatível com o Acrobat 5.0 ou posterior, o nível de compatibilidade de segurança não deverá ser superior ao Acrobat 5.0.

**Restrição de Documento:** As restrições de documento disponíveis dependem da opção de Compatibilidade selecionada.

**Sem criptografia:** não criptografa nenhuma parte do documento.

**Criptografar Todo o Conteúdo do Documento:** Criptografa o documento e os metadados do documento. Quando essa opção é selecionada, os mecanismos de pesquisa não podem acessar os metadados do documento.

**Criptografar Todo O Conteúdo Do Documento Exceto Os Metadados (Acrobat
Compatível com 6 e posterior):** criptografa o conteúdo de um documento, mas ainda permite que os mecanismos de pesquisa acessem os metadados do documento. Essa opção está disponível somente quando a opção Compatibilidade está definida como Acrobat 6.0 ou posterior, Acrobat 7.0 ou posterior, ou Acrobat 9.0 ou posterior.

**Criptografar Somente Anexos De Arquivo (Acrobat 7 E Posterior
Compatível):** Os usuários podem abrir o documento sem uma senha, mas devem digitar uma senha para abrir anexos de arquivo. Essa opção está disponível somente quando a opção Compatibilidade está definida como Acrobat 7.0 ou posterior, ou Acrobat 9.0 ou posterior.

Essas configurações definem a segurança de senha:

>[!NOTE]
>
>Se você esquecer uma senha, ela não poderá ser recuperada do documento. É recomendável que você armazene as senhas em outro local seguro, caso as esqueça. Além disso, mantenha uma cópia de backup do documento que não esteja protegida por senha.

**Exigir Senha para Abrir o Documento:** Habilita as opções de senha.

**Senha para Abrir Documento:** Impede que os usuários abram o documento, a menos que digitem a senha especificada. As senhas diferenciam maiúsculas de minúsculas. A Acrobat usa o método RC4 de segurança da RSA Security Inc. para proteger documentos da PDF com senha. Se você estiver restringindo a impressão e a edição, é recomendável adicionar uma senha para abrir documentos para aumentar a segurança.

**Senha para abrir documento do Retype:** verifique se a senha para abrir o documento está correta.

**Exigir Senha para Abrir Anexos de Arquivo:** Habilita as opções de senha. Essa opção estará disponível somente quando a opção Compatibilidade estiver definida como Acrobat 7.0 ou posterior, ou Acrobat 9.0 ou posterior, e a opção Restrição de documento estiver definida como Criptografar somente anexos de arquivo.

**Senha de Abertura do Anexo de Arquivo:** Garante que seja necessária uma senha para abrir um anexo de arquivo. Os usuários podem abrir o documento sem uma senha. Essa opção estará disponível somente quando a opção Compatibilidade estiver definida como Acrobat 7.0 ou posterior, ou Acrobat 9.0 ou posterior, e a opção Restrição de documento estiver definida como Criptografar somente anexos de arquivo.

**Anexo de Arquivo do Retype:** Garante que a senha esteja correta. Essa opção estará disponível somente quando a opção Compatibilidade estiver definida como Acrobat 7.0 ou posterior, ou Acrobat 9.0 ou posterior, e a opção Restrição de documento estiver definida como Criptografar somente anexos de arquivo.

Essas opções configuram as permissões:

**Usar Uma Senha Para Restringir A Impressão E A Edição De
O documento e suas configurações de segurança:** Habilita restrições de permissões.

**Senha de Permissões:** Impede que os usuários imprimam e editem. Os usuários não podem alterar essas configurações de segurança, a menos que digitem a senha especificada. Não é possível usar a mesma senha usada para a Senha para abrir o documento. Ao definir uma senha de permissões, somente as pessoas que digitarem essa senha poderão alterar as configurações de segurança. Se o documento do PDF tiver os dois tipos de senha, qualquer uma delas o abrirá. No entanto, um usuário só pode definir ou alterar os recursos restritos com a senha de permissões. Se o documento do PDF tiver somente a senha de permissão ou se um usuário abrir o documento usando a senha de abertura do documento, o prompt de senha será exibido quando o usuário tentar alterar as configurações de segurança.

**Senha de Permissões do Retype:** Verifique se a senha das permissões está correta.

**Impressão Permitida:** Especifica a qualidade de impressão do documento PDF:

**Nenhum:** impede que os usuários imprimam o documento.

**Baixa Resolução (150 dpi):** Permite que os usuários imprimam o documento com uma resolução não superior a 150 dpi. A impressão pode ser mais lenta porque cada página é impressa como uma imagem bitmap. Essa opção só estará disponível se um nível de criptografia alto (Acrobat 5.0, 6.0, 7.0 ou 9.0) for selecionado.

**Alta Resolução:** permite que os usuários imprimam em qualquer resolução, direcionando a saída vetorial de alta qualidade para a PostScript e outras impressoras que oferecem suporte a recursos de impressão avançados de alta qualidade.

**Alterações permitidas:** Define quais ações de edição são permitidas no documento do PDF:

**Nenhum:** impede que os usuários alterem o documento, incluindo o preenchimento de campos de assinatura e formulário.

**Inserir, Excluir e Girar Páginas:** Permite que os usuários insiram, excluam e girem páginas, além de criar marcadores e páginas de miniatura. Essa opção só estará disponível se um nível de criptografia alto (Acrobat 5.0, 6.0, 7.0 ou 9.0) for selecionado.

**Preencher Campos De Formulário E Assinar Assinatura Existente
Campos:** Permite que os usuários preencham formulários e adicionem assinaturas digitais. No entanto, os usuários não podem adicionar comentários ou criar campos de formulário. Essa opção só estará disponível se um nível de criptografia alto (Acrobat 5.0, 6.0, 7.0 ou 9.0) for selecionado.

**Comentar, Preencher Campos De Formulário E Assinar Itens Existentes
Campos de assinatura:** Permite que os usuários preencham formulários e adicionem assinaturas digitais e comentários.

**Layout Da Página, Retoque, Preenchimento De Campos De Formulário E Assinatura
Campos de assinatura existentes:** permite que os usuários insiram, girem ou excluam páginas e criem marcadores ou imagens em miniatura, preencham formulários e adicionem assinaturas digitais. Essa opção não permite que os usuários criem campos de formulário. Essa opção só estará disponível se um nível de criptografia baixo (Acrobat 3.0) for selecionado.

**Qualquer Página Exceto a Extração:** Permite que os usuários alterem o documento usando qualquer método na Lista de permissões Alterações, exceto remover páginas.

**Habilitar Cópia de Texto, Imagens e Outro Conteúdo:** Permite que os usuários selecionem e copiem o conteúdo do documento PDF. Ele também permite que os utilitários que precisam de acesso ao conteúdo de um arquivo do PDF, como o Acrobat Catalog, acessem esse conteúdo. Essa opção só estará disponível se um nível de criptografia alto for selecionado.

**Habilitar O Acesso Ao Texto De Dispositivos Screen Reader Para O
Deficientes Visuais:** permite que os usuários com deficiências visuais leiam o documento usando leitores de tela. No entanto, os usuários não podem copiar ou extrair o conteúdo do documento. Essa opção só estará disponível se um nível de criptografia alto for selecionado.

## Excluir uma configuração de segurança {#delete-a-security-setting}

É possível excluir uma configuração de segurança se ela não for mais necessária. No entanto, as configurações de segurança pré-definidas não podem ser excluídas.

1. No console de administração, clique em **[!UICONTROL Serviços > PDF Generator > Configurações de Segurança]**.
1. Marque a caixa de seleção ao lado da configuração a ser excluída. Você pode selecionar várias configurações.
1. Clique em **[!UICONTROL Excluir]** e na página **[!UICONTROL Excluir confirmação]**, clique novamente em **[!UICONTROL Excluir]**.
