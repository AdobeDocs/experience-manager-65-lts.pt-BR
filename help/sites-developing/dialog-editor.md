---
title: Editor de caixa de diálogo
description: O editor de diálogo fornece uma interface gráfica para criar e editar facilmente caixas de diálogo e scaffolds.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing,Developer Tools
role: Developer
source-git-commit: 48cdca14c4e993281ed8c0a4a364aebe7a4611ad
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# Editor de caixa de diálogo{#dialog-editor}

O editor de diálogo fornece uma interface gráfica para criar e editar facilmente caixas de diálogo e scaffolds.

Para ver como funciona, vá para CRXDE Lite, abra a árvore do explorador em `/libs/foundation/components/chart` e clique duas vezes no nó `dialog`:

![chlimage_1-247](assets/chlimage_1-247.png)

O nó da caixa de diálogo se abre no **editor de caixa de diálogo**:

![screen_shot_2012-02-01at25033pm](assets/screen_shot_2012-02-01at25033pm.png)

## Visão geral da interface do usuário {#user-interface-overview}

A interface do editor de caixa de diálogo é composta de quatro painéis:

* A **paleta**, no canto superior esquerdo. Este painel mantém os elementos disponíveis para criar uma caixa de diálogo, como painéis de tabulação, campos de texto, listas de seleção e botões. É possível expandir as diferentes categorias na paleta clicando na barra divisória desejada.
* O painel **estrutura**, no canto inferior esquerdo. Este painel mostra a estrutura hierárquica dos nós que compõem a definição da caixa de diálogo. Você pode ver a mesma estrutura expandindo o nó da caixa de diálogo no CRXDE Lite ou no CRX Content Explorer.
* O painel **render**, no centro da janela. Esse painel mostra como a definição da caixa de diálogo definida no painel de estrutura é renderizada como uma caixa de diálogo real.
* O painel **propriedades**. Esse painel mostra as propriedades do nó destacado no painel de estrutura.

### Usando o Editor de diálogo {#using-the-dialog-editor}

Para criar uma caixa de diálogo, o usuário arrasta e solta elementos da paleta para o painel de estrutura na posição dentro da hierarquia de definição da caixa de diálogo.

Quando a estrutura desejada for concluída, o usuário clica em **Salvar**, na parte superior do painel de renderização.

>[!CAUTION]
>
>O editor de diálogo é usado para criar diálogos simples. Talvez não seja possível editar definições de caixa de diálogo mais complexas. Nos casos em que o editor de caixa de diálogo não permite a edição de uma estrutura de caixa de diálogo, a definição da caixa de diálogo deve ser criada, editada ou ambas manualmente. Para isso, edite diretamente a estrutura do nó usando o CRXDE Lite ou o CRX Content Explorer, por exemplo.

### Criando uma nova caixa de diálogo {#creating-a-new-dialog}

Para criar uma caixa de diálogo, selecione o componente necessário, clique em **Criar...** e em **Criar Caixa de Diálogo...**.

Insira os detalhes necessários e clique em **Salvar tudo**. Agora você pode clicar duas vezes na caixa de diálogo para que ela seja aberta com o editor.

### Usando o Editor de diálogo para scaffolds {#using-the-dialog-editor-for-scaffolds}

Um scaffold é uma página especial que contém um formulário que pode ser preenchido e enviado em uma etapa. Isso permite criar rapidamente uma página usando o conteúdo inserido.

O formulário que compõe um scaffolding é definido por uma definição de caixa de diálogo, como uma caixa de diálogo normal, embora apareça na página de scaffolding em um formulário diferente. Como as definições de caixa de diálogo são usadas para definir scaffolds, os scaffolds podem ser criados usando o editor de caixa de diálogo. Ao usar o editor de caixa de diálogo dessa maneira, o painel de renderização ainda exibe a definição da caixa de diálogo no formato de uma caixa de diálogo, não como um scaffold.
