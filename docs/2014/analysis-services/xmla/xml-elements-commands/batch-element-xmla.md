---
title: Batch elemento (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Batch Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Batch
- microsoft.xml.analysis.batch
- http://schemas.microsoft.com/analysisservices/2003/engine#Batch
helpviewer_keywords:
- Batch command
ms.assetid: 818f3212-9605-4e34-8623-1154d9fae1f0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d402c1f6c35370a506ed57c43b8fbc05d0b6bef7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48178141"
---
# <a name="batch-element-xmla"></a>Elemento Batch (XMLA)
  Esegue uno o più XML per i comandi Analysis (XMLA) come operazione batch, in sequenza o in parallelo, in un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <Batch Transaction="Boolean" ProcessAffectedObjects="Boolean">  
      <Bindings>...</Bindings>  
      <DataSource>...</DataSource>  
      <DataSourceView>...</DataSourceView>  
      <ErrorConfiguration>...</ErrorConfiguration>  
      <Parallel>...</Parallel>  
      <!-- One or more XMLA commands -->  
   </Batch>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Command](../xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|[Associazioni](../xml-elements-properties/bindings-element-xmla.md), [DataSource](../xml-elements-properties/source-element-xmla.md), [DataSourceView](../xml-elements-properties/datasourceview-element-xmla.md), [ErrorConfiguration](../../scripting/objects/errorconfiguration-element-assl.md), [parallele](../xml-elements-properties/parallel-element-xmla.md)<br /><br /> Uno o più dei seguenti comandi XMLA: [Alter](alter-element-xmla.md), [Backup](backup-element-xmla.md), [BeginTransaction](begintransaction-element-xmla.md), [ClearCache](clearcache-element-xmla.md), [ CommitTransaction](committransaction-element-xmla.md), [creare](create-element-xmla.md), [eliminare](delete-element-xmla.md), [DesignAggregations](designaggregations-element-xmla.md), [Drop](drop-element-xmla.md), [Inserire](insert-element-xmla.md), [Lock](lock-element-xmla.md), [MergePartitions](mergepartitions-element-xmla.md), [NotifyTableChange](notifytablechange-element-xmla.md), [processo](process-element-xmla.md), [Ripristinare](restore-element-xmla.md), [RollbackTransaction](rollbacktransaction-element-xmla.md), [SetPasswordEncryptionKey](http://msdn.microsoft.com/en-us/fb262737-f0f4-4441-985e-3b2a94d00a9e), [istruzione](statement-element-xmla.md), [sottoscrizione](subscribe-element-xmla.md), [Sincronizzare](synchronize-element-xmla.md), [sbloccare](unlock-element-xmla.md), [Update](update-element-xmla.md), [UpdateCells](drop-element-xmla.md)|  
  
## <a name="attributes"></a>Attributi  
  
|attribute|Description|  
|---------------|-----------------|  
|ProcessAffectedObjects|(Attributo `Boolean` facoltativo) Indica se tutti gli oggetti che richiedono la rielaborazione saranno elaborati.<br /><br /> Se è impostato su True, l'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] elabora qualsiasi oggetto che richiede la rielaborazione in seguito all'elaborazione di un oggetto incluso nel comando `Batch`.<br /><br /> Se è impostato su `false`, l'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] elabora solo gli oggetti inclusi nel comando `Batch`.|  
|Transaction|(Attributo `Boolean` facoltativo) Indica se i comandi inclusi nel comando `Batch` vengono trattati come una singola transazione o come transazioni separate.<br /><br /> Se è impostato su True, tutti i comandi inclusi nel comando `Batch` sono considerati come una singola transazione. Se un comando ha esito negativo, viene eseguito il rollback dei comandi eseguiti prima di tale comando e il comando `Batch` si arresta senza eseguire i comandi successivi.<br /><br /> Se è impostato su `false`, il comando `Batch` tenta di eseguire ogni comando ed esegue il commit dei risultati di ogni comando completato correttamente.|  
  
## <a name="remarks"></a>Note  
  
> [!WARNING]  
>  In un'operazione Batch non è attualmente supportato un comando, un'esecuzione o un'istruzione.  
  
 Per altre informazioni sull'esecuzione di operazioni batch in XMLA, vedere [esecuzione di operazioni Batch &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/performing-batch-operations-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [I comandi &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
