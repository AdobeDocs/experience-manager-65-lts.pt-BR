---
title: Disponibilizar fontes
description: Verifique se as fontes usadas em um formulário estão disponíveis para uso no servidor de aplicativos J2EE que hospeda o AEM Forms.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 2861bde5-b373-4ab2-9808-7d32ef1dc925
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 2%

---

# Disponibilizar fontes {#make-fonts-available}

>[!NOTE]
> 
> Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

Verifique se as fontes usadas em um formulário estão disponíveis para uso no servidor de aplicativos J2EE que hospeda o AEM Forms. Por exemplo, considere o cenário a seguir. Um designer de formulários adiciona uma fonte ao diretório de fontes que o Designer usa e cria um formulário que usa essa fonte em um computador separado. Para que o Serviço de saída use a fonte, coloque-a no diretório de fontes do cliente. Se o diretório de fontes do cliente não existir, crie um diretório no servidor de aplicativos J2EE que hospeda o AEM Forms.

Para obter informações sobre configurações de fonte adicionais, consulte [Definir configurações gerais de formulários do AEM](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings).

**Especificar o local do diretório de fontes do Cliente**

1. No console de administração, clique em Configurações > Configurações dos sistemas principais > Configurações.
1. Na caixa Localização do Diretório de fontes do sistema, digite o caminho para o diretório de fontes do cliente. É possível adicionar vários diretórios, separados por ponto-e-vírgula **;**
1. Clique em OK.
1. Reinicie o sistema em que o AEM Forms está instalado.

>[!NOTE]
>
>As fontes são selecionadas do cache de fontes do sistema Windows e é necessário reiniciar o sistema para atualizar o cache. Depois de especificar o diretório de fontes do Cliente, reinicie o sistema no qual o AEM Forms está instalado.
