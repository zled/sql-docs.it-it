---
title: Elemento New (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1ed98ed9c42d8cecddb07941855403925b1de6b8
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37969157"
---
# <a name="new-element-xmla"></a>Elemento New (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene il nuovo percorso archiviazione di file system usato da un [cartella](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Folder>  
   ...  
   <New>...</New>  
   ...  
</Folder>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche di elementi  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Elementi-relazioni  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Cartella](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il **New** elemento contiene un percorso UNC che sostituisce il valore della **originale** elemento contenuto nell'elemento padre **cartella** (elemento) per tutti gli oggetti ripristinati o sincronizzati, rispettivamente durante un **ripristinare** oppure **Sincronizza** comando. Il valore della **originale** elemento viene confrontato con il valore della **StorageLocation** (elemento) per ogni cubo, gruppo di misure o partizione e, se viene trovata una corrispondenza, il valore di questo elemento viene utilizzato per aggiornare il **StorageLocation** dell'oggetto durante il ripristino o la sincronizzazione.  
  
 Per altre informazioni sul backup e ripristino degli oggetti, vedere [backup e ripristino di oggetti (XMLA)](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Vedere anche
 [Elemento originale &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/original-element-xmla.md)   
 [Elemento Restore &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Elemento StorageLocation &#40;ASSL&#41;](../../../analysis-services/scripting/properties/storagelocation-element-assl.md)   
 [Elemento Synchronize &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
