---
title: Alteração do esquema de cores da interface
description: Como modificar o esquema de cores das partes da interface do usuário do AEM Forms Workspace de forma seletiva.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: f15ead5f-d48c-401c-98c5-b58f93776f82
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 2e690827bfa8f3d8227860de4efb802758ae0095
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%
---
# Alteração do esquema de cores da interface {#changing-the-color-scheme-of-the-interface}

Você pode modificar o esquema de cores das partes da interface do usuário do AEM Forms Workspace para atender aos seus requisitos. Veja a seguir alguns exemplos de personalizações representativas do esquema de cores. Além das etapas discutidas neste artigo, consulte [Etapas genéricas para personalização do espaço de trabalho do AEM Forms](/help/forms/using/generic-steps-html-workspace-customization.md).

## Barra de navegação superior {#top-navigation-bar}

### Uso da imagem de plano de fundo {#using-background-image}

Para atualizar a barra de navegação na parte superior do Workspace do AEM Forms.

1. Criar uma imagem de plano de fundo para atualizar a cor. Nomeie o arquivo como newBackground.jpg.
1. Faça upload do arquivo de imagem de fundo na pasta /apps/ws/images usando um cliente WebDAV.

   >[!NOTE]
   >
   >Para obter mais informações, consulte [Acesso ao WebDAV](/help/sites-administering/webdav-access.md).

1. Referencie a nova imagem de fundo em /apps/ws/css/newStyle.css adicionando o estilo a seguir.

   ```css
   #header {
       background:#292929 url(../images/newBackground.jpg) repeat-x;
   }
   ```

### Utilização da propriedade de cor no CSS {#using-color-property-in-css}

1. Adicione o seguinte estilo em newStyle.css em /apps/ws/css

   ```css
   #header {
   background : none;
   background-color: gray;
   }
   ```

## Componente da categoria {#category-component}

Componente Categoria exibe as várias categorias de suas tarefas no painel esquerdo. Para alterar a cor, defina a cor do plano de fundo no elemento `.category` do arquivo CSS.

## Componente da tarefa {#task-component}

As tarefas são exibidas no painel do meio chamado de Componente Lista de tarefas. Para alterar sua cor, modifique o estilo associado ao seletor .task na folha de estilos.
