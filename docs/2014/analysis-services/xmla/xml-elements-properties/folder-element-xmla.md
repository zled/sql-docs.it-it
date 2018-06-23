---
title: Elemento Folder (XMLA) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Folder Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.folder
- http://schemas.microsoft.com/analysisservices/2003/engine#Folder
- urn:schemas-microsoft-com:xml-analysis#Folder
helpviewer_keywords:
- Folder element
ms.assetid: 87b305b0-57e3-4ec3-9d80-f1bcf3ce7540
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 64bc73db4cfb1fee4471e474bf498094751edcf5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067884"
---
# <a name="folder-element-xmla"></a>Elemento Folder (XMLA)
  Contiene un percorso di archiviazione di file system da aggiornare per un [posizione](location-element-xmla.md) elemento durante un [ripristinare](../xml-elements-commands/restore-element-xmla.md) oppure [Synchronize](../xml-elements-commands/synchronize-element-xmla.md) comando.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Folders>  
   ...  
   <Folder>  
      <Original>...</Original>  
      <New>...</New>  
   </Folder>  
   ...  
</Folders>  
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
|Elementi padre|[Cartelle](folders-element-xmla.md)|  
|Elementi figlio|[Nuova](new-element-xmla.md), [originale](original-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 L'elemento `Folder`, se specificato, modifica le posizioni di archiviazione degli oggetti contenuti nel file di backup (per i comandi `Restore` ) o nel database dell'istanza di origine (per i comandi `Synchronize` ) in modo che il valore dell'elemento `Original` corrisponda a quello dell'elemento `New`.  
  
 Per ulteriori informazioni sul backup e ripristino degli oggetti, vedere [backup, ripristino e sincronizzazione di database &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento StorageLocation &#40;ASSL&#41;](../../scripting/properties/storagelocation-element-assl.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  