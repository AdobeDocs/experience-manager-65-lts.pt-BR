---
title: Notas de versão atuais do Adobe Experience Manager 6.5 LTS, SP1
description: Encontre informações sobre a versão atual do Adobe Experience Manager 6.5 LTS, Pacote de serviços 1.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: b5a8f555-c061-4fe2-a100-cc01335959cb
source-git-commit: 50f63016e5769939309d5013309043ad476e8b71
workflow-type: tm+mt
source-wordcount: '7219'
ht-degree: 14%

---

# Notas de versão atuais do Adobe Experience Manager 6.5 LTS, SP1 {#release-notes}

## Informações da versão {#release-information}

| Produto | [!DNL Adobe Experience Manager] 6.5 LTS |
|---|---|
| Versão | Service Pack 1 (SP1) <!-- UPDATE FOR EACH NEW RELEASE --> |
| Tipo | Versão do Service Pack |
| Data | 28 de agosto de 2025 <!-- UPDATE FOR EACH NEW RELEASE --> |
| URL de download | [Distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack-lts/cq-quickstart-6.6.1.jar) |

<!-- UPDATE ABOVE FOR EACH NEW RELEASE -->

## O que está incluído no [!DNL Adobe Experience Manager] 6.5 LTS, SP1 {#what-is-new}

<!-- UPDATE EACH RELEASE -->

O [!DNL Experience Manager] 6.5 LTS, SP1 inclui novos recursos, importantes melhorias solicitadas por clientes e correções de erros. Também inclui melhorias de desempenho, estabilidade e segurança lançadas desde a disponibilidade inicial do 6.5 LTS em março de 2025. [Instalar este Service Pack](#install-update) no 6.5 LTS.

<!-- ## Key features and enhancements -->

<!-- 6.5 LTS REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS THAT YOU WANT TO HIGHLIGHT IN THIS RELEASE? -->

<!-- UPDATE EACH RELEASE -->

## Correção de problemas no 6.5 LTS, Service Pack 1 {#fixed-issues}

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

### [!DNL Sites]{#sites-65-LTS-SP1}

#### Acessibilidade {#sites-accessibility-65-lts-sp1}

* Correção de um problema em que o elemento do editor de texto em Fragmentos de conteúdo era truncado por padrão. O editor de texto agora exibe o conteúdo completo sem truncamento. (SITES-33005)
* Correção de um problema em que clicar em caminhos de URL abria a página inicial do Indigo em vez do URL de destino correto. (SITES-33004)
* Correção de um problema de acessibilidade em um componente personalizado do AEM que causava falhas de conformidade com ADA durante testes automatizados. (SITES-30660)
* Correção de problemas de conformidade com a ADA na caixa de diálogo Alerta e nas Mensagens do fluxo de trabalho, garantindo a exibição do texto em preto sobre fundos claros e o cumprimento dos requisitos de contraste da WCAG 2.0. (SITES-30138)
* Correção de um problema de acessibilidade em que o botão &quot;Categoria&quot; no editor do AEM Sites não tinha um rótulo específico, fazendo com que o JAWS anunciasse como &quot;Menu do botão Imagens&quot; em vez de fornecer um rótulo descritivo. (SITES-27497)
* Correção de um problema de acessibilidade em que os ícones de marca de seleção na tela Permissões efetivas não tinham texto alternativo, impedindo que o JAWS lesse e transmitisse seu significado. (SITES-27272)
* Correção de um problema de acessibilidade em que a página Permissões não fornecia um anúncio JAWS claro para a remoção de permissões de usuário ou grupo, causando confusão para os usuários de leitores de tela. (SITES-27238)
* Correção de um problema de acessibilidade em que as mensagens de erro eram exibidas somente como ícones sem texto descritivo, impedindo que o JAWS anunciasse os erros quando eles ocorriam. (SITES-27155)
* Correção de um problema de acessibilidade em que o JAWS lia descrições de botões incorretas e imperceptíveis no ambiente do AEM no local, incluindo a ausência do texto de nível 2 do cabeçalho para a seção de módulos. (SITES-27152)
* Correção de um problema de acessibilidade em que o JAWS não anunciava o número de resultados após filtrar os valores na guia AEM Assets. (SITES-27150)
* Correção de um problema de acessibilidade em que a criação de uma pasta não exibia uma confirmação e o JAWS não a anunciava na interface do usuário do Assets. (SITES-27141)
* Correção de um problema de acessibilidade no AEM Sites. O JAWS não anunciou erros de formulário, o foco foi movido para elementos de erro não interativos e os erros de campo obrigatório não foram exibidos ao sair da guia. (SITES-27138)
* Correção de um problema de acessibilidade em que o menu do botão Linhas do tempo não tinha um rótulo específico, fazendo com que o JAWS lesse somente o &quot;menu do botão Atividades&quot; sem fornecer uma descrição clara. (SITES-27134)
* Correção de um problema de acessibilidade em que o JAWS não anunciava a ação ou a função para itens de contêiner, lendo somente &quot;Navegação estrutural v1&quot; e &quot;botão v2&quot; em vez de rótulos descritivos. (SITES-27131)
* Correção de um problema de acessibilidade em que a janela pop-up de publicação rápida não fornecia uma mensagem de sucesso apropriada, impedindo que os leitores de tela anunciassem comentários de conclusão. (SITES-26912)
* Correção de um problema de acessibilidade na exibição da coluna de coral, em que os elementos com funções ARIA que exigiam funções secundárias não os continham, causando a não conformidade com os padrões de acessibilidade. (SITES-26898)
* Correção de um problema de acessibilidade em que os textos do &quot;modelo&quot; e &quot;propriedades&quot; na navegação superior da página de criação não ficavam visíveis no modo de Refluxo, impedindo o acesso de usuários de teclado e leitores de tela. (SITES-26895)
* Correção de um problema de acessibilidade em que as dicas de ferramentas dos ícones &quot;pesquisa&quot;, &quot;solução&quot;, &quot;ajuda&quot;, &quot;caixa de entrada&quot; e &quot;usuário&quot; na navegação superior não eram acessíveis por meio da navegação pelo teclado. (SITES-26889)
* Correção de um problema de acessibilidade em que os campos de formulário da guia Básico não forneciam sugestões de erro, impedindo que os usuários recebessem orientação quando os campos de entrada necessários ficassem vazios. (SITES-26885)
* Correção de um problema de acessibilidade em que os leitores de tela do NVDA e do Narrador não anunciavam detalhes do arquivo de modelo na página Criar, impedindo que os usuários recebessem informações completas de forma programática. (SITES-26884)
* Correção de um problema de acessibilidade que usava um nome incorreto para a &quot;Caixa de texto do título da página&quot; na guia Básico, impedindo que os leitores de tela fornecessem informações precisas aos usuários. (SITES-26879)
* Atualização das cores do primeiro plano e do plano de fundo do botão para atender aos requisitos mínimos de taxa de contraste da WCAG 2.2 AA, melhorando a legibilidade e a acessibilidade para todos os usuários. (SITES-26877)
* Solução de um problema que fazia com que os textos do &quot;modelo&quot; e &quot;propriedades&quot; na navegação superior da página de criação desaparecessem após o redimensionamento, garantindo visibilidade e acessibilidade para usuários com pouca visão. (SITES-26872)
* Correção de um problema que fazia com que várias barras de rolagem horizontais fossem exibidas na página principal após a aplicação de um Refluxo, garantindo que uma única barra de rolagem fosse exibida para a acessibilidade e a visibilidade do conteúdo apropriadas. (SITES-26800)
* Correção de um problema de acessibilidade no Editor de páginas do AEM, em que o foco do teclado era redefinido inesperadamente para o início da Barra de ferramentas demográfica após a ativação de botões como Persona, Carrinho ou Abandonado. O foco agora permanece no botão ativado para oferecer suporte à navegação consistente do teclado e aos fluxos de trabalho do leitor de tela. (SITES-25306)
* Correção de um problema de associação de rótulo de acessibilidade para os campos de título de página e tags. Agora, a interface do AEM associa corretamente os rótulos de acessibilidade aos campos &quot;Título&quot; e &quot;Título da página&quot; ao usar leitores de tela como JAWS. A correção garante a leitura adequada do rótulo e melhora a conformidade com a ADA na criação de páginas, propriedades e fluxos de trabalho de movimentação. (SITES-27149)
* Corrigido o rótulo visual ausente para campos de entrada de comentários na linha do tempo. Correção da falta de rótulos visuais para os campos de entrada &quot;comentário&quot; na seção de linha do tempo para melhorar a acessibilidade. A atualização garante que os leitores de tela possam anunciar com precisão os rótulos de campo. Essa experiência melhora a navegação e o envio de formulários para todos os usuários, especialmente aqueles que dependem de tecnologias assistivas. (SITES-26903)
* Correção da acessibilidade do teclado para o botão de reticências nos comentários da linha do tempo. Ativação da navegação pelo teclado para o botão de reticências (três pontos) ao lado dos comentários na seção Linha do tempo. Agora os usuários podem acessar e interagir com o botão usando a tecla de guia, melhorando a acessibilidade para usuários que dependem da navegação somente pelo teclado. (SITES-26891)
* Anúncios de NVDA/Narrador aprimorados para resultados de pesquisa em caixas de diálogo de seleção. Atualização da caixa de diálogo Abrir seleção para anunciar se os resultados da pesquisa são encontrados ou não ao usar leitores de tela, como NVDA ou Narrador. Essa melhoria ajuda os usuários que dependem de tecnologias assistivas a entender o resultado de suas ações de pesquisa sem precisar de confirmação visual. (SITES-26883)
* Função ARIA corrigida para o ícone de reticências ao lado do campo de entrada de comentário. Atualização do ícone de reticências (três pontos) ao lado do campo de entrada de comentário para usar a função ARIA correta, garantindo que os leitores de tela possam identificar com precisão o elemento. Essa melhoria melhora a conformidade de acessibilidade e melhora a experiência para usuários que dependem de tecnologias assistivas. (SITES-26881)
* Correção de atributos ARIA inválidos em componentes da interface do usuário Coral. Atualização dos componentes da interface do Coral para garantir que todos os atributos ARIA usem valores válidos, melhorando a conformidade com a acessibilidade. Especificamente, foram solucionados casos em que valores inválidos como `aria-modal="dialog"` eram atribuídos incorretamente. Esse aprimoramento permite que os leitores de tela interpretem os elementos da caixa de diálogo corretamente, melhorando a acessibilidade para usuários que dependem de tecnologias assistivas. (SITES-26873)
* Visibilidade e dicas de ferramentas aprimoradas para ícones em cenários de Refluxo. O comportamento Reflow foi aprimorado para garantir que as dicas de ferramentas sejam exibidas corretamente para os ícones **Download**, **Reprocessar ativos** e **Check-out**. Foco em um problema de acessibilidade em que os ícones e seus rótulos se tornaram invisíveis quando a janela de visualização foi redimensionada ou as configurações de zoom do navegador foram alteradas. Essa correção oferece suporte a usuários com pouca visão, mantendo a visibilidade e fornecendo descrições apropriadas dos ícones durante o Refluxo. (SITES-26871)


#### Interface do usuário do administrador{#sites-adminui-65-lts-sp1}

* Correção de um problema de acessibilidade em que o JAWS não anunciava funções de lista ou fornecia instruções de navegação e ativação na caixa de diálogo Criar site. (SITES-30661)
* O suporte ao leitor de tela para mensagens de status na exibição de filtro Sites funciona conforme esperado, garantindo que os usuários recebam feedback claro e oportuno ao alternar entre as exibições. (SITES-24992)
* O Seletor de datas no painel Filtros é exibido totalmente em seu contêiner, fornecendo um tamanho de destino de toque adequado e eliminando problemas de recorte. (SITES-24988)
* As tags de filtro selecionadas agora usam HTML semântico e rótulos ARIA que correspondem à apresentação visual, garantindo um suporte de função preciso e ações claras para tecnologias de assistência. (SITES-24980)
* Foi adicionado um atributo de rótulo ARIA à região do Painel de referências para fornecer um rótulo descritivo exclusivo para usuários de leitores de tela e garantir uma identificação consistente do ponto de referência na página. (SITES-24973)
* Atualização do Painel de referências para usar unidades relativas para dimensionamento e posicionamento, permitindo que o conteúdo seja dimensionado e permaneça totalmente funcional quando reduzido para 400% em uma janela de visualização de 1280x1024. (SITES-24972)
* Os elementos de tabela confirmados na Exibição da lista da página inicial do Sites contêm funções apropriadas de cabeçalho de coluna, permitindo que os leitores de tela anunciem cabeçalhos para cada célula de dados. (SITES-24942)
* O NVDA agora anuncia a data de modificação no Diretório de árvore, garantindo que os usuários de leitores de tela recebam informações completas sobre detalhes do ativo. (SITES-24782)
* Correção de um problema em que o leitor de tela NVDA anunciava texto incompleto para itens no componente Diretório de árvore no AEM Sites. O NVDA agora lê o texto completo para cada item, melhorando a acessibilidade e a conformidade. (SITES-24780)
* Acessibilidade do teclado adicionada ao Divisor de janelas no Diretório de árvore, permitindo que os usuários redimensionem a barra lateral esquerda usando apenas um teclado. (SITES-24779)
* Os resultados de pesquisa do menu Ajuda foram atualizados para incluir as funções ARIA corretas para os itens da lista, garantindo que os leitores de tela anunciem os links corretamente para melhorar a acessibilidade. (SITES-24729)
* Correção de um problema em que os leitores de tela não anunciavam a mensagem de status &quot;X de Y resultados&quot;. Ou a mensagem &quot;nenhum resultado encontrado&quot; após a aplicação dos filtros no painel Filtro de sites, garantindo que os usuários recebam a confirmação adequada dos resultados. (SITES-24720)
* Correção de atribuições de funções ausentes para links de navegação na navegação do aplicativo. Adição das funções ARIA apropriadas para garantir que os leitores de tela identifiquem e anunciem corretamente os elementos de navegação. (SITES-24719)
* A marcação de função de grade incorreta das tags de filtro selecionadas foi substituída por elementos de botão e nomes acessíveis adicionados, garantindo que os leitores de tela anunciassem e identificassem as tags corretamente. (SITES-24717)
* Adição de anúncios do leitor de tela para a mensagem de status do Painel de referências ao executar várias seleções, garantindo que os usuários recebam a confirmação das alterações. (SITES-24678)
* O comportamento do campo de pesquisa foi corrigido para que o primeiro resultado não fosse anunciado automaticamente. Os leitores de tela agora anunciam o número de resultados encontrados, permitindo que os usuários naveguem na lista sem anúncios de foco incorretos. (SITES-24658)
* Atributos `aria-label` incorretos removidos de elementos estáticos não interativos na Exibição de Lista para impedir que os leitores de tela anunciem informações enganosas ou irrelevantes. (SITES-24515)
* Atualização da caixa de seleção na primeira coluna da Exibição de lista para usar o texto da coluna Título para seu nome acessível, garantindo que os leitores de tela transmitam com precisão a finalidade do campo de formulário. (SITES-24514)
* Adição de atributos ARIA adequados e suporte à região dinâmica para anunciar as mensagens de status de carregamento aos usuários de leitores de tela ao navegar pelo conteúdo. (SITES-24481)
* Design responsivo atualizado para eliminar a rolagem horizontal quando o conteúdo é ampliado para 400% com uma largura de visor de 1280×1024, garantindo visibilidade total sem rolagem lateral. (SITES-24308)
* A navegação de foco na interface do administrador do Sites foi corrigida para seguir uma ordem lógica, retornando o foco para o botão &quot;Selecionar tudo&quot; após pressionar Esc e mover o foco para o próximo elemento interativo após pressionar Tab. (SITES-24307)
* A ordem de foco na interface do Administrador de Sites foi atualizada para que o botão de navegação estrutural no elemento `<betty-titlebar-title>` receba foco na sequência correta durante a navegação pelo teclado. (SITES-24305)
* Verificada a funcionalidade de pular link para garantir que ela mova o foco do teclado para a área de conteúdo principal, permitindo que os usuários de teclado ignorem elementos de cabeçalho e acessem o conteúdo com eficiência. (SITES-24061)


#### Interface do usuário clássica{#sites-classicui-65-lts-sp1}

Correção de um problema na interface clássica em que os rótulos da caixa de seleção estavam ausentes e o HTML era exibido como texto codificado em vários elementos da interface, incluindo Pesquisa de data e interfaces não padrão. (SITES-31822)

#### [!DNL Content Fragments]{#sites-contentfragments-65-lts-sp1}

O AEM agora impede a degradação do desempenho causada por metadados malformados do XMP em ativos de imagem. O Assets que contém nomes de propriedade XMP inválidos ou não compatíveis, como aqueles com segmentos numéricos ou estruturas não qualificadas, não aciona mais logs de aviso repetidos durante o processamento. O sistema filtra metadados problemáticos para garantir que a assimilação e a validação de ativos estejam completas sem erros. (SITES-30683)

<!--
#### [!DNL Content Fragments] - Admin{#sites-admin-65-lts-sp1} -->

#### [!DNL Content Fragments] - Editor de fragmentos{#sites-fragments-editor-65-lts-sp1}

Outros autores ainda podem publicar fragmentos de conteúdo mesmo quando outro autor faz o check-out, o que é contrário ao comportamento pretendido do recurso de check-out. Essa correção impede que outros usuários vejam ou usem os botões de publicação na interface de criação quando é feito o check-out de um fragmento de conteúdo. (SITES-30578)

<!--
#### [!DNL Content Fragments] - GraphQL API {#sites-graphql-api-65-lts-sp1}

#### [!DNL Content Fragments] - GraphQL Query Editor{#sites-graphql-query-editor-65-lts-sp1}

#### [!DNL Content Fragments] - REST API{#sites-restapi-65-lts-sp1} -->

#### Console de componentes{#sites-component-console-65-lts-sp1}

Correção de um problema no componente Lista de produtos em que a caixa de seleção &quot;Selecionar tudo&quot; adicionava somente os primeiros 20 SKUs da página inicial em vez de todos os SKUs nos resultados da pesquisa. (SITES-29191)

#### Infraestrutura principal{#sites-core-backend-65-lts-sp1}

Metadados XMP formatados incorretamente dispararam um erro durante o processamento de ativos de imagem no `ValidationDataServlet`. A correção garante a conformidade do manuseio de metadados e evita a análise redundante de propriedades inválidas. (SITE-30683)

<!--
#### Core Components{#sites-core-components-65-lts-sp1}

#### Campaign integration{#sites-campaign-integration-65-lts-sp1}

#### Experience Fragments{#sites-experiencefragments-65-lts-sp1}

#### Foundation Components (Legacy){#sites-foundation-components-legacy-65-lts-sp1}

#### Launches{#sites-launches-65-lts-sp1}

#### Link Checker{#sites-link-checker-65-lts-sp1} -->

#### MSM - Live Copies{#sites-msm-live-copies-65-lts-sp1}

* Correção de um erro de JavaScript `ns.ui.alert is not a function` que ocorria ao reativar a herança de componentes fantasmas no AEM 6.5 no local. (SITES-31993)
* Correção de um problema em que a opção Implantação &quot;Mais tarde&quot; permitia continuar sem selecionar uma data no AEM 6.5. (SITES-31374)

#### Editor de páginas{#sites-pageeditor-65-lts-sp1}

* Solução de um problema no modal do Teaser em que a guia Link e ações continuava exibindo o estilo do erro, ícones e o atributo aria-invalid após a entrada de dados e a resolução do erro válidas. (SITES-25527)
* Correção de um problema no editor de texto Teaser Modal, em que os botões Listas e Parágrafos não transmitiam seu estado expandido ou recolhido para os leitores de tela, garantindo atualizações de atributos precisas e expandidas. (SITES-25365)
* Correção de um problema na barra de ferramentas Demografia em que o ajuste do controle deslizante do carrinho com a entrada do teclado movia o foco para o botão Carrinho em vez de manter o foco no controle deslizante, melhorando a eficiência da navegação para usuários de teclado. (SITES-25324)
* Adição de um nome acessível ao controle deslizante do carrinho na barra de ferramentas demográficas, atribuindo um valor ao elemento `<label>` associado. Essa correção melhorou a compatibilidade com tecnologias assistivas e melhorou a usabilidade para usuários de leitores de tela. (SITES-25322)
* Adição de funções ARIA e nomes acessíveis aos botões dentro do menu suspenso da Barra de ferramentas demográficas. Essa correção permitiu a identificação adequada por tecnologias assistivas e a navegação aprimorada para usuários de teclado e leitor de tela. (SITES-25315)
* Ajustado o layout da barra de ferramentas demográfica para evitar estouro de conteúdo além do visor a 200% de zoom do navegador, garantindo que todos os controles permaneçam acessíveis sem rolagem horizontal. (SITES-25309)
* Correção do gerenciamento de foco na Barra de ferramentas demográfica para manter o foco do teclado no botão ativado, em vez de redefinir o foco para a posição inicial da barra de ferramentas. (SITES-25306)
* A sobreposição do rótulo do botão funciona conforme projetado, usando uma dica de ferramenta para exibir o rótulo quando os modos com larguras de tela semelhantes estiverem ativos. (SITES-25285)
* A modal de anotação inclui um botão de envio visível, que permite aos usuários enviar anotações sem depender da tecla Escape ou clicar fora da modal. (SITES-25281)
* A modal de anotação inclui um botão de ícone de caneta que permite aos usuários enviar anotações, fornecendo um método de envio claro e acessível. (SITES-25269)
* Anúncios de leitores de tela corrigidos para os botões Anotar e Fechar anotação para fornecer feedback preciso e relevante e remover informações não relacionadas ou confusas. (SITES-25268)
* As seções de tela de desenho nas páginas do Editor do AEM agora oferecem suporte à acessibilidade total do teclado. Os usuários podem ativar títulos de seção e editar botões usando apenas o teclado, sem depender do mouse. Essa atualização garante a conformidade com a WCAG 2.1.1 e melhora a usabilidade entre componentes (como Teaser, Imagem, Carrossel, Layout, Timewarp e Modais de anotação). (SITES-25256)
* Remoção da rolagem horizontal desnecessária no modal Carrossel com largura de 320 px para garantir que todo o conteúdo seja exibido dentro do visor sem a necessidade de navegação lado a lado. (SITES-25254)
* Remoção da rolagem horizontal desnecessária no Modal de imagem com largura de 320 px para garantir que todo o conteúdo seja exibido dentro do visor sem a necessidade de navegação lado a lado. (SITES-25244)
* Remoção da rolagem horizontal desnecessária no modal de teaser com largura de 320 px para garantir que todo o conteúdo seja exibido dentro do visor sem a necessidade de navegação lado a lado. (SITES-25242)
* Navegação do teclado habilitada para o menu pop-up `List` e `Paragraph Format`, ambos no Modal de Teaser. Essa correção permite que os usuários acessem e naveguem esses menus usando teclas de seta. (SITES-25235)
* Anúncios de leitores de tela corrigidos para os botões Anotar e Fechar anotação para fornecer feedback preciso e relevante alinhado com as ações associadas. (SITES-25234)
* O rótulo do botão Ajuda foi aprimorado no modal Teaser para descrever sua finalidade claramente e fornecer um contexto significativo para todos os usuários, incluindo usuários de tecnologia assistiva. (SITES-25224)
* Melhoria da régua do emulador para usuários de leitores de tela, associando medidas de régua aos respectivos dispositivos. Além disso, substitua a dica de ferramenta por um elemento aria-descripbedby. (SITES-24955)
* Nenhuma correção foi implementada porque o botão Editar funciona conforme o esperado e fornece um contexto informativo em vez de executar uma ação. (SITES-24950)
* A ordem de foco confirmada na página do Editor segue uma sequência lógica, permitindo que os usuários naveguem por todos os elementos interativos sem pular ou retornar inesperadamente. (SITES-24937)
* A tela do modo Visualização confirmada atualiza o espaçamento do texto corretamente quando os usuários aplicam configurações personalizadas de espaçamento de texto, garantindo uma formatação consistente em todas as áreas de conteúdo. (SITES-24936)
* O botão Visualização verificado não aciona mais alterações de contexto ou estado em foco, garantindo que os usuários ativem o botão intencionalmente antes das atualizações de exibição de página. (SITES-24784)
* Adição das atribuições de função ARIA corretas aos links de navegação do aplicativo, permitindo que os leitores de tela identifiquem com precisão e anunciem itens de navegação para melhorar a acessibilidade. (SITES-24718)
* O botão Alterar filtros foi atualizado para anunciar estados expandidos e recolhidos aos leitores de tela, atributos ARIA redundantes removidos e rotulagem ajustada para fornecer descrições claras e não duplicadas. (SITES-24713)
* Adição de anúncios do leitor de tela para mensagens de status dos resultados da pesquisa na caixa de diálogo Seleção de link, garantindo que os usuários recebam a confirmação quando os resultados forem carregados ou nenhuma correspondência for encontrada. (SITES-24700)
* Adição de anúncios do leitor de tela para o estado de carregamento do modal de imagem, garantindo que os usuários recebam feedback quando o modal estiver carregando e pronto para interação. (SITES-24697)
* Solução de um problema de acessibilidade em que o cabeçalho adesivo obscurecia o conteúdo modal do Teaser em 200% e 400% de zoom, garantindo visibilidade e usabilidade totais ao usar a ampliação de página. (SITES-24523)
* Adição de uma mensagem de status com o número de resultados de pesquisa ao campo Pesquisa/Filtro, permitindo que os leitores de tela anunciem os resultados aos usuários. (SITES-24506)
* Adição de anúncios do leitor de tela para o número de resultados da pesquisa no campo Pesquisa/Filtro, garantindo que os usuários recebam feedback imediato quando os resultados forem carregados. (SITES-24505)
* Adição de um nome acessível à lista de guias no painel Painel lateral, permitindo que os leitores de tela anunciem sua finalidade em conformidade com as diretrizes WAI-ARIA. (SITES-24492)
* Foram adicionados rótulos descritivos aos ícones ambíguos do editor, garantindo que todos os usuários entendam claramente a função de cada botão. (SITES-24480)
* Ativação da acessibilidade total do teclado para títulos de seção e botões de ação na visualização Tela de desenho, garantindo uma operação consistente para usuários de mouse e teclado. (SITES-24479)

<!--
#### Replication{#sites-replication-65-lts-sp1}

#### Rich Text Editor{#sites-rte-65-lts-sp1} -->

#### Editor universal {#sites-universal-editor-65-lts-sp1}

* Correção de uma condição de corrida no QueryTokenService que causava logons incorretos quando várias solicitações com parâmetros de consulta eram acionadas antes do serviço de token de logon retornar um resultado. (SITES-30659)
* Correção de um problema em UniversalEditorURLService em que salvar uma matriz de caminhos mapeados no Felix ConfigMgr mantinha somente o primeiro item. (SITES-30292)

### [!DNL Assets]{#assets-65-lts-sp1}

Correção de um problema em que a sincronização de ativos do DAM remoto para o Sites local AEM removia o status publicado e as propriedades relacionadas à replicação dos ativos. (Assets-48958)

<!--
#### [!DNL Dynamic Media]{#assets-dm-65-lts-sp1}

#### [!DNL Dynamic Media] - Hybrid Mode {#assets-dm-hybrid-65-lts-sp1}



### [!DNL Forms]{#forms-65-lts-sp1}


#### Forms Designer 

#### Forms

#### Forms JEE 
 
#### Forms Captcha {#forms-captcha-65-lts-sp1} 

#### XMLFM {#forms-xmlfm-65-lts-sp1}

#### [!DNL Adaptive Forms] {#adaptive-forms-65-lts-sp1}

#### [!DNL Forms Designer] {#forms-designer-65-lts-sp1} -->



### Foundation {#foundation-65-lts-sp1}

<!--
#### Apache Felix {#foundation-apachefelix-65-lts-sp1}

#### Campaign{#foundation-campaign-65-lts-sp1}

#### Cloud Services{#foundation-cloudservices-65-lts-sp1}



#### Communities {#foundation-communities-65-lts-sp1}

#### Content distribution{#foundation-content-distribution-65-lts-sp1}

#### CRX {#foundation-crx-65-lts-sp1}

#### Granite{#foundation-granite-65-lts-sp1} -->

#### HTL{#foundatoin-htl-5-lts-sp1}

Correção de ciclos de dependência OSGi que impediam o funcionamento da fábrica do mecanismo de script HTL, garantindo a resolução de serviço e a execução de script apropriadas. (Granite-58275)

#### Integrações{#foundation-integrations-65-lts-sp1}

* Remoção do uso do commons-httpclient 3.x do pacote `com.adobe.cq.cq-analytics-integration` e sua substituição por `org.apache.httpcomponents.httpclient` 4.5.13.B0001 para alinhar-se aos padrões AEM 6.5 LTS mais recentes. (CQ-4360586)
* Remoção do pacote de integração obsoleto Search&amp;Promote do AEM para eliminar componentes não utilizados e reduzir a sobrecarga de manutenção. (CQ-4358030)
* Adição de novos casos de teste de back-end para a integração do SiteCatalyst a fim de melhorar a validação de análises e garantir uma cobertura mais abrangente. (CQ-4359991)
* Corrigido um problema na seção Propriedades da configuração do Launch, onde os menus suspensos Empresa e Propriedade não eram exibidos. Além disso, Salvar e fechar acionavam erros, apesar de todos os campos obrigatórios estarem preenchidos, e mensagens de erro incorretas eram exibidas para Empresa e Propriedade quando apenas o campo Título estava vazio. (CQ-4359853)
* Removida a entrada do caminho de servlet `searchpromote` da versão 6.6 para alinhar-se à remoção do conjunto Search&amp;Promote. (CQ-4359523)
* Correção de casos de teste HTTP para o repositório do Target, a fim de garantir uma validação precisa e maior confiabilidade de teste. (CQ-4359022)
* Remoção do uso de cache Guava do módulo integration-adobeims-console para eliminar as dependências da biblioteca Guava. (CQ-4358710)
* Fluxos de trabalho de integração do DTM, tarefas da caixa de entrada e funcionalidade do projeto validados no AEM 6.6 para garantir a operação adequada no AEM 6.5. (CQ-4358151)
* Funcionalidade Insight de conteúdo validado no AEM 6.6 para garantir a compatibilidade e a operação adequada no AEM 6.5. (CQ-4357774)
* A funcionalidade Serviços em nuvem foi validada no AEM 6.6 para garantir a compatibilidade e a operação adequada no AEM 6.5. (CQ-4357773)
* Validação da integração do console do Adobe IMS no AEM 6.6 para garantir a compatibilidade e a operação adequada no AEM 6.5. (CQ-4357772)
* Atualização do pipeline do Jenkins para que a integração do Test&amp;Target seja executada no Java 17, resolva testes Selenium com falha, mova os testes selecionados para o Playwright e verifique se todos os testes de unidade foram bem-sucedidos. (CQ-4357770)
* Integrações DX, fluxo de trabalho, caixa de entrada e projetos alinhados com a ramificação 6.6.0 atualizando pipelines de compilação e teste. Além disso, resolver problemas de compatibilidade de atualização e validar todos os serviços afetados para estabilidade e funcionalidade. (CQ-4357767)

<!--
#### Jetty{#foundation-jetty-65-lts-sp1} -->

#### Localização{#foundation-localization-65-lts-sp1}

* As cadeias de caracteres localizadas na caixa de diálogo &quot;Remover controle de acesso&quot; da lista &quot;Permissões&quot; para exibir as traduções corretas. (GRANITE-59427)
* Correção de um problema na caixa de diálogo Adicionar regra &quot;Ou Propriedades divididas&quot; do Editor de modelos, onde várias cadeias de caracteres da interface do usuário, incluindo operadores e rótulos de campo, apareciam deslocalizadas. Todas as cadeias de caracteres agora são exibidas com a localização correta. (CQ-4354014)
* Adição de tradução ausente para a dica de ferramenta &quot;Mostrar descrição de&quot; na caixa de diálogo Editar modelos de fluxo de trabalho. (CQ-4347996)

#### Oak {#foundation-oak-65-lts-sp1}

Solução de um problema em que o AEM recriava ou renomeava arquivos de configuração existentes em `/apps/system/config` durante atualizações, substituindo `.cfg.json` arquivos por `.config` arquivos. (GRANITE-58899)

#### Omnisearch{#foundation-omnisearch-65-lts-sp1}

Correção de um problema de acessibilidade em que os espaços reservados apareciam incorretamente como rótulos para campos de entrada. Esse problema faz com que rótulos de campo não apareçam em Pesquisa, Fragmentos de experiência do AEM, Fragmentos de conteúdo e Modelos de fragmento de conteúdo. (Granite-61791)

<!--
#### Platform{#foundation-platform-65-lts-sp1} -->

#### Projetos{#foundation-projects-65-lts-sp1}

* Solução de um problema que exibia um pop-up de erro incorreto ao excluir um projeto na exibição Calendário, apesar da exclusão bem-sucedida do projeto. (CQ-4358890)
* Correção de um problema no Firefox em que o rodapé de cartão &quot;Coleção de ativos&quot; na exibição Projeto se sobrepunha à borda do cartão. Agora o rodapé é é alinhado corretamente sem sobreposição. (CQ-4353317)

#### Quickstart{#foundation-quickstart-65-lts-sp1}

* Incluir na lista de bloqueios Atualização do script de desinstalação para ajustar o intervalo de versão do pacote Guava, impedindo que ele fosse atualizado quando instalado por meio do Gerenciador de pacotes. (GRANITE-59559)
* Correção de um problema na interface do usuário de Replicação que exibia um erro (`#1660`) ao editar agentes de replicação ao corrigir a manipulação de caixas de seleção clássicas na interface. (GRANITE-58302)
* Correção de vários erros de inicialização do armazenamento de dados S3 ao executar o AEM 6.5 LTS com JDK 21, solucionando permissões de serviço ausentes, atualizando o tratamento de configuração e garantindo que os serviços necessários fossem inicializados corretamente. (GRANITE-57082)
* Definição da estratégia de manutenção e manutenção do AEM 6.5. Essa correção incluiu o seguinte:
   * Cadência do Service Pack.
   * Cadência de hotfix.
   * Suporte paralelo com o AEM 6.6.
   * Atualização da matriz de suporte.
   * Responsabilidades de propriedade complementar. (GRANITE-50459)

<!--
#### Security{#foundation-security-65-lts-sp1} -->

#### Sling{#foundation-sling-65-lts-sp1}

* Atualização do Sling ResourceAccessSecurity para a versão 1.1.2 para resolver um `ClassCastException` que ocorria quando várias referências `ResourceAccessGate` inicializavam `ResourceAccessSecurityImpl`. (NPR-42750)
* Correção de um problema na integração do Adobe Stock em que a caixa de diálogo Licença aparecia esmaecida. Esse problema ocorreu devido à remoção de campos de entrada necessários pela função `sunt:initList`. A função foi encontrada nas bibliotecas de clientes da Coral Foundation. Atualização das bibliotecas de clientes para reter os campos necessários, permitindo a funcionalidade adequada da caixa de diálogo de licença. (NPR-42748)
* Correção com suporte para o problema de Sling Scripting que causou `DataTimeParseException` e `String.length()` exceções de ponteiro nulo durante a instalação do pacote. Atualização do Sling Scripting para a versão 2.8.3-1.0.10.6 para reduzir erros de instalação e melhorar a estabilidade. (NPR-42640)

<!--
#### Translation{#foundation-translation-65-lts-sp1} -->

#### Interface do usuário{#foundation-ui-65-lts-sp1}

* Solução de um problema na interface do autor do AEM que limitava a exibição de grupos de usuários a 41. Esse problema ocorria devido a um limite de lote padrão no componente seletor de grupo da interface do Granite. Atualização do componente para exibir todos os grupos sem truncamento. (NPR-42749)
* Solução de um problema no assistente de criação de página no local em que os campos obrigatórios em componentes de vários campos não eram revalidados ao editar as propriedades da página. Esse problema, por sua vez, permitia que os autores ignorassem a validação e continuassem com dados incompletos. (GRANITE-58826)
* Atributos ARIA corrigidos para o botão de ajuda no AEM para garantir que os leitores de tela JAWS anunciem um rótulo claro e amigável em vez de exibir metadados de ícone e texto não traduzidos. (GRANITE-55360)

#### WCM{#foundation-wcm-65-lts-sp1}

* Adição de suporte ao Java 17 para traduções do AEM, atualizando pacotes de tradução, verificando a compatibilidade do pacote Java, removendo dependências obsoletas e garantindo a funcionalidade completa por meio de testes abrangentes. (CQ-4357525)
* Removido o teste Evergreen imperceptível `com.adobe.cq.platform.it.http.workflow.inbox.InboxOnOffTimeIT.testActivateLater` para evitar falhas falsas durante o teste automático. (CQ-4298376)

#### Fluxo de trabalho{#foundation-workflow-65-lts-sp1}

* Adição do atributo `data-detailsurl` ausente nos itens da caixa de entrada para impedir que valores indefinidos sejam exibidos em URLs ao usar o AEM 6.5 LTS com Java 21. (GRANITE-60158)
* Correção de uma NullPointerException no método `deactivate` do pacote `WorkflowToPublishEventService` ao executar o AEM 6.5 LTS com Java 21, garantindo o desligamento adequado do serviço de fluxo de trabalho sem erros. (GRANITE-58151)
* Atualização do índice de fluxo de trabalho para oferecer suporte ao compartilhamento, personalização fora do escritório e resolução de problemas de consulta de linha do tempo. (GRANITE-52640)
* Atualização do índice de fluxo de trabalho para oferecer suporte ao compartilhamento, aos recursos de personalização de ausência temporária e à resolução de problemas de consulta de linha do tempo. (GRANITE-52294)
* Solução do aumento de falhas de log de erros durante a validação da comparação de logs para uma atualização do programa para o AEM versão 10912, garantindo uma execução estável do fluxo de trabalho. (GRANITE-44268)
* Atualização do método de limpeza de URL nos Repositórios de Fluxo de Trabalho para substituir `url.searchParams` por `url.search`, melhorando a proteção XSS para URLs vulneráveis. (CQ-4359585)
* Funcionalidade de fluxo de trabalho, caixa de entrada e projetos validados no AEM 6.6 Forms para garantir a operação e a integração adequadas. (CQ-4358777)
* Automação implementada para lançar artefatos de Conteúdo de Fluxo de Trabalho por meio do Jenkins, permitindo processos de implantação simplificados e consistentes no AEM 6.5. (CQ-4358472)
* Correção de um problema no fluxo de trabalho Criar tarefa da caixa de entrada, em que a caixa de diálogo &quot;Adicionar tarefa&quot; não era fechada após clicar em Enviar, apesar da tarefa estar sendo criada, devido a um erro de sintaxe do JavaScript. (CQ-4355336)
* Correção de um problema que impedia o salvamento da configuração de exibição da Caixa de Entrada devido a uma definição de propriedade ausente para `isEndUserConfigurationEnabled`. (CQ-4287757)

## Forms

### Designer do Forms

* Quando um usuário exporta os dados de uma PDF baseada em XFA usando a exportDataAPI, o XML resultante mostra discrepâncias quando comparado aos dados XML exportados manualmente usando o Acrobat Reader. Valores de alguns campos estavam ausentes na saída em comparação à saída gerada pelo Acrobat Reader. (LC-3922791)
* Gerar uma PDF marcada com o Serviço de saída no Workbench adiciona uma tag de rótulo inesperada na tag de referência em um item de índice. (LC-3922756)
* Ao nivelar PDFs dinâmicos e preenchíveis no formato PDF/A usando o Serviço de saída, o estado dinâmico não é preservado. Isso leva à perda de dados e a possíveis problemas de conformidade, especialmente quando a marcação está ativada. (LC-3922708)
* Quando um usuário coloca legendas de campo com alinhamento inferior ou direito no AEM Forms Designer, a árvore de tags inclui somente a legenda sem o valor correspondente, resultando em marcação de acessibilidade incompleta. (LC-3922619)
* Os códigos QR nos PDFs gerados tornam-se ilegíveis. O texto alternativo para os códigos QR também falha no teste de acessibilidade, afetando a compatibilidade do leitor de tela. (LC-3922551)
* Quando um usuário renderiza uma correspondência na interface do usuário do agente, o conteúdo não é exibido corretamente devido à API FormService render(). (LC-3922461)
* Quando um usuário tenta criar arquivos PDF/A a partir de XDPs com estilo Sunken Square no AEM Forms, isso resulta em problemas de renderização de borda. (LC-3922180)
* O nivelamento de formulários dinâmicos vinculados a um esquema XSD causa perda parcial de dados, pois alguns dados de formulário vinculados não são retidos no PDF final. (LC-3922008)
* Quando um usuário tenta exportar dados de PDFs interativos usando a API extractData no AEM Forms 6.5.13 e versões posteriores, isso resulta na ausência de dados em comparação à exportação manual. (LC-3921983)
* Os usuários enfrentam um problema de conformidade de acessibilidade em que várias tags Link-OBJR estão sendo criadas ao converter formulários XDP em PDFs estáticos usando o AEM Forms Designer ou o serviço de saída, em vez de criar uma única tag de link unificada. (LC-3921977)

### Formulários adaptáveis

* No AEM Forms, ativar a opção &quot;Permitir rich text para título&quot; no painel raiz faz com que a opção &quot;Excluir título do documento de registro&quot; em um painel aninhado oculte incorretamente o título do painel raiz. Isso é feito no documento de registro gerado. (FORMS-19696)
* O sistema ignora a sling personalizada :resourceType atribuída por meio do aem:afProperties em um esquema JSON. O tipo de recurso personalizado é ignorado durante a renderização. (FORMS-19691)
* Quando um usuário envia um Formulário adaptável com anexos pré-preenchidos usando URIs, o envio do formulário falha com uma NullPointerException devido à ausência de dados binários. (FORMS-19371) (FORMS-19486)
* Quando um usuário carrega uma PDF na seção &quot;Forms e documentos&quot;, o recurso de linha do tempo para de funcionar. (FORMS-19407)(FORMS-19234)
* Quando um usuário faz upload de arquivos usando o componente de anexo de arquivo pronto para uso (OOTB) no AEM Forms, as vulnerabilidades de segurança são identificadas. Este problema pode levar à intercepção potencial do processo de envio por entidades não autorizadas. (FORMS-19271)
* Quando um usuário configura um Formulário adaptável pronto para uso no AEM Forms para gerar um Documento de registro (DoR) automaticamente, o campo &quot;Título&quot; nas Propriedades de documento do Acrobat Reader não exibe o título do Documento capturado. Por padrão, o título do formulário não é exibido no lugar do nome do arquivo. (FORMS-19263)
* Quando um usuário abre uma Comunicação interativa na interface do usuário do agente, os dados preenchidos previamente não podem ser completamente apagados; após a remoção, eles são automaticamente preenchidos com os mesmos dados. (FORMS-19151)
* Quando um usuário pré-visualiza um campo de data na interface do usuário do agente, a data é alterada inesperadamente. Esse problema ocorre devido a discrepâncias de fuso horário entre a configuração UTC da VM e a interpretação da data pelo sistema. (FORMS-19115)
* Quando um usuário envia um formulário, os anexos de arquivo podem ser duplicados, resultando em vários uploads do mesmo arquivo. (FORMS-19045)(FORMS-19051)
* A adição de coordenadores a conjuntos de políticas na Segurança de documentos falha em ambientes de produção e inferiores. (FORMS FORMS-18603, FORMS-18212, 19697)
* Quando um usuário clica no &quot;datepicker-calendar-icon&quot; no modo de desktop com um campo vazio, ocorre um erro devido à variável _$focusDate indefinida, interrompendo os scripts personalizados associados. (FORMS-18483)(FORMS-18268)
* Quando um cliente pré-visualiza uma correspondência, o campo &quot;Valor em palavras&quot; não exibe ou atualiza os valores numéricos corretamente, resultando em alinhamento incorreto e espaços ausentes no conteúdo. (FORMS-18437, FORMS-17330, FORMS-18209, FORMS-18557, CTG-4150848,FORMS-19614, LC-3922004)
* Quando um cliente visualiza uma carta salva no RHEL, o conteúdo fica desalinhado, os espaços são ausentes e caracteres inesperados como &quot;x&quot; são exibidos. (FORMS-18422)(FORMS-17641)
* Quando um usuário navega entre guias no AEM Forms, selecionar componentes na primeira guia deixa de responder. (FORMS-18345)
* Quando um usuário converte um arquivo do HTML em PDF usando a opção WebToPDF, a seção de cabeçalho do PDF de saída não aparece, incluindo tags de metadados e título. (FORMS-18223, FORMS-17835, FORMS-19642, FORMS-18224)
* No SDK do AEM JEE Process Manager, quando um usuário chama o método retryAction(long actionOid), o sistema tenta novamente incorretamente a primeira ação encontrada na tabela tb_action_instance. Esse fluxo de trabalho ocorre mesmo quando uma ID de ação específica é fornecida ou quando a ID é nula, resultando em comportamento não intencional. (FORMS-18187)
* O usuário encontra problemas em que as funcionalidades de rascunho e envio salvas falham sem exibir uma mensagem de erro. (FORMS-18069)
* A transição de componentes básicos baseados em XSD para componentes principais impede a implementação de referências entre arquivos em esquemas JSON, afetando a migração adaptável do Forms. (FORMS-18065)
* Quando um usuário pré-visualiza uma correspondência na interface do usuário do agente, o campo de data mostra um valor incorreto devido a problemas de conversão de tempo da IC. Essas discrepâncias surgem das diferenças de fuso horário entre o ambiente da VM e a interpretação de hora do sistema (UTC versus hora local). (FORMS-17988) (FORMS-17248)
* Quando um usuário pré-visualiza cartas usando modelos de Aviso IC no AEM Forms, os tempos de geração do PDF variam significativamente, de 1,5 segundos a mais de 10 segundos, mesmo no mesmo servidor. Essa inconsistência afeta os workflows críticos para os negócios. (FORMS-17951)
* Quando um usuário vincula um objeto de assinatura escritas em um formulário adaptável a um XDP usando a opção &quot;Fontes de dados&quot;, as alterações não podem ser salvas. O motivo é devido a erros persistentes de validação na taxa de proporção, mesmo ao usar valores válidos. (FORMS-17587)
* Quando um usuário usa um XDP específico com muitos campos ocultos para fragmentos de documento, o AEM cria nós do CRX com a propriedade cm:optional definida como false, o que causa falha no envio da IC (Comunicação interativa). (FORMS-17538)
* Quando um cliente pré-visualiza uma correspondência, o campo da caixa numérica não lida corretamente com valores negativos quando os limites de dígito para lead e frac são definidos. Esse problema ocorre devido ao uso de parseFloat, que trata o sinal de menos como parte do número. (FORMS-17451)
* Quando uma correspondência é visualizada, o uso do curinga &quot;*&quot; no arquivo Adobe.json é notado, gerando preocupação sobre sua finalidade e possível modificação. (FORMS-17317)
* Quando um usuário usa um leitor de tela na conta conjunta Aplicar para um economizador de taxa fixa, os cabeçalhos são anunciados incorretamente como clicáveis, causando problemas de acessibilidade. (FORMS-17038)
* Quando um formulário é incorporado, o iframe gerado não tem um atributo de título, resultando em um problema de conformidade de acessibilidade. (FORMS-17010)
* Baixar um formulário usando a interface do usuário do Forms Manager sempre inclui dependências associadas, como temas e fragmentos. (FORMS-15811)
* Quando um usuário acessa o formulário em dispositivos móveis (iOS e Android™), os botões &quot;próximo&quot; e &quot;anterior&quot; na primeira página são desativados. No entanto, o leitor de tela não as identifica como desativadas. (FORMS-15773)
* Quando um usuário salva um formulário grande com fragmentos e carregamento lento ativado, ele não recupera rascunhos, interrompendo o fluxo de trabalho. (FORMS-19890, FORMS-19808)
* Os usuários tiveram problemas ao salvar propriedades de formulário adaptável com base nos Componentes principais. Isso ocorreu porque scripts redundantes do Formulário adaptável baseado no editor de Componentes de base são incluídos, causando conflitos no Formulário adaptável baseado em Componentes principais. editor. (FORMS-17474)
* Os usuários tiveram problemas com a página de assinatura do Adobe Sign GovCloud não sendo renderizada em um iframe. (FORMS-16803)
* Os usuários experimentam erros ao selecionar referências para fragmentos de Componente principal do Adaptive Forms (AF). A mensagem de erro &quot;Não é possível renderizar a referência: não é um caminho absoluto&quot; foi exibida, impedindo a renderização de referência adequada. (FORMS-19678)
* Foi adicionado suporte para conversão de vários segmentos com o Acrobat DC, permitindo que os usuários executem conversões simultâneas de documentos do Word, Excel e PowerPoint para documentos do PDF com mais eficiência. (FORMS-21310)
* Inclusão do pacote `com.adobe.granite.toggle.impl.dev` adicionada ao AEM Service Pack 24, permitindo processos de desenvolvimento mais simplificados ao removê-lo do complemento Forms. (FORMS-20139)
* Remoção de FeatureToggleRenderConditionServlet de forms-foundation e do pacote com.adobe.granite.toggle.impl.dev do complemento de formulários. Essa atualização garante que, após a instalação do complemento de formulários, a condição de renderização seja resolvida corretamente, melhorando a funcionalidade do componente para os clientes. (FORMS-20138)
* O desempenho dos usuários ficou lento devido a consultas de longa execução no Adaptive Forms. Essa atualização faz alterações na consulta de backports para melhorar a eficiência. Os clientes agora podem criar um índice com o nome da tag aemformsAFReferences. (FORMS-21411)
* Os usuários experimentaram posições de cabeçalho desalinhadas ao converter o HTML para o Portable Document Format (PDF) usando WebtoPDF. Esse problema afetava a consistência do layout do documento e a legibilidade da saída. (FORMS-21502, FORMS-21540)
* Os usuários experimentaram falhas de validação do PDF/A-1b apesar da verificação bem-sucedida do PreFlight. Esse problema afetava as verificações de conformidade de documentos para clientes corporativos que usavam as ferramentas de validação da PDF. (FORMS-20196)
* Os usuários experimentaram strings não traduzidas na interface do usuário, causando confusão e dificuldade em entender a interface. (FORMS-6542)
* Os usuários tiveram problemas com notificações por email. A etapa Enviar fluxo de trabalho de email não enviava emails, afetando os processos de comunicação automatizados. (FORMS-17961)
* Os usuários experimentaram falhas nos testes para workflows de formulários, o que afetou sua capacidade de concluir os processos de workflow com eficiência. (FORMS-16231)
* Os usuários não conseguiram usar o recurso de linha do tempo de arquivos PDF em formulários AEM. Esse problema afetava a capacidade dos usuários de rastrear alterações e revisões de documentos com eficiência. Ao fazer upload de qualquer PDF na seção &quot;Forms e documentos&quot; na área de formulários do AEM, a exibição da linha do tempo deixa de funcionar. (FORMS-19408)
* Os usuários experimentam uma exceção de ponteiro nulo ao interagir com OData. Isso causa interrupções nos processos de recuperação de dados. (FORMS-20348)
* Remoção da biblioteca google.common.collect após a remoção de Guava, uma biblioteca Java de código aberto. Essa atualização garante melhor compatibilidade e desempenho para clientes corporativos que usam o Adaptive Forms. (FORMS-17031)

### Forms Captcha

* Adição do suporte a Hcaptcha e Turnstile no Adaptive Forms com base nos Componentes de base. (FORMS-16562)
* Os usuários tiveram problemas de sobreposição de ícones na caixa de diálogo Criar configuração do Captcha. Ao preencher os campos obrigatórios, o ícone de informações se sobrepôs ao ícone de erro, causando confusão durante a configuração. (FORMS-16916)
* Os usuários tiveram uma configuração incorreta sendo coletada para o reCAPTCHA no Adaptive Forms com base em componentes de base. Quando o contêiner de configuração não foi selecionado para um formulário, várias configurações na pasta `conf/global` causaram o problema. (FORMS-19237)
* Os usuários tiveram problemas com o reCAPTCHA não sendo renderizado. Isso afetou os envios de formulários e a validação de segurança para clientes corporativos. (FORMS-17136, FORMS-19596)
* Os usuários enfrentam um problema em que o tamanho da empresa reCAPTCHA não é refletido na interface do usuário. (FORMS-16574)
* Os usuários tiveram problemas com a funcionalidade ReCaptcha devido a um ResourceResolver não fechado em &#39;ReCaptchaConfigurationServiceImpl&#39;, causando falhas de validação intermitentes durante os envios de formulários. (FORMS-19241)
* Os usuários tiveram problemas com a validação do reCAPTCHA quando os formulários são criados no Sites. O AEM Forms não reconheceu o nome do formulário corretamente, causando falhas de validação. (FORMS-20486)
* Os usuários experimentavam envios de formulários mesmo quando a pontuação do reCAPTCHA corporativo era 1.0, resultando em possíveis riscos de segurança. (FORMS-16766){{$include }}
* Melhoria no alerta do reCAPTCHA no Adaptive Forms ao atualizar códigos de erro de envio para 400. Além disso, alertas de registro refinados para distinguir entre tempos limite, expirações e falhas de detecção de bot, melhorando a precisão da solução de problemas e a observação do sistema. (FORMS-19240)
* Fechada uma instância ResourceResolver não fechada em ReCaptchaConfigurationServiceImpl para evitar possíveis vazamentos de recursos e melhorar a estabilidade do sistema ao usar integrações reCAPTCHA no AEM Forms. (FORMS-19242)
* Manuseio de configuração de CAPTCHA aprimorado para AEM Forms, garantindo as associações de configuração corretas para cada formulário quando houver várias entradas na pasta /conf/global. Impede o uso não intencional de configurações incorretas de CAPTCHA quando o contêiner de configuração não está explicitamente selecionado. (FORMS-19239)

### Interface de gerenciamento do Forms

* Os usuários experimentaram strings não localizadas no processo Forms > Criar Watchfolder > Criação Watchfolder. Ao criar uma pasta monitorada, cadeias de caracteres como &quot;Criação do Watchfolder&quot; e &quot;Watchfolder criado com êxito&quot; não foram encontradas, afetando a experiência da interface do usuário. (FORMS-15234)

## [!DNL Experience Manager Foundation] {#experience-manager-foundation}

A plataforma do [!DNL Adobe Experience Manager] 6.5 LTS baseia-se nas versões atualizadas da estrutura baseada em OSGi (Apache Sling e Apache Felix) e do repositório de conteúdo Java™: Apache Jackrabbit Oak 1.68.x.

O Eclipse Jetty 11.0.x é usado como um mecanismo de servlet para o início rápido.

### Compatibilidade com Java™  {#java-support}

* Compatibilidade com Java™ 17 e Java™ 21.
* Para atingir o desempenho ideal, substitua os valores de GC padrão por outros valores. Para obter mais informações, consulte a seção [instalar e atualizar](/help/sites-deploying/custom-standalone-install.md).
* A Adobe distribui atualizações de manutenção do Java™ 17 e do Java™ 21 para uso dos clientes em projetos relacionados ao AEM, quando não estão disponíveis publicamente na Oracle.

### Empacotamento de Uberjar {#uber-jar-packaging}

* Há uma pequena diferença no empacotamento do Uberjar do AEM 6.5 LTS. Para mais informações, consulte [Atualizar a versão Uber Jar do do AEM](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

### Atualizar {#upgrade}

* Para mais detalhes sobre o procedimento de upgrade, consulte a [documentação de upgrade](/help/sites-deploying/upgrade.md).

## Instalar e atualizar {#install-update}

Para conferir os requisitos de instalação, consulte as [instruções de instalação](/help/sites-deploying/custom-standalone-install.md).

>[!NOTE]
>
> Se você estiver atualizando diretamente para o LTS SP1 a partir dos 6.5 SPs antigos, siga as instruções fornecidas para 6.5 para 6.5 LTS GA [atualização](/help/sites-deploying/upgrade.md).


Para instruções mais detalhadas, consulte a [documentação de upgrade](/help/sites-deploying/upgrade.md).

>[!NOTE]
>
> Para novas instalações do AEM 6.5 LTS, as definições de índice precisam ser instaladas separadamente. Para mais informações, consulte [este artigo](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#index-definitions).

## Instalar e atualizar o complemento AEM Forms {#install-update-aem-forms-add-on}

Para obter instruções detalhadas, consulte [Executando uma Atualização no Local](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/release-notes/aem-forms-current-service-pack-installation-instructions).



## Plataformas compatíveis {#supported-platforms}

Encontre o conjunto completo de plataformas compatíveis, incluindo em relação ao suporte, nos [requisitos técnicos do AEM 6.5 LTS](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Java™ 17/Java™ 21 são as versões recomendadas para usar com o AEM 6.5 LTS.


## Recursos obsoletos e removidos {#deprecated-and-removed-features}

<!-- CARRY OVER EACH RELEASE -->

A Adobe analisa continuamente os recursos do produto para melhorar o valor para o cliente, modernizando ou substituindo recursos mais antigos. Essas alterações são feitas com atenção especial à compatibilidade com versões anteriores.

Para comunicar a remoção ou substituição iminente dos recursos do Adobe Experience Manager (AEM), as seguintes regras aplicam-se:

1. O anúncio sobre a descontinuidade é oferecido primeiro. Embora descontinuados, os recursos continuam disponíveis, mas não são mais aprimorados.
1. A remoção de recursos descontinuados ocorre na versão principal a seguir, no mais tardar. A data real da remoção está planejada para ser anunciada posteriormente.

Esse processo oferece a clientes ao menos um ciclo de versão para adaptar sua implementação a uma nova versão ou sucessor de uma funcionalidade descontinuada, antes da remoção.

### Recursos descontinuados {#deprecated-features}

Esta seção lista os recursos e funcionalidades que a Adobe descontinuou no AEM 6.5 LTS. Normalmente, a Adobe descontinua recursos antes de os remover em uma versão futura e fornece uma alternativa.


Clientes devem analisar se usam o recurso/funcionalidade em sua implementação atual, bem como planejar a alteração de sua implementação para usar a alternativa fornecida.

| Área | Destaque | Substituição | Versão (SP) |
| --- | --- | --- | --- |
| Sites | [Editor SPA](/help/sites-developing/spa-overview.md) | Os editores preferidos para gerenciar conteúdo headless no AEM são:<br>- [O editor universal](/help/sites-developing/universal-editor/introduction.md) para edição visual.<br>- [O editor de fragmentos de conteúdo](/help/assets/content-fragments/content-fragments-managing.md) para editar com base em formulários. | 6.5 LTS GA |

### Recursos removidos {#removed-features}

Esta seção lista os recursos e funcionalidades que foram removidas do AEM 6.5 LTS. Nas versões anteriores, esses recursos estavam marcados como descontinuados.

| Área | Destaque | Substituição | Versão (SP) |
| --- | --- | --- | --- |
| Commerce | O AEM CIF Classic não é compatível. | Migre para o [AEM CIF](/help/commerce/cif/migration.md). | 6.5 LTS GA |
| Soluções | Redes sociais/comunidades não são compatíveis. | Não há nenhuma substituição disponível. | 6.5 LTS GA |
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

<!-- DO THESE KNOWN ISSUES CARRY OVER EACH RELEASE? THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THIS LIST. -->

### Problema com o pacote de script JSP no AEM 6.5.21-6.5.23 e AEM 6.5 LTS GA

O AEM 6.5.21, 6.5.22, 6.5.23 e o AEM 6.5 LTS GA são fornecidos com o pacote `org.apache.sling.scripting.jsp:2.6.0`, que contém um problema conhecido. O problema normalmente ocorre com cargas altas, quando a instância do AEM trata muitas solicitações simultâneas.

Quando esse problema ocorre, uma das seguintes exceções pode aparecer nos logs de erros, junto com referências a `org.apache.sling.scripting.jsp:2.6.0`:

* `java.io.IOException: classFile.delete() failed`
* `java.io.IOException: tmpFile.renameTo(classFile) failed`
* `java.lang.ArrayIndexOutOfBoundsException: Index 0 out of bounds for length 0`
* `java.io.FileNotFoundException`

Uma hotfix [cq-6.5.lts.0-hotfix-NPR-42640](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-NPR-42640-1.2.zip) está disponível para resolver esse problema.

### Falha de conexão do Dispatcher com o recurso somente SSL (corrigido no AEM 6.5 LTS SP1 e posterior){#ssl-only-feature}

>[!NOTE]
>
> Esse problema está presente apenas na versão AEM 6.5 LTS GA.

Ao habilitar o recurso de somente SSL em implantações do AEM, há um problema conhecido que afeta a conectividade entre as instâncias do Dispatcher e do AEM. Após habilitar esse recurso, as verificações de integridade podem falhar, e a comunicação entre as instâncias do Dispatcher e do AEM pode ser interrompida. Este problema ocorre especificamente quando os clientes tentam se conectar a instâncias do AEM por meio do `https + IP` a partir do Dispatcher. Ele está relacionado a problemas de validação da indicação do nome do servidor (SNI, na sigla em inglês).

**Impacto:**

* Falhas de verificação da integridade com códigos de resposta HTTP 400
* Tráfego interrompido entre as instâncias do Dispatcher e do AEM
* O conteúdo não pode ser distribuído corretamente por meio do Dispatcher
* Falhas de conexão ao usar HTTPS com endereços IP na configuração do Dispatcher
* Erros HTTP 400 “SNI inválida” ao conectar-se via HTTPS + IP

**Ambientes afetados:**

* Implantações do AEM com configurações do Dispatcher
* Sistemas em que o recurso de somente SSL foi habilitado
* Configurações do Dispatcher, usando-se o método de conexão `https + IP` com instâncias do AEM

**Solução:**
Se você se deparar com esse problema, entre em contato com o suporte ao cliente da Adobe. Uma hotfix [cq-6.5.lts.0-hotfix-CQ-4359803](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-CQ-4359803-1.0.2.zip) está disponível para resolver esse problema. Não tente habilitar recursos de somente SSL até aplicar a hotfix necessária.

## Pacotes OSGi e pacotes de conteúdo incluídos{#osgi-bundles-and-content-packages-included}

Os seguintes documentos de texto listam os pacotes OSGi e os Pacotes de Conteúdo incluídos nesta versão do [!DNL Experience Manager] 6.5 LTS, Service Pack 1:

* [Lista de pacotes OSGi incluídos no Experience Manager 6.5 LTS, Service Pack 1](/help/release-notes/assets/65lts_sp1_bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [Lista de Pacotes de Conteúdo incluídos no Experience Manager 6.5 LTS, Service Pack 1](/help/release-notes/assets/65lts_sp1_packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Sites restritos{#restricted-sites}

Estes sites só estão disponíveis para clientes. Se você for cliente e precisar de acesso, entre em contato com o seu gerente de conta da Adobe.

* [Download do produto em licensing.adobe.com](https://licensing.adobe.com/)
* [Fale com o suporte ao cliente da Adobe](https://experienceleague.adobe.com/pt-br/docs/customer-one/using/home).

