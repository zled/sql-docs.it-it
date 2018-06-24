---
title: Esplorazione di un modello Naive Bayes | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9160b48-3beb-439c-9694-f084e1afa625
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 36031bb080ff80c14a4f91bca102bd859df1f539
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054669"
---
# <a name="browsing-a-naive-bayes-model"></a>Esplorazione di un modello Naïve Bayes
  Quando si apre un modello Naïve Bayes utilizzando **Sfoglia**, il modello viene visualizzato in un visualizzatore interattivo con quattro riquadri diversi. Il visualizzatore consente di esplorare le correlazioni e ottenere informazioni sul modello e sui dati sottostanti.  
  
-   [Rete di dipendenze](#bkmk_DepNet)  
  
-   [Profili attributo](#bkmk_AttProf)  
  
-   [Caratteristiche attributo](#bkmk_AttChar)  
  
-   [Analisi discriminante attributi](#bkmk_AttDisc)  
  
##  <a name="BKMK_Tabs"></a> Esplorare il modello  
 Lo scopo del visualizzatore è consentire di esplorare l'interazione tra gli attributi di input e output (input e variabili dipendenti) che sono stati individuati dal modello [!INCLUDE[msCoName](../includes/msconame-md.md)] Naïve Bayes.  
  
 Se si desidera sperimentare il Visualizzatore Naïve Bayes, utilizzare il [classificare guidata &#40;aggiuntivi di Data Mining per Excel&#41; ](classify-wizard-data-mining-add-ins-for-excel.md) guidata nella barra multifunzione Data Mining, fare clic sui **avanzate** opzione e modificare l'algoritmo da utilizzare l'algoritmo Naïve Bayes  
  
 Per questi esempi, abbiamo utilizzato i dati di origine della cartella di lavoro di esempio e raggruppata la colonna **Yearly Income**, in cinque gruppi di reddito, da **molto bassa** al **molto elevato**. Nel modello Naïve Bayes sono stati quindi analizzati i fattori correlati a ogni categoria di reddito.  
  
###  <a name="bkmk_DepNet"></a> Rete di dipendenze  
 È la prima finestra si userà il **rete di dipendenze**. Vengono visualizzati immediatamente gli input strettamente correlati al risultato selezionato.  
  
 ![rete di dipendenze in Visualizzatore Naive Bayes](media/dm13-nb.gif "rete di dipendenze in Visualizzatore Naive Bayes")  
  
##### <a name="explore-the-dependency-network"></a>Esplorare la rete di dipendenze  
  
1.  In primo luogo, fare clic sul risultato di destinazione **Yearly Income**, rappresentato come un nodo nel grafico.  
  
     I nodi evidenziati che circondano la variabile di destinazione sono quelli correlati statisticamente con questo risultato. Utilizzare la legenda nella parte inferiore del visualizzatore per comprendere la natura della relazione.  
  
2.  Fare clic sul dispositivo di scorrimento a sinistra del visualizzatore e trascinarlo verso il basso.  
  
     Questo controllo consente di filtrare le variabili indipendenti, in base ai livelli di attendibilità delle dipendenze. Quando si trascina il dispositivo di scorrimento verso il basso, nel grafico restano solo i collegamenti più attendibili.  
  
3.  Dopo aver filtrato il grafico, fare clic sul pulsante **copia parte visibile del grafico**. Selezionare quindi un foglio di lavoro in Excel e premere CTRL+V.  
  
     Questa opzione consente di copiare la vista selezionata, inclusi i filtri e l'evidenziazione.  
  
 [Torna all'inizio](#BKMK_Tabs)  
  
###  <a name="bkmk_AttProf"></a> Profili attributo  
 Il **profili attributo** windows offre un'indicazione visiva del modo in cui tutte le altre variabili sono correlate ai singoli risultati.  
  
##### <a name="explore-the-profiles"></a>Esplorazione del profili  
  
1.  Per nascondere alcuni valori in modo da poter confrontare più facilmente i risultati, fare clic sull'intestazione di colonna e trascinarla sotto un'altra colonna.  
  
     ![attributo profili in Visualizzatore Naive Bayes](media/dm13-nb-attprof.gif "attributo profili in Visualizzatore Naive Bayes")  
  
2.  Fare clic su qualsiasi cella per visualizzare la distribuzione dei valori di **legenda Data Mining**.  
  
     Poiché gli attributi associati ai differenti risultati vengono rappresentati visivamente, è facile individuare correlazioni interessanti, ad esempio i redditi sono distribuiti per area.  
  
3.  Per ottenere i dati sottostanti in questa vista, fare clic su **copia in Excel**. Viene generata una tabella in un nuovo foglio di lavoro in cui vengono visualizzate le correlazioni tra singoli attributi e risultati. In questa tabella di Excel è possibile nascondere o filtrare facilmente le colonne.  
  
 [Torna all'inizio](#BKMK_Tabs)  
  
###  <a name="bkmk_AttChar"></a> Caratteristiche attributo  
 Il **caratteristiche attributo** Vista è utile per un esame di una determinata variabile di risultato e fattori determinanti.  
  
 ![attributo caratteristiche in Visualizzatore Naive Bayes](media/dm13-nb-viewer.gif "attributo caratteristiche in Visualizzatore Naive Bayes")  
  
##### <a name="explore-the-attribute-characteristics"></a>Esplorazione delle caratteristiche degli attributi  
  
1.  Fare clic su **valore** e selezionare un elemento dal **valore**.  
  
     Quando si seleziona un risultato di destinazione, il grafico viene aggiornato per visualizzare i fattori associati in modo più sicuro al risultato, ordinati in base alla priorità.  
  
     Si noti che se si crea un modello utilizzando il [analizza fattori di influenza chiave &#40;strumenti di analisi tabelle per Excel&#41; ](analyze-key-influencers-table-analysis-tools-for-excel.md) opzione, è possibile creare modelli che includono più di un attributo stimabile. Tuttavia, tutte le altre procedure guidate nei componenti aggiuntivi Data mining limitano l'utente a un attributo stimabile.  
  
2.  Fare clic su **copia in Excel** per creare una tabella, in un nuovo foglio di lavoro elencati i punteggi per tutti gli attributi correlati al risultato di destinazione selezionato.  
  
 [Torna all'inizio](#BKMK_Tabs)  
  
###  <a name="bkmk_AttDisc"></a> Analisi discriminante attributi  
 Il **analisi discriminante attributi** visualizzazione consente di confrontare due risultati oppure un risultato rispetto a tutti gli altri risultati.  
  
 ![attributo dell'analisi discriminante in Visualizzatore Naive Bayes](media/dm13-nb-attdisc.gif "attributo analisi discriminante in Visualizzatore Naive Bayes")  
  
##### <a name="explore-attribute-discrimination"></a>Esplorazione dell'analisi discriminante attributi  
  
1.  Utilizzare i controlli **valore 1** e **valore 2**, selezionare i risultati che si desidera confrontare.  
  
     Ad esempio, in questo modello sono disponibili alcuni attributi interessanti nel gruppo di reddito basso, quindi si sceglie il gruppo di reddito più basso nel primo elenco a discesa e scelto **tutti gli altri stati** nel secondo elenco a discesa.  
  
     Gli attributi vengono ordinati in ordine di importanza (calcolata in base ai dati di training). Pertanto, occupazione è il fattore più strettamente correlato al reddito (almeno per questo gruppo di destinazione).  
  
     Per visualizzare le cifre esatte, fare clic sulla barra colorata e visualizza i **legenda Data Mining**.  
  
2.  Si noti che anche i redditi inferiori sono correlati con l'area Europa.  
  
     Il modello Naïve Bayes non supporta il drill-down; tuttavia, se si desidera esaminare i case associati a questo gruppo di risultati, è possibile utilizzare una query. Per informazioni sulle query in questo tipo di modello, vedere [Naive Bayes Model Query Examples](data-mining/naive-bayes-model-query-examples.md).  
  
 [Torna all'inizio](#BKMK_Tabs)  
  
## <a name="see-also"></a>Vedere anche  
 [Esplorazione di modelli in Excel &#40;componenti aggiuntivi Data Mining di dati SQL Server&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  