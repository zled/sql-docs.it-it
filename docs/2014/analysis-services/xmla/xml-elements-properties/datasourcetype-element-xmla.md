---
title: Elemento DataSourceType (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DataSourceType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#DataSourceType
- microsoft.xml.analysis.datasourcetype
- http://schemas.microsoft.com/analysisservices/2003/engine#DataSourceType
helpviewer_keywords:
- DataSourceType element
ms.assetid: f5a348b1-911b-4139-832e-4bcb6d80a728
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 54e374aad3980582f0653bc2e36c519b87d4a27b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48169131"
---
# <a name="datasourcetype-element-xmla"></a>Elemento DataSourceType (XMLA)
  Indica se un [posizione](location-element-xmla.md) elemento specificato per un [ripristinare](../xml-elements-commands/restore-element-xmla.md) oppure [Sincronizza](../xml-elements-commands/synchronize-element-xmla.md) comando è locale o remoto.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Location>  
   ...  
   <DataSourceType>...</DataSourceType>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Remote*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Percorso](location-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 L'elemento `DataSourceType` determina se l'origine dati definita dall'elemento `Location` contiene un'origine dati locale o un'origine dati remota. Per altre informazioni sul backup e ripristino di partizioni remote, vedere [backup, ripristino e sincronizzazione di database &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*locale*|L'elemento `Location` definisce un'origine dati locale. Se questo valore è utilizzato, i comandi `Restore` e `Synchronize` utilizzano le informazioni per aggiornare l'origine dati definite nell'elemento `Location`, recuperate dal file di backup specificato nell'elemento `File` per il comando `Backup` o dal database specificato nell'elemento `Source` per il comando `Synchronize`, identificato nell'elemento `DataSourceID` dell'elemento `Location`.<br /><br /> Questo valore consente a oggetti che utilizzano l’archiviazione relazionale OLAP (ROLAP), dopo il ripristino o la sincronizzazione, di utilizzare un database diverso per i dati e i metadati. **Nota:** dati ROLAP, ad esempio i dati nelle tabelle delle dimensioni o tabelle writeback, non vengano ripristinati o sincronizzati. Solo i metadati per gli oggetti ROLAP vengono ripristinati o sincronizzati.|  
|*Remote*|L'elemento `Location` definisce un'origine dati remota. Se viene utilizzato questo valore, i comandi `Restore` e `Synchronize` utilizzano le informazioni per ripristinare o sincronizzare partizioni remote definite nell'elemento `Location`, recuperate dal file di backup specificato nell'elemento `File` del comando `Backup` o il database specificato nell'elemento `Source` per il comando `Synchronize`, all'istanza remota identificata in `DataSourceID` dell'elemento `Location`.|  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento ConnectionString &#40;XMLA&#41;](connectionstring-element-xmla.md)   
 [Elemento DataSourceID &#40;XMLA&#41;](id-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
