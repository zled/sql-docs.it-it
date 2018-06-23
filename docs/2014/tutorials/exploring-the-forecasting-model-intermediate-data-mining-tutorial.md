---
title: Esplorazione del modello di previsione (esercitazione intermedia di Data Mining) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0a00f409-050f-4b92-9763-ba31a6aa3052
caps.latest.revision: 52
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 6f6cffb56dd4ef4a9df6618ce126e2b3d0340640
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/21/2018
ms.locfileid: "36313039"
---
# <a name="exploring-the-forecasting-model-intermediate-data-mining-tutorial"></a>Esplorazione del modello di previsione (Esercitazione intermedia sul data mining)
  Dopo aver creato il modello di data mining forecasting, è possibile esplorare i risultati utilizzando il **visualizzatore modello di Data Mining** scheda Progettazione modelli di Data Mining. Il [!INCLUDE[msCoName](../includes/msconame-md.md)] Visualizzatore Time Series contiene due schede: **grafici** e **modello**.  
  
 È inoltre possibile utilizzare Microsoft Generic Content Tree Viewer con tutti i modelli. Ogni vista presenta un'immagine leggermente diversa delle informazioni nel modello Time Series.  
  
-   [Scheda grafici](#bkmk_Charts)  
  
-   [Scheda modello](#bkmk_Model)  
  
-   [Microsoft Generic Content Tree Viewer](#bkmk_Content)  
  
##  <a name="bkmk_Charts"></a> Scheda grafici  
 Il **grafici** scheda della finestra di [!INCLUDE[msCoName](../includes/msconame-md.md)] Visualizzatore Time Series Mostra graficamente ciascuna delle serie, inclusi i dati cronologici e stime. Ogni linea del grafico della serie temporale rappresenta una combinazione univoca di prodotto, area e attributo stimabile.  
  
 Nella legenda a destra del visualizzatore vengono elencate le serie temporali disponibili, in base alle selezioni nell'elenco a discesa. È possibile scegliere le serie temporali da visualizzare nel grafico selezionando o deselezionando le caselle di controllo.  
  
 È inoltre possibile modificare le opzioni di visualizzazione, ad esempio i colori utilizzati per ogni serie temporale, o decidere se visualizzare i valori in qualsiasi punto del grafico.  
  
#### <a name="to-select-a-time-series"></a>Per selezionare una serie temporale  
  
1.  Fare clic sui **grafici** scheda della finestra di **visualizzatore modello di Data Mining** scheda, se non è visibile.  
  
2.  Fare clic sull'elenco a discesa a destra della vista del grafico e selezionare tutte le caselle di controllo. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     A questo punto il grafico dovrebbe contenere 24 linee delle serie.  
  
3.  Nelle caselle di controllo a destra del grafico deselezionare le caselle per nascondere temporaneamente le linee per tutte le serie basate sull'importo.  
  
     A questo punto deselezionare le caselle di controllo relative alle biciclette R750 e R250.  
  
     Il grafico conterrà solo le sei linee delle serie seguenti, in modo da consentire di confrontare più facilmente le tendenze per le biciclette M200 e T1000.  
  
    -   **M200 Europe: Quantity**  
  
    -   **M200 North America: Quantity**  
  
    -   **M200 Pacific: Quantity**  
  
    -   **T1000 Europe: Quantity**  
  
    -   **T1000 North America: Quantity**  
  
    -   **T1000 Pacific: Quantity**  
  
 ![Stima delle quantità M200 e T1000 serie](../../2014/tutorials/media/6series-defaultforecasting.gif "serie stima delle quantità M200 e T1000")  
  
 Nel grafico riprodotto in questo visualizzatore sono inclusi sia i dati cronologici che quelli stimati. Ai dati stimati viene applicata un'ombreggiatura per distinguerli dai dati cronologici. Per rendere più semplice il confronto tra serie diverse, è inoltre possibile modificare i colori associati a ogni linea nel grafico. Per altre informazioni, vedere [Modificare i colori usati nei visualizzatori data mining](../../2014/analysis-services/data-mining/change-the-colors-used-in-the-data-mining-viewer.md).  
  
 Dalle linee di tendenza è possibile vedere che in genere le vendite totali per tutte le aree sono in aumento e raggiungono il periodo di picco ogni anno nel mese di dicembre. Dal grafico è inoltre possibile vedere che i dati per la bicicletta T1000 hanno inizio molto più tardi dei dati per le altre serie di prodotti. Ciò è dovuto al fatto che si tratta di un prodotto più nuovo, ma essendo questa serie basata su una quantità di dati molto inferiore, è possibile che le stime non siano accurate.  
  
 Per impostazione predefinita, vengono visualizzati cinque intervalli per la stima per ogni serie temporale, sotto forma di linea punteggiata. È possibile modificare questo valore in modo da visualizzare un numero maggiore o minore di stime. È inoltre possibile visualizzare graficamente la deviazione standard per le stime aggiungendo barre di errore al grafico.  
  
#### <a name="to-change-prediction-and-display-options-in-the-chart-view"></a>Per modificare le opzioni relative a stima e visualizzazione nella vista del grafico  
  
1.  Provare a modificare il valore per **intervalli per la stima** aumentandolo da **5** al **10**, quindi tornare a **6**.  
  
     Nel caso di ampie fluttuazioni dei dati cronologici, tali fluttuazioni tendono a essere ripetute o addirittura amplificate man mano che si aumenta il numero di stime. A questo punto è probabilmente necessario effettuare una ricerca per comprendere la causa dell'eccessivo aumento di dati cronologici e decidere quindi se accettare i risultati, cercare di trovare un tipo di correzione nei dati di origine o applicare l'anti-aliasing al modello.  
  
2.  Selezionare il **Mostra deviazioni** casella di controllo.  
  
     Questa opzione consente di visualizzare l'errore stimato per ogni valore stimato.  
  
3.  Osservare la scala dell'asse X. Le modifiche dei dati cronologici e stimati vengono sempre espresse come una percentuale, ma i valori effettivi vengono modificati automaticamente in base a tutti i valori nel grafico. In caso di confronto dei modelli, è pertanto opportuno evitare di basarsi solo sugli elementi visivi. Per ottenere l'esatto valore, o l'aumento percentuale e per le stime, posizionare il mouse sulla linea punteggiata o linee continue oppure fare clic su righe per visualizzare i valori di **legenda Data Mining**.  
  
     **Suggerimento**: se il **legenda Data Mining** non è visibile, passare a **modello** visualizzare, fare doppio clic su qualsiasi nodo e selezionare **Mostra legenda**.  
  
 Analizzando queste tendenze si nota la mancanza di dati per alcune serie e si desidera ottenere stime più affidabili facendo la media delle vendite per modello o eventualmente per area. Si esaminerà questo approccio in una lezione successiva di questa esercitazione.  
  
 [Torna all'inizio](#bkmk_Charts)  
  
##  <a name="bkmk_Model"></a> Scheda modello  
 Il **modello** scheda della finestra di [!INCLUDE[msCoName](../includes/msconame-md.md)] Visualizzatore Time Series in Progettazione modelli di Data Mining consente di visualizzare il modello di previsione sotto forma di un grafico dell'albero.  
  
 Notare innanzitutto che poiché i dati descrivono due misure diverse (Amount e Quantity) per vendite di più linee di prodotti (T1000 e così via) in tre aree diverse (Europa, Nord America e Pacific), il modello compilato contiene in effetti 24 alberi diversi, ognuno dei quali rappresenta un modello dei modelli di vendita per una combinazione diversa di area, prodotto e attributo stimabile.  
  
 È possibile scegliere quale combinazione di linea di prodotti, area e metrica delle vendite si desidera visualizzare selezionando una serie del **albero** elenco a discesa il **modello** scheda.  
  
 Nozioni che è possibile apprendere visualizzando il modello come un albero Verrà effettuato un confronto tra due modelli, ad esempio, uno con diversi livelli nell'albero e un altro con un solo nodo.  
  
-   Quando un grafico dell'albero contiene un singolo nodo, significa che la tendenza individuata nel modello è per lo più omogenea nel tempo. È possibile utilizzare questo singolo nodo, con l'etichetta **tutti**, per visualizzare la formula che descrive la relazione tra le variabili di input e il risultato.  
  
-   Se un grafico dell'albero per una serie temporale dispone di più rami, significa che la serie temporale rilevata è troppo complessa per essere rappresentata come una singola equazione. Al contrario, il grafico dell'albero potrebbe contenere più rami, ognuno identificato con le condizioni che ha causato l'albero *suddividere*. Quando l'albero viene diviso, ogni ramo rappresenta un segmento temporale diverso, all'interno del quale la tendenza può essere descritta come una singola equazione.  
  
     Ad esempio, se si vedere un improvviso nel volume delle vendite avvio a settembre e continua fino alle festività di osservare il grafico, è possibile passare per il **modello** vista per visualizzare la data esatta in cui la tendenza è cambiata. I rami dell'albero che rappresentano "prima di settembre" e "dopo settembre" conterranno formule diverse: una formula descrive matematicamente le tendenze delle vendite fino alla divisione, mentre l'altra descrive le tendenze delle vendite per settembre fino alle festività di fine anno.  
  
#### <a name="to-explore-the-decision-tree-for-a-time-series-model"></a>Per esplorare l'albero delle decisioni per un modello Time Series  
  
1.  Nel **albero** elenco il **modello** scheda del visualizzatore, seleziona il **T1000 Europe: quantità** serie.  
  
     Fare clic sul nodo con etichettato **tutti**.  
  
     Per un **tutti** nodo, la descrizione comando visualizzata include informazioni quali il numero di case nell'intera serie e le equazioni della serie temporale derivate dall'analisi dei dati.  
  
2.  Se il **legenda Data Mining** non è visibile, il pulsante destro del nodo e selezionare **Mostra legenda**.  
  
     Il **legenda Data Mining** fornisce pressoché le stesse informazioni nella descrizione comando. Se una delle variabili indipendenti è discreta, verrà inoltre visualizzato un istogramma che illustra la distribuzione delle variabili nel nodo.  
  
3.  A questo punto selezionare una serie temporale diversa da visualizzare. Utilizzando il **albero** elenco il **modello** scheda del visualizzatore, seleziona il **M200 North America: quantità** serie.  
  
     Il grafico dell'albero contiene ora un' **tutti** nodo e due nodi figlio. Osservando le etichette dei nodi figlio, è possibile identificare il punto in cui la linea di tendenza è stata modificata.  
  
     Per ogni nodo figlio, la descrizione nel **legenda Data Mining** include inoltre il conteggio dei case in ogni ramo dell'albero.  
  
 Nell'elenco seguente vengono descritte alcune funzionalità aggiuntive del visualizzatore alberi:  
  
-   È possibile modificare la variabile rappresentata nel grafico utilizzando il **sfondo** controllo. Per impostazione predefinita, i nodi più scuri contengono più case, perché il valore di **sfondo** è impostata su **popolamento**. Per visualizzare solo il numero di case in un nodo, posiziona il puntatore del mouse su un nodo e visualizzare la descrizione comando viene visualizzata, o fare clic sul nodo e visualizza i numeri nella **legenda data mining** finestra.  
  
-   Nella descrizione comando o facendo clic sul nodo è inoltre possibile visualizzare la formula di regressione del nodo. Se è stato creato un modello misto, è possibile visualizzare due formule, una per ARTXP (nei nodi foglia) e uno per ARIMA (nel nodo radice dell'albero).  
  
-   Nei nodi che rappresentano numeri continui vengono utilizzati piccoli rombi. L'intervallo degli attributi viene visualizzato nella barra su cui è presente il rombo. Il rombo è centrato sulla media del nodo e il relativo spessore rappresenta la varianza dell'attributo in tale nodo.  
  
 [Torna all'inizio](#bkmk_Charts)  
  
##  <a name="bkmk_Content"></a> (Facoltativo) Generic Content Tree Viewer  
 Oltre al visualizzatore personalizzato per la serie temporale, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] fornisce il **MicrosoftGeneric Content Tree Viewer** per l'utilizzo con tutti i modelli di data mining. Questo visualizzatore fornisce alcuni vantaggi:  
  
-   **Visualizzatore Microsoft Time Series**: questa vista vengono uniti i risultati dei due algoritmi. Anche se è possibile visualizzare ogni serie separatamente, non è possibile determinare come sono stati combinati i risultati di ogni algoritmo. Inoltre in questa vista le descrizioni comando e Legenda data mining mostrano solo le statistiche più importanti.  
  
-   **Generic Content Tree Viewer**: consente di esplorare e visualizzare tutte le serie di dati utilizzati nel modello in una sola volta e se è stata creata una combinazione del modello, sia ARIMA e nello stesso grafico vengono visualizzati gli alberi ARTXP.  
  
     È possibile utilizzare questo visualizzatore per ottenere tutte le statistiche da entrambi gli algoritmi, oltre alle distribuzioni dei valori.  
  
     Consigliato per gli utenti esperti di data mining chi desiderano ottenere maggiori informazioni sulle analisi ARIMA e ARTXP.  
  
#### <a name="to-view-details-for-a-particular-data-series-in-the-generic-content-viewer"></a>Per visualizzare i dettagli per una particolare serie di dati in Generic Content Tree Viewer  
  
1.  Nel **visualizzatore modello di Data Mining** , selezionare **Microsoft Generic Content Tree Viewer** dal **Visualizzatore** elenco a discesa.  
  
2.  Nel **didascalia del nodo** riquadro, fare clic sul livello più alto nodo (tutto).  
  
3.  Nel **dettagli nodo** riquadro, visualizzare il valore attribute_name.  
  
     Questo valore indica quale serie, o combinazione di prodotto e area, è contenuta nel nodo. Nell'esempio di AdventureWorks il nodo superiore è relativo alla serie M200 Europe.  
  
4.  Nel **didascalia del nodo** riquadro, individuare il primo nodo che dispone di nodi figlio.  
  
     Se un nodo della serie dispone di figli, la visualizzazione albero che è presente il **modello** scheda del visualizzatore Microsoft Time Series disporrà di una struttura con rami.  
  
5.  Espandere il nodo e fare clic su uno dei nodi figlio.  
  
     La colonna NODE_DESCRIPTION dello schema contiene la condizione che ha causato la suddivisione dell'albero.  
  
6.  Nel **didascalia del nodo** riquadro, fare clic sul nodo ARIMA superiore ed espandere il nodo fino a tutti i nodi figlio sono visibili.  
  
7.  Nel **dettagli nodo** riquadro, visualizzare il valore attribute_name.  
  
     Questo valore indica quale serie temporale è contenuta nel nodo. Il nodo superiore nella sezione ARIMA deve corrispondere al nodo superiore nella sezione (Tutti). Nell'esempio di AdventureWorks questo nodo contiene l'analisi ARIMA relativa alla serie M200 Europe.  
  
 Per altre informazioni, vedere [Contenuto dei modelli di data mining per i modelli Time Series &#40;Analysis Services - Data mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md).  
  
 [Torna all'inizio](#bkmk_Charts)  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Creazione di stime basate su serie temporali &#40;intermedi dell'esercitazione sul Data Mining&#41;](../../2014/tutorials/creating-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Tempo Series Model Query Examples](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)   
 [Riferimento tecnico per l'algoritmo Microsoft Time Series](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)  
  
  