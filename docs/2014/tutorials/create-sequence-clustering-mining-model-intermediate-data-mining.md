---
title: Creazione di una struttura modello di Data Mining (esercitazione intermedia di Data Mining) Sequence Clustering | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e9339227-6c2e-4c4b-8be2-8c1960bc4a8d
caps.latest.revision: 40
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 09aaac50873d6c4c63b46fdf37dd7ee854000886
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312699"
---
# <a name="creating-a-sequence-clustering-mining-model-structure-intermediate-data-mining-tutorial"></a>Creazione di una struttura del modello di data mining Sequence Clustering (Esercitazione intermedia sul data mining)
  Il primo passaggio nella creazione di un modello di data mining Sequence Clustering consiste nell'utilizzo della Creazione guidata modello di data mining per la creazione di una nuova struttura di data mining e di un modello di data mining sulla base dell'algoritmo [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering.  
  
 Verrà utilizzata la stessa vista origine dati impiegata per l'analisi degli acquisti, ma si aggiungerà una colonna che contiene l'identificatore `sequence`. In questo scenario la sequenza indica l'ordine in cui il cliente ha incluso gli articoli tra gli acquisti.  
  
 Verranno anche aggiunte alcune colonne utilizzate in uno dei modelli per raggruppare i clienti in base ai dati demografici.  
  
### <a name="to-create-a-sequence-clustering-structure-and-model"></a>Per creare una struttura e un modello di data mining Sequence Clustering  
  
1.  In Esplora soluzioni [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], fare doppio clic su **strutture di Data Mining** e selezionare **nuova struttura di Data Mining**.  
  
2.  Nella pagina iniziale **Creazione guidata modello di data mining** fare clic su **Avanti**.  
  
3.  Nel **Selezione metodo di definizione** verificare che **da esistente database relazionale o data warehouse** sia selezionata e quindi fare clic su **Avanti**.  
  
4.  Nel **creare la struttura di Data Mining** verificare che l'opzione **Crea struttura di data mining con un modello di data mining** sia selezionata. Successivamente, fare clic sull'elenco a discesa l'opzione **tecnica di data mining si desidera utilizzare?** e selezionare **Microsoft Sequence Clustering**. Scegliere **Avanti**.  
  
     Il **selezione vista origine dati** verrà visualizzata la pagina. Sotto **viste origine dati disponibili**, selezionare `Orders`.  
  
     Orders è la stessa vista origine dati utilizzata per lo scenario di analisi degli acquisti. Se non è stato creato tale vista origine dati, vedere [aggiunta di una vista origine dati con tabelle nidificate &#40;esercitazione intermedia sul Data Mining Data&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md).  
  
5.  Scegliere **Avanti**.  
  
6.  Nel **impostazione tipi di tabelle** pagina, selezionare il **Case** casella di controllo accanto al **vAssocSeqOrders** tabella, quindi selezionare il **Nested** casella di controllo accanto ai **vAssocSeqLineItems** tabella. Scegliere **Avanti**.  
  
    > [!NOTE]  
    >  Se si verifica un errore quando si seleziona il **Case** oppure **Nested** caselle di controllo, è possibile che il join nella vista origine dati non è corretto. La tabella nidificata **vAssocSeqLineItems**, deve essere connessa alla tabella del case, **vAssocSeqOrders,** tramite un join molti-a-uno. È possibile modificare la relazione facendo clic con il pulsante destro del mouse sulla linea di join e invertendo la direzione del join. Per altre informazioni, vedere [Create o finestra di dialogo Modifica relazione &#40;Analysis Services - dati multidimensionali&#41;](../../2014/analysis-services/create-or-edit-relationship-dialog-box-analysis-services-multidimensional-data.md).  
  
7.  Nel **specificano i dati di Training** pagina, scegliere le colonne per l'utilizzo nel modello selezionando una casella di controllo come segue:  
  
    -   **IncomeGroup** selezionare il **Input** casella di controllo.  
  
         Questa colonna contiene interessanti informazioni sui clienti che è possibile utilizzare per il clustering. Verranno utilizzate nel primo modello e ignorate nel secondo modello.  
  
    -   **OrderNumber** selezionare il `Key` casella di controllo.  
  
         Questo campo sarà utilizzato come identificatore per la tabella del case o `Key`. In generale, è consigliabile non utilizzare mai il campo chiave della tabella del case come input, perché la chiave contiene valori univoci che non sono utili per il clustering.  
  
    -   **Area** selezionare il **Input** casella di controllo.  
  
         Questa colonna contiene interessanti informazioni sui clienti che è possibile utilizzare per il clustering. Verranno utilizzate nel primo modello e ignorate nel secondo modello.  
  
    -   **LineNumber** selezionare il `Key` e **Input** caselle di controllo.  
  
         Il **LineNumber** campo verrà utilizzato come identificatore per la tabella nidificata o `Sequence Key`. La chiave di una tabella nidificata deve essere sempre utilizzata per l'input.  
  
    -   **Modello** selezionare il **Input** e **stimabile** caselle di controllo.  
  
     Verificare che le selezioni siano corrette e quindi fare clic su **successivo**.  
  
8.  Nel **di specificare le colonne tipo di contenuto e dati** pagina, verificare che la griglia contenga le colonne, i tipi di contenuto e tipi di dati indicati nella tabella seguente e quindi fare clic su **successivo**.  
  
    |Tabelle/Colonne|Tipo di contenuto|Tipo di dati|  
    |---------------------|------------------|---------------|  
    |IncomeGroup|Discrete|Text|  
    |OrderNumber|Key|Text|  
    |Region|Discrete|Text|  
    |vAssocSeqLineItems|||  
    |Line Number|Key Sequence|Long|  
    |Modello|Discrete|Text|  
  
9. Nel **crea Set di Testing** pagina, modificare il **percentuale di dati per il testing** su 20, quindi fare clic su **Avanti**.  
  
10. Nel **Completamento procedura guidata** pagina per il **nome struttura di Data Mining**, tipo `Sequence Clustering with Region`.  
  
11. Per il **nome del modello di Data Mining**, tipo `Sequence Clustering with Region`.  
  
12. Controllare la **Consenti drill-through** e quindi scegliere **fine**.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [L'elaborazione del modello Sequence Clustering](../../2014/tutorials/processing-the-sequence-clustering-model.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Progettazione di Data Mining](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Algoritmo Microsoft Sequence Clustering](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)  
  
  