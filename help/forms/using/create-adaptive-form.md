---
title: 'Tutorial: Criar um formulário adaptável'
description: Saiba como criar, fazer layout e pré-visualizar um formulário adaptável. Além disso, aprenda a configurar ações de envio.
feature: Adaptive Forms
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '1314'
ht-degree: 9%

---

# Tutorial: Criar um formulário adaptável {#do-not-publish-tutorial-create-an-adaptive-form}

![02-criar-forma-adaptável-imagem-principal](assets/02-create-adaptive-form-main-image.png)

Este tutorial é uma etapa da série [Criar o primeiro formulário adaptável](/help/forms/using/create-your-first-adaptive-form.md). É recomendável seguir a série em sequência cronológica para entender, executar e demonstrar o caso de uso completo do tutorial.

## Sobre o tutorial {#about-the-tutorial}

Formulários adaptáveis são formulários de nova geração que são dinâmicos e responsivos. Você pode usar formulários adaptáveis para fornecer experiências personalizadas. Você também pode integrar formulários adaptáveis com [!DNL Adobe Analytics] para estatísticas de uso e [!DNL Adobe Campaign] para gerenciamento de campanha. Para obter mais informações sobre os recursos de formulários adaptáveis, consulte [Introdução à criação de formulários adaptáveis](/help/forms/using/introduction-forms-authoring.md).

É mais fácil criar e gerenciar formulários quando um processo adequado é seguido. Neste artigo, você aprenderá a:

* [Criar um formulário adaptável que permita ao cliente adicionar um endereço de entrega](/help/forms/using/create-adaptive-form.md#step-create-the-adaptive-form)

* [Campos de layout de um formulário adaptável para exibir e aceitar informações de um cliente](/help/forms/using/create-adaptive-form.md#step-add-header-and-footer)

* [Criar ação de envio para enviar um email com conteúdo de formulário](/help/forms/using/create-adaptive-form.md#step-add-components-to-capture-and-display-information)
* [Pré-visualizar e enviar um formulário adaptável](/help/forms/using/create-adaptive-form.md)

No final do artigo, você terá um formulário semelhante ao seguinte:\
[![Visualização de formulário em dispositivo móvel](do-not-localize/form-preview-mobile.gif)](do-not-localize/form-preview-mobile.gif)

## Etapa 1: criar o formulário adaptável {#step-create-the-adaptive-form}

1. Faça logon na instância de autor do AEM e navegue até **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms e Documentos]**. A URL padrão é [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments).
1. Selecione **[!UICONTROL Criar]** e selecione **[!UICONTROL Formulário adaptável]**. Uma opção para selecionar um modelo é exibida. Selecione o modelo **[!UICONTROL Em branco]** para selecioná-lo e selecione **[!UICONTROL Avançar]**.

1. Uma opção para **[!UICONTROL Adicionar Propriedades]** é exibida. Os campos **[!UICONTROL Título]** e **[!UICONTROL Nome]** são obrigatórios:

   * **Título:** especifique `Add new or update shipping address` no campo **[!UICONTROL Título]**. O campo de título especifica o nome de exibição do formulário. O título ajuda a identificar o formulário na interface do usuário do AEM [!DNL Forms].
   * **Nome:** especifique `shipping-address-add-update-form` no campo **[!UICONTROL Nome]**. O campo Nome especifica o nome do formulário. Um nó com o nome especificado será criado no repositório. Ao começar a digitar um título, o valor do campo de nome é gerado automaticamente. É possível alterar o valor sugerido. O campo de nome pode incluir apenas caracteres alfanuméricos, hifens e sublinhados. Todas as entradas inválidas são substituídas por um hífen.

1. Selecione **[!UICONTROL Criar]**. Um formulário adaptável é criado e uma caixa de diálogo para abrir o formulário para edição é exibida. Selecione **[!UICONTROL Abrir]** para abrir o formulário recém-criado em uma nova guia. O formulário é aberto para edição. Também exibirá a barra lateral para personalizar o formulário recém-criado de acordo com as necessidades.

   Para obter informações sobre a interface de criação de formulários adaptáveis e os componentes disponíveis, consulte [Introdução à criação de formulários adaptáveis](/help/forms/using/creating-adaptive-form.md).

   ![Um formulário adaptável recém-criado.](assets/newly-created-adaptive-form.png)

## Etapa 2: adicionar cabeçalho e rodapé {#step-add-header-and-footer}

O AEM [!DNL Forms] fornece muitos componentes para exibir informações em um formulário adaptável. Os componentes de Cabeçalho e Rodapé ajudam a fornecer uma aparência consistente a um formulário. Um cabeçalho normalmente inclui o logotipo de uma corporação, o título do formulário e o resumo. Um rodapé geralmente inclui informações de direitos autorais e links para outras páginas.

1. Selecione ![alternar painel lateral](assets/toggle-side-panel.png) > ![treeexpandall](assets/treeexpandall.png). O navegador de componentes é aberto. Arraste o componente **[!UICONTROL Cabeçalho]** do navegador de componentes para o formulário adaptável.
1. Selecione **[!UICONTROL Logotipo]**. A barra de ferramentas é exibida. Selecione ![aem_6_3_edit](assets/aem_6_3_edit.png) na barra de ferramentas, digite **We.Retail** e selecione ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

1. Selecione Imagem. A barra de ferramentas é exibida. Selecione ![cmppr](assets/cmppr.png). O navegador de propriedades é aberto à esquerda da tela. **[!UICONTROL Procurar]** e carregar a imagem de logotipo. Selecione ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png). A imagem aparece no cabeçalho.

   É possível selecionar Get file para baixar o logotipo usado neste artigo, caso não tenha um.

[Obter arquivo](assets/logo.png)

1. Arraste o componente **[!UICONTROL Rodapé]** de ![treeexpandall](assets/treeexpandall.png) para o formulário adaptável. Nesse estágio, o formulário tem a seguinte aparência:

   ![formulário-adaptável-com-cabeçalhos-e-rodapés](assets/adaptive-form-with-headers-and-footers.png)

## Etapa 3: adicionar componentes para capturar e exibir informações {#step-add-components-to-capture-and-display-information}

Os componentes são blocos fundamentais de um formulário adaptável. O AEM [!DNL Forms] fornece muitos componentes para capturar e exibir informações em um formulário adaptável. Você pode arrastar os componentes de ![treeexpandall](assets/treeexpandall.png) para um formulário. Para saber mais sobre os componentes disponíveis e a funcionalidade correspondente, consulte [Introdução à criação de formulários adaptáveis](/help/forms/using/introduction-forms-authoring.md).

1. Arraste o **[!UICONTROL componente de Caixa numérica]** para o formulário adaptável. Coloque-o antes do componente de rodapé. Abra as propriedades do componente, altere o **[!UICONTROL Título]** do componente para **`Customer ID`**, altere o **[!UICONTROL Nome do Elemento]** para **`customer_ID`**, habilite a opção **[!UICONTROL Campo Obrigatório]**, habilite a opção **[!UICONTROL Usar Tipo de Entrada Numérica do HTML5]** e selecione ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).
1. Arraste três componentes Caixa de texto para o formulário adaptável. Coloque-os antes do componente de rodapé. Defina as seguintes propriedades para essas caixas de texto.:

   <table> 
    <tbody> 
     <tr> 
      <td><b>Propriedade</b></td> 
      <td><b>Caixa de Texto 1<br/></b></td> 
      <td><b>Caixa de Texto 2<br/></b></td> 
      <td><b>Caixa de Texto 3</b></td> 
     </tr> 
     <tr> 
      <td>Título</td> 
      <td>Nome<br /> </td> 
      <td>Endereço de envio</td> 
      <td>Estado</td> 
     </tr> 
     <tr> 
      <td>Nome do elemento</td> 
      <td>customer_Name<br /> </td> 
      <td>customer_Shipping_Address</td> 
      <td>customer_State</td> 
     </tr> 
     <tr> 
      <td>Campo obrigatório</td> 
      <td>Habilitado</td> 
      <td>Habilitado</td> 
      <td>Habilitado</td> 
     </tr> 
     <tr> 
      <td>Permitir várias linhas<br /> </td> 
      <td>Desabilitado</td> 
      <td>Habilitado</td> 
      <td>Desabilitado</td> 
     </tr> 
    </tbody> 
   </table>

1. Arraste um componente de **[!UICONTROL Caixa Numérica]** antes do componente de rodapé. Abra as propriedades do componente, defina os valores listados na tabela abaixo, Selecione ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Propriedade | Valor |
   |---|---|
   | Título | Código postal |
   | Nome do elemento | customer_ZIPCode |
   | Número máximo de dígitos | 6 |
   | Campo obrigatório | Habilitado |
   | Tipo de padrão de exibição | Sem padrão |

1. Arraste um componente de **[!UICONTROL Email]** antes do componente de rodapé. Abra as propriedades do componente, defina os valores listados na tabela abaixo e selecione ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Propriedade | Valor |
   |---|---|
   | Título | Email |
   | Nome do elemento | customer_Email |
   | Campo obrigatório | Habilitado |

1. Arraste um componente **[!UICONTROL Anexo de arquivo]** antes do componente de rodapé. Abra as propriedades do componente, defina os valores listados na tabela abaixo e selecione ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   <table> 
    <tbody> 
     <tr> 
      <td><b>Propriedade</b></td> 
      <td><b>Valor</b></td> 
     </tr> 
     <tr> 
      <td>Título</td> 
      <td>Prova de endereço aprovada pelo governo<br /> </td> 
     </tr> 
     <tr> 
      <td>Nome do elemento</td> 
      <td>customer_Address_Proof</td> 
     </tr> 
     <tr> 
      <td>Campo obrigatório</td> 
      <td>Habilitado</td> 
     </tr> 
    </tbody> 
   </table>

1. Arraste um componente **[!UICONTROL Botão Enviar]** para o formulário adaptável. Coloque-o antes do componente de rodapé. Abra as propriedades do componente, altere Nome do Elemento para `address_addition_update_submit`, selecione ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png). O layout do formulário está completo e o formulário tem a seguinte aparência:

   ![formulário-adaptável-com-todos-os-componentes](assets/adaptive-form-with-all-the-components.png)

## Etapa 4: configurar a ação de envio para o formulário adaptável {#step-configure-submit-action-for-the-adaptive-form}

Uma ação de envio é acionada quando um usuário toca no botão Enviar em um formulário adaptável. Você pode usar uma ação enviar para salvar dados de formulário no repositório local, enviar dados de formulário para um terminal REST, enviar dados de formulário como um email e muito mais. Os formulários adaptáveis fornecem mais algumas ações de envio prontas para uso. Para obter informações detalhadas, consulte [Configurando a ação Enviar](/help/forms/using/configuring-submit-actions.md).

Usando as etapas a seguir, você pode configurar a ação de envio de email e a ação de envio de demonstração do formulário:

1. Configure o servidor de email. Para obter detalhes, consulte [Configurando Notificação por Email](/help/sites-administering/notification.md).


1. Selecione **[!UICONTROL Contêiner de Formulário]** no Navegador de conteúdo e selecione ![cmppr](assets/cmppr.png). O navegador de propriedades é aberto à esquerda.
1. Ir para **[!UICONTROL Envio]** > **[!UICONTROL Ação de Envio]**. Selecione **[!UICONTROL Enviar Email]**. Especifique os seguintes valores e selecione ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Propriedade | Valor |
   |--- |--- |
   | De | `donotreply@weretail.com` |
   | Para | `${customer_Email}` |
   | Assunto | Confirmação: você adicionou o endereço de entrega no site We.Retail. |
   | Modelo de e-mail | Olá `${customer_Name}`, O seguinte endereço foi adicionado como o endereço de entrega para sua conta: <br>`${customer_Name}`, `${customer_Shipping_Address}`, `${customer_State}`, `${customer_ZIPCode}`<br> Atenciosamente, We.Retail |
   | Incluir anexos | Habilitado |

   Seu formulário está pronto. Agora, você pode visualizar o formulário e testar a funcionalidade. Se você tiver usado o nome mencionado no tutorial e acessado o formulário na máquina que executa o servidor do AEM [!DNL Forms], o formulário estará disponível em [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html).

## Etapa 5: Visualizar e enviar o formulário adaptável {#step-preview-and-submit-the-adaptive-form}

Você pode usar a **[!UICONTROL opção de Visualização]** para avaliar a aparência e o comportamento de um formulário. É possível enviar um formulário no modo de visualização e também verificar as validações aplicadas em um formulário. Por exemplo, se um erro for exibido quando um campo obrigatório estiver vazio.

Os formulários adaptáveis também fornecem uma opção para Emular a experiência de um formulário para vários dispositivos. Por exemplo, iPhone, iPad e Desktop. Você pode usar as opções **[!UICONTROL Visualizar]** e **[!UICONTROL Emulador]** ![régua](assets/ruler.png) juntas entre si para visualizar um formulário para dispositivos de tamanhos de tela diferentes.

1. Selecione a opção **[!UICONTROL Visualizar]** no lado direito do editor de formulários. O formulário é aberto no modo de visualização. Se você tiver usado o nome mencionado no tutorial, a URL de visualização do formulário será [http://localhost:4502/content/dam/formsanddocuments/shipping-address-add-update-form/jcr:content?wcmmode=disabled](http://localhost:4502/content/dam/formsanddocuments/shipping-address-addition-updation-form/jcr:content?wcmmode=disabled)
1. Use a ![régua](assets/ruler.png) para exibir a aparência do formulário em vários dispositivos.
1. Preencha os campos do formulário e selecione **[!UICONTROL Enviar]**. O formulário é enviado e você é redirecionado para a página **Obrigado** padrão. Você também pode especificar uma página de agradecimento personalizada. Para obter detalhes, consulte [Configurando página de redirecionamento](/help/forms/using/configuring-redirect-page.md).

O formulário adaptável para adicionar um endereço está pronto. Se você tiver usado o nome mencionado no tutorial e acessado o formulário na máquina que executa o servidor do AEM Forms, o formulário estará disponível em [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html).
