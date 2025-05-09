---
title: Criação de uma raiz de idioma usando a interface clássica
description: Saiba como criar uma raiz de idioma no Adobe Experience Manager usando a interface clássica.
contentOwner: Guillaume Carlino
feature: Language Copy
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---

# Criação de uma raiz de idioma usando a interface clássica{#creating-a-language-root-using-the-classic-ui}

O procedimento a seguir usa a interface clássica do usuário para criar uma raiz de idioma de um site. Para obter mais informações, consulte [Criando uma raiz de idioma](/help/sites-administering/tc-prep.md#creating-a-language-root).

1. No console Sites, selecione a página raiz na árvore Sites. ([http://localhost:4502/siteadmin#](http://localhost:4502/siteadmin#))
1. Adicione uma nova página secundária que represente a versão de idioma do site:

   1. Clique em Nova > Nova página.
   1. Na caixa de diálogo, especifique o Título e o Nome. O Nome precisa estar no formato de `<language-code>` ou `<language-code>_<country-code>`, por exemplo, en, en_US, en_us, en_GB, en_gb.

      * O código de idioma compatível é o código de duas letras em minúsculas, conforme definido pela ISO-639-1
      * O código do país compatível é o código de duas letras em minúsculas ou maiúsculas, conforme definido pela norma ISO 3166

   1. Selecione o Modelo e clique em Criar.

   ![newpagefr](assets/newpagefr.png)

1. No console Sites, selecione a página raiz na árvore Sites.
1. No menu Ferramentas, selecione Cópia de idioma.

   ![toolslanguageCopy](assets/toolslanguagecopy.png)

   A caixa de diálogo Cópia de idioma exibe uma matriz de versões de idioma e páginas da Web disponíveis. Um x em uma coluna de idioma significa que a página está disponível nesse idioma.

   ![caixa de diálogo de cópia de idioma](assets/languagecopydialog.png)

1. Para copiar uma página ou árvore de página existente para uma versão de idioma, selecione a célula dessa página na coluna de idioma. Clique na seta e selecione o tipo de cópia a ser criada.

   No exemplo a seguir, a página equipamento/óculos escuros/irian está sendo copiada para a versão em francês.

   ![Languagecopydilogdropdown](assets/languagecopydilogdropdown.png)

   | Tipo de cópia de idioma | Descrição |
   |---|---|
   | auto | Usa o comportamento das páginas principais |
   | ignorar | Não cria uma cópia desta página e de suas páginas secundárias |
   | `<language>+` (por exemplo, francês+) | Copia a página e todos os seus filhos desse idioma |
   | `<language>` (por exemplo, francês) | Copia somente a página desse idioma |

1. Clique em OK para fechar a caixa de diálogo.
1. Na próxima caixa de diálogo, clique em Sim para confirmar a cópia.
