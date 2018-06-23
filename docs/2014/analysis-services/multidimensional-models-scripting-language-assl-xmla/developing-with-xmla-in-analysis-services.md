---
title: Sviluppo con XMLA in Analysis Services | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- XML for Analysis, data mining
- commands [XML for Analysis]
- data mining [XML for Analysis]
- XMLA, data mining
- XML for Analysis, Analysis Services tasks
- XMLA, Analysis Services tasks
ms.assetid: 54445ee7-720c-4683-99a6-e75b3dcca904
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 04c3459dca4edabcc56753a076bad1e4ffdddfde
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170673"
---
# <a name="developing-with-xmla-in-analysis-services"></a>Sviluppo con XMLA in Analysis Services
  XML for Analysis (XMLA) è protocollo XML basato su SOAP, progettato in modo specifico per accedere a tutti i dati di qualsiasi origine dati multidimensionale standard accessibile tramite una connessione HTTP. In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] l'unico protocollo utilizzato durante la comunicazione con applicazioni client è XMLA. Fondamentalmente, tutte le librerie client supportate da Analysis Services formulano richieste e risposte in XMLA.  
  
 Gli sviluppatori possono utilizzare XMLA per integrare un'applicazione client con [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], senza dipendenze dalle interfacce .NET Framework o COM. I requisiti delle applicazioni che includono l'hosting su un'ampia gamma di piattaforme possono essere soddisfatti tramite XMLA e una connessione HTTP a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è completamente conforme alla specifica del 1.1 di XMLA, estendendola inoltre all'abilitazione del supporto della definizione, della modifica e del controllo dei dati. Le estensioni di Analysis Services vengono denominate ASSL (Analysis Services Scripting Language). L'utilizzo combinato di XMLA e ASSL abilita un set di funzionalità più ampio rispetto a quello fornito dal solo protocollo XMLA. Per ulteriori informazioni su ASSL, vedere [lo sviluppo con Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Gestione di connessioni e sessioni di &#40;XMLA&#41;](managing-connections-and-sessions-xmla.md)|Viene descritto come connettersi a un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e come gestire sessioni e informazioni sullo stato in XMLA.|  
|[Gestione degli errori e avvisi di &#40;XMLA&#41;](handling-errors-and-warnings-xmla.md)|Descrive il modo in cui [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] restituisce le informazioni di errore e di avviso per metodi e comandi in XMLA.|  
|[Definizione e identificazione di oggetti &#40;XMLA&#41;](../xmla/xml-elements-objects.md)|Descrive identificatori di oggetto e riferimenti all'oggetto e il modo in cui utilizzarli in comandi XMLA.|  
|[La gestione delle transazioni &#40;XMLA&#41;](managing-transactions-xmla.md)|Illustra in dettaglio come utilizzare il [BeginTransaction](../xmla/xml-elements-commands/begintransaction-element-xmla.md), [CommitTransaction](../xmla/xml-elements-commands/committransaction-element-xmla.md), e [RollbackTransaction](../xmla/xml-elements-commands/rollbacktransaction-element-xmla.md) comandi per definire e gestire una transazione su XMLA corrente in modo esplicito sessione.|  
|[Annullamento di comandi &#40;XMLA&#41;](../multidimensional-models-scripting-language-assl-xmla/canceling-commands-xmla.md)|Viene descritto come utilizzare il [annullare](../xmla/xml-elements-commands/cancel-element-xmla.md)comando per annullare comandi, sessioni e connessioni in XMLA.|  
|[Esecuzione di operazioni Batch &#40;XMLA&#41;](performing-batch-operations-xmla.md)|Viene descritto come utilizzare il [Batch](../xmla/xml-elements-commands/batch-element-xmla.md) comando da eseguire XMLA più comandi, in serie o in parallelo, all'interno della stessa transazione o come transazioni separate, utilizzando un unico [Execute](../xmla/xml-elements-methods-execute.md) metodo.|  
|[Creazione e modifica di oggetti &#40;XMLA&#41;](creating-and-altering-objects-xmla.md)|Viene descritto come utilizzare il [Create](../xmla/xml-elements-commands/create-element-xmla.md), [Alter](../xmla/xml-elements-commands/alter-element-xmla.md), e [eliminare](../xmla/xml-elements-commands/delete-element-xmla.md) comandi, insieme a elementi di Analysis Services Scripting Language (ASSL), per definire, modificare o rimuovere oggetti da un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] istanza.|  
|[Blocco e sblocco di database &#40;XMLA&#41;](locking-and-unlocking-databases-xmla.md)|Illustra in dettaglio come utilizzare il [blocco](../xmla/xml-elements-commands/lock-element-xmla.md) e [Unlock](../xmla/xml-elements-commands/unlock-element-xmla.md) comandi per bloccare e sbloccare un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.|  
|[L'elaborazione di oggetti &#40;XMLA&#41;](processing-objects-xmla.md)|Viene descritto come utilizzare il [processo](../xmla/xml-elements-commands/process-element-xmla.md) comando al processo un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oggetto.|  
|[Unione di partizioni &#40;XMLA&#41;](merging-partitions-xmla.md)|Viene descritto come utilizzare il [MergePartitions](../xmla/xml-elements-commands/mergepartitions-element-xmla.md) comando per unire partizioni in un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] istanza.|  
|[Progettazione di aggregazioni &#40;XMLA&#41;](designing-aggregations-xmla.md)|Viene descritto come utilizzare il [DesignAggregations](../xmla/xml-elements-commands/designaggregations-element-xmla.md) comando, in iterativo o in modalità batch, per progettare aggregazioni per una progettazione delle aggregazioni in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Backup, ripristino e la sincronizzazione dei database &#40;XMLA&#41;](backing-up-restoring-and-synchronizing-databases-xmla.md)|Viene descritto come utilizzare il [Backup](../xmla/xml-elements-commands/backup-element-xmla.md) e [ripristinare](../xmla/xml-elements-commands/restore-element-xmla.md) comandi per eseguire il backup e ripristinare un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database da un file di backup.<br /><br /> Viene inoltre descritto come utilizzare il [Synchronize](../xmla/xml-elements-commands/synchronize-element-xmla.md) comando per sincronizzare un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database con un database esistente nella stessa istanza o in un'istanza diversa.|  
|[Inserimento, aggiornamento ed eliminazione di membri &#40;XMLA&#41;](inserting-updating-and-dropping-members-xmla.md)|Viene descritto come utilizzare il [inserire](../xmla/xml-elements-commands/insert-element-xmla.md), [aggiornamento](../xmla/xml-elements-commands/update-element-xmla.md), e [eliminare](../xmla/xml-elements-commands/drop-element-xmla.md) comandi da aggiungere, modificare o eliminare membri da una dimensione abilitata per la scrittura.|  
|[Aggiornamento di celle &#40;XMLA&#41;](updating-cells-xmla.md)|Viene descritto come utilizzare il [UpdateCells](../xmla/xml-elements-commands/updatecells-element-xmla.md) comando per modificare i valori delle celle in una partizione abilitata per la scrittura.|  
|[Gestione delle cache &#40;XMLA&#41;](managing-caches-xmla.md)|Illustra in dettaglio come utilizzare il [ClearCache](../xmla/xml-elements-commands/clearcache-element-xmla.md) comando per cancellare le cache di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oggetti.|  
|[Monitoraggio di tracce &#40;XMLA&#41;](monitoring-traces-xmla.md)|Viene descritto come utilizzare il [Sottoscrivi](../xmla/xml-elements-commands/subscribe-element-xmla.md) comando per sottoscrivere e monitorare una traccia esistente in un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] istanza.|  
  
## <a name="data-mining-with-xmla"></a>Data mining in XMLA  
 In XML for Analysis sono completamente supportati i set di righe dello schema di data mining. Questi set di righe forniscono informazioni per eseguire query sui modelli di data mining utilizzando il [Discover](../xmla/xml-elements-methods-discover.md) metodo. Per ulteriori informazioni sui set di righe dello schema di data mining, vedere [set di righe dello Schema di Data Mining](../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
 Per ulteriori informazioni su DMX, vedere [DMX &#40;DMX&#41; riferimento](/sql/dmx/data-mining-extensions-dmx-reference).  
  
## <a name="namespace-and-schema"></a>Spazio dei nomi e schema  
  
### <a name="namespace"></a>Namespace  
 Lo schema definito in questa specifica utilizza lo spazio dei nomi XML http://schemas.microsoft.com/AnalysisServices/2003/Engine e l'abbreviazione standard "DDL".  
  
### <a name="schema"></a>schema  
 La definizione di uno schema XML Schema Definition Language (XSD) per il linguaggio di definizione dell'oggetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è basata sulla definizione degli elementi e della gerarchia dello schema descritti in questa sezione.  
  
## <a name="extensibility"></a>Estendibilità  
 L'estendibilità dello schema del linguaggio di definizione dell'oggetto viene fornito tramite un elemento `Annotation` incluso in tutti gli oggetti. Tale elemento può contenere qualsiasi valore XML valido da qualsiasi spazio dei nomi XML (diverso dallo spazio dei nomi di destinazione che definisce il linguaggio DDL), soggetto alle regole seguenti:  
  
-   Il valore XML può contenere solo elementi.  
  
-   Ogni elemento deve avere un nome univoco. È consigliabile che il valore dell'elemento `Name` faccia riferimento allo spazio dei nomi di destinazione.  
  
 Queste regole vengono imposte per consentire l'esposizione del tag `Annotation` come set di coppie nome/valore tramite altre interfacce, ad esempio DSO (Decision Support Objects) 9.0.  
  
 I commenti e gli spazi vuoti all'interno del tag `Annotation` non inclusi in un elemento figlio non possono essere mantenuti. Tutti gli elementi devono inoltre essere di lettura/scrittura. Gli elementi di sola lettura vengono ignorati.  
  
 Lo schema del linguaggio di definizione dell'oggetto è chiuso, poiché il server non consente la sostituzione di tipi derivati per gli elementi definiti nello schema. Di conseguenza il server accetta solo il set di elementi definito in questa sezione e nessun altro elemento né attributo. Gli elementi sconosciuti provocano la generazione di un errore da parte del motore di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo con Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Informazioni sull'architettura Microsoft OLAP](../multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  
