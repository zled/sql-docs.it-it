---
title: Batch di elemento (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b9bac80ca284993ba6239b467962217a0866054f
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="batch-element-xmla"></a>Elemento Batch (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Esegue uno o più XML per i comandi Analysis (XMLA) come un'operazione batch, in sequenza o in parallelo, in un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|[Le associazioni](../../../analysis-services/xmla/xml-elements-properties/bindings-element-xmla.md), [DataSource](../../../analysis-services/xmla/xml-elements-properties/datasource-element-xmla.md), [DataSourceView](../../../analysis-services/xmla/xml-elements-properties/datasourceview-element-xmla.md), [ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md), [paralleli](../../../analysis-services/xmla/xml-elements-properties/parallel-element-xmla.md)<br /><br /> Uno o più comandi XMLA seguenti: [Alter](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md), [Backup](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [BeginTransaction](../../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md), [ClearCache](../../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md), [ CommitTransaction](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md), [creare](../../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md), [eliminare](../../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md), [DesignAggregations](../../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md), [Drop](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md), [Inserire](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md), [Lock](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md), [MergePartitions](../../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md), [NotifyTableChange](../../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md), [processo](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md), [Ripristinare](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md), [RollbackTransaction](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md), [SetPasswordEncryptionKey](http://msdn.microsoft.com/en-us/fb262737-f0f4-4441-985e-3b2a94d00a9e), [istruzione](../../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md), [sottoscrizione](../../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md), [Sincronizzare](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md), [sbloccare](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md), [aggiornamento](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md), [UpdateCells](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)|  
  
## <a name="attributes"></a>Attributi  
  
|Attribute|Description|  
|---------------|-----------------|  
|ProcessAffectedObjects|(Facoltativo **booleano** attributo) indica se tutti gli oggetti che richiedono la rielaborazione saranno elaborati.<br /><br /> Se impostato su true, il [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza elabora tutti gli oggetti che richiedono la rielaborazione in seguito all'elaborazione di un oggetto incluso nel **Batch** comando.<br /><br /> Se impostato su **false**, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza elabora solo gli oggetti inclusi nel **Batch** comando.|  
|Transazione|(Facoltativo **booleano** attributo) indica se il comando è incluso nel **Batch** comando vengono considerati come una singola transazione o le singole transazioni.<br /><br /> Se impostato su true, tutti i comandi inclusi nel **Batch** comando sono considerati una singola transazione. Se un comando ha esito negativo, i comandi eseguiti prima del comando non riuscito il rollback e **Batch** comando Arresta senza eseguire i comandi successivi.<br /><br /> Se impostato su **false**, **Batch** comando tenta di eseguire ogni comando e viene eseguito il commit i risultati di ogni comando che viene completata correttamente.|  
  
## <a name="remarks"></a>Osservazioni  
  
> [!WARNING]  
>  In un'operazione Batch non è attualmente supportato un comando, un'esecuzione o un'istruzione.  
  
 Per ulteriori informazioni sull'esecuzione di operazioni batch in XMLA, vedere [l'esecuzione di operazioni Batch &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/performing-batch-operations-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Comandi & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
