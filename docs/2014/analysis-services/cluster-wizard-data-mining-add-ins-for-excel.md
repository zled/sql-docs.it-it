---
title: Procedura guidata (componenti aggiuntivi Data Mining per Excel Data) del cluster | Documenti Microsoft
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- clustering [data mining]
ms.assetid: 85b25625-a7ab-4960-9f9c-df22e8ecae37
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 911d8a69ea934063fe8be31b7980e8c87ff2f7e3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064812"
---
# <a name="cluster-wizard-data-mining-add-ins-for-excel"></a>Procedura guidata Cluster (componenti aggiuntivi Data mining per Excel)
  ![Creazione guidata cluster sulla barra multifunzione Data Mining](media/dmc-cluster.gif "guidata Cluster sulla barra multifunzione Data Mining")  
  
 La procedura guidata Cluster consente di compilare un modello che rileva le righe che condividono gruppi e caratteristiche simili per ottimizzare la distanza tra i gruppi. Questa procedura guidata è utile per trovare i modelli in qualsiasi tipo di dati.  
  
 La procedura guidata Cluster utilizza l'algoritmo Microsoft Clustering e può essere ampiamente personalizzata. Utilizza i dati esistenti di una tabella di Excel, un intervallo di Excel o una query di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Un'analoga funzionalità è disponibile per il [rileva categorie](detect-categories-table-analysis-tools-for-excel.md) degli strumenti, disponibili in strumenti di analisi tabelle per Excel. Tuttavia, lo strumento Rileva categorie non può essere personalizzato e deve utilizzare i dati nelle tabelle di Excel.  
  
## <a name="using-the-cluster-wizard"></a>Utilizzo della procedura guidata Cluster  
  
1.  Nella barra multifunzione Data Mining, fare clic su **Cluster**, quindi fare clic su **successivo**.  
  
2.  Nel **selezione dati di origine** pagina, selezionare una tabella di Excel o un intervallo. Oppure specificare un'origine dati esterna.  
  
     Se si utilizza un'origine dati esterna, è possibile creare viste personalizzate o incollarle nel testo della query personalizzata e salvare il set di dati come origine dati di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
3.  Nel **Clustering** pagina, è possibile personalizzare la modalità di compilazione del modello.  
  
    -   Per **numero di segmenti**, è possibile indicare alla procedura guidata per creare un numero fisso di categorie o lasciare che venga rilevato automaticamente il numero ottimale di raggruppamenti.  
  
    -   Esaminare l'elenco di colonne il **colonne di Input** elencare e deselezionare le colonne che non sono utili nella creazione di modelli. Le colonne che è necessario escludere includono numeri ID, nomi di clienti e così via.  
  
4.  Facoltativamente, fare clic su **parametri** per modificare i parametri dell'algoritmo e personalizzare il comportamento del modello di clustering.  
  
5.  Nel **suddividere i dati in set di training e set di testing** , specificare la quantità di dati da riservare per il testing. Il resto viene sempre utilizzato per il training del modello.  
  
     L'impostazione predefinita è il 30% dei dati di testing e il 70% dei dati di training.  
  
6.  Nel **fine** pagina, fornire un nome descrittivo per il set di dati e il modello e impostare le opzioni seguenti che consentono di controllare l'utilizzo del modello finito:  
  
    -   **Esplora modello**. Quando questa opzione è selezionata, non appena la procedura guidata al termine dell'elaborazione del modello, questo viene aperto un **Sfoglia** finestra che consentono di esplorare i risultati. Il contenuto del visualizzatore dipende dal tipo di modello compilato. Per altre informazioni, vedere [esplorazione di un modello di Clustering](browsing-a-clustering-model.md).  
  
    -   **Consenti drill-through**. Selezionare questa opzione per visualizzare i dati sottostanti dal modello finito. Questa opzione è disponibile solo se si compila un modello Decision Trees.  
  
    -   **Usa modello temporaneo**. Se si seleziona questa opzione, il modello non verrà salvato nel server. I modelli temporanei vengono eliminati quando si chiude Excel.  
  
## <a name="more-about-clustering-models"></a>Ulteriori informazioni sui modelli di clustering  
 È possibile modificare l'algoritmo di clustering utilizzato da questa procedura guidata facendo clic **avanzate** e utilizzando il **i parametri dell'algoritmo** finestra di dialogo.  
  
 L'algoritmo Microsoft Clustering fornisce i metodi di clustering seguenti:  
  
-   K-medie, scalabile o non scalabile.  
  
-   Expectation Maximization (EM), scalabile o non scalabile.  
  
 È anche possibile utilizzare il parametro CLUSTER_SEED per controllare il valore iniziale e assicurarsi che i modelli ripetuti che utilizzano lo stesso set di dati producano gli stessi risultati.  
  
### <a name="requirements"></a>Requisiti  
 Per utilizzare la procedura guidata Cluster, è necessario essere connessi a un database di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Per altre informazioni, vedere [Connetti ai dati di origine &#40;Client di Data Mining per Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un modello di Data Mining](creating-a-data-mining-model.md)   
 [Rileva categorie &#40;strumenti di analisi tabelle per Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)  
  
  