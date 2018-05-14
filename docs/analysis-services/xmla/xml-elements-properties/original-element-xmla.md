---
title: Elemento Original (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ae266466fd503e1f888bdcffd02f3cf2b066050a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="original-element-xmla"></a>Elemento Original (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene il percorso di archiviazione del sistema file originale utilizzato da un [cartella](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Folder>  
   ...  
   <Original>...</Original>  
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
 Il **originale** elemento contiene un percorso UNC da sostituire con il valore di [nuovo](../../../analysis-services/xmla/xml-elements-properties/new-element-xmla.md) elemento contenuto nell'elemento padre **cartella** elemento per tutti gli oggetti ripristinati o sincronizzati, rispettivamente, durante un [ripristinare](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) o [Sincronizza](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) comando. Il valore di questo elemento viene confrontato con il valore della [StorageLocation](../../../analysis-services/scripting/properties/storagelocation-element-assl.md) elemento per ogni cubo, gruppo di misure o partizione e, se viene trovata una corrispondenza, il valore della **New** elemento viene usato per aggiornare il  **StorageLocation** dell'oggetto durante il ripristino o la sincronizzazione.  
  
 Per ulteriori informazioni sul backup e ripristino di oggetti, vedere [backup, ripristino e sincronizzazione di database & #40; XMLA & #41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
