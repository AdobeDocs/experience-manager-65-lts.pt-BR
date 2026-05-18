---
title: Notas de versão atuais do Pacote de serviços 2 do Adobe Experience Manager 6.5 LTS
description: Encontre informações sobre a versão atual do Adobe Experience Manager 6.5 LTS, Pacote de serviços 2.
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
exl-id: b5a8f555-c061-4fe2-a100-cc01335959cb
source-git-commit: 02b7915e1e5554d29577e46960c072d46bcc8b0c
workflow-type: tm+mt
source-wordcount: '7695'
ht-degree: 95%

---


# Notas de versão atuais do Pacote de serviços 2 do Adobe Experience Manager 6.5 LTS {#release-notes}

## Informações da versão {#release-information}

| Produto | [!DNL Adobe Experience Manager] 6.5 LTS |
|---|---|
| Versão | Pacote de serviços 2 (SP2) <!-- UPDATE FOR EACH NEW RELEASE --> |
| Tipo | Versão do pacote de serviços |
| Data | 19 de fevereiro de 2026 <!-- UPDATE FOR EACH NEW RELEASE --> |
| URL de download | [Distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack-lts/cq-quickstart-6.6.2.jar) |


<!-- UPDATE ABOVE FOR EACH NEW RELEASE -->

>[!IMPORTANT]
>
> **Hotfix obrigatória** - Para evitar problemas de SNFE (SegmentNotFoundException) com compactação offline ao instalar o Pacote de serviços 2, instale a hotfix descrita em [Problemas conhecidos - Corrupção do repositório durante a compactação online](#repository-corruption-during-online-compaction-after-offline-compaction-granite-65146).

## O que está incluído no Pacote de serviços 2 do [!DNL Adobe Experience Manager] 6.5 LTS {#what-is-new}

<!-- UPDATE EACH RELEASE -->

O [!DNL Experience Manager] 6.5 LTS SP2 inclui novos recursos, melhorias importantes solicitadas por clientes e correções de erros. Também inclui melhorias de desempenho, estabilidade e segurança lançadas desde a disponibilidade inicial do 6.5 LTS em março de 2025. [Instale este pacote de serviços](#install-update) no 6.5 LTS.

## Recurso principal e aprimoramento

**AEM Sites**

O AEM 6.5 LTS SP2 agora inclui OpenAPIs para [gerenciamento de modelos e fragmentos de conteúdo](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/65lts/) e [inicializações](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/launches/). Essas APIs proporcionam acesso a fragmentos de conteúdo e inicializações para criação e agendamento. Elas usam as mesmas OpenAPIs modernas que o AEM as a Cloud Service.

**AEM Forms**

**O que está incluído no Pacote de serviços 2 do AEM Forms 6.5 LTS**

* Foi adicionado suporte para RDBMK com JBoss® EAP 8.0.

* Experiência do usuário aprimorada no editor visual de regras. Essa atualização inclui:

   * Recarregamento automático da visualização de resumo depois de salvar para mostrar o status atualizado da regra

   * Exibição dos botões “Adicionar” e “Excluir”, além de permissão para ativá-los/desativá-los, em vez de ocultá-los

   * Fornecimento de feedback claro quando uma operação de salvar regra não é concluída com êxito (FORMS-21261)

* Adição da interface de programação de aplicativos (API) do tempo de execução para ativar/desativar o modo de exportação de XML (Extensible Markup Language) legado no AEM Forms, substituindo o parâmetro `Dcom.adobe.fd.forms.export.legacy`. Esse aprimoramento permite que os usuários alternem os modos de exportação com mais eficiência, melhorando a flexibilidade do fluxo de trabalho. (FORMS-23115)

* Foi adicionado suporte para JavaScript Object Notation (JSON) com tags de namespace em formulários adaptáveis. Esse aprimoramento permite que os usuários lidem com estruturas de dados JSON com mais eficácia, melhorando a integração de dados e os recursos de processamento. (FORMS-22519)

* Baixar documento de registro (DoR)/Envio de formulário foi adicionado como um botão pronto para uso (OOTB) no editor de regras. Esse aprimoramento permite que os clientes usem a função downloadDoR sem gravar código personalizado, melhorando a usabilidade e a eficiência. (FORMS-21263)

* Foi adicionado suporte para JavaScript Object Notation (JSON) com tags de namespace em formulários adaptáveis. Esse aprimoramento permite que os usuários preencham formulários com mais precisão e eficiência, melhorando a integração de dados e reduzindo os erros de entrada manuais. (FORMS-10883)

<!-- UPDATE THE EACH RELEASE -->

## Problemas corrigidos no 6.5 LTS, Pacote de serviços 2 {#fixed-issues}

### [!DNL Sites]{#sites-65-LTS-SP2}

#### Acessibilidade {#sites-accessibility-65-lts-sp2}

* O componente de Texto perdeu o foco do teclado quando os autores passaram o mouse sobre os itens no Navegador de componentes durante a edição. Isso interrompeu a digitação e acionou uma falha de acessibilidade em WCAG 3.2.1. A correção impede que o estilo aplicado ao passar o cursor do mouse mude o foco e mantém o componente Texto em foco durante a interação do Navegador de componentes. (SITES-35370)
* Gerenciamento de foco corrigido no campo rich text Descrição que bloqueava o avanço na navegação com a tecla Tab. Os usuários ficaram presos no RTE porque o componente dependia de um comando de teclado não padrão para mudar o foco, o que afetava a navegação da caixa de diálogo esperada. A alteração impõe a interação padrão do teclado e preserva o sequenciamento lógico da tecla Tab em toda a caixa de diálogo. (SITES-35228)
* Problema corrigido no editor Sites que interrompia o comportamento esperado durante a criação da página e resultava em interação inconsistente do componente. Os autores obtiveram respostas não confiáveis da interface do usuário que interferiram nas tarefas de edição padrão e reduziram a eficiência do fluxo de trabalho. A atualização refina a lógica subjacente do editor e restaura uma interação estável e previsível entre os componentes afetados. (SITES-35227)
* Uma regressão que afetou o seletor de ativos no editor de páginas e o impediu de carregar em cenários específicos de edição de páginas. Agora os autores podem abrir e usar o seletor de ativos normalmente ao escolher ou navegar pelos ativos ao editar uma página. Essa alteração restaura o acesso consistente a fluxos de trabalho de seleção de ativos que havia sido interrompido por falhas no carregamento. (SITES-35226)
* Eliminado um problema no editor Sites que causava um comportamento inconsistente durante a interação de página e interrompia os fluxos de trabalho de criação padrão. O defeito levou a respostas inesperadas da interface do usuário que interferiram na configuração do componente e nas atualizações de conteúdo. A atualização estabiliza a funcionalidade afetada e restaura a execução confiável das ações de edição nas páginas. (SITES-35225)
* Eliminado um problema na interface de criação do Sites que causava comportamento inconsistente durante a edição de página e interrompeu os fluxos de trabalho normais. Os autores encontraram respostas inesperadas da interface do usuário que interferiram na interação do componente e nas atualizações de conteúdo. A atualização estabiliza a funcionalidade afetada e restaura um comportamento confiável e previsível nos cenários de edição. (SITES-35224)
* O AEM Sites agora inclui suporte a texto `alt` em imagens para atender aos requisitos da ADA e WCAG. A saída da página não omite mais os atributos `alt`, portanto os leitores de tela recebem o texto alternativo correto. (SITES-27153)
* Corrigido o layout da barra de ferramentas `Note Add` de forma que o botão Adicionar não sobreponha mais o título na largura do viewport de 320px. O Reflow de tela pequena foi aprimorado para que os controles permaneçam legíveis e utilizáveis durante o zoom de 400%. (SITES-25376)
* Avisos de ausência do leitor de tela corrigidos quanto a erros da caixa de diálogo Seleção de link. A interface do usuário agora publica o texto do erro por meio de um contêiner de mensagem de status, de forma que o NVDA leia a mensagem assim que ela é exibida. (SITES-25368)
* Funções de grade ARIA e célula de grade removidas da lista de ativos do painel lateral. Restaurada a semântica de lista padrão e a ordem de foco do teclado, o que melhorou a navegação do leitor de tela e reduziu as paradas extras no uso da tecla Tab. (SITES-25361)
* Corrigida a sequência de foco no painel lateral Ativos. Os usuários do teclado agora alcançam cada ação de ativo, incluindo Editar, por meio de um caminho de Tab consistente. (SITES-25360)
* Corrigido o estouro de layout no modal Pesquisar ativos na largura do viewport de 320 px. O conteúdo do modal agora reflui e permanece legível, de modo que os controles não se sobreponham nem ultrapassem os limites da caixa de diálogo. (SITES-25330)
* Corrigida a saída NVDA do botão Editar. O NVDA agora anuncia a ação Editar, não &quot;botão Visualizar pressionado&quot;. (SITES-25320)
* Corrigidas entradas de texto da barra de ferramentas Demografia sem nome que causavam saída de leitor de tela silenciosa ou genérica. Cada informação inserida agora expõe um nome acessível claro com base em rótulo, o que melhora a navegação pelo teclado e por uma tecnologia assistiva. (SITES-25316)
* Corrigida a ordem de foco do teclado na barra de ferramentas Demográfico durante a navegação Visualização de layout. A navegação de tabulações agora se move diretamente do botão Demográfico para os controles da barra de ferramentas, sem pular para a barra de ferramentas secundária. (SITES-25305)
* Corrigida a ordem incorreta de anúncio dos rótulos &quot;Telas menores&quot; e &quot;Tablet&quot; na régua Editar layout. Agora, os leitores de tela anunciam esses rótulos nos marcadores de régua corretos, que correspondem ao layout da página. (SITES-25291)
* Corrigido o estouro da barra de ferramentas Editar layout em 200% de zoom. O conteúdo agora permanece dentro do viewport e pode ser acessado por meio da rolagem. (SITES-25288)
* Resolvida a ordem de foco incorreta na sobreposição Anotações. A tabulação de teclado agora passa pelos controles de sobreposição e itens de anotação. A página principal não assume mais o foco por trás da sobreposição. (SITES-25282)
* Corrigida a manipulação de foco de popover de amostras. A caixa de diálogo agora move o foco para um cabeçalho limpo e inicia a saída do leitor de tela nesse ponto de entrada. O NVDA não lê mais o conteúdo completo da caixa de diálogo fora de sequência. (SITES-25275)
* Corrigida a manipulação de foco do modal Timewarp após o fechamento do Seletor de data. `Escape` agora retorna o foco ao botão Seletor de data. A seleção de data agora coloca o foco no campo de entrada ao lado do controle Seletor de data, evitando a perda do foco e o acesso à página em segundo plano. (SITES-25264)
* Corrigida a manipulação de foco do teclado na caixa de diálogo Excluir anotação. Cancelar agora retorna o foco ao controle `Delete` que abriu a caixa de diálogo, não ao controle Confirmar valor hexadecimal. Os leitores de tela não anunciam mais conteúdo de caixa de diálogo não relacionado após Cancelar. (SITES-25258)
* Corrigida a manipulação de foco da caixa de diálogo do modal Anotação. Abrir a caixa de diálogo agora define o foco no cabeçalho da caixa de diálogo e impede que o NVDA leia o conteúdo da tela e o texto da caixa de diálogo não relacionado. A navegação pelo teclado agora permanece dentro da caixa de diálogo até fechar. (SITES-25257)
* Problemas de layout do modal Pesquisa corrigidos na largura de 320 px. O conteúdo do modal agora se ajusta corretamente e evita sobreposição com a árvore de diretórios. Os usuários podem visualizar os resultados e navegar pelo diretório sem controles obscuros. (SITES-25246)
* O texto do modal Pesquisa não é mais recortado depois que o espaçamento do texto aumenta. O layout da árvore de diretórios agora mantém uma separação clara, de modo que os rótulos e as entradas permaneçam legíveis. Agora, os usuários podem concluir a pesquisa e a navegação sem texto sobreposto ou cortado. (SITES-25245)
* A ativação de Anotar agora move o foco do teclado para o conteúdo da anotação, não para o botão Sair da anotação. A ordem de tabulação segue uma sequência lógica e mantém os controles relacionados acessíveis sem navegação reversa. (SITES-25241)
* Os links Definir data e Sair do Timewarp não tinham um indicador de foco visível durante a navegação pelo teclado. A interface do usuário agora renderiza um estilo de foco distinto e de alto contraste, de forma que os usuários possam identificar o link ativo rapidamente. (SITES-25232)
* O cabeçalho Modal de teaser não impede mais que os usuários de teclado movam a caixa de diálogo. Os controles do teclado agora permitem ações de selecionar, mover e soltar, melhorando a usabilidade do leitor de tela e a operabilidade geral. (SITES-25226)
* O AEM agora usa um rótulo acessível significativo para o botão Informações do modal de teaser. Os leitores de tela anunciam um nome de ação claro em vez da string de texto alternativo do ícone padrão. (SITES-25223)
* Agora, os leitores de tela anunciam a ação correta quando os usuários ativam o botão Editar. O NVDA não relata mais &quot;Botão Visualizar pressionado&quot;, resultando em feedback enganoso e confusão durante a navegação pelo teclado. (SITES-25208)
* Agora, ao expandir o painel esquerdo, o foco do teclado é movido para o primeiro controle do painel esquerdo. A sequência de tabulações não salta mais para a barra de ferramentas secundária ou chega ao meio da lista, portanto, os usuários do teclado podem acessar o conteúdo do painel esquerdo sem navegar em ordem inversa. (SITES-24998)
* O conteúdo da barra do emulador de dispositivo agora permanece totalmente visível na largura do viewport de 320 px. O texto e os controles da barra de ferramentas quebram automaticamente em vez de truncar, reduzindo a sobreposição e melhorando a legibilidade. (SITES-24953)
* O AEM agora exibe o rótulo completo do dispositivo iPhone na barra de ferramentas do emulador. O texto não fica mais truncado na largura padrão, melhorando a legibilidade e a clareza da seleção de dispositivos. (SITES-24952)
* Os cabeçalhos da tabela Visualização de lista agora expõem o estado de classificação por meio de ARIA. Os leitores de tela anunciam uma ordem crescente ou decrescente após uma ação de classificação de coluna. (SITES-24943)
* O AEM agora preserva a visibilidade do rótulo do menu Mais ações na Visualização de cartão durante as alterações de espaçamento de texto. As opções de menu mantêm o texto completo, incluindo Publicação rápida, e o menu permanece legível durante qualquer configuração de espaçamento de texto da WCAG. (SITES-24941)
* A barra de menus Ações do cartão agora expõe um nome acessível em Visualização de cartão. Os leitores de tela apresentam claramente a finalidade da barra de menu, e o controle de voz pode selecionar o controle por nome. (SITES-24938)
* A Visualização de cartão não depende mais da semântica de grade ARIA, que causou um comportamento confuso do leitor de tela. A interface do usuário agora fornece funções e rótulos significativos para o conteúdo do cartão e a barra de ação do cartão, o que reduz a perda de controles durante o uso do teclado. (SITES-24933)
* A dica de ferramenta `Delete Modal` agora aparece sempre que os usuários passam o mouse sobre o ícone da dica de ferramenta. As ações de foco agora mostram o mesmo texto da dica de ferramenta, melhorando o acesso repetido para usuários de mouse e teclado. (SITES-24778)
* A navegação no painel esquerdo agora segue a ordem de foco do teclado esperada depois que os usuários configuram o painel. O foco da tabulação chega à área selecionada do painel esquerdo em vez de Alternar exibição, o que melhora a clareza de navegação do leitor de tela. (SITES-24754)
* Corrigido o feedback incorreto do NVDA durante a navegação com amostra de cor no modal Preferências do usuário. O NVDA agora lê o rótulo da amostra que recebe o foco, removendo a saída de cores enganosas. O conjunto de amostras agora oferece suporte à navegação consistente por teclado e à percepção de seleção clara. (SITES-24739)
* Saída NVDA detalhada reduzida para o controle `Spin`. Removida a rotulagem de grupo redundante que duplicava o rótulo de entrada, de modo que o NVDA anuncia o nome do controle uma vez. A navegação por teclado e leitor de tela agora oferece um anúncio único e claro. (SITES-24725)
* A caixa de diálogo Carrossel agora coloca o foco no título da caixa de diálogo, não na guia Itens. Os botões Cancelar e Esc restauram o foco para o controle que iniciou a caixa de diálogo, o que reduz a saída NVDA detalhada. (SITES-24716)
* A caixa de diálogo Seleção de link agora alinha o rótulo programático ao rótulo na tela para itens da árvore de último nível. A navegação com tecla de seta aciona um anúncio confiável do leitor de tela para cada item e remove a saída de rótulo enganosa. (SITES-24710)
* A caixa de diálogo Vincular abrir seleção agora se ajusta corretamente em um viewport de 320 px. O conteúdo não ultrapassa mais o limite do modal ou trunca, e o modal não mostra mais uma barra de rolagem horizontal. (SITES-24709)
* A caixa de diálogo Vincular abrir seleção agora restaura o foco do teclado para o acionador da caixa de diálogo após Fechar ou Cancelar. O foco não salta mais para a entrada Link, o que mantém o contexto do leitor de tela estável e reduz a navegação extra. (SITES-24707)
* A caixa de diálogo Modal da imagem agora segue uma sequência de foco lógica. O foco não ignora mais os controles anteriores ou cai no ponto de referência da página após Cancelar, e os usuários recuperam o foco no botão Configurar após sair. (SITES-24693)
* A caixa de diálogo do modal Painel de referências agora captura o foco do teclado. Tab e Shift+Tab permanecem dentro dos controles da caixa de diálogo, e o foco não é mai deslocado para o conteúdo da página. Os leitores de tela anunciam somente o conteúdo da caixa de diálogo. (SITES-24683)
* O modal Seleção de caminho de hiperlink agora define o foco no cabeçalho da caixa de diálogo ao abrir. Cancelar fecha a caixa de diálogo e restaura o foco para o botão da caixa de diálogo Abrir seleção, o que impede a perda de foco e a saída do leitor de tela redundante. (SITES-24672)
* O campo Pesquisar agora usa um rótulo persistente na tela em vez de texto de espaço reservado. O rótulo permanece visível durante a entrada, melhorando a clareza para usuários de teclado, leitor de tela e comando de voz. (SITES-24529)
* A caixa de diálogo modal Teaser agora define o foco no cabeçalho da caixa de diálogo ao ser aberta. Fechar a caixa de diálogo retorna o foco ao controle `Configure`, o que evita a perda de foco e o excesso de saída do leitor de tela. (SITES-24522)
* O painel Ativos do painel lateral agora inclui um controle Fechar. Fechar retorna o foco do teclado ao botão de alternância Painel lateral e impede a tabulação forçada pelo conteúdo do painel. (SITES-24489)
* A tabulação de teclado agora atinge botões e links dentro de tabelas de administração. Os usuários não dependem mais da navegação de célula com tecla de seta para encontrar controles interativos. (SITES-24285)
* A caixa de diálogo Componente de Imagem não expõe mais ícones decorativos de Ajuda e Tela cheia como imagens. Os leitores de tela agora ignoram esses ícones, mantendo o foco em controles acionáveis e conteúdo de campo. (SITES-2940)
* O Administrador de sites agora remove a função de imagem dos ícones de miniatura da pasta. A tecnologia assistiva ignora esses elementos decorativos, mantendo o foco nos nomes de pasta e ações. (SITES-2852)
* A Árvore de conteúdo agora direciona o foco do teclado para o item de árvore ativo ou o primeiro item de árvore. O container de árvore não funciona mais como uma parada de tabulação em branco, impedindo armadilhas de foco Shift+Tab. (SITES-1577)

#### Interface do usuário administrador{#sites-adminui-65-lts-sp2}

As configurações de visualização da lista do console Sites não refletiam as colunas mostradas na Visualização da lista. A caixa de diálogo foi aberta com caixas de seleção desmarcadas e uma contagem incorreta de colunas selecionadas. A correção sincroniza o estado da caixa de diálogo com as colunas de grade ativas e atualiza o contador para corresponder à visibilidade real da coluna. (SITES-38576)

#### Interface do usuário clássica{#sites-classicui-65-lts-sp2}

A edição do componente de texto da interface do usuário clássica exibia tags HTML originais, em vez de rich text após uma atualização. O Pacote de serviços 2 corrige a renderização do RTE da interface do usuário clássica para que o editor exiba o conteúdo formatado e preserve a marcação armazenada. A correção também interrompe a expansão de marcação durante edições repetidas e salva. (SITES-38709)

#### [!DNL Content Fragments]{#sites-contentfragments-65-lts-sp2}

O suporte a eventos headless não tinha eventos OSGi necessários para fragmentos de conteúdo e modelos no 6.5 LTS. A atualização adiciona o pacote de eventos e as dependências necessárias, além de incluir um build do 6.5 LTS. Os eventos Fragmento de conteúdo e Modelo agora são acionados corretamente e oferecem suporte aos fluxos de trabalho da API de Inicializações. (SITES-35329)

#### [!DNL Content Fragments] — Admin{#sites-admin-65-lts-sp2}

* A manipulação de componentes foi ajustada na interface de criação do Sites para interromper comportamentos irregulares durante atualizações de página. O defeito levou a respostas imprevisíveis do editor que interferiram nas modificações de conteúdo de rotina e reduziram a eficiência do fluxo de trabalho. A atualização alinha a lógica do editor aos padrões de interação esperados e fornece desempenho confiável durante as atividades de criação. (SITES-35078) CRÍTICO

* Uma regressão interrompeu a Visualização de lista do console do Assets quanto a fragmentos de conteúdo e acionou um erro durante a renderização da lista. A atualização corrige a lógica de visualização de lista após a remoção de preview-info e restaura a saída da lista estável. O console agora exibe Fragmentos de conteúdo sem falhas e mantém as interações de lista utilizáveis. (SITES-38683)
* O Editor de fragmento de conteúdo agora localiza o rótulo Tags. O editor também localiza o rótulo Coleções, de modo que o texto da interface do usuário corresponda à localidade selecionada. (SITES-977)


#### [!DNL Content Fragments] — Editor de fragmentos{#sites-fragments-editor-65-lts-sp2}

* As tags de variação do Fragmento de conteúdo desapareceram quando o botão de alternância de recurso permaneceu desativado após a refatoração. A correção restaura o suporte à tag de variação mesmo quando o botão de alternância permanece desativado. Os autores podem adicionar e visualizar novamente as tags de variação no Editor de fragmento de conteúdo. (SITES-38682) CRÍTICO
* Os fragmentos de conteúdo editados desapareceram da lista do console do Assets depois que os autores voltaram do Editor de fragmento de conteúdo. O armazenamento em cache do navegador retornou uma lista obsoleta e ocultou o fragmento atualizado até uma atualização manual. A correção adiciona a manipulação do controle de cache para o caminho de retorno do editor, de modo que a lista seja recarregada corretamente e mantenha o fragmento editado visível. (SITES-35374) CRÍTICO

* O RTE do fragmento de conteúdo apresentou problemas visuais e de layout após alterações recentes no estilo da interface do usuário. O Pacote de serviços 2 refina o estilo do RTE para que a barra de ferramentas e a área editável sejam renderizadas corretamente e permaneçam legíveis. O Editor de fragmento de conteúdo agora se alinha à aparência e ao comportamento do Editor de páginas. (SITES-38684)
* A remoção de escopos IMS do Seletor de ativos Polaris interrompeu a integração do Fragmento de conteúdo com o ponto de acesso de entrega. Os autores detectam falhas ao abrir o seletor de ativos remoto e selecionar ativos. A atualização adiciona novamente os escopos IMS necessários e restaura o acesso estável da camada de entrega. (SITES-35837)
* O painel Conteúdo associado não renderiza mais um espaço reservado &quot;indefinido&quot; codificado. O Editor de fragmento de conteúdo agora resolve esse texto por meio de recursos de localização, para que os editores vejam o texto da interface do usuário traduzido. (SITES-33675)
  <!-- REMOVED FROM BUG LIST FEBRUARY 13, 2026 * Preview error messaging now uses localized strings instead of raw `Cannot print fragment's Json` text. The Content Fragment Editor now shows translated output across locales during GraphQL endpoint resolution failures. (SITES-33666)-->
* O Editor de fragmento de conteúdo agora exibe um rótulo de guia Geral traduzido nas localidades. O editor substitui o texto de guia não localizado e remove as IDs internas dos títulos das guias. (SITES-30715)
* O Editor de fragmento de conteúdo agora exibe nomes traduzidos para os tipos de ativos permitidos. A lista do seletor não mescla mais strings internas e rótulos somente em inglês quando os autores configuram restrições de referência de conteúdo. (SITES-29699)

#### [!DNL Content Fragments] — API GraphQL {#sites-graphql-api-65-lts-sp2}

* A manipulação de validação de consulta do GraphQL foi refinada para interromper falhas de implantação causadas por erros de execução de filtro. O defeito gerou exceções durante a inicialização do aplicativo e bloqueou a implantação bem-sucedida em ambientes afetados. A revisão garante um comportamento de validação consistente e permite uma implantação fácil sem interrupções de validação de consulta em tempo de execução. (SITES-34301) CRÍTICO

* A caixa de diálogo Editar ponto de acesso do GraphQL agora exibe strings da interface do usuário localizadas. A caixa de diálogo não mostra mais texto somente em inglês, como &quot;O esquema do GraphQL foi retirado da configuração&quot;, e os rótulos relacionados são renderizados corretamente nas localidades. (SITES-34018)

#### [!DNL Content Fragments] — Editor de consultas GraphQL{#sites-graphql-query-editor-65-lts-sp2}

* A manipulação de validação de consulta do GraphQL foi refinada para interromper falhas de implantação causadas por erros de execução de filtro. O defeito gerou exceções durante a inicialização do aplicativo e bloqueou a implantação bem-sucedida em ambientes afetados. A revisão garante um comportamento de validação consistente e permite uma implantação fácil sem interrupções de validação de consulta em tempo de execução. (SITES-35529)
* O GraphQL Explorer não falha mais quando um nome do Navegador de configuração contém caracteres CJK. A criação de pontos de acesso e o acesso a consultas salvas funcionam normalmente e a página Editor de consultas do GraphQL permanece sem erros. (SITES-31616)

#### [!DNL Content Fragments] — Editor de modelos{#sites-model-editor-65-lts-sp2}

* Os modelos de Fragmento de conteúdo aninhados pararam de funcionar quando a refatoração vinculou o recurso a um botão de alternância desativado. A correção restaura o suporte a modelo aninhado sem exigir alterações de alternância. Os autores podem criar e usar modelos aninhados novamente no Editor de modelos. (SITES-38681) CRÍTICO

* O painel de filtro Modelos de fragmento de conteúdo não expõe mais as strings não localizadas. O AEM agora exibe rótulos de filtro localizados e valores de status localizados em todas as localidades. (SITES-30863)
* O Editor de modelo de fragmento de conteúdo agora renderiza strings localizadas para a caixa de diálogo de aviso de bloqueio. A interface do usuário substitui mensagens em inglês não localizadas por recursos de localidade em todos os idiomas compatíveis. (SITES-28592)

#### [!DNL Content Fragments] — API REST{#sites-restapi-65-lts-sp2}

O AEM Headless exigia uma ramificação de versão dedicada para evitar dependências e conflitos de versão de pacote com builds principais. A atualização adiciona uma ramificação headless `release/6.5lts` e alinha conjuntos de dependências e versões de pacotes. O Jenkins agora cria a base de código headless de maneira limpa, sem colisões de versão. (SITES-36585)

<!-- #### Component console{#sites-component-console-65-lts-sp2} -->

#### API de conteúdo{#sites-content-api-65-lts-sp2}

Uma falha de alternância de recurso relatou incorretamente o status da API de gerenciamento de página. A atualização adiciona um sinalizador de ativação dedicado e o avalia junto com o botão de alternância existente. A API de gerenciamento de página agora mostra um status estável. A API de gerenciamento de site permanece na fase experimental. (SITES-39284)

#### Back-end principal{#sites-core-backend-65-lts-sp2}

* Uma alteração na experiência de criação do Sites para resolver comportamentos inconsistentes que interromperam fluxos de trabalho de edição de página padrão. Os autores encontraram resultados inesperados durante a interação do componente, o que interferiu nas atualizações de conteúdo e reduziu a confiabilidade. A alteração restaura o comportamento estável do editor e garante a execução consistente das ações de criação nos cenários afetados. (SITES-35162) CRÍTICO

* O comportamento de criação do Sites foi refinado para resolver um problema que interrompeu a edição da página e causou resultados inconsistentes durante a interação do componente. Os autores tiveram respostas inesperadas da interface do usuário que interferiram nas atualizações do conteúdo e reduziram a confiabilidade do fluxo de trabalho. A alteração restaura o gerenciamento estável do estado do editor e garante a execução previsível das ações de criação nos cenários afetados. (SITES-34499)

<!--
#### Core Components{#sites-core-components-65-lts-sp2}

#### Campaign integration{#sites-campaign-integration-65-lts-sp2}

#### Experience Fragments{#sites-experiencefragments-65-lts-sp2}

#### Foundation Components (Legacy){#sites-foundation-components-legacy-65-lts-sp2}
-->

#### Lançamentos{#sites-launches-65-lts-sp2}

* A Linha do tempo do Sites mostrava um texto em inglês codificado durante a promoção do Launch: &quot;Created version ... before promoting launch.&quot; A atualização substitui a string codificada pelo manuseio de mensagem localizado. A Linha do tempo agora exibe o texto localizado e alinha a entrada com o comportamento de localização padrão do AEM. (SITES-39157)
* O escopo de promoção do Launch mudou quando os autores promoveram uma subseção usando Promover página atual e subpáginas. O AEM também promoveu páginas não relacionadas e causou modificações inesperadas no site ativo. A correção corrige o cálculo do escopo do Launch para que somente a subárvore escolhida seja promovida. (SITES-38315)
* Os fragmentos de conteúdo dentro de inicializações não participavam do índice `damAssetLucene`, o que limitava os resultados da pesquisa e a eficiência das consultas. Essa alteração adiciona caminhos de fragmento de conteúdo de inicialização à definição do índice. A pesquisa e as consultas personalizadas agora encontram fragmentos de conteúdo em `/content/launches`. (SITES-35634)
* A interface de inicializações exibia controles de inicialização de fragmentos de conteúdo, embora o produto não disponibilize inicializações de fragmentos de conteúdo na interface por toque. Esta alteração remove os caminhos de código de inicialização de fragmentos de conteúdo do cq-launches-content e ajusta a filtragem da lista de inicializações. Os autores agora veem opções consistentes de inicialização de página sem entradas de inicializações de fragmentos de conteúdo. (SITES-35633)
* O Quickstart do AEM 6.5 LTS não tinha os pacotes e pré-requisitos necessários de para inicialização, o que bloqueava a ativação da OpenAPI de inicializações. A atualização adiciona pacotes de inicializações e dependências necessárias, como suporte a métricas, atualizações de DAM-cfm e configuração de fila. As APIs de inicializações agora são executadas no Quickstart 6.5 LTS com os componentes de tempo de execução necessários presentes. (SITES-35297)
* O pacote de inicializações de fragmentos de conteúdo incluía versões mais recentes de dependências e bibliotecas GraphQL desnecessárias, o que complicava a integração com o AEM 6.5 LTS. Essa alteração alinha as versões das dependências com a linha de base do AEM 6.5 LTS e remove as dependências de GraphQL não utilizadas. A resolução do pacote agora permanece consistente e a inicialização de fragmentos de conteúdo permanece estável. (SITES-35295)
* As inicializações do AEM agora executam um pipeline dedicado do Jenkins para a ramificação 6.5 LTS. O pipeline é executado durante a noite e cria e envia alertas de falha por email. Essa configuração aumenta a cobertura dos testes e detecta regressões antecipadamente. (SITES-35293)
* O AEM 6.5 LTS agora inclui um pacote atualizado da API de lançamentos com versões de artefatos alinhadas. O pacote acompanha a linha de código principal, mantendo a versão correta da versão 6.5 LTS. Esta atualização estabiliza o uso da API de lançamentos em toda a pilha da versão 6.5 LTS. (SITES-35292)
* O AEM 6.5 LTS agora inclui um pacote launches-core atualizado com versões de dependências alinhadas. A atualização adiciona ao launches-core o tratamento dos tipos de dados UUID de fragmento e UUID de referência. O processamento de lançamento agora mantém um comportamento consistente entre os fluxos de trabalho de lançamentos e fragmentos de conteúdo. (SITES-35290)
* Aprimoramos o editor de sites para resolver um comportamento inconsistente que prejudicava os fluxos de trabalho normais de criação de páginas. Os autores encontraram uma interação inesperada de componentes que interferiu nas atualizações de conteúdo e reduziu a confiabilidade da edição. A alteração restaura o gerenciamento consistente do estado da interface do usuário e garante a execução previsível das ações de criação nos cenários afetados. (SITES-35138)
* Editar lançamentos agora exibe textos de erro localizados em vez da string `Provided path is not a launch` codificada. Agora a interface do usuário renderiza mensagens traduzidas entre idiomas quando Editar recebe um caminho de lançamento inválido. (SITES-33360)
* O AEM 6.5 LTS agora inclui o trabalho de side-port da OpenAPI de lançamentos. A atualização coloca em paridade os pacotes de APIs de lançamentos, os pacotes de conteúdo e os artefatos necessários do Quickstart, além de habilitar cenários da OpenAPI para lançamentos de fragmentos de conteúdo com validação estável de CI. (SITES-32050)
* A interface do usuário de lançamentos agora localiza o rótulo do modelo substituído. Os detalhes da substituição de modelo agora exibem o texto traduzido, em vez de uma string apenas em inglês. (SITES-29525)
* O AEM corrigiu uma chave de localização ausente em **Sites** > **Lançamentos** > **Editar**. Os usuários agora veem uma mensagem de erro traduzida em vez da string bruta &quot;Não é possível atualizar a lista de origem de lançamento&quot;. (SITES-21499)
* A interface da promoção de lançamento agora exibe rótulos e ações de status localizados. A área de visualização mostra o texto traduzido para **Excluído**, **Novo** e **Exibição**, em vez de strings brutas em inglês. (SITES-13540)
* A criação de lançamentos agora mostra mensagens de erro localizadas. A UI não exibe mais strings brutas em inglês, como `Unable to create launch page`, `Source root resource is not a page` ou `Mandatory parameter is missing`. (SITES-13085)


<!-- #### Link Checker{#sites-link-checker-65-lts-sp2} -->


#### MSM: Live Copies{#sites-msm-live-copies-65-lts-sp2}

* Os administradores tinham visibilidade limitada do processamento push-on-modify do MSM durante as alterações de conteúdo. A correção adiciona um registro detalhado sobre a recepção de eventos do MSM e a execução de implantação. A saída de depuração agora mostra quais eventos foram acionados, quais caminhos de conteúdo foram alterados e quem acionou a alteração. (SITES-38029)
* O AEM corrigiu um problema de layout de localização no campo de data Implantação de blueprint. O prompt de data agora se encaixa no controle e permanece legível nos idiomas compatíveis, incluindo `fr_FR`. (SITES-14961)

<!-- #### Page editor{#sites-pageeditor-65-lts-sp2} -->

#### Replicação{#sites-replication-65-lts-sp2}

A publicação do Editor de páginas agora lida com URLs que contêm seletores ou sufixos. A solicitação publicada agora envia o caminho da página JCR, não um seletor ou uma string de URL de sufixo, portanto, a ativação é concluída e o conteúdo é publicado. A replicação agora retorna um status de erro em caso de falha, o que impede mensagens falsas de &quot;publicação iniciada&quot;. (NPR-43288)

<!-- #### Rich Text Editor{#sites-rte-65-lts-sp2} -->

#### Editor de modelo{#sites-template-editor-65-lts-sp2}

Texto de status do modelo exibido verticalmente em **Ferramentas** > **Geral** > **Modelos** para algumas localidades. O rótulo &quot;desatualizado&quot; comprometia o layout e era exibido como uma coluna de caracteres. A correção corrige o estilo de status do modelo para que o rótulo seja renderizado em uma única linha horizontal. (SITES-36797)

#### Editor universal {#sites-universal-editor-65-lts-sp2}

* Uma configuração padrão OSGi foi definida como `preview=true` e forçou o Editor universal a iniciar no modo Visualização. Essa atualização corrige o valor padrão e restaura o comportamento padrão da entrada de Produção. O Editor universal agora é aberto no modo Produção, a menos que um administrador ative explicitamente o modo Visualização. (SITES-37193)
* O comando Abrir do Editor universal agora é padronizado para o modo Visualização nos ambientes de Desenvolvimento e Preparo. O comando adiciona `preview=true`, que mantém as verificações do autor alinhadas ao contexto de visualização e evita aberturas acidentais de Produção. (SITES-33839)

### [!DNL Assets]{#assets-65-lts-sp2}

O Assets Relacionar agora funciona para nomes de arquivo que incluem espaços. A lógica do cliente Relacionar atualizada agora lida corretamente com caminhos que contêm espaço e evita erros de origem `undefined` durante a seleção da relação. A caixa de diálogo Relacionar agora abre e salva as relações sem interrupções ou spinners na interface do usuário. Os usuários do DAM podem relacionar, derivar e não relacionar ativos sem renomear arquivos. (Assets-56418)

#### [!DNL Dynamic Media]{#assets-dm-65-lts-sp2}

* Nova integração do reprodutor de vídeo Dynamic Media (implantação limitada) - Uma nova experiência do reprodutor de vídeo Dynamic Media agora está disponível no AEM 6.6 Quickstart. No momento, esse aprimoramento está habilitado apenas para clientes iniciais como parte de uma implantação controlada. (Assets-60165)
* Resolvido um problema em que a opção Selecionar miniatura na caixa de diálogo Propriedades de vídeo não abria o seletor de ativos, restaurando a capacidade de os usuários escolherem miniaturas personalizadas para ativos de vídeo. (Assets-58926)
* No vídeo do Dynamic Media, foi adicionado suporte para selecionar árabe na lista suspensa de idioma Legendas e faixas de áudio, permitindo que os autores gerenciem legendas em árabes diretamente no AEM. (Assets‑61771)

<!-- #### [!DNL Dynamic Media] - Hybrid Mode {#assets-dm-hybrid-65-lts-sp2} -->

<!--
#### Forms Designer
-->

### [!DNL Forms]{#forms-65-lts-sp2}

* Os usuários tiveram problemas com a funcionalidade `Data Source / Enter Keyword` do editor de Modelo de dados de formulário (FDM). Esse problema afetou a capacidade de pesquisar e selecionar fontes de dados. (FORMS-23971)
* Em dispositivos móveis, o componente de tabela no Adaptive Forms renderizava um cabeçalho oculto na parte superior, fazendo com que os leitores de tela anunciassem incorretamente o conteúdo. Isso afetava os usuários que dependiam de leitores de tela para navegação. (FORMS-23754)
* Os usuários tiveram problemas com os Componentes principais baseados em Formulários adaptáveis que fazem referência a tipos de recursos sinalizados como granite:InternalArea, que afetaram a funcionalidade de vários componentes granite no complemento Forms no local. (FORMS-23632)
* Falha no envio do formulário após a atualização para o AEM 6.5 LTS SP1. Os usuários observaram que a ausência do pacote com.adobe.cq.social.commons.CollabUtil estava causando erros de compilação de JSP e falhas nas ações de email. (FORMS-23457)
* Os usuários enfrentavam problemas com o hCaptcha não sendo traduzido corretamente em formulários adaptáveis baseados em componentes fundamentais. Isso afetou a capacidade dos usuários que não falavam inglês de preencher formulários com precisão. (FORMS-23426)
* Os usuários tiveram falhas no envio do formulário com uma SAXParseException: “O conteúdo não é permitido no prólogo” (HTTP 500). Esse problema ocorreu devido a um valor nulo no XML de dados pré-preenchidos, o que causou uma falha na análise do XML no lado do servidor. (FORMS-22633)
* Os usuários enfrentavam problemas com Formulários adaptáveis que falhavam em auditorias das Diretrizes de Acessibilidade para Conteúdo da Web (WCAG). O motivo foi que a marcação de navegação por guias do formulário estava inválida. Ou seja, um elemento que não seja de lista é exibido como um filho direto de uma lista, onde apenas itens de lista são permitidos. Esse problema impediu que o formulário fosse aprovado pelos validadores de acessibilidade e afetou as organizações que precisam cumprir requisitos legais ou internos de conformidade. (FORMS-22101)
* Os usuários enfrentaram problemas de acessibilidade com o documento de registro (DoR) / PDF de envio, nos quais campos em branco do formulário não estavam marcados como elementos de formulário. Isso causou dificuldades para os leitores de tela, prejudicando a capacidade dos usuários com deficiência de navegar e preencher formulários de maneira eficaz. (FORMS-21989)
* Os usuários enfrentaram um problema em que as notas de rodapé dos componentes dentro de um subpainel não eram exibidas durante o carregamento do formulário. Esse problema ocorria quando o item com a nota de rodapé era o último componente na página. (FORMS-21925)
* Os usuários enfrentaram problemas ao selecionar componentes no editor do AEM Forms. Ao alternar entre as guias e voltar à primeira guia, alguns campos deixavam de poder ser selecionados, dificultando a identificação e a interação. (FORMS-21814)
* Os usuários detectaram uma vulnerabilidade de segurança no painel dos formulários adaptativos. Especificamente, foi identificado um problema de cross-site scripting (XSS) no arquivo startpointcontrol.js que poderia permitir potencialmente a execução de scripts maliciosos. (FORMS-20679)
* Nas implantações em cluster do AEM Forms 6.5 LTS no JBoss® EAP 8, os arquivos `domain/configuration/domain_oracle.xml`, `domain_mysql.xml` e `domain_mssql.xml` não contêm mais uma tag `<security>` duplicada que causava um XML inválido e impedia o início do controlador de domínio. (FORMS-24687)
* No modo Turnkey, a atualização da porta do banco de dados agora é aplicada corretamente durante a nova instalação e atualização. No modo de instalação nova, os usuários podem escolher entre todas as portas disponíveis; já no modo de atualização, a porta do banco de dados atualizada no arquivo lc_turnkey.xml é referenciada corretamente durante o processo de atualização. (FORMS-24689)
* Ao configurar o JBoss® EAP 8.0 no Linux®, os scripts de shell modificados no Windows não causam mais erros `/bin/sh^M: bad interpreter or $'\r': command not found` devido aos finais de linha CRLF. (FORMS-24688)
* Em implantações do Forms JEE LTS em execução no JBoss® EAP 8, a interface do usuário do Reader Extensions pode falhar com um erro interno do servidor. (FORMS-24894)
* No Linux®, os usuários tiveram problemas de tempo de execução ou implantação quando o Gerenciador de Configuração do Forms JEE LTS foi executado com um valor `OSFileSetIntendedFor` incorreto ou indefinido em `configurationManager/config/solcomp/LFS_Foundation.properties`, o que impediu que a configuração fosse personalizada corretamente para o Linux®. Após a instalação e antes de executar o Configuration Manager, defina `OSFileSetIntendedFor=Linux` nesse arquivo. (FORMS-24741)

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
* O AEM agora evita entradas de ACL duplicadas para o grupo `contributor` no `WEB-INF/resources/provisioning/model.txt` gerado. A saída do WAR agora contém um único bloco de ACL consistente, o que evita diferenças confusas nas permissões durante a revisão. (GRANITE-63269)
* O AEM não limpa mais as configurações da lista de bloqueios e da lista de permissões do firewall de desserialização durante as operações de atualização de pacotes. A lógica atualizada de registro de filtros mantém a instância ativa do firewall alinhada com a configuração salva, de modo que a proteção permanece ativada sem a necessidade de reinicialização. (GRANITE-61382)
* O Felix Web Console não apresenta mais erros intermitentes `NullPointerException` durante o acesso `/system/console`. A atualização do tratamento do ServiceTracker evita que o estado do rastreador seja nulo. O logon e a navegação do console permanecem estáveis durante solicitações repetidas e validações automatizadas. (GRANITE-61042)

<!--
#### Campaign{#foundation-campaign-65-lts-sp2}

#### Cloud Services{#foundation-cloudservices-65-lts-sp2}

#### Communities {#foundation-communities-65-lts-sp2}

#### Content distribution{#foundation-content-distribution-65-lts-sp2}
-->

#### CRX {#foundation-crx-65-lts-sp2}

O CRXDE Lite não mostra mais uma guia em branco ao abrir um arquivo JSP após uma atualização do Pacote de serviços. O AEM agora fornece versões correspondentes do código principal e dos complementos do CodeMirror, o que evita o erro fatal no navegador e mantém o editor utilizável. (GRANITE-64333)

#### Granite{#foundation-granite-65-lts-sp2}

O Validador de segurança de expressão agora lida com valores de configuração OSGi em branco ou nulos. Ele aplica padrões seguros, ignora matrizes em branco e registra logs limpos, impedindo o erro NullPointerException e resultados de validação imprevisíveis. (NPR-43163)

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

O pacote de serviços 2 do AEM 6.5 LTS exige o S3 Connector 1.60.10 ou posterior. A configuração do armazenamento de dados S3 agora inclui `crossRegionAccess` e `mode` para que os administradores possam habilitar o acesso ao bloco entre regiões e alternar o armazenamento para GCP quando necessário. O `s3EndPoint` agora espera uma região alinhada a `s3Region`, ou ela permanece em branco para que o driver gere o ponto de acesso. (GRANITE-64873)


#### Início rápido{#foundation-quickstart-65-lts-sp2}

* O Sling atualiza a lista de permissões de login administrativo para utilizar terminologia inclusiva e novos PIDs de configuração. Essa alteração está em conformidade com o Sling JCR Base 3.2.0. (GRANITE-63756)

  **Impacto**

   * O Sling considera esses PIDs obsoletos, e você deve removê-los de suas configurações:
      * PID de fábrica: `org.apache.sling.jcr.base.internal.LoginAdminWhitelist.fragment`
      * PID global: `org.apache.sling.jcr.base.internal.LoginAdminWhitelist`
Essas configurações mais antigas usam propriedades, como `whitelist.name` e `whitelist.bundles`.

   * O Sling ainda fornece compatibilidade retroativa parcial para os PIDs obsoletos, mas não os use em novas configurações. Em vez disso, use os `LoginAdminAllowList.*` PIDs mais recentes.
   * Não execute configurações obsoletas e novas de lista de permissões ao mesmo tempo. Configurações mistas podem criar ambiguidade e produzir comportamento não intencional. Ao migrar para o AEM 6.5 LTS SP2, remova os PIDs obsoletos completamente.

  **O que você deve fazer**

   1. Encontre configurações de lista de permissões que utilizem PIDs `LoginAdminWhitelist*`.
   1. Substitua-os pelos novos PIDs apropriados:

      * PID de fábrica: `org.apache.sling.jcr.base.LoginAdminAllowList.fragment`
      * PID global: `org.apache.sling.jcr.base.LoginAdminAllowList`

      Para obter mais detalhes, consulte [Abordagem obsoleta para pacotes de lista de permissões para login administrativo](https://sling.apache.org/documentation/the-sling-engine/service-authentication.html#deprecated-approach-to-allowlist-bundles-for-administrative-login).

* O AEM 6.5 LTS SP2 atualiza o conjunto de pacotes de camada de base para Sling, Oak e Felix. Essas atualizações fortalecem a estabilidade do tempo de execução principal e alinham as versões de dependência na plataforma. (GRANITE-61874)

<!--
#### Security{#foundation-security-65-lts-sp2}

AEM now prevents NullPointerException errors when a logged-in user lacks read access for some groups and opens the Groups tab. The tab now hides groups without access and renders group membership details without a blank or unresponsive UI. (NPR-43311)
-->

#### Sling{#foundation-sling-65-lts-sp2}

O AEM agora inclui o Sling Engine 2.16.6. Essa alteração elimina violações XSS sinalizadas por ferramentas de segurança e melhora a segurança e a estabilidade da renderização principal. (NPR-43105)

<!--
#### Translation{#foundation-translation-65-lts-sp2}

#### User interface{#foundation-ui-65-lts-sp2}
-->

#### WCM{#foundation-wcm-65-lts-sp2}

As traduções do AEM já não apresentam falhas no Java 17 ou no Java 21 devido a problemas com o formato XLIFF. O pipeline de exportação agora gera arquivos XLIFF em conformidade com os padrões, aceitos pelos prestadores de serviços de tradução. Essa alteração remove as interrupções do trabalho de tradução e restaura a entrega previsível entre o AEM e os serviços de tradução. Os fluxos de trabalho de tradução agora permanecem estáveis em tempos de execução Java compatíveis. (CQ-4360217)

#### Fluxo de trabalho{#foundation-workflow-65-lts-sp2}

EmailNotificationService-Processor não aciona mais erros &quot;Segmento não encontrado&quot; repetidos durante o manuseio de notificação do fluxo de trabalho. O tratamento de exceção atualizado detecta SegmentNotFoundException e interrompe o loop de processamento em vez de continuar com leituras inválidas. A execução do fluxo de trabalho permanece estável e registra quedas de ruído durante o acesso à caixa de entrada e ao item de trabalho. (GRANITE-62635)




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

Veja também [Atualizar a versão do AEM Uber Jar](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

### Atualizar {#upgrade}

* Para mais detalhes sobre o procedimento de upgrade, consulte a [documentação de upgrade](/help/sites-deploying/upgrade.md).
* Para obter instruções detalhadas de atualização, consulte o [Guia de atualização do AEM Forms 6.5 LTS SP1 no JEE](https://experienceleague.adobe.com/en/docs/experience-manager-65-lts/content/forms/upgrade-aem-forms/upgrade)

#### Práticas recomendadas para as atualizações do Pacote de serviços do AEM 6.5 LTS

<!-- THE INFORMATION UNDER THIS HEADING CAME FROM CQDOC-23078 -->

**Ambiente**
Aplica-se a: clientes do AEM 6.5 LTS (No local) que estejam instalando o Pacote de serviços 2 (SP2). O SP2 é fornecido como um JAR do Quickstart.

**Por que essa prática de atualização é importante**
O SP2 para o AEM 6.5 LTS é fornecido como um arquivo JAR do Quickstart, em vez de um ZIP para instalação pelo gerenciador de Pacotes. Clientes locais realizam a atualização por substituir o arquivo JAR de início rápido, fazer a extração do conteúdo e reiniciar. Esse método é consistente com o procedimento de atualização no local da Adobe.

**Fluxo de atualização recomendado (Autor ou Publicação)**

1. Verifique se a instância AEM 6.5 LTS está íntegra e acessível.
1. Baixe o arquivo JAR do Quickstart (por exemplo, `cq-quickstart-6.6.x.jar`) na seção de distribuição de software.
1. Interrompa a instância de execução.
1. No diretório de instalação do AEM (fora de `crx-quickstart/`), substitua o JAR do Quickstart anterior pelo JAR do SP2.
1. Extraia o arquivo JAR:

   ```java
   java -jar cq-quickstart-6.6.x.jar -unpack
   ```

   (Ajuste sinalizadores de heap conforme necessário.)

1. Renomeie o arquivo JAR extraído para corresponder à função e à porta como, por exemplo, `cq-author-4502.jar` ou `cq-publish-4503.jar`.
1. Inicie o AEM e confirme a atualização na interface (Ajuda > Sobre) e nos logs.

**Boas práticas para a integridade do sistema**

* Execute a atualização em ambientes de teste ou inferiores antes de colocá-la em produção.
* Faça um backup completo e restaurável (repositório mais qualquer armazenamento de dados externo) antes de começar.
* Revise a orientação para atualização da Adobe no local e os requisitos técnicos (Java 17/21 recomendado para LTS).

>[!NOTE]
>
>Os nomes de arquivo mostrados acima (por exemplo, `cq-quickstart-6.6.x.jar`) refletem a nomenclatura de artefatos do Quickstart adotada nesta versão LTS; utilize sempre o nome exato do arquivo baixado na distribuição de software.

## Instalar e atualizar{#install-update}

Para conferir os requisitos de instalação, consulte as [instruções de instalação](/help/sites-deploying/custom-standalone-install.md).

>[!NOTE]
>
> Se você estiver atualizando diretamente de SPs antigos do 6.5 para o LTS SP1, siga as instruções fornecidas para a [atualização](/help/sites-deploying/upgrade.md) do 6.5 para o 6.5 LTS GA.


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

A Adobe analisa e aprimora continuamente os recursos de seus produtos para oferecer mais valor aos clientes, modernizando ou substituindo recursos legados. Essas alterações são implementadas considerando cuidadosamente a compatibilidade com versões anteriores.

Para garantir a transparência e permitir o planejamento adequado, a Adobe segue esse processo de descontinuação do Adobe Experience Manager (AEM):

* A descontinuação é anunciada primeiro. Os recursos descontinuados continuam disponíveis, mas não são mais aprimorados.
* A remoção não ocorre antes da próxima versão principal. A linha do tempo de remoção planejada é comunicada separadamente.
* É disponibilizado pelo menos um ciclo de lançamento de versão para que os clientes façam a transição para alternativas compatíveis antes da remoção de um recurso.

### Recursos descontinuados {#deprecated-features}

Esta seção lista os recursos e funcionalidades que a Adobe descontinuou no AEM 6.5 LTS. Normalmente, a Adobe descontinua recursos antes de os remover em uma versão futura e fornece uma alternativa.

Os clientes são aconselhados a analisar se usam o recurso/funcionalidade em sua implantação atual. Faça planos para alterar a implementação a fim de utilizar a alternativa oferecida.

| Área | Destaque | Substituição | Versão (SP) |
| --- | --- | --- | --- |
| Início rápido | APIs do Mongo | As APIs do Mongo agora estão obsoletas e devem ser removidas em versões futuras. | 6.5 TS SP2 |
| Sites | Suporte a Fragmento de conteúdo na API REST do AEM Assets | O AEM 6.5 LTS SP2 fornece OpenAPIs modernas para gerenciamento de fragmentos de conteúdo e modelos. Portanto, os pontos de acesso mais antigos de suporte a fragmentos de conteúdo na API REST do AEM Assets agora estão obsoletos.<br>A Adobe pretende manter esses pontos de acesso mais antigos disponíveis até que seja feito um anúncio de fim de vida útil. A Adobe não planeja melhorias adicionais para os pontos de acesso obsoletos. | 6.5 LTS SP2 |
| Sites | [Editor SPA](/help/sites-developing/spa-overview.md) | Os editores recomendados para gerenciar conteúdo headless no AEM são:<br>- [O Editor Universal](/help/sites-developing/universal-editor/introduction.md) para edição visual.<br>- [O Editor de Fragmentos de Conteúdo](/help/assets/content-fragments/content-fragments-managing.md) para edição baseada em formulários. | 6.5 LTS GA |
| [!DNL Foundation] | Suporte para com.adobe.granite.oauth.server | Integração do Adobe IMS |  |

### Recursos removidos {#removed-features}

Esta seção lista os recursos e funcionalidades que foram removidas do AEM 6.5 LTS. Nas versões anteriores, esses recursos estavam marcados como descontinuados.

* O suporte de RDBMK na persistência de repositório do CRX foi removido.
* Em ambientes agrupados, o MongoMK agora é a única opção compatível de persistência do repositório.

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

* No Configuration Manager, a inicialização do banco de dados falha durante o bootstrap no AEM Forms 6.5 LTS JEE Turnkey no modo personalizado quando nenhum módulo ou apenas componentes limitados são selecionados. A falha se deve a uma dependência ausente (xalan-2.7.2.jar), resultando em um erro. Adicionar o arquivo JAR ao adobe-livecycle-jboss.ear\lib resolve o problema. (FORMS-24690)
* No Forms JEE LTS em execução no JBoss®, a funcionalidade relacionada ao email pode falhar. Ao tentar usar recursos de email, o servidor pode registrar um erro semelhante a `Error IMAPProvider not a subtype`. (FORMS-24892)

### Corrupção do repositório durante a compactação online após a compactação offline (GRANITE-65146) {#repository-corruption-during-online-compaction-after-offline-compaction-granite-65146}

Os usuários podem enfrentar corrupção do repositório durante a compactação online se a compactação offline tiver sido executada anteriormente no repositório JCR. Um `SegmentNotFoundException` (SNFE) pode ocorrer neste cenário e pode levar à corrupção do repositório.

Para resolver o problema, instale o Hotfix de [Distribuição de Software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.2-hotfix-GRANITE-65388-1.0.zip). Como o hotfix inclui um pacote de baixo nível `oak-segment-tar`, a instância é reiniciada após a instalação.

Planeje o tempo de inatividade da instância ao aplicá-la. Para compactação offline, use o [`oak-run` jar](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/oak-run-1.88.1-B006.jar) correspondente, também disponível na Distribuição de Software.

>[!NOTE]
>
> * Para qualquer operação `oak-run`, use o [`oak-run` 1.88.1-B006 jar](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/oak-run-1.88.1-B006.jar).
>
> * Inicie o AEM definindo a propriedade do sistema `oak.compaction.legacy=true`.

### Pacote `com.adobe.granite.apicontroller` ausente no AEM 6.5 LTS SP2 (GRANITE-67640) {#missing-apicontroller-bundle-granite-67640}

O pacote `com.adobe.granite.apicontroller` está ausente no AEM 6.5 LTS SP2. Esse pacote controla como os pacotes OSGi são resolvidos e pode impedir que os pacotes sejam resolvidos para outros pacotes, o que é útil para limitar as APIs expostas.

Instale o hotfix de [Distribuição de Software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.2-hotfix-GRANITE-67640-1.0.zip) para usar esta funcionalidade.

>[!NOTE]
>
> Após instalar o hotfix, verifique o status do pacote de todos os pacotes instalados para garantir que a configuração padrão do `com.adobe.granite.apicontroller` não tenha introduzido restrições de resolução não intencionais que possam afetar as implementações personalizadas existentes.

### Comentários JSON não são mais compatíveis com Sling-Initial-Content (SP2) {#json-comments-no-longer-supported-in-sling-initial-content}

Esse problema afeta os desenvolvedores e administradores de pacotes OSGi que implantam pacotes que usam `Sling-Initial-Content` com arquivos JSON.

A partir do AEM 6.5 LTS SP2, os arquivos JSON usados em pacotes `Sling-Initial-Content` não aceitam mais comentários (`//` ou `/* */`). As versões anteriores do AEM aceitaram comentários porque o provedor `javax.json` foi tolerante com relação a isso. O AEM 6.5 LTS SP2 atualizou o `org.apache.sling.jcr.contentloader` para a versão 2.6.0, que alterou o analisador JSON para `jakarta.json`. Embora a [especificação JSON (RFC 8259)](https://datatracker.ietf.org/doc/html/rfc8259) não defina a sintaxe para comentários, versões anteriores do AEM as aceitaram devido à clemência do provedor `javax.json`. O provedor `jakarta.json` não oferece essa extensão.

A falha é silenciosa: os nós de conteúdo não são carregados na ativação do pacote sem erros exibidos no instalador. Se o conteúdo estiver ausente inesperadamente após a atualização para o SP2, verifique se há erros de análise JSON nos registros do instalador OSGi. Para identificar os pacotes afetados, pesquise por `//` ou `/* */` dentro dos arquivos JSON listados em `Sling-Initial-Content` cabeçalhos de manifesto.

>[!CAUTION]
>
> Remova todos os comentários dos arquivos JSON em seus pacotes `Sling-Initial-Content` para evitar falhas de carregamento de conteúdo após a atualização para o AEM 6.5 LTS SP2.

### Instale os índices Oak necessários para as APIs do Sites Headless{#site-headless-api}

Algumas APIs que foram movidas para o Sites Headless exigem índices Oak adicionais para funcionalidade completa.

Instale o pacote `cq-dam-cfm-indices` para usar os seguintes recursos:

* Lista de modelos de fragmentos de conteúdo
* Lista de fragmentos de conteúdo
* API de pesquisa
* Fluxos de trabalhos

Baixe o pacote de índice [cq-dam-cfm-indices](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/cq-dam-cfm-indices-1.1.2.zip) do Portal de Distribuição de Software da Adobe.

### Falha de conexão do Dispatcher com o recurso somente SSL (corrigido no AEM 6.5 LTS SP1 e posterior){#ssl-only-feature}

>[!NOTE]
>
> Esse problema está presente apenas na versão GA do AEM 6.5 LTS.

Ao habilitar o recurso de somente SSL em implantações do AEM, há um problema conhecido que afeta a conectividade entre as instâncias do Dispatcher e do AEM. Após habilitar esse recurso, as verificações de integridade podem falhar, e a comunicação entre as instâncias do Dispatcher e do AEM pode ser interrompida. Este problema ocorre especificamente quando os clientes tentam se conectar a instâncias do AEM por meio do `https + IP` a partir do Dispatcher. Ele está relacionado a problemas de validação da indicação do nome do servidor (SNI, na sigla em inglês).

**Impacto**

* Falhas de verificação da integridade com códigos de resposta HTTP 400.
* Tráfego interrompido entre as instâncias do Dispatcher e do AEM.
* O conteúdo não pode ser distribuído corretamente por meio do Dispatcher.
* Falhas de conexão ao usar HTTPS com endereços IP na configuração do Dispatcher.
* Erros HTTP 400 “SNI inválida” ao conectar-se via HTTPS + IP.

**Ambientes afetados**

* Implantações do AEM com configurações do Dispatcher.
* Sistemas em que o recurso de somente SSL foi habilitado.
* Configurações do Dispatcher, usando-se o método de conexão `https + IP` com instâncias do AEM.

**Solução**

Se você se deparar com esse problema, entre em contato com o suporte ao cliente da Adobe. Uma hotfix [cq-6.5.lts.0-hotfix-CQ-4359803](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-CQ-4359803-1.0.2.zip) está disponível para resolver esse problema. Não tente habilitar recursos de somente SSL até aplicar a hotfix necessária.

## Pacotes da OSGi e pacotes de conteúdo inclusos{#osgi-bundles-and-content-packages-included}

Os documentos de texto a seguir listam os pacotes OSGi e os pacotes de conteúdo incluídos nesta versão [!DNL Experience Manager] 6.5 LTS, Pacote de serviços 2: <!-- UPDATE FOR EACH NEW RELEASE -->

* [Lista de pacotes OSGi incluídos no Experience Manager 6.5 LTS, Pacote de serviços 2](/help/release-notes/assets/65lts_sp2_bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [Lista de pacotes de conteúdo incluídos no Experience Manager 6.5 LTS, Pacote de serviços 2](/help/release-notes/assets/65lts_sp2_packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Sites restritos{#restricted-sites}

Estes sites só estão disponíveis para clientes. Se você for cliente e precisar de acesso, entre em contato com o seu gerente de conta da Adobe.

* [Download do produto em licensing.adobe.com](https://licensing.adobe.com/)
* [Fale com o suporte ao cliente da Adobe](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-customer-support-experience).

