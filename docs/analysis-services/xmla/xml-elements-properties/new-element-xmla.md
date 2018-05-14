---
title: Nuovo elemento (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: acb0043613c784b5677f3446beef22b6ecc12321
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="new-element-xmla"></a>Elemento New (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene il nuovo percorso archiviazione di file system utilizzato da un [cartella](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Folder>  
   ...  
   <New>...</New>  
   ...  
</Folder>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Cartella](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il **New** elemento contiene un percorso UNC che sostituisce il valore della **originale** elemento contenuto nell'elemento padre **cartella** elemento per tutti gli oggetti ripristinati o sincronizzati, rispettivamente durante un **ripristinare** o **Sincronizza** comando. Il valore della **originale** elemento viene confrontato con il valore della **StorageLocation** elemento per ogni cubo, gruppo di misure o partizione e, se viene trovata una corrispondenza, il valore di questo elemento viene utilizzato per aggiornare il **StorageLocation** dell'oggetto durante il ripristino o la sincronizzazione.  
  
 Per ulteriori informazioni sul backup e ripristino di oggetti, vedere [backup e ripristino di oggetti (XMLA)](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Originale elemento & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/original-element-xmla.md)   
 [Ripristinare l'elemento & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Elemento StorageLocation & #40; ASSL & #41;](../../../analysis-services/scripting/properties/storagelocation-element-assl.md)   
 [Sincronizzare elemento & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [Proprietà & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
