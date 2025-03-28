---
title: Perfis para processamento de metadados, imagens e vídeos
description: Um perfil inclui um conjunto de regras sobre as opções a serem aplicadas aos ativos carregados em uma pasta. Especifique qual perfil de metadados e perfil de codificação de vídeo serão aplicados aos ativos de vídeo que você fez upload. Para ativos de imagem, você também pode especificar qual perfil de imagem aplicar aos ativos de imagem para cortá-los corretamente.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: administering
content-type: reference
docset: aem65
role: User, Admin
feature: Workflow,Asset Management,Renditions
solution: Experience Manager, Experience Manager Assets
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '1391'
ht-degree: 0%

---

# Perfis para processamento de metadados, imagens e vídeos{#profiles-for-processing-metadata-images-and-videos}

Um perfil é uma fórmula para quais opções serão aplicadas a ativos que são carregados em uma pasta. Por exemplo, você pode especificar o perfil de metadados e o perfil de codificação de vídeo a serem aplicados aos ativos de vídeo carregados. Ou qual perfil de imagens aplicar aos ativos de imagem para cortá-los corretamente.

Essas regras podem incluir a adição de metadados, o recorte inteligente de imagens ou o estabelecimento de perfis de codificação de vídeo. No Adobe Experience Manager, você pode criar três tipos de perfis, que são abordados em detalhes nos seguintes links:

* [Perfis de metadados](/help/assets/metadata-config.md#metadata-profiles)
* [Perfis de imagem](/help/assets/image-profiles.md)
* [Perfis de vídeo](/help/assets/video-profiles.md)

Você precisa de direitos de Administrador para criar, editar e excluir perfis de metadados, imagens ou vídeos.

Após criar o perfil de metadados, imagem ou vídeo, atribua-o a uma ou mais pastas que você usa como destino para ativos recém-carregados.

Um conceito importante sobre o uso de perfis no Experience Manager Assets é que eles são atribuídos a pastas. Em um perfil são configurações na forma de perfis de metadados, juntamente com perfis de vídeo ou perfis de imagem. Essas configurações processam o conteúdo de uma pasta junto com qualquer uma de suas subpastas. Portanto, a maneira como você nomeia arquivos e pastas, organiza subpastas e lida com os arquivos dentro dessas pastas tem um impacto significativo na maneira como esses ativos são processados por um perfil.
Ao usar estratégias consistentes e apropriadas de nomenclatura de arquivos e pastas e boas práticas de metadados, você aproveita ao máximo sua coleção de ativos digitais e garante que os arquivos certos sejam processados pelo perfil correto.

>[!NOTE]
>
>O Assets que você move de uma pasta para outra não é reprocessado. Por exemplo, suponha que você tenha uma Pasta 1 com o perfil A atribuído a ela e uma Pasta 2 com o perfil B atribuído a ela. Se você mover ativos da Pasta 1 para a Pasta 2, os ativos movidos manterão o processamento original da Pasta 1.
>
>O mesmo é verdadeiro mesmo quando você move ativos entre duas pastas que têm o mesmo perfil atribuído a elas.

## Reprocessar ativos em uma pasta {#reprocessing-assets}

>[!NOTE]
>
>Aplicável ao *Dynamic Media - Modo Scene7* somente no Experience Manager 6.4.6.0 ou posterior.

Você pode reprocessar ativos em uma pasta que já tenha um perfil de processamento existente que você alterou posteriormente.

Por exemplo, suponha que você criou um perfil de imagem e o atribuiu a uma pasta. Todos os ativos de imagem carregados na pasta automaticamente tinham o perfil de imagem aplicado aos ativos. No entanto, mais tarde, você decide adicionar uma nova taxa de corte inteligente ao perfil. Agora, em vez de selecionar e recarregar os ativos para a pasta novamente, você simplesmente executa o fluxo de trabalho *Reprocessamento do Dynamic Media* <!-- *Scene7: Reprocess Assets* -->.

Você pode executar o fluxo de trabalho de reprocessamento em um ativo cujo processamento falhou pela primeira vez. Dessa forma, mesmo que você não tenha editado um perfil de processamento ou aplicado um perfil de processamento, ainda será possível executar o fluxo de trabalho de reprocessamento em uma pasta de ativos a qualquer momento.

Como opção, é possível ajustar o tamanho do lote do fluxo de trabalho de reprocessamento de um padrão de 50 ativos até 1000 ativos. Ao executar o fluxo de trabalho _Scene7: Reprocessar Assets_ em uma pasta, os ativos são agrupados em lotes e, em seguida, enviados ao servidor do Dynamic Media para processamento. Após o processamento, os metadados de cada ativo em todo o conjunto de lotes são atualizados no Experience Manager. Se o tamanho do lote for grande, você pode enfrentar um atraso no processamento. Ou, se o tamanho do lote for muito pequeno, isso poderá causar muitas viagens de ida e volta para o servidor do Dynamic Media.

Consulte [Ajustar o tamanho do lote do fluxo de trabalho de reprocessamento](#adjusting-load).

>[!NOTE]
>
>Se você estiver executando uma migração em massa de ativos do Dynamic Media Classic para o Experience Manager, será necessário habilitar o agente de replicação de migração no servidor do Dynamic Media. Quando a migração for concluída, desative o agente.
>
>O agente de publicação de migração deve ser desativado no servidor do Dynamic Media para que o fluxo de trabalho de reprocessamento funcione conforme esperado.

<!-- Batch size is the number of assets that are amalgamated into a single IPS (Dynamic Media's Image Production System) job. When you run the Dynamic Media Reprocess workflow, the job is triggered on IPS. The number of IPS jobs that are triggered is based on the total number of assets in the folder, divided by the batch size. For example, suppose you had a folder with 150 assets and a batch size of 50. In this case, three IPS jobs are triggered. The assets are updated when the entire batch size (50 in our example) is processed in IPS. The job then moves onto the next IPS job, and so on, until complete. If you increase the batch size, you may notice a longer delay with assets getting updated. -->

**Para reprocessar ativos em uma pasta:**

1. No Experience Manager, na página Assets, navegue até uma pasta de ativos que tenha um perfil de processamento atribuído a ele e à qual você deseja aplicar o fluxo de trabalho **[!UICONTROL Reprocessamento do Dynamic Media]**,

   As pastas que têm um perfil de processamento já atribuído a elas são indicadas ao exibir do nome do perfil logo abaixo do nome da pasta na Exibição de cartão.

1. Selecione uma pasta.

   * O fluxo de trabalho considera todos os arquivos na pasta selecionada de forma recursiva.
   * Se houver uma ou mais subpastas com ativos na pasta principal selecionada, o fluxo de trabalho reprocessará cada ativo na hierarquia de pastas.
   * Como prática recomendada, evite executar esse fluxo de trabalho em uma hierarquia de pastas com mais de 1000 ativos.

1. Próximo ao canto superior esquerdo da página, na lista suspensa, selecione **[!UICONTROL Linha do tempo]**.
1. Próximo ao canto inferior esquerdo da página, à direita do campo Comentário, selecione o ícone de quilate ( **^** ).

   ![Reprocessar fluxo de trabalho de ativos 1](/help/assets/assets/reprocess-assets1.png)

1. Selecione **[!UICONTROL Iniciar Fluxo de Trabalho]**.
1. Na lista suspensa **[!UICONTROL Iniciar Fluxo de Trabalho]**, escolha **[!UICONTROL Reprocessamento do Dynamic Media]**.
1. (Opcional) No campo de texto **Inserir título do fluxo de trabalho**, digite um nome para o fluxo de trabalho. Você pode usar o nome para fazer referência à instância do workflow, se necessário.

   ![Reprocessar ativos 2](/help/assets/assets/reprocess-assets2.png)

1. Selecione **[!UICONTROL Iniciar]** e **[!UICONTROL Confirmar]**.

   Para monitorar o fluxo de trabalho ou verificar seu progresso, na página principal do console do Experience Manager, selecione **[!UICONTROL Ferramentas]** > **[!UICONTROL Fluxo de trabalho]**. Na página Instâncias do fluxo de trabalho, selecione um fluxo de trabalho. Na barra de menus, selecione **[!UICONTROL Abrir Histórico]**. Você também pode encerrar, suspender ou renomear um workflow selecionado na mesma página Instâncias do workflow.

### Ajustar o tamanho do lote do fluxo de trabalho de reprocessamento {#adjusting-load}

(Opcional) O tamanho de lote padrão no fluxo de trabalho de reprocessamento é de 50 ativos por trabalho. Esse tamanho ideal do lote é determinado pelo tamanho médio do ativo e pelos tipos MIME de ativos nos quais o reprocessamento é executado. Um valor mais alto significa que você tem muitos arquivos em um único trabalho de reprocessamento. Portanto, o banner de processamento permanece nos ativos do Experience Manager por mais tempo. No entanto, se o tamanho médio do arquivo for pequeno - 1 MB ou menos - a Adobe recomenda aumentar o valor para vários 100, mas nunca mais de 1000. Se o tamanho médio do arquivo for grande, como centenas de megabytes, a Adobe recomenda reduzir o tamanho do lote para 10.

**Para ajustar opcionalmente o tamanho do lote do fluxo de trabalho de reprocessamento:**

1. No Experience Manager, selecione **[!UICONTROL Adobe Experience Manager]** para acessar o console de navegação global e, em seguida, selecione o ícone **[!UICONTROL Ferramentas]** (martelo) > **[!UICONTROL Fluxo de trabalho]** > **[!UICONTROL Modelos]**.
1. Na página Modelos de fluxo de trabalho, no Modo de exibição de cartão ou no Modo de exibição de lista, selecione **[!UICONTROL Reprocessamento do Dynamic Media]**.

   ![Página de Modelos de Fluxo de Trabalho com Fluxo de Trabalho de Reprocessamento do Dynamic Media selecionado na Exibição de Cartão](/help/assets/assets-dm/reprocess-assets7.png)

1. Na barra de ferramentas, selecione **[!UICONTROL Editar]**. Uma nova guia do navegador abre a página de modelo de fluxo de trabalho de Reprocessamento do Dynamic Media.
1. Na página de fluxo de trabalho Reprocessamento de Dynamic Media, próximo ao canto superior direito, selecione **[!UICONTROL Editar]** para &quot;desbloquear&quot; o fluxo de trabalho.
1. No fluxo de trabalho, selecione o componente de Carregamento em lote do Scene7 para abrir a barra de ferramentas e selecione **[!UICONTROL Configurar]** na barra de ferramentas.

   ![Componente de carregamento em lote do Scene7](/help/assets/assets-dm/reprocess-assets8.png)

1. Na caixa de diálogo **[!UICONTROL Carregar em lote para o Scene7 - Propriedades da etapa]**, defina o seguinte:
   * Nos campos de texto **[!UICONTROL Título]** e **[!UICONTROL Descrição]**, insira um novo título e descrição para o trabalho, se desejado.
   * Selecione **[!UICONTROL Avanço do manipulador]** se o seu manipulador avançar para a próxima etapa.
   * No campo **[!UICONTROL Tempo limite]**, insira o tempo limite do processo externo (segundos).
   * No campo **[!UICONTROL Período]**, insira um intervalo de sondagem (segundos) para testar a conclusão do processo externo.
   * No **[!UICONTROL Campo de lote]**, insira o número máximo de ativos (50-1000) a serem processados em um trabalho de carregamento de processamento em massa do servidor Dynamic Media.
   * Selecione **[!UICONTROL Avançar no tempo limite]** se desejar avançar quando o tempo limite for atingido. Cancele a seleção se desejar continuar com a caixa de entrada quando o tempo limite for atingido.

   ![Caixa de diálogo Propriedades](/help/assets/assets-dm/reprocess-assets3.png)

1. No canto superior direito da caixa de diálogo **[!UICONTROL Carregamento em lote para o Scene7 - Propriedades da etapa]**, selecione **[!UICONTROL Concluído]**.

1. No canto superior direito da página do modelo de fluxo de trabalho de Reprocessamento do Dynamic Media, selecione **[!UICONTROL Sincronizar]**. Quando você vê **[!UICONTROL Sincronizado]**, o modelo de tempo de execução de fluxo de trabalho foi sincronizado com êxito e está pronto para reprocessar ativos em uma pasta.

   ![Sincronizar o modelo de fluxo de trabalho](/help/assets/assets-dm/reprocess-assets1.png)

1. Feche a guia do navegador que mostra o modelo de fluxo de trabalho de Reprocessamento do Dynamic Media.

<!--1. Return to the browser tab that has the open Workflow Models page, then press **Esc** to exit the selection.
1. In the upper-left corner of the page, select **[!UICONTROL Adobe Experience Manager]** to access the global navigation console, then select the **[!UICONTROL Tools]** (hammer) icon > **[!UICONTROL General > CRXDE Lite]**.
1. In the folder tree on the left side of the CRXDE Lite page, navigate to the following location:

   `/conf/global/settings/workflow/models/scene7_reprocess_assets/jcr:content/flow/reprocess/metaData`

   ![CRXDE Lite](/help/assets/assets/workflow-models9.png)

1. On the right side of the CRXDE Lite page, in the lower portion, enter the following name, type, and value in its respective field:
    * **[!UICONTROL Name]**: `reprocess-batch-size`
    * **[!UICONTROL Type]**: `Long`
    * **[!UICONTROL Value]**: enter a default value (50-1000) for the batch size
1. In the lower-right corner, select **[!UICONTROL Add]**. The new property appears as the following:

    ![Saving the new property](/help/assets/assets/workflow-models10.png)

1. On the menu bar of the CRXDE Lite page, select **[!UICONTROL Save All]**.
1. In the upper-left corner of the page, select **[!UICONTROL CRXDE Lite]** to return to the main Experience Manager console
1. Repeat steps 1-7 to re-synchronize the new batch size to the Dynamic Media Reprocess workflow model.-->
