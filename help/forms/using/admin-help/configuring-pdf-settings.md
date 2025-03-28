---
title: Definição das configurações do Adobe PDF
description: Saiba como definir as configurações do Adobe PDF visíveis na página Configurações do Adobe PDF. Você pode usar qualquer uma das configurações predefinidas do PDF ou criar as suas próprias configurações.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: PDF Generator
solution: Experience Manager, Experience Manager Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 41a8a4b0-cb39-40a6-82b6-085f2c635e0c
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '7415'
ht-degree: 0%

---

# Definição das configurações do Adobe PDF{#configuring-adobe-pdf-settings}

A página Configurações do Adobe PDF mostra as configurações de conversão que você pode especificar para suas fontes utilizarem. Você pode usar qualquer uma das configurações predefinidas do PDF ou criar as suas próprias configurações. As configurações do PDF determinam precisamente como os arquivos são convertidos e sua estrutura e recursos resultantes do PDF. As configurações do Adobe PDF eram conhecidas anteriormente como parâmetros ou opções de trabalho do Distiller®.

Na página Configurações do Adobe PDF, é possível realizar as seguintes tarefas:

* Exibir as configurações predefinidas do PDF. (Consulte [Sobre as configurações predefinidas do PDF](configuring-pdf-settings.md#about-the-predefined-pdf-settings).)
* Crie uma configuração do PDF ou edite uma criada anteriormente. (Consulte [Adicionar ou editar configurações do PDF](configuring-pdf-settings.md#add-or-edit-pdf-settings).)
* Especifique as configurações padrão do PDF. (Consulte [Alterar as configurações padrão](/help/forms/using/admin-help/configuring-file-type-settings.md#change-the-default-settings))
* Carregue um arquivo de configurações do PDF no servidor. (Consulte [Carregar configurações do PDF](configuring-pdf-settings.md#upload-pdf-settings).)
* Exclua as configurações personalizadas do PDF. (Consulte [Excluir configurações do PDF](configuring-pdf-settings.md#delete-pdf-settings).)
* Fazer upload e download de arquivos de prólogo e epílogo. (Consulte [Upload e download de arquivos de prólogo e epílogo](configuring-pdf-settings.md#uploading-and-downloading-prologue-and-epilogue-files).)

As configurações do Adobe PDF são aplicáveis somente às conversões baseadas em PDFMaker. Isso inclui as seguintes conversões:

* Documento do Microsoft Word (DOC, DOCX, RTF, TXT)
* Documento do Microsoft Excel (XLS, XLSX)
* Documento do Microsoft PowerPoint (PPT, PPTX)
* Documento de projeto do Microsoft (MPP)
* Documento do Microsoft Visio (VSD)

>[!NOTE]
>
>Ao usar o OpenOffice para converter os formatos acima, as configurações do Adobe PDF não são aplicadas.

## Sobre as configurações predefinidas do PDF {#about-the-predefined-pdf-settings}

O PDF Generator fornece várias configurações predefinidas do PDF para você usar. Não é possível modificar essas configurações predefinidas; no entanto, você pode criar uma configuração com base em uma existente editando a configuração e salvando-a com um novo nome.

**Impressão de Alta Qualidade:** Cria arquivos PDF para saída de alta qualidade. Esta configuração:

* reduz a resolução de imagens coloridas e em tons de cinza a 300 dpi
* reduz a resolução de imagens monocromáticas a 1200 dpi
* imprime em uma resolução de imagem mais alta
* O usa outras configurações para preservar a quantidade máxima de informações sobre o documento original.

Esses arquivos PDF podem ser abertos no Adobe Acrobat 5 e Adobe Acrobat Reader® 5 ou posterior.

**Páginas Superdimensionadas:** cria documentos do PDF adequados para visualização e impressão confiáveis de desenhos de engenharia com mais de 200 x 200 polegadas. Os documentos criados no PDF podem ser abertos no Adobe Acrobat Professional e no Acrobat Standard, versão 7 ou posterior, e no Adobe Reader 7 ou posterior.

**PDF/A-1B 2005 CMYK / PDF/A-1B 2005 RGB:** Verifica a conformidade dos trabalhos de entrada com o padrão ISO para preservação de longo prazo (arquivamento) de documentos eletrônicos e cria arquivos PDF/A somente se estiver em conformidade. Esses arquivos são usados principalmente para arquivamento. Arquivos compatíveis podem conter somente texto, imagens rasterizadas e objetos de vetor; eles não podem conter criptografia e scripts. Além disso, todas as fontes devem ser incorporadas para que os documentos possam ser abertos e exibidos como criados. O PDF/A-1b usa o PDF 1.4 e converte todas as cores em CMYK ou RGB, dependendo do padrão escolhido. Os arquivos do PDF criados com esse arquivo de configurações podem ser abertos no Acrobat 5 e no Acrobat Reader 5 e versões posteriores. Para obter mais informações sobre o PDF/A, consulte Adobe e padrões do setor.

**PDF/X-1a 2001:** verifica os trabalhos de entrada quanto à conformidade com o PDF/X-1a e cria arquivos PDF somente se forem compatíveis. PDF/X-1a é um padrão ISO para troca de conteúdo gráfico. O PDF/X-1a exige que todas as fontes sejam incorporadas, que as caixas adequadas do PDF sejam especificadas e que a cor seja exibida como CMYK ou cores especiais. Os arquivos PDF que atendem aos requisitos do PDF/X-1a são direcionados a uma condição de saída específica, como impressão offset da Web de acordo com as especificações de publicações de Web Offset. Para obter mais informações sobre o PDF/X, consulte Adobe e padrões do setor.

**PDF/X-3 2002:** verifica os trabalhos de entrada quanto à conformidade com o PDF/X-3 e cria arquivos PDF somente se forem compatíveis. Como o PDF/X-1a, o PDF/X-3 é um padrão ISO para troca de conteúdo gráfico. A principal diferença é que o PDF/X-3 é compatível com cores independentes de dispositivo.

**Qualidade de impressão:** cria arquivos PDF para uma produção de impressão de alta qualidade (por exemplo, em uma fotocompositora ou fotocompositora). Nesse caso, o tamanho do arquivo não é uma consideração. O objetivo é manter todas as informações em um arquivo PDF que uma impressora comercial ou um prestador de serviços de prova de prelo precisa para imprimir o documento corretamente. Este conjunto de opções:

* reduz a resolução de imagens coloridas e em tons de cinza a 300 dpi
* reduz a resolução de imagens monocromáticas a 1200 dpi
* incorpora subconjuntos de todas as fontes usadas no documento
* imprime em uma resolução de imagem mais alta,
* O não gira automaticamente as páginas com base na orientação dos comentários do texto ou das convenções de estruturação do documento (DSC)
* O usa outras configurações para preservar a quantidade máxima de informações sobre o documento original.

Os trabalhos de impressão falharão se tiverem fontes que não podem ser incorporadas. Esses arquivos do PDF podem ser abertos no Acrobat 5 e no Acrobat Reader 5 e versões posteriores.

>[!NOTE]
>
>Antes de criar um arquivo PDF para enviar a uma impressora comercial ou a um provedor de serviços de prova de prelo, determine a resolução de saída e outras configurações ou solicite um arquivo .joboptions com as configurações recomendadas. Talvez seja necessário personalizar as configurações do Adobe PDF para um provedor específico e, em seguida, fornecer um arquivo .joboptions.

**Menor Tamanho de Arquivo:** Cria arquivos PDF para exibição na Web ou em uma intranet, ou para distribuição através de um sistema de email para exibição na tela. Esse conjunto de opções usa compactação, redução da resolução e uma resolução de imagem relativamente baixa. Ele converte todas as cores em sRGB e não incorpora fontes, a menos que seja necessário. Ele também otimiza arquivos para o serviço de bytes. Esses arquivos do PDF podem ser abertos no Acrobat 5 e no Acrobat Reader 5.0 e versões posteriores.

**Padrão:** cria arquivos PDF para imprimir em impressoras desktop ou copiadoras digitais, publicar em um CD ou enviar a um cliente como uma prova de publicação. Esse conjunto de opções usa compactação e redução da resolução para reduzir o tamanho do arquivo. Ele também incorpora subconjuntos de todas as fontes usadas no arquivo, converte todas as cores em sRGB e imprime em uma resolução média para criar uma representação razoavelmente precisa do documento original. Observe que os subconjuntos de fontes do Microsoft Windows não são incorporados por padrão. Esses arquivos do PDF podem ser abertos no Acrobat 5 e no Acrobat Reader 5.0 e versões posteriores.

## Adicionar ou editar configurações do PDF {#add-or-edit-pdf-settings}

>[!NOTE]
> 
> Verifique se o usuário tem privilégios de administrador para acessar o console do administrador.

As configurações do PDF determinam com precisão como os arquivos são convertidos e sua estrutura e recursos resultantes do PDF. Defina uma nova configuração do PDF ou edite uma criada anteriormente. Não é possível modificar configurações predefinidas, mas você pode criar uma configuração com base em uma existente editando a configuração e salvando-a com um novo nome.

1. No console de administração, clique em Serviços > PDF Generator > Configurações do Adobe PDF.
1. Clique em Novo ou clique no nome de uma configuração existente.
1. Na página Nova/Editar configuração do Adobe PDF, preencha as informações necessárias nestas seções:

[Opções gerais](configuring-pdf-settings.md#general-options)

[Opções de imagens](configuring-pdf-settings.md#images-options)

[Opções de fontes](configuring-pdf-settings.md#fonts-options)

[Opções de cores](configuring-pdf-settings.md#color-options)

[Opções avançadas](configuring-pdf-settings.md#advanced-options)

[Opções de conformidade e emissão de relatórios de padrões](configuring-pdf-settings.md#standards-reporting-and-compliance-options)

[Opções de exibição inicial](configuring-pdf-settings.md#initial-view-options)

   Para ir para outra seção, clique no link na página da Web ou use os botões Next e Previous.

1. Após preencher as informações em todas as seções, clique em Salvar ou Salvar como e forneça um nome para a configuração.

## Fazer upload das configurações do PDF {#upload-pdf-settings}

Você pode ter as configurações do PDF disponíveis no servidor do PDF Generator fazendo upload delas de um computador local ou de um local de rede.

1. No console de administração, clique em Serviços > PDF Generator > Configurações do Adobe PDF e clique em Fazer upload.
1. Na página Fazer upload da configuração do Adobe PDF, clique em Procurar, localize o arquivo de configurações do PDF e clique em Abrir.
1. Clique em OK e em OK novamente.

## Excluir configurações do PDF {#delete-pdf-settings}

É possível excluir permanentemente as configurações do PDF se elas não forem mais necessárias.

1. No console de administração, clique em Serviços > PDF Generator > Configurações do Adobe PDF.
1. Marque a caixa de seleção ao lado da configuração a ser excluída. Você pode selecionar várias configurações.
1. Clique em Excluir e, na página Confirmação de exclusão, clique novamente em Excluir.

## Opções gerais {#general-options}

Use as opções gerais para especificar a versão do Acrobat a ser usada para compatibilidade de arquivos e outras opções de arquivos e dispositivos. Para obter instruções sobre como acessar as opções Gerais, consulte [Adicionar ou editar configurações do PDF](configuring-pdf-settings.md#add-or-edit-pdf-settings).

### Opções de arquivo {#file-options}

**Compatibilidade:** o nível de compatibilidade do arquivo PDF. Para documentos que serão amplamente distribuídos, considere selecionar o Acrobat 4 (PDF 1.3) ou o Acrobat 5 (PDF 1.4) para garantir que todos os usuários possam visualizar e imprimir o documento. Se você criar arquivos usando a compatibilidade com o Acrobat 5 ou posterior, eles podem não ser compatíveis com versões anteriores do Acrobat. As subseções a seguir mostram algumas das diferenças entre os arquivos PDF criados com o uso de diferentes níveis de compatibilidade com o Acrobat.

<table>
 <tbody>
  <tr>
   <th><p>Acrobat 4 (PDF 1.3)</p> </th>
   <th><p>Acrobat 5 (PDF 1.4)</p> </th>
   <th><p>Acrobat 6 (PDF 1.5)</p> </th>
   <th><p>Acrobat 7 (PDF 1.6) e Acrobat 8 (PDF 1.7)</p> </th>
  </tr>
  <tr>
   <td><p>Pode ser aberto com o Acrobat 3.0, o Acrobat Reader 3.0 e versões posteriores.</p> </td>
   <td><p>Pode ser aberto com o Acrobat 3.0, o Acrobat Reader 3.0 e versões posteriores. Os recursos específicos das versões posteriores podem ser perdidos ou não ser visualizados.</p> </td>
   <td><p>A maioria pode ser aberta com o Acrobat 4 e o Acrobat Reader 4.0 e versões posteriores. Os recursos específicos das versões posteriores podem ser perdidos ou não ser visualizados.</p> </td>
   <td><p>A maioria pode ser aberta com o Acrobat 4 e o Acrobat Reader 4.0 e versões posteriores. Os recursos específicos das versões posteriores podem ser perdidos ou não ser visualizados.</p> </td>
  </tr>
  <tr>
   <td><p>Não pode conter um trabalho artístico que use efeitos de transparência em tempo real. Qualquer transparência deve ser nivelada antes da conversão para o PDF 1.3.</p> </td>
   <td><p>Apoia o uso de transparência em tempo real no trabalho artístico. (O recurso Acrobat Distiller nivela a transparência.)</p> </td>
   <td><p>Apoia o uso de transparência em tempo real no trabalho artístico. (O recurso Acrobat Distiller nivela a transparência.)</p> </td>
   <td><p>Apoia o uso de transparência em tempo real no trabalho artístico. (O recurso Acrobat Distiller nivela a transparência.)</p> </td>
  </tr>
  <tr>
   <td><p>Camadas não são suportadas.</p> </td>
   <td><p>Camadas não são suportadas.</p> </td>
   <td><p>Preserva as camadas ao criar arquivos PDF a partir de aplicativos que oferecem suporte à geração de documentos em camadas do PDF, como Adobe Illustrator® CS ou Adobe InDesign® CS e posteriores.</p> </td>
   <td><p>Preserva as camadas ao criar arquivos PDF a partir de aplicativos que oferecem suporte à geração de documentos em camadas do PDF, como Illustrator CS ou InDesign CS e posteriores.</p> </td>
  </tr>
  <tr>
   <td><p>O espaço de cores DeviceN com 8 cores é suportado.</p> </td>
   <td><p>O espaço de cores DeviceN com 8 cores é suportado.</p> </td>
   <td><p>Há suporte para o espaço de cores DeviceN com até 31 corantes.</p> </td>
   <td><p>Há suporte para o espaço de cores DeviceN com até 31 corantes.</p> </td>
  </tr>
  <tr>
   <td><p>Fontes multibyte podem ser incorporadas. (O Distiller converte as fontes ao incorporar.)</p> </td>
   <td><p>Fontes multibyte podem ser incorporadas.</p> </td>
   <td><p>Fontes multibyte podem ser incorporadas.</p> </td>
   <td><p>Fontes multibyte podem ser incorporadas.</p> </td>
  </tr>
  <tr>
   <td><p>A segurança RC4 de 40 bits é compatível.</p> </td>
   <td><p>A segurança RC4 de 128 bits é compatível.</p> </td>
   <td><p>A segurança RC4 de 128 bits é compatível.</p> </td>
   <td><p>Suporte para segurança RC4 de 128 bits e AES (Advanced Encryption Standard) de 128 bits.</p> </td>
  </tr>
 </tbody>
</table>

**Compactação em Nível de Objeto:** Consolida objetos pequenos (cada um deles não pode ser compactado) em fluxos que podem ser compactados com eficiência.

**Desativado:** não compacta nenhuma informação estrutural no documento do PDF. Selecione esta opção se desejar que os usuários visualizem, naveguem e interajam com marcadores e outras informações estruturais usando o Acrobat 5 e versões posteriores.

**Somente marcas:** compacta informações estruturais no documento do PDF. Usar essa opção resulta em um arquivo PDF que pode ser aberto e impresso usando o Acrobat 5. Os usuários não podem visualizar nenhuma informação de acessibilidade, estrutura ou marcada do PDF no Acrobat 5 ou Acrobat Reader 5.0, mas podem visualizar essas informações no Acrobat 6 e no Adobe Reader 6.0.

**Girar páginas automaticamente:** define a rotação automática de páginas com base na orientação do texto ou dos comentários do DSC. Por exemplo, algumas páginas (como páginas que contêm tabelas) podem exigir que o usuário as vire de lado para lê-las. Selecione Individualmente para girar cada página com base na direção do texto nessa página. Selecione Coletivamente por arquivo para girar todas as páginas do documento com base na orientação da maioria do texto.

>[!NOTE]
>
>Se Processar comentários DSC estiver selecionado nas configurações avançadas e se os comentários de %%Orientação de Exibição estiverem incluídos, esses comentários terão prioridade na determinação da orientação da página.

**Associação:** especifica se um arquivo PDF deve ser exibido com associação no lado esquerdo ou direito. Essa configuração afeta a exibição de páginas na página faceada - layout contínuo e a exibição de miniaturas lado a lado.

**Resolução:** define a emulação para a resolução de uma impressora para arquivos de entrada que ajustam seu comportamento de acordo com a resolução da impressora na qual eles estão imprimindo. Para a maioria dos arquivos de entrada, uma configuração de resolução mais alta resulta em arquivos PDF maiores, mas de qualidade superior, e uma configuração mais baixa resulta em arquivos PDF menores, mas de qualidade inferior. Normalmente, a resolução determina o número de etapas em um gradiente ou mistura. Você pode inserir um valor de 72 a 4000. Mantenha essa configuração como padrão, a menos que você planeje imprimir o arquivo PDF em uma impressora específica e emule a resolução definida no arquivo de entrada original.

>[!NOTE]
>
>O aumento da configuração de resolução aumenta o tamanho do arquivo e pode aumentar um pouco o tempo necessário para processar alguns arquivos.

**Todas as Páginas ou Páginas de:** Especifica quais páginas serão convertidas. Deixe a caixa Para vazia para criar um intervalo do número de página inserido na caixa De até o final do arquivo.

**Otimizar para Modo de Exibição Rápido na Web:** Reestrutura o arquivo para download de página por vez (serviço de bytes) dos servidores Web. Essa opção compacta texto e arte vetorial, independentemente do que você selecionou como configurações de compactação na guia Imagens. A compactação resulta em acesso e visualização mais rápidos ao baixar o arquivo da Web ou de uma rede. Por padrão, essa opção não está ativada.

### Tamanho de página padrão {#default-page-size}

As opções de Tamanho de página padrão especificam o tamanho de página a ser usado quando não houver um especificado no arquivo original. Normalmente, os arquivos Adobe PostScript incluem essas informações, exceto os arquivos Encapsulated PostScript (EPS), que fornecem um tamanho de caixa delimitadora, mas não um tamanho de página. O tamanho máximo de página permitido é de 31.800.000 cm (15.000.000 polegadas) em qualquer direção. Essas opções configuram o tamanho de página padrão:

**Largura:** Largura da página

**Altura:** Altura da página

**Unidades:** Unidades a serem usadas para as configurações de largura e altura

## Opções de imagens {#images-options}

As opções de Imagens especificam a compactação e a redefinição da resolução de imagens. Você pode experimentar essas opções para encontrar um equilíbrio apropriado entre o tamanho do arquivo e a qualidade da imagem. Para obter instruções sobre como acessar as configurações de Imagens, consulte [Adicionar ou editar configurações do PDF](configuring-pdf-settings.md#add-or-edit-pdf-settings).

Essas opções configuram imagens coloridas, em tons de cinza e monocromáticas:

**Redução da amostra:** Defina um valor para cada tipo de imagem. Para diminuir a resolução de imagens coloridas, em tons de cinza ou monocromáticas, o PDF Generator combina pixels em uma área de amostra para criar um pixel maior. Forneça a resolução do dispositivo de saída em pontos por polegada (dpi) e insira uma resolução em dpi na caixa Para imagens acima. Para imagens com uma resolução acima desse limite, o PDF Generator combina pixels, conforme necessário, para reduzir a resolução da imagem (pixels por polegada) para a configuração de dpi especificada. Para desativar a redução de resolução, selecione Desativado. Estas são as opções:

**Redução da Resolução Média para:** Calcula a média dos pixels em uma área de amostra e substitui toda a área pela cor média dos pixels na resolução especificada.

**Redução de resolução bicúbica para:** usa uma média ponderada para determinar a cor dos pixels e geralmente produz resultados melhores do que o método de redução de resolução simples. Bicúbico é o método mais lento, mas mais preciso e resulta nas gradações tonais mais suaves.

**Subamostragem para:** Seleciona um pixel no centro da área de amostra e substitui toda a área por esse pixel na resolução especificada. A subamostragem reduz significativamente o tempo de conversão em comparação à redução da resolução, mas resulta em imagens menos suaves e contínuas.

A configuração de resolução para cores e tons de cinza deve ser de 1,5 a 2 vezes maior que a linha de controle da tela em que o arquivo será impresso. (Desde que você não fique abaixo dessa configuração de resolução recomendada, imagens sem linhas retas ou padrões geométricos ou repetitivos não serão afetadas por uma resolução mais baixa.) A resolução para imagens monocromáticas deve ser a mesma que o dispositivo de saída. Entretanto, salvar uma imagem monocromática em uma resolução superior a 1500 dpi aumenta o tamanho do arquivo sem melhorar significativamente a qualidade da imagem.

Considere também se os usuários precisam ampliar uma página. Por exemplo, se estiver criando um documento PDF de um mapa, considere usar uma resolução de imagem mais alta para que os usuários possam ampliar o mapa.

>[!NOTE]
>
>A reamostragem de imagens monocromáticas pode ter resultados de visualização inesperados, como nenhuma exibição de imagem. Se esse problema ocorrer, desative a reamostragem e converta o arquivo novamente. Esse problema é mais provável de ocorrer com a subamostragem e menos provável de ocorrer com a redução da resolução bicúbica.

Esta tabela mostra tipos de impressoras e sua resolução medida em dpi, sua regra de tela padrão medida em linhas por polegada (lpi) e uma resolução de reamostragem para imagens medidas em pixels por polegada (ppi). Por exemplo, para imprimir em uma impressora a laser de 600 dpi, digite 170 para obter a resolução das imagens em.

<table>
 <tbody>
  <tr>
   <th><p>Resolução da impressora</p> </th>
   <th><p>Tela de linha padrão</p> </th>
   <th><p>Resolução da imagem</p> </th>
  </tr>
  <tr>
   <td><p>300 dpi (impressora a laser)</p> </td>
   <td><p>60 lpp</p> </td>
   <td><p>120 ppi</p> </td>
  </tr>
  <tr>
   <td><p>600 dpi (impressora a laser)</p> </td>
   <td><p>85 lpp</p> </td>
   <td><p>170 ppi</p> </td>
  </tr>
  <tr>
   <td><p>1200 ppp (fotocompositora)</p> </td>
   <td><p>120 lpp</p> </td>
   <td><p>240 ppi</p> </td>
  </tr>
  <tr>
   <td><p>2400 ppp (fotocompositora)</p> </td>
   <td><p>150 lpp</p> </td>
   <td><p>300 ppi</p> </td>
  </tr>
 </tbody>
</table>

**Compactação:** Defina um valor para aplicar a imagens coloridas, em escala de cinza e monocromáticas. Para imagens coloridas e em tons de cinza, defina também a qualidade da imagem:

* Para imagens coloridas ou em tons de cinza, selecione ZIP para aplicar uma compactação que funcione bem em imagens que tenham grandes áreas de cores únicas ou padrões de repetição. Exemplos são capturas de tela, imagens simples criadas com programas de pintura e imagens monocromáticas que contêm padrões de repetição. Selecione JPEG, qualidade mínima a máxima, para aplicar uma compactação adequada para imagens em tons de cinza ou coloridas, como fotografias de tons contínuos que contêm mais detalhes do que podem ser reproduzidas na tela ou em impressão. Selecione Automático (JPEG) para determinar automaticamente a melhor qualidade para imagens coloridas e em tons de cinza.
* Para imagens monocromáticas, selecione CCITT Grupo 4, CCITT Grupo 3, ZIP, JPEG200, Automático (JPEG2000) ou Compactação Run Length.

Verifique se as imagens monocromáticas são digitalizadas como monocromáticas e não como tons de cinza. Às vezes, o texto digitalizado é salvo como imagens em tons de cinza por padrão. O texto em tons de cinza compactado com o método de compactação JPEG não está claro e pode estar ilegível.

**Qualidade da Imagem:** Configura a qualidade da imagem para imagens coloridas e em tons de cinza. As opções são mínimo, baixo, médio, alto e máximo.

**Suavização de Serrilhado para Cinza:** Suaviza bordas irregulares em imagens monocromáticas. Selecione 2 bits, 4 bits ou 8 bits para especificar 4, 16 ou 256 níveis de cinza. (A suavização de serrilhado pode desfocar pequenos tipos ou linhas finas.)

>[!NOTE]
>
>A compactação de texto e arte vetorial está sempre ativada.

**Política de Imagem:** Defina uma política para imagens coloridas, em tons de cinza e monocromáticas. Se a resolução da imagem ficar abaixo da resolução especificada, você ainda poderá optar por continuar (Ignorar), fornecer uma mensagem de aviso ou cancelar o trabalho.

## Opções de fontes {#fonts-options}

As opções de Fontes especificam quais fontes devem ser incorporadas em um arquivo PDF e se um subconjunto de caracteres deve ser incorporado no arquivo PDF. Para obter instruções sobre como acessar as opções de Fontes, consulte [Adicionar ou editar configurações do PDF](configuring-pdf-settings.md#add-or-edit-pdf-settings).

>[!NOTE]
>
>Quando você combina arquivos PDF com o mesmo subconjunto de fontes, o PDF Generator tenta combinar os subconjuntos de fontes.

**Incorporar Todas as Fontes:** Incorpora todas as fontes usadas no arquivo. A incorporação de fontes é necessária para a conformidade com o PDF/X.

**Subconjunto De Fontes Inseridas Quando A Porcentagem De Caracteres Usados
É Menor que:** Se você selecionar esta opção, especifique uma porcentagem limite para incorporar apenas um subconjunto das fontes. Por exemplo, se o limite for de 35 e menos de 35% dos caracteres forem usados, o PDF Generator incorporará somente esses caracteres. Somente fontes com bits de permissão apropriados são incorporadas.

**Quando a Incorporação Falhar:** Especifica como o PDF Generator responderá se não encontrar uma fonte a ser inserida durante o processamento de um arquivo. Você pode fazer com que o PDF Generator ignore a solicitação e substitua a fonte, avise e substitua a fonte ou cancele o processamento do trabalho atual.

**Font Source:** o local das fontes que o PDF Generator usa.

### Especificar quais fontes serão incorporadas {#specify-which-fonts-to-embed}

1. No console de administração, clique em Serviços > PDF Generator > Configurações do Adobe PDF.
1. Clique em Novo ou clique no nome de uma configuração.
1. Clique em Fontes e desmarque Incorporar todas as fontes.
1. Na lista Origem da fonte, selecione uma origem de fonte e clique em Ir para atualizar a lista de fontes na caixa à esquerda.
1. Clique em uma fonte na caixa à esquerda. Em seguida, clique em Adicionar ao lado da caixa apropriada para movê-la para a lista Sempre incorporar ou Nunca incorporar. Repita o procedimento para cada fonte. Use Ctrl-clique para selecionar várias fontes para mover.
1. Para remover uma fonte da lista Sempre incorporar ou Nunca incorporar, selecione-a e clique em Remover ao lado da caixa apropriada. Essa ação não remove a fonte do sistema, apenas remove a referência a ela na lista.
1. Se a fonte que você deseja especificar não for exibida, digite seu nome na caixa Adicionar fonte e clique em Sempre incorporar ou Nunca incorporar. Os nomes de fonte não podem conter caracteres alfanuméricos.

>[!NOTE]
>
>Uma fonte TrueType pode conter uma configuração adicionada pelo designer de fontes que impede a incorporação da fonte em arquivos PDF.

>[!NOTE]
>
>As fontes são selecionadas do cache de fontes do sistema Windows e é necessário reiniciar o sistema para atualizar o cache. Depois de especificar o diretório de fontes do Cliente, reinicie o sistema no qual o AEM Forms está instalado.

## Opções de cores {#color-options}

As opções de Cores definem todas as informações de gerenciamento de cores do PDF Generator. Para obter instruções sobre como acessar as opções de Cor, consulte [Adicionar ou editar configurações do PDF](configuring-pdf-settings.md#add-or-edit-pdf-settings).

### Configurações do Adobe Color {#adobe-color-settings}

**Arquivo de Configurações:** Esta lista contém uma lista de configurações de cores que também são usadas nos principais aplicativos gráficos, como Adobe Photoshop e Adobe Illustrator. A configuração de cor selecionada determina as outras configurações de cor do Adobe nesta página. Por exemplo, se você selecionar uma configuração diferente de Nenhum, todas as opções diferentes daquelas para Dados dependentes do dispositivo serão predefinidas e esmaecidas. Só é possível editar as configurações de Políticas de gerenciamento de cores e Espaços de trabalho se você selecionar Nenhum para Arquivo de configurações.

### Políticas de gerenciamento de cores {#color-management-policies}

Se você selecionou Nenhum para o Arquivo de configurações, a área Políticas de gerenciamento de cores especifica como o PDF Generator converte cores não gerenciadas em um arquivo PostScript.

**Manter Cor Inalterada:** Deixa as cores dependentes de dispositivo inalteradas e preserva as cores independentes de dispositivo como o equivalente mais próximo possível no PDF. Essa opção é útil para imprimir lojas que calibraram todos os seus dispositivos, usaram essas informações para especificar cores no arquivo e saída apenas para esses dispositivos.

**Marcar Tudo para Gerenciamento de Cores:** incorpora um perfil do Consórcio Internacional de Cores ao destilar arquivos e calibrar cores nas imagens, o que torna as cores nos arquivos PDF resultantes independentes do dispositivo, caso você tenha selecionado o Acrobat 4 (PDF 1.3) ou compatibilidade posterior. No entanto, os espaços de cores dependentes de dispositivo em arquivos (RGB, Tons de cinza e CMYK) são convertidos em espaços de cores independentes de dispositivo (CalRGB, CalGray e LAB).

**Marcar Somente Imagens para Gerenciamento de Cores:** incorpora perfis ICC somente em imagens, não em texto ou gráficos, ao destilar arquivos, se você tiver selecionado a compatibilidade com o Acrobat 4 (PDF 1.3). Essa opção impede que o texto em preto seja submetido a qualquer mudança de cor. No entanto, os espaços de cores dependentes de dispositivo em imagens (RGB, Tons de cinza e CMYK) são convertidos em espaços de cores independentes de dispositivo (CalRGB, CalGray e LAB). Texto e gráficos não são convertidos.

**Converter Todas as Cores em sRGB ou Converter Todas as Cores em
CMYK:** Calibra cores no arquivo, tornando a cor independente do dispositivo, semelhante a Marcar Tudo para Gerenciamento de Cores. Se você selecionou compatibilidade com o Acrobat 4 (PDF 1.3) ou posterior e converteu para sRGB, as imagens CMYK e RGB serão convertidas para sRGB.

Independentemente da opção de compatibilidade selecionada, as imagens em tons de cinza permanecem inalteradas. Isso geralmente reduz o tamanho e aumenta a velocidade de exibição dos arquivos PDF, pois são necessárias menos informações para descrever imagens RGB do que imagens CMYK. Como o RGB é o espaço de cores nativo usado nos monitores, nenhuma conversão de cores é necessária durante a exibição, o que contribui para a rápida visualização online. Essa opção é recomendada se o arquivo PDF for para uso online ou com impressoras de baixa resolução.

**Tentativa de Renderização do Documento:** O método para mapear cores entre espaços de cores. O resultado de qualquer método específico depende dos perfis dos espaços de cores. Por exemplo, alguns perfis produzem resultados idênticos com métodos diferentes. Estas opções estão disponíveis:

>[!NOTE]
>
>Em todos os casos, as intenções podem ser ignoradas ou substituídas pelas operações de gerenciamento de cores que ocorrem após a criação do arquivo do PDF.

**Preservar:** significa que a intenção está especificada no dispositivo de saída em vez de no arquivo PDF. Em muitos dispositivos de saída, Colorimétrico relativo é a intenção padrão.

**Perceptivo:** mantém os valores de cor relativos entre os pixels originais à medida que são mapeados para o gamut de destino. Esse método preserva a relação visual entre cores, embora os próprios valores de cor possam mudar.

**Saturação:** Mantém os valores de saturação relativos dos pixels originais. Esse método é adequado para gráficos de negócios, em que a relação exata entre cores não é tão importante quanto ter cores saturadas brilhantes.

**Colorimétrica Relativa:** Mapeia novamente o ponto branco do espaço de origem para o ponto branco do espaço de destino.

**Colorimétrica Absoluta:** Desabilita a correspondência de pontos brancos e pretos ao converter cores. Este método não é recomendado, a menos que seja necessário preservar as cores da assinatura, como as usadas em marcas comerciais ou logotipos.

### Espaços de trabalho {#working-spaces}

Para todos os valores na lista em Políticas de gerenciamento de cores, diferentes de Deixar a cor inalterada, selecione nas listas da área Espaço de trabalho para especificar quais perfis ICC são usados para definir e calibrar os espaços de cores em tons de cinza, RGB e CMYK em arquivos PDF destilados. Estas opções estão disponíveis:

**Cinza:** Define o espaço de cores de todas as imagens em tons de cinza nos arquivos. Essa opção estará disponível somente se você escolher Marcar tudo para gerenciamento de cores ou Marcar somente imagens para gerenciamento de cores. O perfil ICC padrão para imagens cinza é Gama cinza 2.2. Também é possível selecionar Nenhum para impedir a conversão de imagens em tons de cinza.

**RGB:** Define o espaço de cores de todas as imagens RGB em arquivos. O padrão, sRGB IEC61966-2.1, geralmente é uma boa escolha porque está se tornando um padrão do setor e muitos dispositivos de saída o reconhecem. Você também pode selecionar Nenhum para impedir a conversão de imagens do RGB.

**CMYK:** Define o espaço de cores de todas as imagens CMYK em arquivos. O padrão é U.S. Web Coated (SWOP) v2. Você também pode selecionar Nenhum para impedir a conversão de imagens CMYK.

>[!NOTE]
>
>Selecionar Nenhum para todos os três espaços de trabalho tem o mesmo efeito que selecionar Deixar cor inalterada.

**Preservar Valores CMYK para Espaços de Cores CMYK Calibrados:** Quando selecionados, os valores CMYK independentes de dispositivo são tratados como valores dependentes de dispositivo (DeviceCMYK), os espaços de cores independentes de dispositivo são descartados e os arquivos PDF/X-1a usam o valor Converter Todas as Cores em CMYK. Quando desmarcada, os espaços de cores independentes do dispositivo são convertidos em CMYK se a política de gerenciamento de cores estiver definida como Converter todas as cores em CMYK.

### Dados dependentes de dispositivo {#device-dependent-data}

Essas opções se aplicam se você trabalhar com documentos criados com aplicativos de documentação e gráficos avançados, como o Adobe Illustrator e o Adobe InDesign. Para obter mais informações, consulte a documentação fornecida com o aplicativo.

As funções de transferência são utilizadas para efeitos artísticos e para ajustar as especificações de um dispositivo de saída específico. Por exemplo, um arquivo destinado à saída em uma fotocompositora específica pode conter funções de transferência que compensam o ganho de pontos inerente a essa impressora.

**Preservar Sob Remoção de Cores e Geração de Preto:** Mantém essas configurações, se elas existirem no arquivo PostScript. A geração de preto calcula a quantidade de preto a ser usada quando você está tentando reproduzir uma cor específica. A remoção das cores subjacentes (UCR) reduz a quantidade de componentes ciano, magenta e amarelo para compensar a quantidade de preto adicionada pela geração de preto. Como usa menos tinta, o UCR geralmente é usado para papel de jornal e estoque sem revestimento.

**Quando as Funções de Transferência são Encontradas:** Determina o que fazer quando as funções de transferência são encontradas:

**Preservar:** retém as funções de transferência tradicionalmente usadas para compensar o ganho ou a perda de pontos que pode ocorrer quando uma imagem é transferida para filme. O ganho de pontos ocorre quando os pontos de tinta que compõem uma imagem impressa são maiores (por exemplo, devido à propagação no papel) do que na tela de meio-tom; a perda de pontos ocorre quando os pontos são impressos menores. Com essa opção, as funções de transferência são mantidas como parte do arquivo e são aplicadas ao arquivo quando ele é emitido.

**Aplicar:** Não mantém a função de transferência, mas a aplica ao arquivo, o que altera as cores no arquivo. Essa opção é útil para criar efeitos de cor em um arquivo. Por padrão, essa opção é selecionada para novas configurações.

**Remover:** remove todas as funções de transferência aplicadas. Remova as funções de transferência aplicadas, a menos que o arquivo PDF seja enviado para o mesmo dispositivo para o qual o arquivo PostScript de origem foi criado.

**Preservar Informações de Meio-Tom:** Retém todas as informações de meio-tom nos arquivos. As informações de meio-tom consistem em pontos que controlam quanto os dispositivos de meio-tom de tinta depositam em um local específico no papel. Variar o tamanho e a densidade dos pontos cria a ilusão de variações de cinza ou cor contínua. Para uma imagem CMYK, quatro telas de meio-tom são usadas, uma para cada tinta usada no processo de impressão.

Na produção de impressão tradicional, um meio-tom é produzido colocando uma tela de meio-tom entre um pedaço de filme e a imagem e, em seguida, expondo o filme. Equivalentes eletrônicos, como no Adobe Photoshop, permitem que os usuários especifiquem os atributos da tela de meio-tom antes de produzirem a saída de filme ou papel. As informações de meio-tom devem ser usadas com um dispositivo de saída específico.

## Opções avançadas {#advanced-options}

As opções avançadas especificam quais comentários do Document Structuring Convention (DSC) devem ser mantidos no arquivo PDF e como definir outras opções que afetam a conversão do PostScript. Em um arquivo do PostScript, os comentários do DSC contêm informações sobre o arquivo (como o aplicativo de origem, a data de criação e a orientação da página). Eles também fornecem estrutura para descrições de página no arquivo (como instruções de início e término para uma seção de prólogo). Os comentários DSC podem ser úteis quando o documento for impresso ou impresso. Para obter instruções sobre como acessar as opções avançadas, consulte [Adicionar ou editar configurações do PDF](configuring-pdf-settings.md#add-or-edit-pdf-settings).

Ao trabalhar com as opções Avançadas, é útil compreender o idioma do PostScript e como ele é traduzido para o PDF. (Consulte [Adobe PostScript 3](https://www.adobe.com/products/postscript/main.html).)

**Permitir que o arquivo do PostScript substitua as configurações do Adobe PDF:** Usa configurações armazenadas em um arquivo do PostScript em vez do arquivo de configurações do Adobe PDF atual. Antes de processar um arquivo do PostScript, você pode colocar parâmetros no arquivo para controlar os seguintes aspectos:

* compactação de texto e gráficos
* redução da resolução e codificação de imagens amostradas
* incorporação de fontes Type 1 e instâncias de fontes Type 1 Multiple Master

**Permitir XObjects do PostScript PostScript:** os XObjects armazenam informações que aparecem em muitas páginas do mesmo arquivo, como informações de imagem de plano de fundo ou de cabeçalho e rodapé. O uso de PostScript XObjects pode resultar em uma impressão mais rápida, mas requer mais memória de impressora. Para impedir a criação de PostScript XObjects, desmarque essa opção se criar arquivos PDF compatíveis com o Acrobat 5 (PDF 1.4) ou posterior.

**Converter gradientes em sombras suaves:** converte mesclagens em sombras suaves para o Acrobat 4 e posterior, tornando os arquivos PDF menores e melhorando potencialmente a qualidade da saída final. O PDF Generator converte gradientes do Adobe Illustrator, Adobe InDesign, Adobe FreeHand MX, CorelDraw, Quark Xpress e Microsoft PowerPoint.

**Converter Linhas Suaves em Curvas:** Reduz a quantidade de pontos de controle usados para criar curvas em desenhos CAD, o que resulta em PDFs menores e renderização mais rápida na tela.

**Preservar Semântica de Página de Cópia de Nível 2:** Usa o operador de página de cópia definido no PostScript LanguageLevel 2 em vez de no PostScript LanguageLevel 3. Se você tiver um arquivo PostScript e selecionar essa opção, um operador de página de cópia copiará a página. Se esta opção não estiver selecionada, o equivalente de uma operação de página de exibição será executado, mas o estado dos gráficos não será reinicializado.

**Preservar Configurações de Superimposição:** Mantém todas as configurações de superimposição em arquivos que estão sendo convertidos para o PDF. Cores superimpostas são duas ou mais tintas impressas uma sobre a outra. Por exemplo, quando uma tinta ciano é impressa sobre uma tinta amarela, a superimposição resultante é uma cor verde. Sem a superimposição, o amarelo subjacente não seria impresso, resultando em uma cor ciano.

**A Superimposição Padrão é Diferente de Zero A Superimposição:** Impede que objetos superimpostos com valores CMYK zero sejam vazados dos objetos CMYK que estão abaixo deles. Esse efeito é realizado inserindo o parâmetro de estado gráfico OPM 1 no arquivo do PDF onde quer que o operador Setoverprint esteja presente.

**Salvar configurações do Adobe PDF no arquivo do PDF:** Incorpora o arquivo de configurações usado para criar o arquivo do PDF. Você pode abrir e exibir o arquivo de configurações (que tem uma extensão de arquivo .joboptions) na caixa de diálogo Anexos de arquivo no Acrobat. O arquivo de configurações do Adobe PDF se torna um item na árvore EmbeddedFiles dentro do arquivo PDF.

**Salvar imagens originais do JPEG no PDF, se possível:** Processa todas as imagens compactadas do JPEG (imagens já compactadas com a codificação DCT) sem compactá-las. Se essa opção estiver selecionada, o PDF Generator descompacta as imagens do JPEG para garantir que elas não estejam corrompidas. No entanto, ela não faz a recompressão de imagens válidas, processando a imagem original intocada. Com essa opção selecionada, o desempenho melhora porque ocorre somente a descompactação (e não a descompactação), e os dados e metadados da imagem são preservados.

**Salvar tíquete de trabalho portátil no arquivo do PDF:** preserva um tíquete de trabalho do PostScript em um arquivo do PDF. O ticket de trabalho contém informações sobre o arquivo PostScript, como tamanho da página, resolução e informações de interrupção, em vez de informações sobre o conteúdo. Essas informações podem ser usadas posteriormente em um fluxo de trabalho ou para imprimir a PDF.

**Usar Prolog.ps e Epilog.ps:** envia um arquivo de prólogo e epílogo com cada trabalho. Esses arquivos têm muitos propósitos. Por exemplo, os arquivos de perfil podem ser editados para especificar folhas de rosto. Os arquivos epilog podem ser editados para resolver uma série de procedimentos em um arquivo do PostScript. Você pode fazer upload ou download dos arquivos. (Consulte Upload e download de arquivos de prólogo e epílogo.)

**Processar Comentários DSC:** Mantém as informações DSC de um arquivo PostScript. Estas subopções estão disponíveis:

**Registrar avisos DSC:** Exibe mensagens de aviso sobre comentários DSC problemáticos durante o processamento e os adiciona a um arquivo de log.

**Preservar Informações do EPS do DSC:** Mantém informações, como o aplicativo de origem e a data de criação de um arquivo do EPS. Se essa opção não estiver selecionada, a página será dimensionada e centralizada com base no canto superior esquerdo do objeto superior esquerdo e no canto inferior direito do objeto inferior direito na página.

**Preservar Comentários OPI:** retém as informações necessárias para substituir uma imagem FPO (Somente para Posicionamento) ou um comentário pela imagem de alta resolução localizada em servidores que oferecem suporte às versões 1.3 e 2.0 da OPI (Interface Aberta de Pré-Impressão).

**Preservar Informações do Documento de DSC:** Mantém informações como título, data de criação e hora. Quando você abre um arquivo do PDF no Acrobat, essas informações são exibidas no painel Descrição das propriedades do documento.

**Redimensionar Página e Centralizar Arte para Arquivos EPS:** Centraliza uma imagem EPS e redimensiona a página para ajustá-la ao redor da imagem. Essa opção se aplica somente a tarefas que consistem em um único arquivo do EPS.

## Opções de conformidade e emissão de relatórios de padrões {#standards-reporting-and-compliance-options}

O PDF Generator pode verificar o conteúdo do documento em um arquivo PostScript para garantir que ele atenda aos critérios padrão do PDF/X-1a, PDF/X-3 ou PDF/A antes de criar o arquivo PDF. Para arquivos compatíveis com PDF/X, você também pode exigir que o arquivo PostScript atenda a critérios adicionais selecionando outras opções em &quot;Relatórios e conformidade padrão&quot;. A disponibilidade das opções depende do padrão selecionado.

Arquivos compatíveis com PDF/X são usados principalmente como um formato padronizado para a troca de arquivos PDF destinados à produção de impressão de alta resolução. A menos que esteja criando um documento PDF para produção de impressão, você pode ignorar os padrões de conformidade do PDF/X.

Os arquivos compatíveis com PDF/A são usados principalmente para arquivamento. Como a preservação de longo prazo é a meta, o documento deve conter somente o que é necessário para abertura e visualização durante toda a vida útil pretendida do documento. Por exemplo, arquivos compatíveis com PDF/A podem conter apenas texto, imagens rasterizadas e objetos de vetor; não podem conter criptografia e scripts. Além disso, todas as fontes devem ser incorporadas para que os documentos possam ser abertos e exibidos como criados. Em outras palavras, os documentos compatíveis com o PDF/A são *mais finos* do que seus equivalentes no PDF/X, que se destinam à produção high-end.

>[!NOTE]
>
>Se você configurar uma pasta monitorada para criar arquivos compatíveis com o PDF/A, certifique-se de não adicionar segurança à pasta; o padrão PDF/A não permite criptografia.

Para obter instruções sobre como acessar as opções de conformidade e relatórios de Padrões, consulte [Adicionar ou editar configurações do PDF](configuring-pdf-settings.md#add-or-edit-pdf-settings).

**Padrão de Conformidade:** Selecione um padrão para produzir um relatório que indique se o arquivo está em conformidade com os requisitos e, se não estiver, quais problemas foram encontrados. Quando a opção Compatibilidade na página Configurações gerais estiver definida como Acrobat 4.0, as seguintes opções serão ativadas. Quando a Compatibilidade está definida como Acrobat 5.0, somente as opções do Acrobat 5.0 estão disponíveis para seleção. Quando a Compatibilidade é definida como uma opção alternativa, as seguintes opções ficam esmaecidas:

* PDF/X-1a (compatível com o Acrobat 4.0)
* PDF/X-3 (compatível com o Acrobat 4.0)
* PDF/X-1a (compatível com Acrobat 5.0)
* PDF/X-3 (compatível com o Acrobat 5.0)
* PDF/A-1b (compatível com o Acrobat 5.0)

### Opções para padrões PDF/X {#options-for-pdf-x-standards}

**Quando Não Compatível:** Especifica se o arquivo PDF deve ser criado se o arquivo PostScript não estiver em conformidade com os requisitos PDF/X. Esta opção está disponível quando o Padrão de Conformidade na página Padrões, Geração de Relatórios e Conformidade é definido como uma opção diferente de Nenhum.

**Continuar:** cria um arquivo PDF.

**Cancelar Trabalho:** cria um arquivo PDF somente se o arquivo PostScript atender aos requisitos PDF/X das opções de relatório selecionadas e for válido. Se ambas as opções de relatório do PDF/X forem selecionadas e o arquivo PostScript atender apenas um conjunto de critérios do PDF/X (por exemplo, PDF/X-3), o PDF Generator criará o arquivo compatível.

**Se TrimBox e ArtBox não forem especificados:** Disponível quando o Padrão de Conformidade na página Conformidade e Relatórios de Padrões estiver definido como uma opção diferente de Nenhum.

**Relatar como Erro:** Sinaliza o arquivo PostScript como não compatível se uma das opções de relatório estiver selecionada e uma caixa de apara ou de arte estiver ausente em qualquer página.

**Definir TrimBox como MediaBox com Deslocamentos:** Calcula valores em pontos para a caixa de apara com base nos deslocamentos da caixa de mídia das respectivas páginas se a caixa de apara e a caixa de arte não forem especificadas. A caixa de apara é sempre tão pequena ou menor que a caixa de mídia de fechamento.

**Se BleedBox Não For Especificada:** Disponível quando o Padrão de Conformidade na página Padrões de Relatório e Conformidade estiver definido como uma opção diferente de Nenhum.

**Definir BleedBox como MediaBox:** Usa os valores da caixa de mídia para a caixa de sangria se ela não estiver especificada.

**Definir BleedBox como TrimBox com Deslocamentos:** Calcula valores em pontos para a caixa de sangria com base nos deslocamentos da caixa de apara das respectivas páginas, se a caixa de sangria não estiver especificada. A caixa de sangria é sempre tão grande ou maior do que a caixa de apara fechada.

**Valores Padrão Se Não Especificados no Documento:** Essa opção estará disponível quando o Padrão de Conformidade na página Padrões de Relatório e Conformidade for definido como uma opção diferente de Nenhum.

**Nome do Perfil de Propósito de Saída:** Indica a condição de impressão caracterizada para a qual o documento está preparado. Se um documento não especificar um nome OutputIntent, o PDF Generator usará o valor selecionado nesse menu. Você pode selecionar um dos nomes fornecidos ou inserir um nome no espaço fornecido. Se o fluxo de trabalho exigir que o documento especifique o propósito de saída, selecione Nenhum. Qualquer documento que não atenda aos requisitos falha na verificação de conformidade.

**Identificador de Condição de Saída:** Indica o nome de referência especificado pelo Registro do nome do perfil de intenção de saída.

**Condição de Saída:** Descreve a condição de impressão desejada. Essa entrada pode ser útil para o destinatário pretendido do documento PDF.

**Nome do Registro (URL):** Indica o endereço Web para obter mais informações sobre o Registro. O URL é inserido automaticamente para os nomes de registro ICC.

**Trapped:** indica o estado do trapping no documento. A conformidade com o PDF/X exige um valor Verdadeiro ou Falso. Se o documento não especificar o estado preso, o valor fornecido aqui será usado. Se o fluxo de trabalho exigir que o documento especifique o estado bloqueado, selecione Deixar indefinido. Qualquer documento que não atenda aos requisitos falha na verificação de conformidade.

### Opções para o padrão PDF/A {#options-for-pdf-a-standard}

Essas opções são ativadas quando a Compatibilidade (na área Geral) está definida como Acrobat 4 (PDF 1.3) ou Acrobat 5 (PDF 1.4).

**Quando Não Compatível:** Especifica se o arquivo PDF deve ser criado se o arquivo PostScript não estiver em conformidade com os requisitos PDF/A.

**Continuar:** cria um arquivo PDF mesmo que o arquivo PostScript não atenda aos requisitos do padrão.

**Cancelar Trabalho:** cria um arquivo do PDF somente se o arquivo do PostScript atender aos requisitos do PDF/A e for válido.

**Nome do Perfil de Propósito de Saída:** Indica a condição de impressão caracterizada para a qual o documento foi preparado e é necessário para conformidade com o PDF/A. Se o fluxo de trabalho exigir que o documento especifique informações de Propósito de saída, selecione &quot;Nenhum&quot;. O documento não passará na verificação de conformidade se essas informações não forem fornecidas.

**Condição de Saída:** Descreve a condição de impressão desejada. Essa entrada não é necessária, mas pode ser usada para fornecer informações úteis ao destinatário pretendido do documento PDF.

## Opções de exibição inicial {#initial-view-options}

Essas opções são organizadas em três áreas: Opções de Documento, Opções de Janela e Opções de Interface do Usuário. Para obter instruções sobre como acessar as opções de exibição Inicial, consulte [Adicionar ou editar configurações do PDF](configuring-pdf-settings.md#add-or-edit-pdf-settings).

Para usar qualquer opção, selecione Definir configurações de exibição inicial.

### Opções de documento {#document-options}

As opções de documento controlam a aparência do documento na janela do documento, como o nível de ampliação e a rolagem.

**Mostrar:** Determina quais painéis e guias são exibidos na janela do aplicativo por padrão. Painel de marcadores e Página abre o painel do documento e exibe a guia Marcadores.

**Layout da página:** determina se o documento é exibido no modo de página única, página oposta, página contínua ou página oposta contínua.

**Ampliação:** define o nível de zoom usado para exibir o documento quando aberto. O padrão usa o valor de ampliação configurado pelo usuário nas preferências do Acrobat ou do Adobe Reader.

**Abrir em Número de Página:** Define a página na qual o documento abre, que geralmente é a página 1.

>[!NOTE]
>
>A definição de Padrão para as opções de ampliação e layout de página usa as configurações do usuário individuais nas preferências de Exibição de página no Acrobat ou no Adobe Reader.

### Opções de janela {#window-options}

As opções de janela determinam como a janela se ajusta na área da tela quando um usuário abre o documento. No entanto, as opções não têm efeito quando um documento do PDF é visualizado em um navegador da Web.

**Redimensionar Janela para Página Inicial** Ajusta a janela do documento para que ela se ajuste perfeitamente ao redor da página de abertura, de acordo com as opções selecionadas em Opções do Documento.

**Centralizar Janela na Tela:** Posiciona a janela no centro da área da tela.

**Abrir no Modo de Tela Inteira:** Maximiza a janela do documento e exibe o documento sem a barra de menu, a barra de ferramentas ou os controles de janela.

**Mostrar:** Nome do arquivo mostra o nome do arquivo na barra de título da janela. Título do documento mostra o título do documento na barra de título da janela.

### Opções da interface do usuário {#user-interface-options}

As opções da interface do usuário determinam quais controles são exibidos ou ocultos quando o usuário abre o documento.

**Ocultar Barra de Menus:** Se selecionada, oculta a barra de menus

**Ocultar Barras de Ferramentas:** Se selecionada, oculta as barras de ferramentas

**Ocultar Controles de Janela:** Se selecionado, oculta os controles de janela

>[!NOTE]
>
>Se você ocultar a barra de menus e a barra de ferramentas, os usuários não poderão aplicar comandos e selecionar ferramentas, a menos que conheçam os atalhos de teclado ao abrir o arquivo no Acrobat.

## Upload e download de arquivos de prólogo e epílogo {#uploading-and-downloading-prologue-and-epilogue-files}

Os arquivos de perfil são usados para adicionar código PostScript personalizado que é executado no início de cada trabalho do PostScript que está sendo destilado. Os arquivos de epílogo são usados para adicionar um código PostScript personalizado, executado no final de cada tarefa do PostScript. Você pode baixar os arquivos de prólogo e epílogo do servidor para salvá-los localmente. Talvez você queira baixar os arquivos para configurá-los de forma independente ou carregá-los em outro local ou em outro computador.

Esses arquivos têm muitos propósitos. Por exemplo, os arquivos de perfil podem ser editados para especificar folhas de rosto; os arquivos de epílogo podem ser editados para resolver uma série de procedimentos em um arquivo PostScript. Você também pode selecionar e fazer upload dos arquivos de prólogo e epílogo a serem enviados com cada tarefa.

### Baixar um arquivo de prólogo ou epílogo {#download-a-prologue-or-epilogue-file}

1. No console de administração, clique em Serviços > PDF Generator > Configurações do Adobe PDF.
1. Clique em Novo ou clique no nome de uma configuração.
1. Clique em Avançado e, em seguida, ao lado da opção Usar Prolog.ps e Epilog.ps, clique em Download.
1. Na página Baixar arquivos de Prolog e Epilog, clique em Prolog.ps ou Epilog.ps e clique em Salvar.

### Carregar um arquivo de prólogo ou epílogo {#upload-a-prologue-or-epilogue-file}

1. No console de administração, clique em Serviços > PDF Generator > Configurações do Adobe PDF.
1. Clique em Novo ou clique no nome de uma configuração.
1. Clique em Avançado e, em seguida, ao lado da opção Usar Prolog.ps e Epilog.ps, clique em Fazer upload.
1. Na página Fazer upload dos arquivos de prólogo e epílogo, clique em Procurar para selecionar um arquivo de prólogo ou de epílogo.
1. Localize o arquivo e clique em Abrir.
1. Para usar o arquivo, verifique se Usar Prolog.ps e Epilog.ps está selecionado na área Avançado da página Nova/Editar configuração do Adobe PDF.
1. Clique em Salvar

>[!NOTE]
>
>O PDF Generator oferece suporte aos arquivos prolog e epilog somente para a conversão de arquivos PostScript e Encapsulated PostScript em PDF.
