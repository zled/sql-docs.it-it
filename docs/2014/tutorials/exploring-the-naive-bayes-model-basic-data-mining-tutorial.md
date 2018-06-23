---
title: Esplorazione del modello Naive Bayes (esercitazione di base di Data Mining) | Documenti Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b06708d5-4477-4a51-bf8d-0b1e3c1f9ebb
caps.latest.revision: 25
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ce01a9d352513e4b69bb4a9e735f30cc657a9c97
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/21/2018
ms.locfileid: "36311859"
---
# <a name="exploring-the-naive-bayes-model-basic-data-mining-tutorial"></a>Esplorazione del modello Naive Bayes (Esercitazione di base sul data mining)
  Il [!INCLUDE[msCoName](../includes/msconame-md.md)] algoritmo Naive Bayes fornisce diversi metodi per la visualizzazione dell'interazione tra biciclette e gli attributi di input.  
  
 Il [!INCLUDE[msCoName](../includes/msconame-md.md)] Visualizzatore Naive Bayes sono disponibili le schede seguenti per l'esplorazione dei modelli di data mining Naive Bayes:  
  
 
  
##  <a name="DependencyNetwork"></a> Rete di dipendenze  
 Il **rete di dipendenze** tab funziona esattamente come il **rete di dipendenze** per la scheda di [!INCLUDE[msCoName](../includes/msconame-md.md)] Tree Viewer. Ogni nodo nel visualizzatore rappresenta un attributo e le righe tra i nodi rappresentano le relazioni. Nel visualizzatore è possibile osservare tutti gli attributi che influiscono sullo stato dell'attributo stimabile, ovvero Bike Buyer.  
  
#### <a name="to-explore-the-model-in-the-dependency-network-tab"></a>Per esplorare il modello nella scheda Rete di dipendenze  
  
1.  Utilizzare la **modello di Data Mining** nella parte superiore dell'elenco il **visualizzatore modello di Data Mining** tab per passare al `TM_NaiveBayes` modello.  
  
2.  Usare la **Visualizzatore** elenco per passare alla **visualizzatore Microsoft Naive Bayes**.  
  
3.  Fare clic sul `Bike Buyer` nodo per identificare le relative dipendenze.  
  
     L'ombreggiatura rosa indica che tutti gli attributi influenzano l'acquisto di biciclette.  
  
4.  Regolare il dispositivo di scorrimento per identificare l'attributo più influente.  
  
     Spostando verso il basso il dispositivo di scorrimento rimangono visibili solo gli attributi che incidono maggiormente sulla colonna [Bike Buyer]. Se si sposta il dispositivo di scorrimento è possibile individuare che alcuni degli attributi più influenti sono il numero di automobili possedute, la distanza dal luogo di lavoro e il numero complessivo di figli.  
 
  
##  <a name="AttributeProfiles"></a> Profili attributo  
 Il **profili attributo** scheda descrive come i diversi stati di attributi di input sul risultato dell'attributo stimabile.  
  
#### <a name="to-explore-the-model-in-the-attribute-profiles-tab"></a>Per esplorare il modello nella scheda Profili attributo  
  
1.  Nel **stimabile** , verificare che `Bike Buyer` sia selezionata.  
  
2.  Se il **legenda Data Mining** blocca la visualizzazione del **profili dell'attributo**, spostare la legenda.  
  
3.  Nel **istogramma** barre, quindi selezionare **5**.  
  
     Nel modello utilizzato in questo esempio 5 è il numero massimo di stati per ogni singola variabile.  
  
     Gli attributi che influiscono sullo stato di questo attributo stimabile vengono elencati in combinazione con i valori di ogni stato degli attributi di input e la loro distribuzione in ogni stato dell'attributo stimabile.  
  
4.  Nel **attributi** colonna, trovare **Number Cars Owned**.  Si notino le differenze negli istogrammi tra gli acquirenti di biciclette (la colonna con etichetta 1) e i non acquirenti (la colonna con etichetta 0). È molto più probabile che una bicicletta venga acquistata da una persona priva di automobili o che ne possiede una sola.  
  
5.  Fare doppio clic sui **Number Cars Owned** cella degli acquirenti di biciclette colonna (colonna con etichettata 1).  
  
     Il **legenda Data Mining** consente di visualizzare una visualizzazione più dettagliata.  
  
  
##  <a name="AttributeCharacteristics"></a> Caratteristiche attributo  
 Con il **caratteristiche attributo** scheda, è possibile selezionare un attributo e un valore per verificare la frequenza con cui i valori per altri attributi vengono visualizzati nei casi di valore selezionato.  
  
#### <a name="to-explore-the-model-in-the-attribute-characteristics-tab"></a>Per esplorare il modello nella scheda Caratteristiche attributo  
  
1.  Nel **attributo** elenco, verificare che `Bike Buyer` sia selezionata.  
  
2.  Impostare il **valore** alla **1**.  
  
     Nel visualizzatore si osserverà che è più probabile che una bicicletta venga acquistata dai clienti senza figli, che abitano a breve distanza dal luogo di lavoro e che vivono nell'area dell'America del nord.  
  
  
##  <a name="AttributeDiscrimination"></a> Analisi discriminante attributi  
 Con il **analisi discriminante attributi** scheda, è possibile esaminare la relazione tra due valori discreti dell'acquisto di biciclette e altri valori di attributo. Poiché il `TM_NaiveBayes` modello ha solo due stati, 1 e 0, non è necessario apportare modifiche al visualizzatore.  
  
 Nel visualizzatore è possibile osservare che le persone che non possiedono un'automobile tendenzialmente acquistano biciclette, mentre le persone che possiedono due automobili in genere non ne acquistano.  
  
## <a name="related-tasks"></a>Related Tasks  
 Per esplorare gli altri modelli di data mining, vedere gli argomenti seguenti.  
  
-   [Esplorazione del modello di albero delle decisioni &#40;esercitazione di base di Data Mining&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [Esplorazione del modello di Clustering &#40;esercitazione di base di Data Mining&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Lezione successiva  
 [Lezione 5: Testare i modelli &#40;esercitazione di base di Data Mining&#41;](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>Attività precedente della lezione  
 [Esplorazione del modello di Clustering &#40;esercitazione di base di Data Mining&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare un modello utilizzando il visualizzatore Microsoft Naive Bayes](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)   
 [Scheda Analisi discriminante tra dell'attributo &#40;visualizzatore modello di Data Mining&#41;](../../2014/analysis-services/attribute-discrimination-tab-mining-model-viewer.md)   
 [Attributo profili della scheda &#40;visualizzatore modello di Data Mining&#41;](../../2014/analysis-services/attribute-profiles-tab-mining-model-viewer.md)   
 [Scheda Caratteristiche attributo &#40;visualizzatore modello di Data Mining&#41;](../../2014/analysis-services/attribute-characteristics-tab-mining-model-viewer.md)   
 [Scheda rete di dipendenze &#40;visualizzatore modello di Data Mining&#41;](../../2014/analysis-services/dependency-network-tab-mining-model-viewer.md)  
  
  