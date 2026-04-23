---
title: Notas de versão atuais do Adobe Experience Manager 6.5 LTS, SP2
description: Encontre informações sobre a versão atual do Adobe Experience Manager 6.5 LTS, Service Pack 2.
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
exl-id: b5a8f555-c061-4fe2-a100-cc01335959cb
source-git-commit: 560d505465362d33f2864f13e9b75921b83ba5e4
workflow-type: tm+mt
source-wordcount: '7427'
ht-degree: 13%

---


# Notas de versão atuais do Adobe Experience Manager 6.5 LTS, SP2 {#release-notes}

## Informações da versão {#release-information}

| Produto | [!DNL Adobe Experience Manager] 6.5 LTS |
|---|---|
| Versão | Service Pack 2 (SP2) <!-- UPDATE FOR EACH NEW RELEASE --> |
| Tipo | Versão do pacote de serviços |
| Data | 19 de fevereiro de 2026 <!-- UPDATE FOR EACH NEW RELEASE --> |
| URL de download | [Distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack-lts/cq-quickstart-6.6.2.jar) |


<!-- UPDATE ABOVE FOR EACH NEW RELEASE -->

>[!IMPORTANT]
>
> **Hotfix Obrigatório** - Para evitar problemas de SNFE (SegmentNotFoundException) com compactação offline ao instalar o SP2, instale o hotfix descrito em [Problemas conhecidos - Corrupção do repositório durante a compactação online](#repository-corruption-during-online-compaction-after-offline-compaction-granite-65146).

## O que está incluído no [!DNL Adobe Experience Manager] 6.5 LTS, SP2 {#what-is-new}

<!-- UPDATE EACH RELEASE -->

O [!DNL Experience Manager] 6.5 LTS, SP2 inclui novos recursos, importantes melhorias solicitadas por clientes e correções de erros. Também inclui melhorias de desempenho, estabilidade e segurança lançadas desde a disponibilidade inicial do 6.5 LTS em março de 2025. [Instale este pacote de serviços](#install-update) no 6.5 LTS.

## Principais recursos e aprimoramentos

**AEM Sites**

O AEM 6.5 LTS SP2 agora inclui OpenAPIs para [Gerenciamento de modelos e fragmentos de conteúdo](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/65lts/) e [Inicializações](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/launches/). Essas APIs fornecem acesso aos Fragmentos de conteúdo e inicializações para criação e programação. Eles usam as mesmas OpenAPIs modernas que o AEM as a Cloud Service.

**AEM Forms**

**O que está incluído no AEM Forms 6.5 LTS SP2**

* Suporte para RDBMK com JBoss® EAP 8.0  foi adicionado.

* Experiência do usuário aprimorada no editor visual de regras. Esta atualização inclui:

   * Recarregar automaticamente a visualização de resumo após um salvamento para mostrar o status atualizado da regra

   * Mostrar os botões &quot;Adicionar&quot;/&quot;Excluir&quot; e permitir a alternância em vez de ocultá-los

   * Fornecer feedback claro quando uma operação de salvamento de regra não for bem-sucedida (FORMS-21261)

* Adicionada a API de tempo de execução para alternar o modo de exportação herdado da Linguagem de Marcação Extensível (XML) no AEM Forms, substituindo o parâmetro `Dcom.adobe.fd.forms.export.legacy`. Essa melhoria permite que os usuários alternem os modos de exportação com mais eficiência, melhorando a flexibilidade do fluxo de trabalho. (FORMS-23115)

* Adição de suporte para JavaScript Object Notation (JSON) com tags de namespace no Adaptive Forms. Esse aprimoramento permite que os usuários lidem com estruturas de dados JSON com mais eficiência, melhorando a integração de dados e os recursos de processamento. (FORMS-22519)

* Adição de Baixar documento de registro (DoR)/Envio de formulário como um botão pronto para uso (OOTB) no editor de regras. Esse aprimoramento permite que os clientes usem a função downloadDoR sem gravar código personalizado, melhorando a usabilidade e a eficiência. (FORMS-21263)

* Adição de suporte para JavaScript Object Notation (JSON) com tags de namespace no Adaptive Forms. Esse aprimoramento permite que os usuários preencham formulários com mais precisão e eficiência, melhorando a integração de dados e reduzindo os erros manuais de entrada. (FORMS-10883)

<!-- UPDATE THE EACH RELEASE -->

## Correção de problemas no 6.5 LTS, Service Pack 2 {#fixed-issues}

### [!DNL Sites]{#sites-65-LTS-SP2}

#### Acessibilidade {#sites-accessibility-65-lts-sp2}

* O componente de Texto perdeu o foco do teclado quando os autores passaram o mouse sobre os itens no Navegador de componentes durante a edição. Isso interrompeu a digitação e acionou uma falha de acessibilidade na WCAG 3.2.1. A correção impede que o estilo de flutuação mude de foco e mantém o componente de Texto focalizado durante a interação do Navegador de componentes. (SITES-35370)
* Correção do gerenciamento de foco no campo Rich text Description que bloqueava a navegação para frente com a tecla Tab. Os usuários ficaram presos no RTE porque o componente dependia de um comando de teclado não padrão para mudar o foco, o que afetava a navegação da caixa de diálogo esperada. A alteração impõe a interação padrão do teclado e preserva o sequenciamento lógico de guias em toda a caixa de diálogo. (SITES-35228)
* Correção de um problema no editor de sites que interrompia o comportamento esperado durante a criação da página e resultava em interação inconsistente do componente. Os autores obtiveram respostas não confiáveis da interface do usuário que interferiram nas tarefas de edição padrão e reduziram a eficiência do fluxo de trabalho. A atualização refina a lógica subjacente do editor e restaura uma interação estável e previsível entre os componentes afetados. (SITES-35227)
* Uma regressão que quebrou o seletor de ativos no editor de páginas e o impediu de carregar em cenários específicos de edição de páginas. Agora os autores podem abrir e usar o seletor de ativos normalmente ao escolher ou navegar pelos ativos ao editar uma página. Essa alteração restaura o acesso consistente a workflows de seleção de ativos que causaram interrupções ao carregar falhas. (SITES-35226)
* Eliminação de um problema no editor de sites que causava um comportamento inconsistente durante a interação da página e interrompeu os fluxos de trabalho de criação padrão. O defeito levou a respostas inesperadas da interface do usuário que interferiram na configuração do componente e nas atualizações de conteúdo. A atualização estabiliza a funcionalidade afetada e restaura a execução confiável das ações de edição nas páginas. (SITES-35225)
* Eliminação de um defeito na interface de criação do Sites que causava comportamento inconsistente durante a edição da página e interrompeu os fluxos de trabalho normais. Os autores encontraram respostas inesperadas da interface do usuário que interferiram na interação do componente e nas atualizações de conteúdo. A atualização estabiliza a funcionalidade afetada e restaura um comportamento confiável e previsível em todos os cenários de edição. (SITES-35224)
* O AEM Sites agora inclui suporte a texto `alt` em imagens para atender aos requisitos da ADA e da WCAG. A saída da página não omite mais os atributos `alt`, portanto, os leitores de tela recebem o texto alternativo correto. (SITES-27153)
* Corrigido o layout da barra de ferramentas `Note Add` de forma que o botão Adicionar não sobrepusesse mais o título na largura da janela de visualização de 320px. Refluxo de tela pequena aprimorado para que os controles permaneçam legíveis e utilizáveis durante o zoom de 400%. (SITES-25376)
* Correção de avisos de ausência do leitor de tela para erros da caixa de diálogo de seleção de link. A interface do usuário agora publica o texto de erro por meio de um contêiner de mensagem de status, portanto, o NVDA lê a mensagem assim que ela é exibida. (SITES-25368)
* Remoção das funções de grade ARIA e célula de grade da lista de ativos do painel lateral. Restaurada a semântica de lista padrão e a ordem de foco do teclado, o que melhorou a navegação do leitor de tela e reduziu as paradas de tabulação extras. (SITES-25361)
* Sequência de foco corrigida no Assets do painel lateral. Os usuários do teclado agora alcançam cada ação de ativo, incluindo Editar, por meio de um caminho de guia consistente. (SITES-25360)
* Corrigido o estouro de layout no modal do Search Assets na largura do visor de 320 px. O conteúdo modal agora reflui e permanece legível, de modo que os controles não se sobrepõem ou sobrescrevem a caixa de diálogo. (SITES-25330)
* Saída NVDA corrigida para o botão Editar. O NVDA agora anuncia a ação Editar, não o &quot;botão Visualizar pressionado&quot;. (SITES-25320)
* Correção de entradas de texto da barra de ferramentas Demografia sem nome que causavam saída de leitor de tela silenciosa ou genérica. Cada entrada agora expõe um nome acessível com base em rótulo claro, o que melhora a navegação pelo teclado e a tecnologia assistiva. (SITES-25316)
* A ordem de foco do teclado foi corrigida para a barra de ferramentas Demográfica durante a navegação da Visualização de layout. A navegação por guias agora se move diretamente do botão Demográfico para os controles da barra de ferramentas, sem pular para a barra de ferramentas secundária. (SITES-25305)
* Correção da ordem incorreta de anúncio dos rótulos &quot;Screens Menor&quot; e &quot;Tablet&quot; na régua Editar layout. Agora, os leitores de tela anunciam esses rótulos nos marcadores de régua corretos, que correspondem ao layout da página. (SITES-25291)
* Corrigido o estouro da barra de ferramentas Editar layout em 200% de zoom. O conteúdo agora permanece dentro da janela de visualização e pode ser acessado por meio da rolagem. (SITES-25288)
* Correção da ordem de foco incorreta na sobreposição de anotações. A tabulação de teclado agora circula pelos controles de sobreposição e itens de anotação. A página principal não assume mais o foco por trás da sobreposição. (SITES-25282)
* Manipulação de foco de popover de amostras corrigidas. A caixa de diálogo agora move o foco para um cabeçalho limpo e inicia a saída do leitor de tela nesse ponto de entrada. O NVDA não lê mais o conteúdo completo da caixa de diálogo fora de sequência. (SITES-25275)
* Correção do manuseio de foco modal do Timewarp após o fechamento do Seletor de datas. `Escape` agora retorna o foco ao botão Seletor de Data. A seleção de data agora coloca o foco no campo de entrada ao lado do controle Seletor de datas, evitando a perda do foco e o acesso à página em segundo plano. (SITES-25264)
* Correção da manipulação de foco do teclado para a caixa de diálogo Excluir anotação. Cancelar agora retorna o foco ao controle `Delete` que abriu a caixa de diálogo, não ao controle de valor hexadecimal Confirmar. Os leitores de tela não anunciam mais conteúdo de caixa de diálogo não relacionado após Cancelar. (SITES-25258)
* Corrigido o tratamento de foco da caixa de diálogo modal Anotação. Abrir a caixa de diálogo agora define o foco no cabeçalho da caixa de diálogo e impede que o NVDA leia o conteúdo da tela e o texto da caixa de diálogo não relacionado. A navegação pelo teclado agora permanece dentro da caixa de diálogo até fechar. (SITES-25257)
* Correção de problemas de layout modal de Pesquisa com largura de 320 px. O conteúdo modal agora reflui perfeitamente e evita sobreposições com o diretório da árvore. Os usuários podem visualizar os resultados e navegar pelo diretório sem controles obscuros. (SITES-25246)
* O texto modal de pesquisa não é mais recortado depois que o espaçamento do texto aumenta. O layout do diretório de árvore agora mantém uma separação clara, de modo que os rótulos e as entradas permanecem legíveis. Agora, os usuários podem concluir a pesquisa e a navegação sem sobreposição ou cortar texto. (SITES-25245)
* Ativar a Anotação agora move o foco do teclado para o conteúdo da anotação, não para o botão Sair da anotação. A ordem de tabulação segue uma sequência lógica e mantém os controles relacionados acessíveis sem navegação reversa. (SITES-25241)
* Os links Definir Data e Saída do Timewarp não tinham um indicador de foco visível durante a navegação pelo teclado. A interface do usuário agora renderiza um estilo de foco distinto e de alto contraste, para que os usuários possam identificar o link ativo rapidamente. (SITES-25232)
* O cabeçalho Modal de teaser não impede mais que os usuários de teclado movam a caixa de diálogo. Os controles do teclado agora permitem ações de retirar, mover e soltar, o que melhora a usabilidade do leitor de tela e a operabilidade geral. (SITES-25226)
* O AEM agora usa um rótulo acessível significativo para o botão Informações modais do teaser. Os leitores de tela anunciam um nome de ação claro em vez da sequência de caracteres de texto alternativo do ícone padrão. (SITES-25223)
* Agora, os leitores de tela anunciam a ação correta quando os usuários ativam o botão Editar. O NVDA não relata mais &quot;Botão de visualização pressionado&quot;, o que causou feedback enganoso e confusão durante a navegação pelo teclado. (SITES-25208)
* Expandir o painel esquerdo agora move o foco do teclado para o primeiro controle do painel esquerdo. A sequência de guias não salta mais para a barra de ferramentas secundária ou chega ao meio da lista, portanto, os usuários do teclado podem acessar o conteúdo do painel esquerdo sem navegar para trás. (SITES-24998)
* O conteúdo da barra do emulador de dispositivo agora permanece totalmente visível na largura da janela de visualização de 320 px. O texto e os controles da barra de ferramentas quebram automaticamente em vez de truncar, reduzindo a sobreposição e melhorando a legibilidade. (SITES-24953)
* O AEM agora exibe o rótulo completo do dispositivo iPhone na barra de ferramentas do emulador. O texto não fica mais truncado na largura padrão, melhorando a legibilidade e a clareza da seleção de dispositivos. (SITES-24952)
* Os cabeçalhos de tabela de Exibição de lista agora expõem o estado de classificação por meio de ARIA. Os leitores de tela anunciam uma ordem crescente ou decrescente após uma ação de classificação de coluna. (SITES-24943)
* O AEM agora preserva a visibilidade do rótulo do menu Mais ações na Exibição de cartão durante as alterações de espaçamento do texto. As opções de menu mantêm o texto completo, incluindo a Publicação rápida, e o menu permanece legível durante qualquer configuração de espaçamento de texto da WCAG. (SITES-24941)
* A barra de menus Ações do cartão agora expõe um nome acessível na Exibição de cartão. Os leitores de tela anunciam a finalidade da barra de menu claramente, e o controle de voz pode direcionar o controle por nome. (SITES-24938)
* A Exibição de cartão não depende mais da semântica de grade ARIA, que causou um comportamento confuso do leitor de tela. A interface do usuário agora fornece funções e rótulos significativos para o conteúdo do cartão e a barra de ação do cartão, o que reduz a perda de controles durante o uso do teclado. (SITES-24933)
* A dica de ferramenta `Delete Modal` agora aparece sempre que os usuários passam o mouse sobre o ícone da dica de ferramenta. As ações de foco agora mostram o mesmo texto de dica de ferramenta, o que melhora o acesso repetido para usuários de mouse e teclado. (SITES-24778)
* A navegação no painel esquerdo agora segue a ordem de foco do teclado esperada depois que os usuários configuram o painel. O foco da guia chega à área selecionada do painel esquerdo em vez de Alternar exibição, o que melhora a clareza de navegação do leitor de tela. (SITES-24754)
* Correção de comentários NVDA incorretos durante a navegação com amostra de cor no modal Preferências do usuário. O NVDA agora lê o rótulo da amostra que recebe foco, o que remove a saída de cores enganosas. O conjunto de amostras agora oferece suporte à navegação consistente do teclado e à percepção de seleção clara. (SITES-24739)
* Saída NVDA detalhada reduzida para o controle `Spin`. Remoção da rotulagem de grupo redundante que duplicava o rótulo de entrada, de modo que o NVDA anuncia o nome do controle uma vez. A navegação por teclados e leitores de tela agora oferece um anúncio único e claro. (SITES-24725)
* A caixa de diálogo Carrossel agora coloca o foco no cabeçalho da caixa de diálogo, em vez da guia Itens. Cancele e Esc restaure o foco para o controle que iniciou a caixa de diálogo, o que reduz a saída NVDA detalhada. (SITES-24716)
* A caixa de diálogo Seleção de link agora alinha o rótulo programático ao rótulo na tela para itens da árvore de último nível. A navegação com tecla de seta aciona um anúncio confiável do leitor de tela para cada item e remove a saída de rótulo enganosa. (SITES-24710)
* A caixa de diálogo Vincular abrir seleção agora flui corretamente em uma janela de visualização de 320 px. O conteúdo não ultrapassa mais o modal ou trunca, e o modal não mostra mais uma barra de rolagem horizontal. (SITES-24709)
* A caixa de diálogo Vincular abrir seleção agora restaura o foco do teclado para o acionador da caixa de diálogo após Fechar ou Cancelar. O foco não salta mais para a entrada Link, o que mantém o contexto do leitor de tela estável e reduz a navegação extra. (SITES-24707)
* A caixa de diálogo modal da imagem agora segue uma sequência de foco lógica. O foco não ignora mais os controles anteriores ou cai no ponto de referência da página após Cancelar, e os usuários recuperam o foco no botão Configurar após sair. (SITES-24693)
* A caixa de diálogo modal Referências do painel agora captura o foco do teclado. Tab e Shift+Tab permanecem dentro dos controles da caixa de diálogo, e o foco não escapa mais para o conteúdo da página. Os leitores de tela anunciam somente o conteúdo da caixa de diálogo. (SITES-24683)
* O modal Seleção de caminho de hiperlink agora define o foco no cabeçalho da caixa de diálogo ao abrir. Cancelar fecha a caixa de diálogo e restaura o foco para o botão Abrir caixa de diálogo de seleção, o que impede a perda de foco e a saída do leitor de tela redundante. (SITES-24672)
* O campo de Pesquisa agora usa um rótulo persistente na tela em vez de texto de espaço reservado. O rótulo permanece visível durante a entrada, o que melhora a clareza para o teclado, leitor de tela e usuários de fala. (SITES-24529)
* A caixa de diálogo modal do Teaser agora define o foco no cabeçalho da caixa de diálogo como aberto. Fechar a caixa de diálogo retorna o foco ao controle `Configure`, o que evita a perda de foco e o excesso de saída do leitor de tela. (SITES-24522)
* O painel Assets do painel lateral agora inclui um controle Fechar. Fechar retorna o foco do teclado ao botão de alternância do painel lateral e impede a tabulação forçada pelo conteúdo do painel. (SITES-24489)
* A tabulação de teclado agora atinge botões e links dentro de tabelas de administração. Os usuários não dependem mais da navegação de célula com tecla de seta para encontrar controles interativos. (SITES-24285)
* A caixa de diálogo do componente de Imagem não expõe mais ícones decorativos de Ajuda e Tela cheia como imagens. Os leitores de tela agora ignoram esses ícones, mantendo o foco em controles acionáveis e conteúdo de campo. (SITES-2940)
* O Administrador de sites agora remove a função de imagem dos ícones de miniatura da pasta. A tecnologia assistiva ignora esses elementos decorativos, mantendo o foco nos nomes e ações das pastas. (SITES-2852)
* A Árvore de conteúdo agora direciona o foco do teclado para o item de árvore ativo ou o primeiro item de árvore. O contêiner de árvore não atua mais como uma parada de tabulação vazia, impedindo armadilhas de foco Shift+Tab. (SITES-1577)

#### Interface do usuário administrador{#sites-adminui-65-lts-sp2}

As configurações de exibição de lista do console Sites não refletiam as colunas mostradas na exibição de lista. A caixa de diálogo foi aberta com caixas de seleção desmarcadas e uma contagem incorreta de colunas selecionadas. O estado da caixa de diálogo corrigir sincronizações com as colunas de grade ativas e atualiza o contador para corresponder à visibilidade real da coluna. (SITES-38576)

#### Interface do usuário clássica{#sites-classicui-65-lts-sp2}

A edição do componente de texto da interface clássica exibia tags brutas do HTML em vez de rich text após uma atualização. O Service Pack 2 corrige a renderização do RTE (Rich Text Editor, Editor de Rich Text) da interface clássica para que o editor exiba o conteúdo formatado e preserve a marcação armazenada. A correção também interrompe a expansão de marcação durante edições e salvamentos repetidos. (SITES-38709)

#### [!DNL Content Fragments]{#sites-contentfragments-65-lts-sp2}

O suporte a eventos headless não tinha eventos OSGi necessários para fragmentos de conteúdo e modelos no 6.5 LTS. A atualização adiciona o pacote de eventos e as dependências necessárias, além de incluir uma build 6.5 LTS. Os eventos Fragmento de conteúdo e Modelo agora são acionados corretamente e oferecem suporte aos fluxos de trabalho da API de inicializações. (SITES-35329)

#### [!DNL Content Fragments] - Administrador{#sites-admin-65-lts-sp2}

* O manuseio de componentes na interface de criação do Sites foi ajustado para interromper comportamentos irregulares durante atualizações de página. O defeito levou a respostas imprevisíveis do editor que interferiram nas modificações de conteúdo de rotina e reduziram a eficiência do fluxo de trabalho. A atualização alinha a lógica do editor aos padrões de interação esperados e fornece desempenho confiável durante as atividades de criação. (SITES-35078) CRÍTICO

* Uma regressão interrompeu a Exibição de lista do console do Assets para fragmentos de conteúdo e acionou um erro durante a renderização da lista. A atualização corrige a lógica de visualização de lista após a remoção de preview-info e restaura a saída da lista estável. O console agora exibe Fragmentos de conteúdo sem falhas e mantém as interações de lista utilizáveis. (SITES-38683)
* O Editor de fragmento de conteúdo agora localiza o rótulo Tags. O editor também localiza o rótulo Coleções, de modo que o texto da interface do usuário corresponde ao local selecionado. (SITES-977)


#### [!DNL Content Fragments] - Editor de fragmentos{#sites-fragments-editor-65-lts-sp2}

* As tags de variação do Fragmento do conteúdo desapareceram quando o botão de recurso permaneceu desativado após a refatoração. A correção restaura o suporte à tag de variação mesmo quando esse botão permanece desativado. Os autores podem adicionar e exibir novamente as tags de variação no Editor de fragmento de conteúdo. (SITES-38682) CRÍTICO
* Os fragmentos de conteúdo editados desaparecem da lista do console do Assets depois que os autores voltam do editor de fragmentos de conteúdo. O armazenamento em cache do navegador retornou uma lista obsoleta e ocultou o fragmento atualizado até uma atualização manual. A correção adiciona a manipulação do controle de cache para o caminho de retorno do editor, de modo que a lista seja recarregada corretamente e mantenha o fragmento editado visível. (SITES-35374) CRÍTICO

* O RTE do fragmento de conteúdo mostrava problemas visuais e de layout após alterações recentes no estilo da interface do usuário. O Service Pack 2 refina o estilo do RTE para que a barra de ferramentas e a área editável sejam renderizadas corretamente e permaneçam legíveis. O Editor de fragmento de conteúdo agora se alinha à aparência e ao comportamento do Editor de páginas. (SITES-38684)
* A remoção de escopos IMS do Seletor de ativos Polaris interrompeu a integração do Fragmento de conteúdo com o endpoint de entrega. Os autores detectam falhas ao abrir o seletor de ativos remoto e selecionar ativos. A atualização adiciona novamente os escopos IMS necessários e restaura o acesso estável da camada de entrega. (SITES-35837)
* O painel Conteúdo associado não renderiza mais um espaço reservado &quot;indefinido&quot; codificado. O Editor de fragmento de conteúdo agora resolve esse texto por meio de recursos de localização, para que os editores vejam o texto da interface traduzido. (SITES-33675)
  <!-- REMOVED FROM BUG LIST FEBRUARY 13, 2026 * Preview error messaging now uses localized strings instead of raw `Cannot print fragment's Json` text. The Content Fragment Editor now shows translated output across locales during GraphQL endpoint resolution failures. (SITES-33666)-->
* O Editor de fragmento de conteúdo agora exibe um rótulo de guia Geral traduzido nas localidades. O editor substitui o texto de guia não localizado e remove as IDs internas dos títulos de guia. (SITES-30715)
* O Editor de fragmento de conteúdo agora exibe nomes traduzidos para tipos de ativos permitidos. A lista do seletor não mescla mais strings internas e rótulos somente em inglês quando os autores configuram restrições de referência de conteúdo. (SITES-29699)

#### [!DNL Content Fragments] - API GraphQL {#sites-graphql-api-65-lts-sp2}

* Tratamento refinado de validação de consulta do GraphQL para interromper falhas de implantação causadas por erros de execução de filtro. O defeito gerou exceções durante a inicialização do aplicativo e bloqueou a implantação bem-sucedida em ambientes afetados. A revisão garante um comportamento de validação consistente e permite uma implantação suave sem interrupções de validação de consulta em tempo de execução. (SITES-34301) CRÍTICO

* A caixa de diálogo Editar endpoint do GraphQL agora exibe cadeias de caracteres da interface do usuário localizadas. A caixa de diálogo não mostra mais texto somente em inglês, como &quot;O esquema do GraphQL foi retirado da configuração&quot;, e os rótulos relacionados são renderizados corretamente nas localidades. (SITES-34018)

#### [!DNL Content Fragments] - Editor de consultas do GraphQL{#sites-graphql-query-editor-65-lts-sp2}

* Tratamento refinado de validação de consulta do GraphQL para interromper falhas de implantação causadas por erros de execução de filtro. O defeito gerou exceções durante a inicialização do aplicativo e bloqueou a implantação bem-sucedida em ambientes afetados. A revisão garante um comportamento de validação consistente e permite uma implantação suave sem interrupções de validação de consulta em tempo de execução. (SITES-35529)
* O GraphQL Explorer não falha mais quando um nome do Navegador de configuração contém caracteres CJK. A criação de pontos de extremidade e o acesso a consultas salvas funcionam normalmente e a página do Editor de consultas do GraphQL permanece sem erros. (SITES-31616)

#### [!DNL Content Fragments] - Editor de modelos{#sites-model-editor-65-lts-sp2}

* Os modelos de Fragmento de conteúdo aninhados pararam de funcionar quando a refatoração vinculou o recurso a um botão de alternância desativado. A correção restaura o suporte a modelo aninhado sem exigir alterações de alternância. Os autores podem criar e usar modelos aninhados novamente no Editor de modelos. (SITES-38681) CRÍTICO

* O painel de filtro Modelos de fragmento de conteúdo não expõe mais as cadeias de caracteres não localizadas. O AEM agora exibe rótulos de filtro localizados e valores de status localizados em todas as localidades. (SITES-30863)
* O Editor de modelo de fragmento de conteúdo agora renderiza cadeias de caracteres localizadas para a caixa de diálogo de aviso de bloqueio. A interface do usuário substitui mensagens em inglês não localizadas por recursos de localidade em todos os idiomas compatíveis. (SITES-28592)

#### [!DNL Content Fragments] - API REST{#sites-restapi-65-lts-sp2}

O AEM Headless exigia uma ramificação de versão dedicada para evitar dependências e conflitos de versão de pacote com builds principais. A atualização adiciona uma ramificação headless `release/6.5lts` e alinha conjuntos de dependências e versões agrupadas. O Jenkins agora cria a base de código headless de maneira limpa, sem colisões de versão. (SITES-36585)

<!-- #### Component console{#sites-component-console-65-lts-sp2} -->

#### API de conteúdo{#sites-content-api-65-lts-sp2}

Um defeito de recurso de alternância relatou incorretamente o status da API de gerenciamento de página. A atualização adiciona um sinalizador de ativação dedicado e o avalia junto com o botão de alternância existente. A API de gerenciamento de página agora mostra um status estável. A API de gerenciamento de site permanece experimental. (SITES-39284)

#### Back-end principal{#sites-core-backend-65-lts-sp2}

* Uma alteração na experiência de criação do Sites para resolver comportamentos inconsistentes que interromperam os fluxos de trabalho de edição de página padrão. Os autores encontraram resultados inesperados durante a interação do componente, o que interferiu nas atualizações de conteúdo e reduziu a confiabilidade. A alteração restaura o comportamento estável do editor e garante a execução consistente das ações de criação nos cenários afetados. (SITES-35162) CRÍTICO

* O comportamento de criação do Sites foi refinado para resolver um problema que interrompeu a edição da página e causou resultados inconsistentes durante a interação do componente. Os autores tiveram respostas inesperadas da interface do usuário que interferiram nas atualizações do conteúdo e reduziram a confiabilidade do fluxo de trabalho. A alteração restaura o gerenciamento estável do estado do editor e garante a execução previsível das ações de criação nos cenários afetados. (SITES-34499)

<!--
#### Core Components{#sites-core-components-65-lts-sp2}

#### Campaign integration{#sites-campaign-integration-65-lts-sp2}

#### Experience Fragments{#sites-experiencefragments-65-lts-sp2}

#### Foundation Components (Legacy){#sites-foundation-components-legacy-65-lts-sp2}
-->

#### Lançamentos{#sites-launches-65-lts-sp2}

* A Linha do tempo do Sites mostrava um texto em inglês codificado durante a promoção do Launch: &quot;Versão criada ... antes de promover a inicialização&quot;. A atualização substitui a cadeia de caracteres codificada pelo manuseio de mensagem localizado. A Linha do tempo agora exibe o texto localizado e alinha a entrada com o comportamento de localização padrão do AEM. (SITES-39157)
* O escopo de promoção do Launch mudou quando os autores promoveram uma subseção usando Promover página atual e subpáginas. O AEM também promoveu páginas não relacionadas e causou modificações inesperadas no site. A correção corrige o cálculo do escopo do Launch para que somente a subárvore escolhida promova. (SITES-38315)
* Fragmentos de conteúdo em Inicializações não participaram do índice `damAssetLucene`, com resultados de pesquisa e eficiência de consulta limitadas. Essa alteração adiciona caminhos de Fragmento de conteúdo do Launch à definição do índice. As consultas de pesquisa e personalizadas agora encontram fragmentos de conteúdo em `/content/launches`. (SITES-35634)
* A interface de inicializações mostrava controles de Inicialização de fragmentos de conteúdo, mesmo que o produto não exponha as Inicializações de fragmentos de conteúdo na interface de toque. Essa alteração desmonta os caminhos de código da Inicialização de fragmento de conteúdo do cq-launches-content e ajusta a filtragem da lista de Inicializações. Agora os autores veem opções consistentes de inicialização de página sem entradas de inicialização de fragmento de conteúdo. (SITES-35633)
* O Quickstart do AEM 6.5 LTS não tinha os pacotes e pré-requisitos necessários do Launches, o que bloqueava a ativação da OpenAPI do Launches. A atualização adiciona pacotes de Inicializações e dependências necessárias, como suporte a métricas, atualizações de DAM-cfm e configuração de fila. As APIs do Launches agora são executadas no Quickstart 6.5 LTS com os componentes de tempo de execução necessários presentes. (SITES-35297)
* O pacote CF Launches recebeu versões de dependência mais recentes e bibliotecas GraphQL desnecessárias, o que complicou a integração do AEM 6.5 LTS. Essa alteração alinha as versões de dependência à linha de base do AEM 6.5 LTS e elimina as dependências de GraphQL não usadas. A resolução do pacote agora permanece consistente e a inicialização do CF Launches permanece estável. (SITES-35295)
* O AEM Launches agora executa um pipeline Jenkins dedicado para a ramificação 6.5 LTS. O pipeline é executado durante a noite e cria e envia alertas de falha por email. Essa configuração aumenta a cobertura dos testes e as regressões das capturas antecipadamente. (SITES-35293)
* O AEM 6.5 LTS agora envia um pacote atualizado de API do Launches com versões de artefato alinhadas. O pacote rastreia a linha de código primária enquanto mantém a versão correta da versão 6.5 LTS. Essa atualização estabiliza o consumo da API do Launches na pilha 6.5 LTS. (SITES-35292)
* O AEM 6.5 LTS agora inclui um pacote atualizado do launches-core com versões de dependência alinhadas. A atualização adiciona o manuseio do núcleo de inicializações para os tipos de dados UUID de fragmento e UUID de referência. O processamento de lançamentos agora mantém o comportamento consistente em inicializações e fluxos de trabalho de Fragmento de conteúdo. (SITES-35290)
* Refinamento do editor do Sites para resolver comportamentos inconsistentes que interromperam os fluxos de trabalho normais de criação de página. Os autores encontraram uma interação inesperada de componentes que interferiu nas atualizações de conteúdo e reduziu a confiabilidade da edição. A alteração restaura o gerenciamento consistente do estado da interface do usuário e garante a execução previsível das ações de criação nos cenários afetados. (SITES-35138)
* Iniciar Edição agora mostra texto de erro localizado em vez da cadeia de caracteres `Provided path is not a launch` codificada. Agora a interface do usuário renderiza mensagens traduzidas entre idiomas quando Editar recebe um caminho de inicialização inválido. (SITES-33360)
* O AEM 6.5 LTS agora inclui o trabalho de porta lateral do Launches OpenAPI. A atualização coloca em paridade os pacotes de APIs do Launches, os pacotes de conteúdo e os artefatos de Início rápido necessários e ativa os cenários de APIs abertas do Fragmento de conteúdo com validação de CI estável. (SITES-32050)
* A interface do usuário do Launches agora localiza o rótulo do modelo Substituído. Os detalhes de substituição do modelo agora exibem o texto traduzido em vez de uma cadeia de caracteres somente em inglês. (SITES-29525)
* O AEM resolveu uma chave de localização ausente em **Sites** > **Inicializações** > **Editar**. Os usuários agora veem uma mensagem de erro traduzida em vez da string bruta &quot;Não é possível atualizar a lista de origem de inicialização&quot;. (SITES-21499)
* A interface da promoção do Launch agora exibe rótulos e ações de status localizados. A área de visualização mostra o texto traduzido para **Excluído**, **Novo** e **Exibição**, em vez de cadeias de caracteres brutas em inglês. (SITES-13540)
* A criação de lançamentos agora mostra mensagens de erro localizadas. A interface do usuário não exibe mais cadeias de caracteres brutas em inglês, como `Unable to create launch page`, `Source root resource is not a page` ou `Mandatory parameter is missing`. (SITES-13085)


<!-- #### Link Checker{#sites-link-checker-65-lts-sp2} -->


#### MSM: Live Copies{#sites-msm-live-copies-65-lts-sp2}

* Os administradores tinham visibilidade limitada do processamento de push-on-modify do MSM durante as alterações de conteúdo. A correção adiciona um registro detalhado sobre a recepção de eventos do MSM e a execução de implantação. A saída da depuração agora mostra quais eventos foram acionados, quais caminhos de conteúdo foram alterados e quem acionou a alteração. (SITES-38029)
* O AEM corrigiu um problema de layout de localização no campo de data Implantação de blueprint. O prompt de data agora se encaixa no controle e permanece legível nos idiomas compatíveis, incluindo `fr_FR`. (SITES-14961)

<!-- #### Page editor{#sites-pageeditor-65-lts-sp2} -->

#### Replicação{#sites-replication-65-lts-sp2}

A publicação do Editor de páginas agora lida com URLs que contêm seletores ou sufixos. A solicitação publicada agora envia o caminho da página JCR, não uma sequência de caracteres de URL de seletor ou sufixo, portanto, a ativação é concluída e o conteúdo é publicado. A replicação agora retorna um status de erro em caso de falha, o que impede mensagens falsas de &quot;publicação iniciada&quot;. (NPR-43288)

<!-- #### Rich Text Editor{#sites-rte-65-lts-sp2} -->

#### Editor de modelo{#sites-template-editor-65-lts-sp2}

Texto de status do modelo exibido verticalmente em **Ferramentas** > **Geral** > **Modelos** para algumas localidades. O rótulo &quot;desatualizado&quot; quebrou o layout e foi lido como uma coluna de caracteres. A correção corrige o estilo de status do modelo para que o rótulo seja renderizado em uma única linha horizontal. (SITES-36797)

#### Editor universal {#sites-universal-editor-65-lts-sp2}

* Uma configuração padrão OSGi foi definida como `preview=true` e forçou o Editor Universal a iniciar no modo de Visualização. Essa atualização corrige o valor padrão e restaura o comportamento padrão da entrada de Produção. O Editor universal agora é aberto no modo Produção, a menos que um administrador ative explicitamente o modo Visualização. (SITES-37193)
* O comando Abrir do editor universal agora é padronizado para o modo Visualização nos ambientes de Desenvolvimento e Preparo. O comando adiciona `preview=true`, que mantém as verificações do autor alinhadas ao contexto de visualização e evita aberturas acidentais de Produção. (SITES-33839)

### [!DNL Assets]{#assets-65-lts-sp2}

O Assets Relate agora funciona para nomes de arquivo que incluem espaços. A lógica do cliente Relate atualizada agora lida corretamente com caminhos que contêm espaço e evita `undefined` erros de origem durante a seleção da relação. A caixa de diálogo Relacionar agora abre e salva as relações sem interrupções ou spinners na interface do usuário. Os usuários do DAM podem relacionar, derivar e não relacionar ativos sem renomear arquivos. (Assets-56418)

#### [!DNL Dynamic Media]{#assets-dm-65-lts-sp2}

* Nova integração do reprodutor de vídeo Dynamic Media (implantação limitada) - Uma nova experiência do reprodutor de vídeo Dynamic Media agora está disponível no Quickstart do AEM 6.6. No momento, esse aprimoramento está ativado apenas para clientes iniciais como parte de uma implantação controlada. (Assets-60165)
* Correção de um problema em que a opção Selecionar miniatura na caixa de diálogo Propriedades de vídeo não abria o seletor de ativos, restaurando a capacidade de os usuários escolherem miniaturas personalizadas para ativos de vídeo. (Assets-58926)
* No vídeo do Dynamic Media, foi adicionado suporte para selecionar árabe na lista suspensa de idioma Legendas e faixas de áudio, permitindo que os autores gerenciem legendas árabes diretamente no AEM. (Assets-61771)

<!-- #### [!DNL Dynamic Media] - Hybrid Mode {#assets-dm-hybrid-65-lts-sp2} -->

<!--
#### Forms Designer-->

### [!DNL Forms]{#forms-65-lts-sp2}

* Os usuários tiveram problemas com a funcionalidade `Data Source / Enter Keyword` do editor do Form Data Model (FDM). Esse problema afetou a capacidade de pesquisar e selecionar fontes de dados. (FORMS-23971)
* Em dispositivos móveis, o componente Tabela no Adaptive Forms renderizava um cabeçalho oculto na parte superior, fazendo com que os leitores de tela anunciassem incorretamente o conteúdo. Isso afetava os usuários que dependiam de leitores de tela para navegação. (FORMS-23754)
* Os usuários tiveram problemas com os Componentes principais baseados no Forms adaptável referenciando tipos de recursos sinalizados como granite:InternalArea, que afetaram a funcionalidade de vários componentes granite no complemento local do Forms. (FORMS-23632)
* Falha no envio do formulário após a atualização para o AEM 6.5 LTS SP1. Os usuários sentiram o com.adobe.cq.social.commons.CollabUtil ausente, causando erros de compilação de JSP e falhas de ação de email. (FORMS-23457)
* Os usuários tiveram problemas com a tradução incorreta do hCaptcha em Componentes do Foundation com base no Adaptive Forms. Isso afetou a capacidade dos usuários que não falavam inglês de preencher formulários com precisão. (FORMS-23426)
* Os usuários tiveram falhas no envio do formulário com uma SAXParseException: &quot;O conteúdo não é permitido no prólogo&quot; (HTTP 500). Esse problema ocorreu devido a um valor nulo no XML de dados de preenchimento prévio, causando falha na análise do XML do lado do servidor. (FORMS-22633)
* Os usuários experimentaram o Adaptive Forms com falha nas auditorias de Web Content Accessibility Guidelines (WCAG). O motivo foi porque a marcação de navegação por guia do formulário era inválida. Ou seja, um elemento que não é de lista é renderizado como um filho direto de uma lista, onde somente os itens de lista são permitidos. Esse problema impedia que o formulário passasse validadores de acessibilidade e organizações afetadas que devem atender aos requisitos legais ou internos de conformidade. (FORMS-22101)
* Os usuários tiveram problemas de acessibilidade com o Documento de registro (DoR)/PDF de envio, em que campos de formulário vazios não eram marcados como elementos de formulário. Isso causava dificuldades para os leitores de tela, afetando a capacidade dos usuários com deficiência de navegar e preencher formulários de maneira eficaz. (FORMS-21989)
* Os usuários tiveram um problema em que as notas de rodapé de componentes dentro de um subpainel não eram exibidas durante o carregamento do formulário. Esse problema ocorria quando o item com a nota de rodapé era o último componente na página. (FORMS-21925)
* Os usuários tiveram problemas ao selecionar componentes no Editor do AEM Forms. Ao navegar entre guias e retornar à primeira guia, alguns contêineres se tornaram inselecionáveis, impedindo uma fácil identificação e interação. (FORMS-21814)
* Os usuários experimentaram uma vulnerabilidade de segurança no painel Adaptive Forms. Especificamente, um problema de criação de script entre sites (XSS) foi identificado no arquivo startpointcontrol.js, o que poderia potencialmente permitir a execução de scripts mal-intencionados. (FORMS-20679)
* Nas implantações de cluster do AEM Forms 6.5 LTS no JBoss® EAP 8, os arquivos `domain/configuration/domain_oracle.xml`, `domain_mysql.xml` e `domain_mssql.xml` não contêm mais uma marca `<security>` duplicada que causou XML inválido e impediu o início do Controlador de Domínio. (FORMS-24687)
* No modo Turnkey, a atualização da porta do banco de dados agora é aplicada corretamente durante a nova instalação e atualização. No modo de instalação nova, os usuários podem selecionar entre todas as portas disponíveis e, no modo de Atualização, a porta do banco de dados atualizada em lc_turnkey.xml é referenciada corretamente durante o processo de atualização. (FORMS-24689)
* Ao configurar o JBoss® EAP 8.0 no Linux®, scripts de shell modificados no Windows não causam mais erros `/bin/sh^M: bad interpreter or $'\r': command not found` devido ao fim de linha CRLF. (FORMS-24688)

<!--
#### Forms JEE 

#### Forms Captcha {#forms-captcha-65-lts-sp2}

#### XMLFM {#forms-xmlfm-65-lts-sp2}

#### [!DNL Adaptive Forms] {#adaptive-forms-65-lts-sp2}

#### [!DNL Forms Designer] {#forms-designer-65-lts-sp2}

#### Forms Designer

#### AdaptIve Forms

#### Forms Captcha

#### Forms Management UI
-->


### Foundation {#foundation-65-lts-sp2}

#### Apache Felix {#foundation-apachefelix-65-lts-sp2}

* O Sling Resource Access Security agora é executado na versão 1.1.2. ResourceAccessSecurityImpl não lança mais um ClassCastException durante a inicialização quando vários serviços ResourceAccessGateHandler são registrados. A inicialização agora é concluída com confiança e evita falhas de inicialização em ambientes com vários manipuladores. (NPR-42750)
* O Console JMX e o Console da Web agora enviam um `Content-Type: text/css header` para recursos CSS de console. A verificação MIME estrita não bloqueia mais o carregamento da folha de estilos, portanto, a interface do usuário `/system/console/jmx` é renderizada com estilo normal. (GRANITE-63677)
* O AEM agora evita entradas de ACL duplicadas para o grupo `contributor` no `WEB-INF/resources/provisioning/model.txt` gerado. A saída WAR agora contém um bloco de ACL consistente, o que impede diferenças de permissão confusas durante a revisão. (GRANITE-63269)
* O AEM não limpa mais as configurações de inclui na lista de bloqueios e inclui na lista de permissões do Firewall de desserialização durante as operações de atualização de pacote. A lógica de registro de filtro atualizada mantém a instância de firewall ativa alinhada à configuração salva, para que a proteção permaneça ativada sem uma reinicialização. (GRANITE-61382)
* O Felix Web Console não lança mais erros `NullPointerException` intermitentes durante o acesso `/system/console`. A manipulação atualizada do ServiceTracker impede um estado de rastreador nulo. O logon e a navegação do console permanecem estáveis durante solicitações repetidas e validações automatizadas. (GRANITE-61042)

<!--
#### Campaign{#foundation-campaign-65-lts-sp2}

#### Cloud Services{#foundation-cloudservices-65-lts-sp2}

#### Communities {#foundation-communities-65-lts-sp2}

#### Content distribution{#foundation-content-distribution-65-lts-sp2}
-->

#### CRX {#foundation-crx-65-lts-sp2}

O CRXDE Lite não mostra mais uma guia em branco ao abrir um arquivo JSP após uma atualização do Service Pack. O AEM agora é enviado com o código principal e complementar do CodeMirror correspondente, o que impede o erro fatal do navegador e mantém o editor utilizável. (GRANITE-64333)

#### Granite{#foundation-granite-65-lts-sp2}

O Validador de segurança de expressão agora lida com valores de configuração OSGi vazios ou nulos. Ela aplica padrões seguros, ignora matrizes vazias e registra logs limpos, impedindo NullPointerException e resultados de validação imprevisíveis. (NPR-43163)

<!-- #### HTL{#foundatoin-htl-5-lts-sp2} -->

#### Integrações{#foundation-integrations-65-lts-sp2}

O AEM agora sincroniza atividades do Adobe Target mesmo quando existem datas de início e término. A carga do Target agora formata as datas de atividade como carimbos de data e hora completos da ISO 8601, incluindo segundos, milissegundos e fuso horário. O Target não rejeita mais a solicitação com `InvalidJson.Json`. As atividades agendadas agora passam para um estado sincronizado, em vez de ficarem fora de sincronia. (CQ-4360733)

<!--
#### Jetty{#foundation-jetty-65-lts-sp2}

#### Localization{#foundation-localization-65-lts-sp2} 

#### Omnisearch{#foundation-omnisearch-65-lts-sp2}

#### Platform{#foundation-platform-65-lts-sp2}

#### Projects{#foundation-projects-65-lts-sp2}
-->

#### Oak {#foundation-oak-65-lts-sp2}

O AEM 6.5 LTS Service Pack 2 exige o S3 Connector 1.60.10 ou posterior. A configuração do armazenamento de dados S3 agora inclui `crossRegionAccess` e `mode` para que os administradores possam habilitar o acesso ao bucket entre regiões e alternar o armazenamento para GCP quando necessário. O `s3EndPoint` agora espera uma região alinhada a `s3Region`, ou ela permanece vazia para que o driver gere o ponto de extremidade. (GRANITE-64873)


#### Início rápido{#foundation-quickstart-65-lts-sp2}

* O Sling atualiza o incluo na lista de permissões de logon administrativo para usar terminologia inclusiva e novos PIDs de configuração. Essa alteração está alinhada com a Base JCR do Sling 3.2.0. (GRANITE-63756)

  **Impacto**

   * O Sling substitui esses PIDs e você deve removê-los de suas configurações:
      * PID de Fábrica: `org.apache.sling.jcr.base.internal.LoginAdminWhitelist.fragment`
      * PID global: `org.apache.sling.jcr.base.internal.LoginAdminWhitelist`
Essas configurações mais antigas usam propriedades, como `whitelist.name` e `whitelist.bundles`.

   * O Sling ainda fornece compatibilidade parcial com versões anteriores para os PIDs obsoletos, mas não os usa para novas configurações. Em vez disso, use os `LoginAdminAllowList.*` PIDs mais recentes.
   * Não execute configurações obsoletas e novas configurações de incluo na lista de permissões ao mesmo tempo. Configurações mistas podem criar ambiguidade e produzir comportamento não intencional. Ao migrar para o AEM 6.5 LTS SP2, remova os PIDs obsoletos completamente.

  **O que você deve fazer**

   1. Localizar configurações de incluo na lista de permissões que usam `LoginAdminWhitelist*` PIDs.
   1. Substitua-os pelos novos PIDs apropriados:

      * PID de Fábrica: `org.apache.sling.jcr.base.LoginAdminAllowList.fragment`
      * PID Global: `org.apache.sling.jcr.base.LoginAdminAllowList`

      Para obter detalhes adicionais, consulte [Abordagem obsoleta para incluir na lista de permissões pacotes para logon administrativo](https://sling.apache.org/documentation/the-sling-engine/service-authentication.html#deprecated-approach-to-allowlist-bundles-for-administrative-login).

* O AEM 6.5 LTS SP2 atualiza o conjunto de pacotes de camada de base para Sling, Oak e Felix. Essas atualizações fortalecem a estabilidade do tempo de execução principal e alinham as versões de dependência na plataforma. (GRANITE-61874)

<!--
#### Security{#foundation-security-65-lts-sp2}

AEM now prevents NullPointerException errors when a logged-in user lacks read access for some groups and opens the Groups tab. The tab now hides groups without access and renders group membership details without a blank or unresponsive UI. (NPR-43311) -->

#### Sling{#foundation-sling-65-lts-sp2}

O AEM agora inclui o Sling Engine 2.16.6. Essa alteração elimina violações XSS sinalizadas por ferramentas de segurança e melhora a segurança e a estabilidade da renderização principal. (NPR-43105)

<!--
#### Translation{#foundation-translation-65-lts-sp2}

#### User interface{#foundation-ui-65-lts-sp2}
-->

#### WCM{#foundation-wcm-65-lts-sp2}

O AEM Translations não apresenta mais falhas no Java 17 ou Java 21 devido a problemas de formato XLIFF. O pipeline de exportação agora produz XLIFF compatíveis com os padrões que os provedores de tradução aceitam. Essa alteração remove as interrupções do trabalho de tradução e restaura a entrega previsível entre o AEM e os serviços de tradução. Os fluxos de trabalho de tradução agora permanecem estáveis em tempos de execução Java compatíveis. (CQ-4360217)

#### Fluxo de trabalho{#foundation-workflow-65-lts-sp2}

EmailNotificationService-Processor não aciona mais erros &quot;Segmento não encontrado&quot; repetidos durante o manuseio de notificação do workflow. O tratamento de exceção atualizado detecta SegmentNotFoundException e interrompe o loop de processamento em vez de continuar com leituras inválidas. A execução do workflow permanece estável e registra quedas de ruído durante o acesso à caixa de entrada e ao item de trabalho. (GRANITE-62635)




## Sobre [!DNL Experience Manager Foundation] {#experience-manager-foundation}

A plataforma do [!DNL Adobe Experience Manager] 6.5 LTS baseia-se nas versões atualizadas da estrutura baseada em OSGi (Apache Sling e Apache Felix) e do repositório de conteúdo Java™: Apache Jackrabbit Oak 1.68.x.

O Eclipse Jetty 11.0.x é usado como um mecanismo de servlet para o início rápido.

### Compatibilidade com Java™  {#java-support}

* Compatibilidade com Java™ 17 e Java™ 21.
* Para atingir o desempenho ideal, substitua os valores de GC padrão por outros valores. Para obter mais informações, consulte a seção [instalar e atualizar](/help/sites-deploying/custom-standalone-install.md).
* A Adobe distribui atualizações de manutenção do Java™ 17 e do Java™ 21 para uso dos clientes em projetos relacionados ao AEM, quando não estão disponíveis publicamente na Oracle.

### Empacotamento de Uberjar {#uber-jar-packaging}

O UberJar para AEM 6.5 LTS SP2 usa o AEM 6.5 LTS UberJar versão 6.6.2. Você pode recuperar os artefatos UberJar correspondentes do Repositório central Maven. Ao contrário do AEM 6.5, o AEM 6.5 LTS separa APIs públicas e APIs obsoletas em dois artefatos diferentes.

Para compilar nas APIs públicas, use o seguinte:

```xml
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.6.2</version>
    <classifier>apis</classifier>
    <scope>provided</scope>
</dependency>
```

Se o código também depender de APIs obsoletas, adicione o seguinte:

```xml
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.6.2</version>
    <classifier>deprecated-apis</classifier>
    <scope>provided</scope>
</dependency>
```

Consulte também [Atualizar a versão do AEM Uber Jar](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

### Atualizar {#upgrade}

* Para mais detalhes sobre o procedimento de upgrade, consulte a [documentação de upgrade](/help/sites-deploying/upgrade.md).
* Para obter instruções detalhadas de atualização, consulte o [Guia de Atualização para o AEM Forms 6.5 LTS SP1 no JEE](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65-lts/content/forms/upgrade-aem-forms/upgrade)

#### Práticas recomendadas para as atualizações do Pacote de serviços do AEM 6.5 LTS

<!-- THE INFORMATION UNDER THIS HEADING CAME FROM CQDOC-23078 -->

**Ambiente**
Aplicável a: clientes do AEM 6.5 LTS (no local) que instalam o Service Pack 2 (SP2). O SP2 é fornecido como um JAR de início rápido.

**Por que esta prática de atualização é importante**
O SP2 para AEM 6.5 LTS é fornecido como um JAR de início rápido em vez de um ZIP para instalação por meio do Gerenciador de pacotes. Clientes locais realizam a atualização por substituir o arquivo JAR de início rápido, fazer a extração do conteúdo e reiniciar. Esse método é consistente com o procedimento de atualização no local da Adobe.

**Fluxo de atualização recomendado (Autor ou Publicação)**

1. Verifique se a instância do AEM 6.5 LTS está íntegra e acessível.
1. Baixe o JAR de início rápido (por exemplo, `cq-quickstart-6.6.x.jar`) da Distribuição de software.
1. Interrompa a instância de execução.
1. No diretório de instalação do AEM (fora de `crx-quickstart/`), substitua o JAR de início rápido anterior pelo JAR SP2.
1. Extraia o arquivo JAR:

   ```java
   java -jar cq-quickstart-6.6.x.jar -unpack
   ```

   (Ajuste sinalizadores de heap conforme necessário.)

1. Renomeie o arquivo JAR extraído para corresponder à função e à porta como, por exemplo, `cq-author-4502.jar` ou `cq-publish-4503.jar`.
1. Inicie o AEM e confirme a atualização na interface (Ajuda > Sobre) e nos logs.

**Boas práticas para a integridade do sistema**

* Execute a atualização em ambientes inferiores/de teste antes da produção.
* Faça um backup completo e restaurável (repositório mais qualquer armazenamento de dados externo) antes de começar.
* Revise a orientação para atualização da Adobe no local e os requisitos técnicos (Java 17/21 recomendado para LTS).

>[!NOTE]
>
>Os nomes de arquivo mostrados acima (por exemplo, `cq-quickstart-6.6.x.jar`) refletem a nomenclatura de artefato de Início Rápido observada para esta versão LTS; sempre use o nome de arquivo exato que você baixar da Distribuição de Software.

## Instalar e atualizar{#install-update}

Para conferir os requisitos de instalação, consulte as [instruções de instalação](/help/sites-deploying/custom-standalone-install.md).

>[!NOTE]
>
> Se você estiver atualizando diretamente para o LTS SP1 dos 6.5 SPs antigos, siga as instruções fornecidas para 6.5 para 6.5 LTS GA [atualização](/help/sites-deploying/upgrade.md).


Para instruções mais detalhadas, consulte a [documentação de upgrade](/help/sites-deploying/upgrade.md).

>[!NOTE]
>
> Para novas instalações do AEM 6.5 LTS, as definições de índice precisam ser instaladas separadamente. Para mais informações, consulte [este artigo](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#index-definitions).

## Instalar e atualizar o complemento AEM Forms {#install-update-aem-forms-add-on}

Para instruções detalhadas, consulte [Realizar um upgrade no local](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/release-notes/aem-forms-current-service-pack-installation-instructions).


## Plataformas compatíveis {#supported-platforms}

Encontre o conjunto completo de plataformas compatíveis, incluindo em relação ao suporte, nos [requisitos técnicos do AEM 6.5 LTS](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Java™ 17/Java™ 21 são as versões recomendadas para usar com o AEM 6.5 LTS.


## Recursos obsoletos e removidos {#deprecated-and-removed-features}

<!-- CARRY OVER EACH RELEASE -->

A Adobe analisa e desenvolve continuamente os recursos do produto para oferecer maior valor ao cliente, modernizando ou substituindo os recursos herdados. Essas alterações são implementadas considerando cuidadosamente a compatibilidade com versões anteriores.

Para garantir a transparência e permitir o planejamento adequado, o Adobe segue esse processo de desativação do Adobe Experience Manager (AEM):

* A descontinuação é anunciada primeiro. Os recursos obsoletos continuam disponíveis, mas não são mais aprimorados.
* A remoção não ocorre antes da próxima versão principal. O cronograma de remoção planejado é comunicado separadamente.
* Um ciclo mínimo de versão é fornecido para que os clientes façam a transição para alternativas compatíveis antes da remoção de um recurso.

### Recursos descontinuados {#deprecated-features}

Esta seção lista os recursos e funcionalidades que a Adobe descontinuou no AEM 6.5 LTS. Normalmente, a Adobe descontinua recursos antes de os remover em uma versão futura e fornece uma alternativa.

Os clientes são aconselhados a analisar se usam o recurso/funcionalidade em sua implantação atual. Fazer planos para alterar sua implementação para usar a alternativa fornecida.

| Área | Destaque | Substituição | Versão (SP) |
| --- | --- | --- | --- |
| Início rápido | APIs Mongo | As APIs Mongo agora estão obsoletas e estão planejadas para remoção em versões futuras. | 6.5 TS SP2 |
| Sites | Suporte a Fragmento de conteúdo na API REST do AEM Assets | O AEM 6.5 LTS SP2 fornece OpenAPIs modernas para gerenciamento de fragmentos de conteúdo e modelos. Portanto, os endpoints mais antigos de suporte a fragmentos de conteúdo na API REST do AEM Assets agora estão obsoletos.<br>A Adobe pretende manter esses endpoints mais antigos disponíveis até um anúncio do fim da vida útil. A Adobe não planeja melhorias adicionais para os endpoints obsoletos. | 6.5 LTS SP2 |
| Sites | [Editor SPA](/help/sites-developing/spa-overview.md) | Os editores preferenciais para o gerenciamento de conteúdo headless no AEM são:<br>- [O Editor Universal](/help/sites-developing/universal-editor/introduction.md) para edição visual.<br>- [O Editor de Fragmento de Conteúdo](/help/assets/content-fragments/content-fragments-managing.md) para edição baseada em formulário. | 6.5 LTS GA |
| [!DNL Foundation] | Suporte para com.adobe.granite.oauth.server | Integração do Adobe IMS |  |

### Recursos removidos {#removed-features}

Esta seção lista os recursos e funcionalidades que foram removidas do AEM 6.5 LTS. Nas versões anteriores, esses recursos estavam marcados como descontinuados.

* O suporte para RDBMK para persistência de repositório do CRX foi removido.
* Em ambientes em cluster, o MongoMK agora é a única opção compatível para a persistência do repositório.

| Área | Destaque | Substituição | Versão (SP) |
| --- | --- | --- | --- |
| Commerce | O AEM CIF Classic não é compatível. | Migre para o [AEM CIF](/help/commerce/cif/migration.md). | 6.5 LTS GA |
| Soluções | Social/Communities não são compatíveis. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Screens | Telas não são compatíveis. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Ativos | `dam-pim` e `dam-rating` não são compatíveis, pois esses conjuntos dependem de redes sociais. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Ativos | `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettings()` foi removido. | Use a API alternativa `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettingsList()` que foi adicionada. | 6.5 LTS GA |
| Portal | O AEM Portal Diretor não é compatível. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Granite | O pacote `com.adobe.granite.socketio` foi removido. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Granite | `com.adobe.granite.crx-explorer` não é compatível. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Granite | `crx2oak` não é compatível. | Escolha a versão apropriada de [Oak-upgrade](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-upgrade) | 6.5 LTS GA |
| Adobe | `com.adobe.cq.cq-searchpromote-integration` não é compatível. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Guava | Todas as dependências do Guava foram removidas do AEM; portanto, o pacote `com.adobe.granite.osgi.wrapper.guava-15.0.0-0002` não faz parte do AEM. | Os clientes podem adicionar o Guava por conta própria se dependerem dele ou substituir o código do Guava por coleções de Java ou outras alternativas, se possível. | 6.5 LTS GA |
| `We.Retail` | O site de exemplo `We-retail` não é compatível. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Fonte aberta | O pacote `oak-solr-osgi` não é compatível. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Fonte aberta | `org.apache.servicemix.bundles.abdera-parser`, `org.apache.servicemix.bundles.jdom` e `org.apache.sling.atom.taglib` não são compatíveis. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
| Fonte aberta | Os pacotes `org.apache.commons.io` foram exportados de `org.apache.commons.commons-io`. | Nenhuma alteração necessária. | 6.5 LTS GA |
| Fonte aberta | Os pacotes `javax.mail` estão sendo exportados do pacote `com.sun.javax.mail`. | Nenhuma alteração necessária. | 6.5 LTS GA |
| Fonte aberta | Os pacotes `org.apache.jackrabbit.api` agora são exportados do pacote `org.apache.jackrabbit.oak-jackrabbit-api`. | Nenhuma alteração necessária. | 6.5 LTS GA |
| Fonte aberta | `com.github.jknack.handlebars` não é compatível. | Escolha a [versão](https://mvnrepository.com/artifact/com.github.jknack/handlebars) adequada | 6.5 LTS GA |


## Problemas conhecidos {#known-issues}

### AEM Forms

* No Configuration Manager, a Inicialização do Banco de Dados falha durante o Bootstrap no modo Personalizado Turnkey do AEM Forms 6.5 LTS JEE quando nenhum módulo ou somente componentes limitados são selecionados. A falha se deve a uma dependência ausente (xalan-2.7.2.jar), resultando em um erro. Adicionar o arquivo JAR ao adobe-livecycle-jboss.ear\lib resolve o problema. (FORMS-24690)
* Em implantações do Forms JEE LTS em execução no JBoss® EAP 8, a interface do usuário do Reader Extensions pode falhar com um erro interno do servidor. (FORMS-24894)
* No Forms JEE LTS em execução no JBoss®, a funcionalidade relacionada ao email pode falhar. Ao tentar usar recursos de email, o servidor pode registrar um erro semelhante a `Error IMAPProvider not a subtype`. (FORMS-24892)
* Em plataformas Linux®, o Forms JEE LTS requer que a propriedade `OSFileSetIntendedFor` em `LFS_Foundation.properties` seja definida corretamente antes da execução do Configuration Manager. Se não for atualizada, a configuração pode não ser adaptada corretamente para Linux®, o que pode levar a problemas de tempo de execução ou implantação. Para resolver o problema, após executar o instalador e antes de executar o Configuration Manager, navegue até `configurationManager/config/solcomp/`, abra `LFS_Foundation.properties`, defina `OSFileSetIntendedFor=Linux`, salve o arquivo e execute o Configuration Manager. (FORMS-24741)

### Corrupção do repositório durante a compactação online após a compactação offline (GRANITE-65146) {#repository-corruption-during-online-compaction-after-offline-compaction-granite-65146}

Os usuários podem enfrentar corrupção do repositório durante a compactação online se a compactação offline tiver sido executada anteriormente no repositório JCR. Um `SegmentNotFoundException` (SNFE) pode ocorrer neste cenário e pode levar à corrupção do repositório.

Para resolver o problema, instale o Hotfix de [Distribuição de Software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.2-hotfix-GRANITE-65388-1.0.zip). Como o hotfix inclui um pacote de baixo nível `oak-segment-tar`, a instância é reiniciada após a instalação.

Planeje o tempo de inatividade da instância ao aplicá-la. Para compactação offline, use o [`oak-run` jar](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/oak-run-1.88.1-B006.jar) correspondente, também disponível na Distribuição de Software.

>[!NOTE]
>
> * Para qualquer operação `oak-run`, use o [`oak-run` 1.88.1-B006 jar](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/oak-run-1.88.1-B006.jar).
>
> * Inicie o AEM definindo a propriedade do sistema `oak.compaction.legacy=true`.

### Instale os índices Oak necessários para as APIs do Sites Headless{#site-headless-api}

Algumas APIs que foram movidas para o Sites Headless exigem índices Oak adicionais para funcionalidade completa.

Instale o pacote `cq-dam-cfm-indices` para usar os seguintes recursos:

* Listar modelos de fragmento de conteúdo
* Listar fragmentos de conteúdo
* API de pesquisa
* Fluxos de trabalhos

Baixe o pacote de índice [cq-dam-cfm-indices](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/cq-dam-cfm-indices-1.1.2.zip) do Portal de Distribuição de Software da Adobe.

### Falha de conexão do Dispatcher com o recurso somente SSL (corrigido no AEM 6.5 LTS SP1 e posterior){#ssl-only-feature}

>[!NOTE]
>
> Esse problema está presente apenas na versão GA do AEM 6.5 LTS.

Ao habilitar o recurso de somente SSL em implantações do AEM, há um problema conhecido que afeta a conectividade entre as instâncias do Dispatcher e do AEM. Após habilitar esse recurso, as verificações de integridade podem falhar, e a comunicação entre as instâncias do Dispatcher e do AEM pode ser interrompida. Este problema ocorre especificamente quando os clientes tentam se conectar a instâncias do AEM por meio do `https + IP` a partir do Dispatcher. Ele está relacionado a problemas de validação da indicação do nome do servidor (SNI, na sigla em inglês).

**Impacto**

* Falhas de verificação de integridade com códigos de resposta HTTP 400.
* Tráfego interrompido entre instâncias do Dispatcher e do AEM.
* O conteúdo não pode ser distribuído corretamente por meio da Dispatcher.
* Falhas de conexão ao usar HTTPS com endereços IP na configuração do Dispatcher.
* HTTP 400 - Erros &quot;SNI inválido&quot; ao conectar via HTTPS + IP.

**Ambientes afetados**

* Implantações do AEM com configurações do Dispatcher.
* Sistemas em que o recurso somente SSL foi ativado.
* Configurações do Dispatcher usando o método de conexão `https + IP` com instâncias do AEM.

**Solução**

Se você enfrentar esse problema, entre em contato com o Suporte ao cliente da Adobe. Uma hotfix [cq-6.5.lts.0-hotfix-CQ-4359803](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-CQ-4359803-1.0.2.zip) está disponível para resolver esse problema. Não tente habilitar recursos de somente SSL até aplicar a hotfix necessária.

## Pacotes da OSGi e pacotes de conteúdo inclusos{#osgi-bundles-and-content-packages-included}

Os seguintes documentos de texto listam os pacotes OSGi e os Pacotes de Conteúdo incluídos nesta versão do [!DNL Experience Manager] 6.5 LTS, Service Pack 2: <!-- UPDATE FOR EACH NEW RELEASE -->

* [Lista de pacotes OSGi incluídos no Experience Manager 6.5 LTS, Service Pack 2](/help/release-notes/assets/65lts_sp2_bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [Lista de Pacotes de Conteúdo incluídos no Experience Manager 6.5 LTS, Service Pack 2](/help/release-notes/assets/65lts_sp2_packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Sites restritos{#restricted-sites}

Estes sites só estão disponíveis para clientes. Se você for cliente e precisar de acesso, entre em contato com o seu gerente de conta da Adobe.

* [Download do produto em licensing.adobe.com](https://licensing.adobe.com/)
* [Fale com o suporte ao cliente da Adobe](https://experienceleague.adobe.com/pt-br/docs/support-resources/adobe-support-tools-guide/adobe-customer-support-experience).

