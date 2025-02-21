---
title: Configuração das extensões do Acrobat Reader DC para captura de dados
description: Saiba como configurar as extensões do Acrobat Reader DC para captura de dados.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms,Document Services,Reader Extensions
source-git-commit: eded255b54ff83f60f73cece8824c778d3a87680
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Configuração das extensões do Acrobat Reader DC para captura de dados {#configuring-acrobat-reader-dc-extensions-for-data-capture}

>[!NOTE]
> 
> Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

Se os usuários da instalação do AEM Forms usarem a funcionalidade de captura de dados do Content Services (Obsoleto), será recomendável criar uma função com acesso somente leitura para esses usuários.

***Observação **: o Adobe® LiveCycle® Content Services ES (obsoleto) é um sistema de gerenciamento de conteúdo instalado com o LiveCycle. Ele permite que os usuários projetem, gerenciem, monitorem e otimizem processos centrados no ser humano. O suporte aos Content Services (obsoleto) termina em 31/12/2014. Consulte o [documento sobre o ciclo de vida do produto Adobe](https://helpx.adobe.com/br/support/programs/eol-matrix.html).*

A captura de dados exige que você atribua uma função de usuário para acessar SampleReaderExtensionsCredential. Você pode atribuir a função Administrador Confiável padrão. No entanto, considere que essa função oferece privilégios gerais de administrador de usuários não administrativos que controlam as configurações de Confiança da PKI e gerenciam Credenciais da PKI, o que pode comprometer a segurança da instalação dos AEM Forms em um ambiente de produção. Recomenda-se que o administrador do sistema do AEM Forms crie uma função que conceda somente leitura ao Armazenamento de confiança e atribua essa nova função a usuários não administradores que usam captura de dados.

## Criar uma função para usuários de captura de dados {#create-a-role-for-data-capture-users}

1. No console de administração, clique em Configurações > Gerenciamento de usuários > Gerenciamento de funções e, em seguida, clique em Nova função.
1. Insira o nome da função (por exemplo, Usuário da Captura de Dados) e a descrição nos campos apropriados, depois clique em Próximo.
1. Na tela Permissões de função, clique em Localizar permissões e selecione Leitura de credencial na lista de permissões disponíveis.
1. Clique em OK e em Finish.

## Atribuir a função de captura de dados {#assign-the-data-capture-role}

1. No console de administração, clique em Configurações > Gerenciamento de usuários > Gerenciamento de funções e clique em Localizar.
1. Clique na função de usuário de captura de dados criada.
1. Na guia Usuários/Grupos de função, clique em Localizar usuários/grupos.
1. Na tela Localizar usuários e grupos, clique em Localizar, selecione os usuários que requerem a função de usuário de captura de dados e clique em OK.
1. Na tela Editar função, clique em Salvar.
