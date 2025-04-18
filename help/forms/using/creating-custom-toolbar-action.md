---
title: Criar uma ação personalizada de barra de ferramentas
description: Os desenvolvedores de formulários podem criar ações personalizadas da barra de ferramentas para formulários adaptáveis no AEM Forms. O uso de ações personalizadas de autores de formulários pode fornecer mais fluxos de trabalho e opções aos usuários finais.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
docset: aem65
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms,Foundation Components
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# Criar uma ação personalizada de barra de ferramentas{#creating-a-custom-toolbar-action}

## Pré-requisitos {#prerequisite}

Antes de criar uma ação personalizada de barra de ferramentas, familiarize-se com o [Uso de bibliotecas do lado do cliente](/help/sites-developing/clientlibs.md) e o [Desenvolvimento com o CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

## O que é uma ação {#what-is-an-action-br}

Um formulário adaptável fornece uma barra de ferramentas que permite ao autor do formulário configurar um conjunto de opções. Essas opções são definidas como ações para o formulário adaptável. Clique no botão Editar na barra de ferramentas do Painel para definir as ações compatíveis com formulários adaptáveis.

![Ações padrão da barra de ferramentas](assets/default_toolbar_actions.png)

Além do conjunto de ações fornecido por padrão, você pode criar ações personalizadas na barra de ferramentas. Por exemplo, você pode adicionar uma ação para permitir que o usuário revise todos os campos de formulário adaptáveis antes que um formulário seja enviado.

## Etapas para criar uma ação personalizada em formulários adaptáveis {#steps}

Para ilustrar a criação de uma ação personalizada de barra de ferramentas, as etapas a seguir orientam você a criar um botão para que os usuários finais revisem todos os campos de formulário adaptáveis antes de enviar um formulário preenchido.

1. Todas as ações padrão suportadas pelos formulários adaptáveis estão presentes na pasta `/libs/fd/af/components/actions`. No CRXDE, copie o nó `fileattachmentlisting` de `/libs/fd/af/components/actions/fileattachmentlisting` para `/apps/customaction`.

1. Após copiar o nó para a pasta `apps/customaction`, renomeie o nome do nó para `reviewbeforesubmit`. Além disso, altere as propriedades `jcr:title` e `jcr:description` do nó.

   A propriedade `jcr:title` contém o nome da ação que é exibida na caixa de diálogo da barra de ferramentas. A propriedade `jcr:description` contém mais informações exibidas quando um usuário passa o ponteiro sobre a ação.

   ![Hierarquia de nós para personalização da barra de ferramentas](assets/action3.png)

1. Selecione o nó `cq:template` no nó `reviewbeforesubmit`. Verifique se o valor da propriedade `guideNodeClass` é `guideButton` e altere a propriedade `jcr:title` de acordo.
1. Altere a propriedade do tipo no nó `cq:Template`. Para o exemplo atual, altere a propriedade type para button.

   O valor de tipo é adicionado como uma classe CSS no HTML gerado para o componente. Os usuários podem usar essa classe CSS para estilizar suas ações. O estilo padrão para dispositivos móveis e desktop é fornecido para os valores de botão, enviar, redefinir e salvar.

1. Selecione a ação personalizada na caixa de diálogo da barra de ferramentas de edição do formulário adaptável. Um botão Revisar é exibido na barra de ferramentas do painel.

   ![A ação personalizada está disponível na barra de ferramentas](assets/custom_action_available_in_toolbar.png) ![Exibindo a ação de barra de ferramentas criada de forma personalizada](assets/action7.png)

1. Para fornecer funcionalidade ao botão Revisar, adicione algum código JavaScript e CSS e código do lado do servidor no arquivo init.jsp, presente no nó `reviewbeforesubmit`.

   Adicione o seguinte código em `init.jsp`.

   ```jsp
   <%@include file="/libs/fd/af/components/guidesglobal.jsp" %>
   <guide:initializeBean name="guideField" className="com.adobe.aemds.guide.common.GuideButton"/>
   
   <c:if test="${not isEditMode}">
           <cq:includeClientLib categories="reviewsubmitclientlibruntime" />
   </c:if>
   
   <%--- BootStrap Modal Dialog  --------------%>
   <div class="modal fade" id="reviewSubmit" tabindex="-1">
       <div class="modal-dialog">
           <div class="modal-content">
               <div class="modal-header">
                   <h3>Review the Form Fields</h3>
               </div>
               <div class="modal-body">
                   <div class="modal-list">
                       <table class="table table-bordered">
                           <tr class="name">
                               <td class="reviewlabel col-md-3 active">
                                   <label>Your Name is: </label>
                               </td>
                           </tr>
                           <tr class="pan">
                               <td class="reviewlabel col-md-3 active">
                                   <label>Your Pan Number is: </label>
                               </td>
                           </tr>
                           <tr class="dob">
                               <td class="reviewlabel col-md-3 active">
                                   <label>Your Date Of Birth is: </label>
                               </td>
                           </tr>
                           <tr class="80cdeclaration">
                               <td class="reviewlabel col-md-3 active">
                                   <label>Your Total 80C Declaration Amount is: </label>
                               </td>
                           </tr>
                           <tr class="rentpaid">
                               <td class="reviewlabel col-md-3 active">
                                   <label>Your Total HRA Amount is: </label>
                               </td>
                           </tr>
                       </table>
                   </div>
               </div><!-- /.modal-body -->
               <div class="modal-footer">
                   <div class="fileAttachmentListingCloseButton col-md-2 col-xs-2 col-sm-2">
                       <button data-dismiss="modal">Close</button>
                   </div>
               </div>
           </div><!-- /.modal-content -->
       </div><!-- /.modal-dialog -->
   </div><!-- /.modal -->
   ```

   Adicione o seguinte código no arquivo `ReviewBeforeSubmit.js`.

   ```javascript
   /*anonymous function to handle show of review before submit view */
   $(function () {
       if($("div.reviewbeforesubmit button[id*=reviewbeforesubmit]").length > 0) {
           $("div.reviewbeforesubmit button[id*=reviewbeforesubmit]").click(function(){
               // Create the options object to be passed to the getElementProperty API
               var options = {},
                   result = [];
               options.somExpressions = [];
               options.propertyName = "value";
               guideBridge.visit(function(model){
                   if(model.name === "name" || model.name === "pan" || model.name === "dateofbirth" || model.name === "total" || model.name === "totalmonthlyrent"){
                           options.somExpressions.push(model.somExpression);
                   }
               }, this);
               result = guideBridge.getElementProperty(options);
   
               $('#reviewSubmit .reviewlabel').each(function(index, item){
                   var data = ((result.data[index] == null) ? "No Data Filled" : result.data[index]);
                   if($(this).next().hasClass("reviewlabelvalue")){
                       $(this).next().html(data);
                   } else {
                       $(this).after($("<td></td>").addClass("reviewlabelvalue col-md-6 active").html(data));
                   }
               });
               // added because in mobile devices it was causing problem of backdrop
               $("#reviewSubmit").appendTo('body');
               $("#reviewSubmit").modal("show");
           });
       }
   });
   ```

   Adicione o código a seguir ao arquivo `ReviewBeforeSubmit.css`.

   ```css
   .modal-list .reviewlabel {
       white-space: normal;
       text-align: right;
       padding:2px;
   }
   
   .modal-list .reviewlabelvalue {
       border: #cde0ec 1px solid;
       padding:2px;
   }
   
   /* Adding icon for this action in mobile devices */
   /* This is the glyphicon provided by bootstrap eye-open */
   /* .<type> .iconButton-icon */
   .reviewbeforesubmit .iconButton-icon {
       position: relative;
       top: -8px;
       font-family: 'Glyphicons Halflings';
       font-style: normal;
   }
   
   .reviewbeforesubmit .iconButton-icon:before {
       content: "\e105"
   }
   ```

1. Para verificar a funcionalidade da ação personalizada, abra o formulário adaptável no modo de Visualização e clique em Revisar na barra de ferramentas.

   >[!NOTE]
   >
   >A biblioteca `GuideBridge` não está carregada no modo de criação. Portanto, essa ação personalizada não funciona no modo de criação.

   ![Demonstração da ação do botão de revisão personalizado](assets/action9.png)

## Amostras {#samples}

O arquivo a seguir contém um pacote de conteúdo. O pacote inclui um formulário adaptável relacionado à demonstração acima da ação personalizada da barra de ferramentas.

[Obter arquivo](assets/customtoolbaractiondemo.zip)
