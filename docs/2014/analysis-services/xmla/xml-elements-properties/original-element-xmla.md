---
title: Elemento Original (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Original Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.original
- http://schemas.microsoft.com/analysisservices/2003/engine#Original
- urn:schemas-microsoft-com:xml-analysis#Original
helpviewer_keywords:
- Original element
ms.assetid: c98a3700-ac19-4341-85d9-5afedf662601
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b09f2388c47206b1b879a5c8dc98f10a28675342
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48212071"
---
# <a name="original-element-xmla"></a>Elemento Original (XMLA)
  Contiene il percorso di archiviazione del sistema file originale utilizzato da un [cartella](folder-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Folder>  
   ...  
   <Original>...</Original>  
   ...  
</Folder>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Cartella](folder-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il `Original` elemento contiene un percorso UNC da sostituire con il valore della [New](new-element-xmla.md) elemento contenuto nell'elemento padre `Folder` per tutti gli oggetti ripristinati o sincronizzati rispettivamente durante un [ripristinare ](../xml-elements-commands/restore-element-xmla.md) oppure [Synchronize](../xml-elements-commands/synchronize-element-xmla.md) comando. Il valore di questo elemento viene confrontato con il valore della [StorageLocation](../../scripting/properties/storagelocation-element-assl.md) (elemento) per ogni cubo, gruppo di misure o partizione e, se viene trovata una corrispondenza, il valore del `New` elemento viene usato per aggiornare il `StorageLocation` del oggetto durante il ripristino o la sincronizzazione.  
  
 Per altre informazioni sul backup e ripristino degli oggetti, vedere [backup, ripristino e sincronizzazione di database &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
