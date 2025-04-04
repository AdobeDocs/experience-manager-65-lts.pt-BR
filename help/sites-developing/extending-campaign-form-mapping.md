---
title: Criação de mapeamentos de formulário personalizados
description: Ao criar uma tabela personalizada no Adobe Campaign, talvez você queira criar um formulário no AEM que mapeie para essa tabela personalizada
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# Criação de mapeamentos de formulário personalizados{#creating-custom-form-mappings}

Ao criar uma tabela personalizada no Adobe Campaign, talvez você queira criar um formulário no AEM que mapeie para essa tabela personalizada.

Este documento descreve como criar mapeamentos de formulário personalizados. Ao concluir as etapas deste documento, você fornecerá aos usuários uma página de evento na qual eles poderão se inscrever para um evento futuro. Em seguida, acompanhe esses usuários por meio do Adobe Campaign.

## Pré-requisitos {#prerequisites}

Você precisa ter o seguinte instalado:

* Adobe Experience Manager
* Adobe Campaign Classic

Consulte [Integrando o AEM com o Adobe Campaign Classic](/help/sites-administering/campaignonpremise.md) para obter mais informações.

## Criação de mapeamentos de formulário personalizados {#creating-custom-form-mappings-2}

Para criar mapeamentos de formulário personalizados, você precisa seguir essas etapas de alto nível, que são descritas detalhadamente nas seguintes seções:

1. Criar uma tabela personalizada.
1. Estender a tabela **seed**.
1. Crie um mapeamento personalizado.
1. Crie um delivery com base no mapeamento personalizado.
1. Crie o formulário no AEM, que usará o delivery criado.
1. Envie o formulário para testá-lo.

### Criação da tabela personalizada no Adobe Campaign {#creating-the-custom-table-in-adobe-campaign}

Comece criando uma tabela personalizada no Adobe Campaign. Neste exemplo, estamos usando a seguinte definição para criar uma tabela de eventos:

```xml
<element autopk="true" label="Event" labelSingular="Event" name="event">
 <attribute label="Event Date" name="eventdate" type="date"/>
 <attribute label="Event Name" name="eventname" type="string"/>
 <attribute label="Email" name="email" type="string"/>
 <attribute label="Number of Seats" name="seats" type="long"/>
</element>
```

Depois de criar a tabela de eventos, execute o **Assistente de atualização da estrutura do banco de dados** para criar a tabela.

### Extensão da Seed Table {#extending-the-seed-table}

No Adobe Campaign, selecione **Adicionar** para criar uma extensão da tabela **Seed addresses (nms)**.

![chlimage_1-194](assets/chlimage_1-194.png)

Agora, use os campos da tabela **event** para estender a tabela **seed**:

```xml
<element label="Event" name="custom_cus_event">
 <attribute name="eventname" template="cus:event:event/@eventname"/>
 <attribute name="eventdate" template="cus:event:event/@eventdate"/>
 <attribute name="email" template="cus:event:event/@email"/>
 <attribute name="seats" template="cus:event:event/@seats"/>
 </element>
```

Depois disso, execute o **Assistente de atualização de banco de dados** para aplicar as alterações.

### Criação de target mapping personalizado {#creating-custom-target-mapping}

Em **Administração/Gerenciamento de Campanha** t, vá para **Target Mappings** e adicione um novo T **Target Mapping.**

>[!NOTE]
>
>Use um nome significativo para **Nome interno**.

![chlimage_1-195](assets/chlimage_1-195.png)

### Criação de um template de delivery personalizado {#creating-a-custom-delivery-template}

Nesta etapa, você está adicionando um modelo de entrega que usa o **Target mapping** criado.

Em **Recursos/Modelos**, navegue até o Modelo de Entrega e duplique a entrega existente do AEM. Ao clicar em **Para**, selecione o evento de criação **Target mapping**.

![chlimage_1-196](assets/chlimage_1-196.png)

### Criação do formulário no AEM {#building-the-form-in-aem}

No AEM, verifique se você configurou uma Cloud Service em **Propriedades da página**.

Em seguida, na guia **Adobe Campaign**, selecione a entrega criada em [Criação de um Modelo de Entrega Personalizado](#creating-a-custom-delivery-template).

![chlimage_1-197](assets/chlimage_1-197.png)

Ao configurar os campos, especifique nomes de elemento exclusivos para os campos de formulário.

Após a configuração dos campos, é necessário alterar manualmente o mapeamento.

No CRXDE-lite, vá para o nó **jcr:content** (da página) e altere o valor **acMapping** para o nome interno do **Target mapping**.

![chlimage_1-198](assets/chlimage_1-198.png)

Na configuração do formulário, marque a caixa de seleção para criar se não existir

![chlimage_1-199](assets/chlimage_1-199.png)

### Envio do formulário {#submitting-the-form}

Agora você pode enviar o formulário e validar no lado do Adobe Campaign se os valores são salvos.

![chlimage_1-200](assets/chlimage_1-200.png)

## Resolução de problemas {#troubleshooting}

**&quot;Tipo inválido para o valor &#39;02/02/2015&#39; do elemento &#39;@eventdate&#39; (documento do tipo &#39;Evento ([adb:event])&#39;)&quot;**

Ao enviar o formulário, este erro é registrado no **error.log** no AEM.

Isso se deve a um formato inválido para o campo de data. A solução alternativa é fornecer **aaaa-mm-dd** como o valor.
