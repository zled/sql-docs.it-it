---
title: CREARE IL MODELLO DI DATA MINING (DMX) | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CREATE MINING MODEL
- CREATE
- CREATE_MINING_MODEL
dev_langs:
- DMX
helpviewer_keywords:
- RELATED TO column
- mining models [Analysis Services], creating
- column definition lists [DMX]
- parameter lists [DMX]
- SESSION clause
- CREATE MINING MODEL statement
ms.assetid: 43e4b591-7b34-494c-9b2d-7f0fe69af788
caps.latest.revision: 57
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 6d3d8471754918eaff793bb6787f383b67f33a77
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="create-mining-model-dmx"></a>CREATE MINING MODEL (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Consente di creare sia un nuovo modello di data mining che una struttura di data mining nel database. Per creare un modello è possibile definirlo nell'istruzione oppure utilizzare il linguaggio PMML (Predictive Model Markup Language). La seconda soluzione è consigliata solo agli utenti esperti.  
  
 Il nome della struttura di data mining viene creato aggiungendo il suffisso "_structure" al nome del modello, per assicurare l'utilizzo di un nome univoco derivato dal nome del modello.  
  
 Per creare un modello di data mining per una struttura di data mining esistente, usare il [ALTER MINING STRUCTURE &#40;DMX&#41; ](../dmx/alter-mining-structure-dmx.md) istruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CREATE [SESSION] MINING MODEL <model>  
(  
    [(<column definition list>)]  
)  
USING <algorithm> [(<parameter list>)] [WITH DRILLTHROUGH]  
CREATE MINING MODEL <model> FROM PMML <xml string>  
```  
  
## <a name="arguments"></a>Argomenti  
 *model*  
 Nome univoco del modello.  
  
 *elenco delle definizioni di colonna*  
 Elenco delimitato da virgole contenente le definizioni delle colonne.  
  
 *Algoritmo*  
 Nome di un algoritmo di data mining, secondo quanto definito dal provider corrente.  
  
> [!NOTE]  
>  Un elenco degli algoritmi supportati dal provider corrente può essere recuperato tramite [set di righe DMSCHEMA_MINING_SERVICES](../analysis-services/schema-rowsets/data-mining/dmschema-mining-services-rowset.md). Per visualizzare gli algoritmi supportati nell'istanza corrente di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], vedere [proprietà di Data Mining](../analysis-services/server-properties/data-mining-properties.md).  
  
 *Elenco di parametri*  
 Facoltativa. Elenco delimitato da virgole dei parametri definiti dal provider per l'algoritmo.  
  
 *Stringa XML*  
 (Riservato agli utenti esperti). Modello con codifica XML (PMML). La stringa deve essere racchiusa tra virgolette singole (').  
  
 Il **sessione** clausola consente di creare un modello di data mining che viene rimosso automaticamente dal server quando si chiude la connessione o la sessione scade. **SESSIONE** modelli di data mining sono utili perché non richiedono che l'utente sia un amministratore del database e utilizzano solo lo spazio su disco per fino a quando la connessione è aperta.  
  
 Il **WITH DRILLTHROUGH** clausola consente il drill-through sul nuovo modello di data mining. È possibile attivare il drill-through solo al momento della creazione del modello. Per alcuni tipi di modello, il drill-through è necessario per esplorare il modello nel visualizzatore personalizzato. Il drill-through non è richiesto per stima o per esplorare il modello tramite Microsoft Generic Content Tree Viewer.  
  
 Il **CREATE MINING MODEL** istruzione crea un nuovo modello di data mining che si basa sull'elenco delle definizioni di colonna, l'algoritmo e nell'elenco di parametri di algoritmo.  
  
### <a name="column-definition-list"></a>Elenco delle definizioni di colonna  
 Per definire la struttura di un modello che utilizza l'elenco delle definizioni di colonna, è necessario includere le informazioni seguenti per ogni colonna:  
  
-   Nome (obbligatorio)  
  
-   Tipo di dati (obbligatorio)  
  
-   Distribuzione  
  
-   Elenco dei flag di modellazione  
  
-   Tipo di contenuto (obbligatorio)  
  
-   Richiesta di stima, che indica l'algoritmo per stimare la colonna, indicato dal **PREDICT** o **PREDICT_ONLY** clausola  
  
-   Relazione con una colonna di attributo (obbligatoria solo se applicabile), indicata dal **RELATED TO** clausola  
  
 Per definire una singola colonna utilizzare la sintassi seguente nell'elenco delle definizioni di colonna:  
  
```  
<column name>    <data type>    [<Distribution>]    [<Modeling Flags>]    <Content Type>    [<prediction>]    [<column relationship>]   
```  
  
 Per definire una colonna di tabella nidificata utilizzare la sintassi seguente nell'elenco delle definizioni di colonna:  
  
```  
<column name>    TABLE    [<prediction>] ( <non-table column definition list> )  
```  
  
 Ad eccezione dei flag di modellazione, per definire una colonna non è possibile utilizzare più di una clausola di uno stesso gruppo. È invece possibile definire più flag di modellazione per una stessa colonna.  
  
 Per un elenco dei tipi di dati, dei tipi di contenuto, delle distribuzioni di colonna e dei flag di modellazione che è possibile utilizzare per definire una colonna, vedere gli argomenti seguenti:  
  
-   [Tipi di dati & #40; Data Mining & #41;](../analysis-services/data-mining/data-types-data-mining.md)  
  
-   [Contenuto di Data Mining tipi & #40; & #41;](../analysis-services/data-mining/content-types-data-mining.md)  
  
-   [Distribuzioni delle colonne &#40;Data Mining&#41;](../analysis-services/data-mining/column-distributions-data-mining.md)  
  
-   [Modello di Data Mining flag & #40; & #41;](../analysis-services/data-mining/modeling-flags-data-mining.md)  
  
 Per descrivere la relazione tra due colonne, è possibile aggiungere una clausola alla descrizione. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] supporta l'utilizzo delle operazioni seguenti \<relazione a colonna > clausola.  
  
 **CORRELATI A**  
 Questa forma indica una gerarchia di valori. La destinazione di una colonna con clausola RELATED TO può essere una colonna chiave in una tabella nidificata, una colonna con valori discreti nella riga dei case oppure un'altra colonna con una clausola RELATED TO, che indica una gerarchia con più livelli.  
  
 Per descrivere la modalità di utilizzo della colonna di stima, utilizzare una clausola di stima. Nella tabella seguente vengono descritte le due clausole disponibili.  
  
|\<stima > clausola|Description|  
|---------------------------|-----------------|  
|**PREDICT**|Questa colonna può essere stimata dal modello e può essere specificata nei case di input per stimare il valore di altre colonne stimabili.|  
|**PREDICT_ONLY**|Questa colonna può essere stimata dal modello, ma i relativi valori non possono essere utilizzati nei case di input per stimare il valore di altre colonne stimabili.|  
  
### <a name="parameter-definition-list"></a>Elenco delle definizioni di parametro  
 È possibile utilizzare l'elenco dei parametri per regolare le prestazioni e le funzionalità di un modello di data mining. La sintassi dell'elenco dei parametri è la seguente:  
  
```  
[<parameter> = <value>, <parameter> = <value>,…]  
```  
  
 Per un elenco dei parametri associati a ogni algoritmo, vedere [algoritmi di Data Mining &#40;Analysis Services - Data Mining&#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md).  
  
## <a name="remarks"></a>Osservazioni  
 Per creare un modello che dispone di un set di dati di testing incorporati, è necessario utilizzare l'istruzione CREATE MINING STRUCTURE seguita da ALTER MINING STRUCTURE. Tuttavia, non tutti i tipi di modello supportano un set di dati di controllo. Per altre informazioni, vedere [CREATE MINING STRUCTURE &#40;DMX&#41;](../dmx/create-mining-structure-dmx.md).  
  
 Per una procedura dettagliata di come creare un modello di data mining utilizzando l'istruzione CREATEMODEL, vedere [esercitazione su DMX stima serie tempo](http://msdn.microsoft.com/library/38ea7c03-4754-4e71-896a-f68cc2c98ce2).  
  
## <a name="naive-bayes-example"></a>Esempio sull'algoritmo Naive Bayes  
 Nell'esempio seguente viene utilizzato l'algoritmo [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes per creare un nuovo modello di data mining. La colonna Bike Buyer è definita come attributo stimabile.  
  
```  
CREATE MINING MODEL [NBSample]  
(  
    CustomerKey LONG KEY,   
    Gender TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Bike Buyer] LONG DISCRETE PREDICT  
)  
USING Microsoft_Naive_Bayes  
```  
  
## <a name="association-model-example"></a>Esempio sul modello Association Rules  
 Nell'esempio seguente viene utilizzato l'algoritmo [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules per creare un nuovo modello di data mining. L'istruzione sfrutta la possibilità di nidificare una tabella nella definizione del modello tramite una colonna di tabella. Il modello viene modificato utilizzando il *MINIMUM_PROBABILITY* e *MINIMUM_SUPPORT* parametri.  
  
```  
CREATE MINING MODEL MyAssociationModel (  
    OrderNumber TEXT KEY,  
    [Products] TABLE PREDICT (  
        [Model] TEXT KEY  
    )  
)  
USING Microsoft_Association_Rules (Minimum_Probability = 0.1, MINIMUM_SUPPORT = 0.01)  
```  
  
## <a name="sequence-clustering-example"></a>Esempio sull'algoritmo Sequence Clustering  
 Nell'esempio seguente viene utilizzato l'algoritmo [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering per creare un nuovo modello di data mining. Per definire il modello vengono utilizzate due chiavi. La colonna OrderNumber viene utilizzata come chiave del case e specifica singoli ordini. La colonna LineNumber viene utilizzata come chiave della tabella nidificata e specifica la sequenza nella quale gli elementi sono aggiunti a un ordine.  
  
```  
CREATE MINING MODEL BuyingSequence (  
    [Order Number] TEXT KEY,  
    [Products] TABLE   
     (  
        [Line Number] LONG KEY SEQUENCE,  
        [Model] TEXT DISCRETE PREDICT  
    )  
)  
USING Microsoft_Sequence_Clustering  
```  
  
## <a name="time-series-example"></a>Esempio sull'algoritmo Time Series  
 Nell'esempio seguente viene utilizzato l'algoritmo [!INCLUDE[msCoName](../includes/msconame-md.md)] Times Series per creare un nuovo modello di data mining utilizzando l'algoritmo ARTxp. ReportingDate è la colonna chiave per la serie temporale e ModelRegion è la colonna chiave per la serie di dati. In questo esempio si presuppone che i dati abbiano una periodicità di 12 mesi. Pertanto, il *PERIODICITY_HINT* parametro è impostato su 12.  
  
> [!NOTE]  
>  È necessario specificare il *PERIODICITY_HINT* parametro utilizzando i caratteri parentesi graffa. Inoltre, poiché il valore è una stringa, è necessario racchiuderlo tra virgolette singole: "{\<valore numerico >}".  
  
```  
CREATE MINING MODEL SalesForecast (  
        ReportingDate DATE KEY TIME,  
        ModelRegion TEXT KEY,  
        Amount LONG CONTINUOUS PREDICT,  
        Quantity LONG CONTINUOUS PREDICT  
)  
USING Microsoft_Time_Series (PERIODICITY_HINT = '{12}', FORECAST_METHOD = 'ARTXP')  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni Data Mining &#40;DMX&#41; le istruzioni di definizione dei dati](../dmx/dmx-statements-data-definition.md)   
 [Estensioni Data Mining &#40;DMX&#41; istruzioni Data Manipulation](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining Extensions & #40; DMX & #41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
