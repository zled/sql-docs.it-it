---
title: Elemento Synchronize (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 11804b9b6ca9ac430bdb47c0b9050b8c6995cf7f
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38007182"
---
# <a name="synchronize-element-xmla"></a>Elemento Synchronize (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Consente di sincronizzare un database di Analysis Services con un altro database esistente.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <Synchronize>  
      <Source>...</Source>  
      <SynchronizeSecurity>...</SynchronizeSecurity>  
      <ApplyCompression>...</ApplyCompression>  
      <Locations>...</Locations>  
   </Synchronize>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche di elementi  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Elementi-relazioni  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|[ApplyCompression](../../../analysis-services/xmla/xml-elements-properties/applycompression-element-xmla.md), [posizioni](../../../analysis-services/xmla/xml-elements-properties/locations-element-xmla.md), [origine](../../../analysis-services/xmla/xml-elements-properties/source-element-synchronize-xmla.md), [SynchronizeSecurity](../../../analysis-services/xmla/xml-elements-properties/synchronizesecurity-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Il **Synchronize** comando viene sincronizzato il database di destinazione con un'istanza di origine e il database specificato nella **origine** elemento. Facoltativamente, il **Synchronize** comando Sincronizza partizioni remote definite sul database di origine.  
  
 A seconda della modalità di archiviazione utilizzata da oggetti archiviati nel file di backup, il **Synchronize** comando Sincronizza le informazioni come elencato nella tabella seguente.  
  
|Modalità di archiviazione|Informazioni|  
|------------------|-----------------|  
|OLAP multidimensionale (MOLAP)|Dati di origine, aggregazioni e metadati|  
|OLAP ibrido (HOLAP)|Aggregazioni e metadati|  
|OLAP relazionale (ROLAP)|Metadati|  
  
 Durante una **Synchronize** comando, viene inserito un blocco di lettura sul database di origine e viene inserito un blocco di scrittura nel database di destinazione. Entrambi i blocchi vengono rilasciati dopo la **Synchronize** completamento del comando.  
  
 Per altre informazioni sulla sincronizzazione di database, vedere [backup, ripristino e sincronizzazione di database &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Vedere anche
 [Elemento di backup &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)   
 [Elemento batch &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)   
 [Elemento in parallelo &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/parallel-element-xmla.md)   
 [Elemento Restore &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [I comandi &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
