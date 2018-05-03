---
title: Query drill-through (Data Mining) | Documenti Microsoft
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: data-mining
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 804497bfe94c6d6d93f63d9b8a2242246122c034
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="drillthrough-queries-data-mining"></a>Query drill-through (Data mining)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Una *query drill-through* consente di recuperare i dettagli dei case o dei dati della struttura sottostanti mediante l'invio di una query al modello di data mining. Il drill-through è utile se si desidera confrontare i case utilizzati per il training del modello con quelli utilizzati per il test del modello oppure se si desidera visualizzare ulteriori dettagli dei dati dei case.  
  
 Nel data mining di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sono disponibili due opzioni diverse per il drill-through:  
  
-   Drill-through nei **case del modello**  
  
     Il drill-through nei case del modello viene utilizzato quando si desidera passare da uno schema specifico del modello, ad esempio un cluster o un ramo di un albero delle decisioni, e visualizzare dettagli sui singoli case.  
  
-   Drill-through nei **case della struttura**  
  
     Il drill-through nei case della struttura viene utilizzato se nella struttura sono contenute informazioni che potrebbero non essere disponibili nel modello. Ad esempio, non vengono utilizzate informazioni di contatto del cliente in un modello di clustering, anche se i dati sono inclusi nella struttura. Tuttavia, dopo avere creato il modello, è possibile recuperare informazioni di contatto dei clienti raggruppati in un determinato cluster.  
  
 In questa sezione vengono forniti esempi su come creare queste query.  
  
 [Utilizzo del drill-through in Progettazione modelli di data mining](#bkmk_Designer)  
  
 [Creazione di query drill-through tramite DMX](#bkmk_DMX)  
  
 [Considerazioni sull'utilizzo del drill-through](#bkmk_Considerations)  
  
-   [Problemi relativi alla sicurezza](#bkmk_Security)  
  
-   [Limitazioni](#bkmk_Limits)  
  
##  <a name="bkmk_Designer"></a> Utilizzo del drill-through in Progettazione modelli di data mining  
 Se un modello di data mining è stato configurato per consentire il drill-through e se si dispone delle autorizzazioni appropriate, quando si esplora il modello è possibile fare clic su un nodo nel visualizzatore adatto e recuperare informazioni dettagliate sui case in quel determinato nodo.  
  
 [Eseguire il drill-through sui dati del case da un modello di data mining](../../analysis-services/data-mining/drill-through-to-case-data-from-a-mining-model.md).  
  
 Se i case di training sono stati memorizzati nella cache durante l'elaborazione della struttura di data mining e si dispone delle autorizzazioni necessarie, è possibile restituire le informazioni dai case del modello e dalla struttura di data mining, comprese le colonne che non erano state incluse nel modello di data mining.  
  
##  <a name="bkmk_DMX"></a> Creazione di query drill-through tramite DMX  
 È possibile eseguire il drill-through nei dati del case creando una query DMX se si dispone delle autorizzazioni necessarie per il modello o la struttura. Per esempi relativi alla sintassi per la creazione di query drill-through in DMX, vedere l'argomento seguente:  
  
 [Creare query drill-through tramite DMX](../../analysis-services/data-mining/create-drillthrough-queries-using-dmx.md)  
  
##  <a name="bkmk_Considerations"></a> Considerazioni sull'utilizzo del drill-through  
  
-   Se si utilizza Creazione guidata modello di data mining, l'opzione per abilitare il drill-through nei case del modello si trova nell'ultima pagina della procedura guidata. Per impostazione predefinita, il drill-through è disabilitato. Per altre informazioni, vedere [Completamento procedura guidata &#40;Creazione guidata modello di data mining&#41;](http://msdn.microsoft.com/library/6aef1548-35eb-42fd-ae87-63650a79eda1).  
  
-   È possibile aggiungere la capacità di eseguire il drill-through in un modello di data mining esistente, ma in tal caso il modello deve essere rielaborato prima che sia possibile eseguire il drill-through nei dati.  
  
-   Il drill-through consiste nel recupero delle informazioni sui case di training memorizzati nella cache durante l'elaborazione della struttura di data mining. Pertanto, se i dati memorizzati nella cache sono stati cancellati dopo l'elaborazione della struttura impostando la proprietà <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> su **ClearAfterProcessing**, il drill-through non funzionerà. Per abilitare il drill-through per le colonne della struttura, è necessario impostare la proprietà <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> su **KeepTrainingCases** e rielaborare la struttura.  
  
-   Se la struttura di data mining non consente il drill-through, mentre il modello di data mining lo consente, è possibile visualizzare solo le informazioni dai case del modello e non dalla struttura di data mining.  
  
###  <a name="bkmk_Security"></a> Problemi di sicurezza correlati al drill-through  
 Se si vuole eseguire il drill-through nei case della struttura dal modello, è necessario verificare che la proprietà [AllowDrillThrough](../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md) sia impostata su **True**sia per la struttura che per il modello di data mining. È inoltre necessario essere membro di un ruolo che disponga delle autorizzazioni di drill-through sia per la struttura sia per il modello. Per altre informazioni sulla creazione di ruoli, vedere [Progettazione ruoli &#40;Analysis Services - Dati multidimensionali&#41;](http://msdn.microsoft.com/library/e8ba42db-0565-4d68-b3ab-0c63d8d07192). .  
  
 Le autorizzazioni di drill-through vengono impostate separatamente per la struttura e per il modello. L'autorizzazione del modello consente di eseguire il drill-through dal modello, anche se non si dispone di autorizzazioni sulla struttura. Le autorizzazioni di drill-through per la struttura consentono di includere colonne della struttura nelle query di drill-through dal modello usando la funzione [StructureColumn &#40;DMX&#41;](../../dmx/structurecolumn-dmx.md).  
  
> [!NOTE]  
>  Se si abilita il drill-through per la struttura e per il modello di data mining, qualsiasi utente che sia un membro di un ruolo che dispone delle autorizzazioni di drill-through per il modello di data mining può anche visualizzare le colonne della struttura di data mining, anche se tali colonne non sono incluse nel modello di data mining. Pertanto, per proteggere i dati sensibili, è necessario configurare la vista origine dati per mascherare le informazioni personali e consentire l'accesso drill-through alla struttura di data mining solo quando necessario.  
  
###  <a name="bkmk_Limits"></a> Limitazioni relative al drill-through  
  
-   Le limitazioni seguenti vengono applicate alle operazioni di drill-through su un modello, a seconda dell'algoritmo utilizzato per creare il modello:  
  
|Nome algoritmo|Problema|  
|--------------------|-----------|  
|Algoritmo Microsoft Naive Bayes|Non supportato. Questi algoritmi non assegnano case ai nodi specifici nel contenuto.|  
|Algoritmo Microsoft Neural Network|Non supportato. Questi algoritmi non assegnano case ai nodi specifici nel contenuto.|  
|Algoritmo Microsoft Logistic Regression|Non supportato. Questi algoritmi non assegnano case ai nodi specifici nel contenuto.|  
|Algoritmo Microsoft Linear Regression|Supportato. Tuttavia, poiché il modello crea un solo nodo, **All**, il drill-through restituisce tutti i case di training del modello. Se le dimensioni del set di training sono elevate, il caricamento dei risultati può richiedere molto tempo.|  
|Algoritmo Microsoft Time Series|Supportato. Tuttavia, non è possibile eseguire il drill-through ai dati della struttura o del case usando il **Visualizzatore modello di data mining** nella Progettazione modelli di data mining. È necessario creare invece una query DMX.<br /><br /> Inoltre, non è possibile eseguire il drill-through su nodi specifici o scrivere una query DMX per recuperare case in nodi specifici di un modello Time Series. È possibile recuperare dati del case dal modello o dalla struttura utilizzando altri criteri, ad esempio una data o i valori dell'attributo.<br /><br /> È inoltre possibile restituire le date dai case nel modello usando la funzione [Lag &#40;DMX&#41;](../../dmx/lag-dmx.md).<br /><br /> Se si vogliono visualizzare i dettagli dei nodi ARTXP e ARIMA creati dall'algoritmo Microsoft Time Series, è possibile usare [Microsoft Generic Content Tree Viewer &#40;Data mining&#41;](http://msdn.microsoft.com/library/751b4393-f6fd-48c1-bcef-bdca589ce34c).|  
  
##  <a name="bkmk_Tasks"></a> Attività correlate  
 Utilizzare i collegamenti seguenti per utilizzare il drill-through in scenari specifici.  
  
|Attività|Collegamento|  
|----------|----------|  
|Procedura in cui viene descritto l'utilizzo del drill-through in Progettazione modelli di data mining|[Drill-Through nei dati del Case da un modello di Data Mining](../../analysis-services/data-mining/drill-through-to-case-data-from-a-mining-model.md)|  
|Per modificare un modello di data mining esistente al fine di consentire il drill-through|[Consenti drill-through per un modello di Data Mining](../../analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md)|  
|Abilitazione del drill-through in una struttura di data mining utilizzando la clausola WITH DRILLTHROUGH di DMX|[CREARE UNA STRUTTURA DI DATA MINING & #40; DMX & #41;](../../dmx/create-mining-structure-dmx.md)|  
|Per informazioni sull'assegnazione di autorizzazioni applicabili al drill-through in strutture e modelli di data mining|[Concedere le autorizzazioni per strutture di data mining e modelli & #40; Analysis Services & #41;](../../analysis-services/multidimensional-models/grant-permissions-on-data-mining-structures-and-models-analysis-services.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzatori modello di Data Mining](../../analysis-services/data-mining/data-mining-model-viewers.md)   
 [Query di Data Mining](../../analysis-services/data-mining/data-mining-queries.md)  
  
  
