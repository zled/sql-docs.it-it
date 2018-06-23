---
title: Creazione di una struttura di modello di Data Mining Targeted Mailing (esercitazione di base di Data Mining) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a9c67f29-0c47-4a5a-862b-db0f5213c2c9
caps.latest.revision: 54
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3f0a8632df2009846d8b17d956c750ae12356829
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312479"
---
# <a name="creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial"></a>Creazione di una struttura del modello di data mining Targeted Mailing (Esercitazione di base sul data mining)
  Il primo passaggio nella creazione di uno scenario relativo al mailing diretto consiste nell'utilizzo di Creazione guidata modello di data mining in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] per creare una nuova struttura e un nuovo modello di data mining basato su un albero delle decisioni.  
  
 In questa attività si verrà imposta una nuova struttura di data mining e aggiungere un modello di data mining iniziale in base il [!INCLUDE[msCoName](../includes/msconame-md.md)] algoritmo Decision Trees. Per creare la struttura, verranno innanzitutto selezionate le tabelle e le viste, quindi si identificheranno le colonne da utilizzare rispettivamente per il training e per il testing.  
  
### <a name="to-create-a-mining-structure-for-the-targeted-mailing-scenario"></a>Per creare una struttura di data mining per lo scenario relativo al mailing diretto  
  
1.  In Esplora soluzioni fare doppio clic su **strutture di Data Mining** e selezionare **nuova struttura di Data Mining** per avviare Creazione guidata di Data Mining.  
  
2.  Nella pagina iniziale **Creazione guidata modello di data mining** fare clic su **Avanti**.  
  
3.  Nel **Selezione metodo di definizione** verificare che **da esistente database relazionale o data warehouse** sia selezionata e quindi fare clic su **Avanti**.  
  
4.  Nel **creare la struttura di Data Mining** nella pagina **tecnica di data mining si desidera utilizzare?**, selezionare **Microsoft Decision Trees**.  
  
    > [!NOTE]  
    >  Se viene visualizzato un avviso relativo al mancato rilevamento di algoritmi di data mining, è possibile che le proprietà del progetto non siano state configurate correttamente. Questo avviso viene visualizzato quando il progetto tenta di recuperare un elenco di algoritmi di data mining dal server di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] e quest'ultimo non viene rilevato. Per impostazione predefinita [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] utilizzerà **localhost** del server. Se si utilizza un'istanza diversa o un'istanza denominata, è necessario modificare le proprietà del progetto. Per altre informazioni, vedere [creazione di un progetto di Analysis Services &#40;Basic Data Mining Tutorial&#41;](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md).  
  
5.  Scegliere **Avanti**.  
  
6.  Nel **selezione vista origine dati** nella pagina di **viste origine dati disponibili** riquadro, selezionare **Targeted Mailing**. È possibile fare clic **esplorare** per visualizzare le tabelle nella vista origine dati e quindi fare clic su **Chiudi** per tornare alla procedura guidata.  
  
7.  Scegliere **Avanti**.  
  
8.  Nel **impostazione tipi di tabelle** pagina, selezionare la casella di controllo nel **Case** colonna vTargetMail per utilizzarlo come tabella del case, quindi fare clic su per **Avanti**. La tabella ProspectiveBuyer verrà utilizzata in un secondo momento per il testing. Per il momento, ignorarla.  
  
9. Nel **specificano i dati di Training** pagina, sarà possibile identificare almeno una colonna stimabile, una colonna chiave e una colonna di input per il modello. Selezionare la casella di controllo di **stimabile** colonna il **BikeBuyer** riga.  
  
    > [!NOTE]  
    >  Si noti il messaggio di avviso nella parte inferiore della finestra. Non sarà in grado di passare alla pagina successiva sarà necessario selezionare almeno un **Input** e una **stimabile** colonna.  
  
10. Fare clic su **Suggerisci** per aprire la **Suggerisci colonne correlate** finestra di dialogo.  
  
     Il **Suggerisci** pulsante è abilitato ogni volta che è stato selezionato almeno un attributo stimabile. Il **Suggerisci colonne correlate** finestra di dialogo sono elencate le colonne che sono più strettamente correlate alla colonna stimabile e gli attributi per la correlazione con l'attributo stimabile. Le colonne che presentano una correlazione significativa (confidenza maggiore del 95%) vengono selezionate automaticamente per essere incluse nel modello.  
  
     Rivedere i suggerimenti e quindi fare clic su **annullare** toignore i suggerimenti.  
  
    > [!NOTE]  
    >  Se si fa clic su **OK**, descritto in tutti i suggerimenti verranno contrassegnati come colonne di input nella procedura guidata. Se si accetta solo una parte dei suggerimenti, è necessario modificare i valori manualmente.  
  
11. Verificare che la casella di controllo il **chiave** viene selezionata nella colonna il **CustomerKey** riga.  
  
    > [!NOTE]  
    >  Se la tabella di origine nella vista origine dati indica una chiave, Creazione guidata modello di data mining sceglierà automaticamente tale colonna come chiave per il modello.  
  
12. Selezionare le caselle di controllo nel **Input** colonna nelle righe seguenti. È possibile selezionare più colonne evidenziando un intervallo di celle e premendo CTRL mentre si seleziona una casella di controllo.  
  
    -   **Età**  
  
    -   **CommuteDistance**  
  
    -   **EnglishEducation**  
  
    -   **EnglishOccupation**  
  
    -   **Gender**  
  
    -   **GeographyKey**  
  
    -   **HouseOwnerFlag**  
  
    -   **MaritalStatus**  
  
    -   **NumberCarsOwned**  
  
    -   **NumberChildrenAtHome**  
  
    -   **Region**  
  
    -   **TotalChildren**  
  
    -   **YearlyIncome**  
  
13. Nella colonna all'estrema sinistra della pagina selezionare le caselle di controllo relative alle righe seguenti.  
  
    -   **AddressLine1**  
  
    -   **AddressLine2**  
  
    -   **DateFirstPurchase**  
  
    -   **EmailAddress**  
  
    -   **FirstName**  
  
    -   **LastName**  
  
     Assicurarsi che queste righe contengano segni di spunta solo nella colonna sinistra. Le colonne corrispondenti verranno aggiunte alla struttura ma non verranno incluse nel modello. Tuttavia, dopo la compilazione del modello, saranno disponibili per il drill-through e il testing. Per ulteriori informazioni sul drill-through, vedere [query drill-through &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)  
  
14. Scegliere **Avanti**.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Specifica il tipo di dati e il tipo di contenuto &#40;esercitazione di base di Data Mining&#41;](../../2014/tutorials/specifying-the-data-type-and-content-type-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Specificare i tipi di tabella &#40;Creazione guidata di Data Mining&#41;](../../2014/analysis-services/specify-table-types-data-mining-wizard.md)   
 [Progettazione di Data Mining](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Algoritmo Microsoft Decision Trees](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)  
  
  