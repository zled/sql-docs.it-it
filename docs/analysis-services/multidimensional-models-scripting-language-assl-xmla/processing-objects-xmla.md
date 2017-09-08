---
title: L'elaborazione di oggetti (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- errors [XML for Analysis]
- objects [XML for Analysis]
- XML for Analysis, objects
- XMLA, partitions
- partitions [Analysis Services], XML for Analysis
- XML for Analysis, partitions
- writeback [Analysis Services], XML for Analysis
- out-of-line bindings
- processing objects [XML for Analysis]
- XMLA, objects
ms.assetid: a65b3249-303d-49c6-98af-6ac6eed11a03
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6dfc2fafb76d19ea986b697ec065abec738f4c05
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="processing-objects-xmla"></a>Elaborazione di oggetti (XMLA)
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], l'elaborazione è il passaggio o serie di passaggi necessari per trasformare dati in informazioni per l'analisi aziendale. L'elaborazione varia a seconda del tipo di oggetto, ma rappresenta sempre una fase della trasformazione dei dati in informazioni.  
  
 Al processo un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dell'oggetto, è possibile utilizzare il [processo](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) comando. Il **processo** comando è possibile elaborare gli oggetti seguenti in un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] istanza:  
  
-   Cubi  
  
-   Database  
  
-   Dimensioni  
  
-   Gruppi di misure  
  
-   Modelli di data mining  
  
-   Strutture di data mining  
  
-   Partizioni  
  
 Per controllare l'elaborazione di oggetti, il **processo** comando dispone di varie proprietà che possono essere impostate. Il **processo** comando dispone di proprietà che controllano: la quantità dell'elaborazione, gli oggetti che verranno elaborati, se si desidera utilizzare associazioni out-of-line, come gestire gli errori e come gestire le tabelle writeback.  
  
## <a name="specifying-processing-options"></a>Impostazione delle opzioni di elaborazione  
 Il [tipo](../../analysis-services/xmla/xml-elements-properties/type-element-xmla.md) proprietà del **processo** comando specifica l'opzione di elaborazione da utilizzare durante l'elaborazione dell'oggetto. Per altre informazioni sulle opzioni di elaborazione, vedere [Opzioni e impostazioni di elaborazione &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
 Nella tabella seguente sono elencate le costanti per il **tipo** proprietà e i vari oggetti che possono essere elaborati utilizzando ciascuna costante.  
  
|**Tipo** valore|Oggetti applicabili|  
|--------------------|------------------------|  
|*ProcessFull*|Cubo, database, dimensione, gruppo di misure, modello di data mining, struttura di data mining, partizione|  
|*ProcessAdd*|Dimensione, partizione|  
|*ProcessUpdate*|Dimensione|  
|*ProcessIndexes*|Dimensione, cubo, gruppo di misure, partizione|  
|*ProcessData*|Dimensione, cubo, gruppo di misure, partizione|  
|*ProcessDefault*|Cubo, database, dimensione, gruppo di misure, modello di data mining, struttura di data mining, partizione|  
|*ProcessClear*|Cubo, database, dimensione, gruppo di misure, modello di data mining, struttura di data mining, partizione|  
|*ProcessStructure*|Cubo, struttura di data mining|  
|*ProcessClearStructureOnly*|Struttura di data mining|  
|*ProcessScriptCache*|Cube|  
  
 Per ulteriori informazioni sull'elaborazione [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] degli oggetti, vedere [l'elaborazione di un modello multidimensionale &#40; Analysis Services &#41; ](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
## <a name="specifying-objects-to-be-processed"></a>Specifica degli oggetti da elaborare  
 Il [oggetto](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md) proprietà del **processo** comando contiene l'identificatore dell'oggetto da elaborare. È possibile specificare solo un oggetto un **processo** comando, ma l'elaborazione di un oggetto elabora anche gli eventuali oggetti figlio. L'elaborazione di un gruppo di misure in un cubo, ad esempio, determina l'elaborazione di tutte le partizioni di tale gruppo, mentre l'elaborazione di un database determina l'elaborazione di tutti gli oggetti, quali cubi, dimensioni e strutture di data mining, contenuti nel database.  
  
 Se si imposta la **ProcessAffectedObjects** attributo del **processo** comando su true, le relative oggetto interessato dall'elaborazione dell'oggetto specificato viene elaborato. Ad esempio, se un aggiornamento incrementale utilizzando il *ProcessUpdate* l'opzione di elaborazione di **processo** comando, qualsiasi partizione le cui le aggregazioni vengono invalidate a causa di membri da aggiunta o eliminazione viene elaborata anche [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] se **ProcessAffectedObjects** è impostata su true. In questo caso, un unico **processo** comando è possibile elaborare più oggetti in un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] istanza, ma [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] determina gli oggetti che oltre all'oggetto specificato nella **processo** comando deve inoltre essere elaborato.  
  
 Tuttavia, è possibile elaborare più oggetti, ad esempio dimensioni, nello stesso momento usando più **processo** comandi all'interno di un **Batch** comando. Operazioni batch consentono un migliore livello di controllo per l'elaborazione seriale o parallelo degli oggetti in un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] istanza rispetto all'utilizzo di **ProcessAffectedObjects** attributo e consentono di ottimizzare l'approccio all'elaborazione per più grande [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database. Per ulteriori informazioni sull'esecuzione di operazioni batch, vedere [esecuzione di operazioni Batch &#40; XMLA &#41; ](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/performing-batch-operations-xmla.md).  
  
## <a name="specifying-out-of-line-bindings"></a>Specifica di associazioni out-of-line  
 Se il **processo** comando non è contenuto in un **Batch** comando, è possibile specificare associazioni out-of-line nel [associazioni](../../analysis-services/xmla/xml-elements-properties/bindings-element-xmla.md), [DataSource](../../analysis-services/xmla/xml-elements-properties/datasource-element-xmla.md), e [DataSourceView](../../analysis-services/xmla/xml-elements-properties/datasourceview-element-xmla.md) le proprietà del **processo** comando per gli oggetti da elaborare. Le associazioni out-of-line sono riferimenti a origini dati, viste origine dati e altri oggetti in cui l'associazione è presente solo durante l'esecuzione del **processo** comando e cui eseguire l'override di qualsiasi binding esistente associato il oggetti in fase di elaborazione. Se non è specificata alcuna associazione out-of-line, vengono utilizzate le associazioni attualmente associate agli oggetti da elaborare.  
  
 Le associazioni out-of-line vengono utilizzate nelle seguenti situazioni:  
  
-   Elaborazione incrementale di una partizione in cui è necessario specificare una tabella dei fatti alternativa o un filtro sulla tabella dei fatti esistente per garantire che le righe non vengono contate due volte.  
  
-   Utilizzo di un'attività flusso di dati in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] per fornire i dati durante l'elaborazione di una dimensione, un modello di data mining o una partizione.  
  
 Le associazioni out-of-line vengono descritte come parte del linguaggio ASSL (Analysis Services Scripting Language). Per ulteriori informazioni sulle associazioni out-of-line in ASSL, vedere [origini dati e associazioni &#40; SSAS multidimensionale &#41; ](../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
### <a name="incrementally-updating-partitions"></a>Aggiornamento incrementale di partizioni  
 Per eseguire l'aggiornamento incrementale di una partizione già elaborata, è necessario utilizzare un'associazione out-of-line poiché l'associazione specificata per la partizione fa riferimento a dati della tabella dei fatti già aggregati all'interno della partizione. Quando l'aggiornamento incrementale di una partizione già elaborata tramite il **processo** comando [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] esegue le azioni seguenti:  
  
-   Creazione di una partizione temporanea con una struttura identica a quella della partizione da aggiornare in modo incrementale.  
  
-   Elaborazione della partizione temporanea, utilizzando l'associazione out-of-line specificata nel **processo** comando.  
  
-   Unione della partizione temporanea con la partizione esistente selezionata.  
  
 Per ulteriori informazioni sull'unione di partizioni utilizzando XML for Analysis (XMLA), vedere [unione di partizioni &#40; XMLA &#41; ](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/merging-partitions-xmla.md).  
  
## <a name="handling-processing-errors"></a>Gestione degli errori di elaborazione  
 Il [ErrorConfiguration](../../analysis-services/xmla/xml-elements-properties/errorconfiguration-element-xmla.md) proprietà del **processo** consente di specificare come gestire gli errori rilevati durante l'elaborazione di un oggetto. Ad esempio durante l'elaborazione di una dimensione in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] viene rilevato un valore duplicato nella colonna chiave dell'attributo chiave. Poiché le chiavi dell'attributo devono essere univoche, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] elimina i record duplicati. In base il [KeyDuplicate](../../analysis-services/scripting/properties/keyduplicate-element-assl.md) proprietà di **ErrorConfiguration**, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Impossibile:  
  
-   Continuazione dell'elaborazione della dimensione poiché il messaggio viene ignorato.  
  
-   Restituzione di un messaggio che indica che in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è stata rilevata una chiave duplicata e continuazione dell'elaborazione.  
  
 Esistono numerose condizioni analoghe per cui **ErrorConfiguration** fornisce opzioni durante un **processo** comando.  
  
## <a name="managing-writeback-tables"></a>Gestione di tabelle writeback  
 Se il **processo** comando rileva una partizione abilitata per la scrittura o un cubo o gruppo di misure per tale partizione, che non è già completamente elaborata, una tabella writeback non esiste per la partizione. Il [WritebackTableCreation](../../analysis-services/xmla/xml-elements-properties/writebacktablecreation-element-xmla.md) proprietà del **processo** comando determina se [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] deve creare una tabella writeback.  
  
## <a name="examples"></a>Esempi  
  
### <a name="description"></a>Description  
 Nell'esempio seguente viene elaborato completamente il database di esempio [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
### <a name="code"></a>Codice  
  
```  
<Process xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Object>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
  </Object>  
  <Type>ProcessFull</Type>  
  <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
</Process>  
```  
  
### <a name="description"></a>Description  
 Nell'esempio seguente viene elaborata in modo incrementale la **Internet_Sales_2004** partizione il **Internet Sales** gruppo di misure del **Adventure Works DW** cubo il [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] esempio [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database. Il **processo** comando aggiunge le aggregazioni per ordine di date entro il 31 dicembre 2006 alla partizione utilizzando un'associazione di query out-of-line nel **associazioni** proprietà del **processo**  comando per recuperare le righe della tabella dei fatti da cui generare le aggregazioni da aggiungere alla partizione.  
  
### <a name="code"></a>Codice  
  
```  
<Process ProcessAffectedObjects="true" xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Object>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works DW</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2006</PartitionID>  
  </Object>  
  <Bindings>  
    <Binding>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2006</PartitionID>  
      <Source xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="QueryBinding">  
        <DataSourceID>Adventure Works DW</DataSourceID>  
        <QueryDefinition>  
          SELECT  
            [dbo].[FactInternetSales].[ProductKey],  
            [dbo].[FactInternetSales].[OrderDateKey],  
            [dbo].[FactInternetSales].[DueDateKey],  
            [dbo].[FactInternetSales].[ShipDateKey],   
            [dbo].[FactInternetSales].[CustomerKey],   
            [dbo].[FactInternetSales].[PromotionKey],  
            [dbo].[FactInternetSales].[CurrencyKey],  
            [dbo].[FactInternetSales].[SalesTerritoryKey],  
            [dbo].[FactInternetSales].[SalesOrderNumber],  
            [dbo].[FactInternetSales].[SalesOrderLineNumber],  
            [dbo].[FactInternetSales].[RevisionNumber],  
            [dbo].[FactInternetSales].[OrderQuantity],  
            [dbo].[FactInternetSales].[UnitPrice],  
            [dbo].[FactInternetSales].[ExtendedAmount],  
            [dbo].[FactInternetSales].[UnitPriceDiscountPct],  
            [dbo].[FactInternetSales].[DiscountAmount],  
            [dbo].[FactInternetSales].[ProductStandardCost],  
            [dbo].[FactInternetSales].[TotalProductCost],  
            [dbo].[FactInternetSales].[SalesAmount],  
            [dbo].[FactInternetSales].[TaxAmt],  
            [dbo].[FactInternetSales].[Freight],  
            [dbo].[FactInternetSales].[CarrierTrackingNumber],  
            [dbo].[FactInternetSales].[CustomerPONumber]  
          FROM [dbo].[FactInternetSales]  
          WHERE OrderDateKey > '1280'  
        </QueryDefinition>  
      </Source>  
    </Binding>  
  </Bindings>  
  <Type>ProcessAdd</Type>  
  <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
</Process>  
```  
  
  
