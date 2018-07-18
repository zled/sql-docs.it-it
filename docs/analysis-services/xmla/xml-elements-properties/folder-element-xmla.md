---
title: Elemento Folder (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 47919671460d83e4b7c470c110da8d002c6ba53f
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34575153"
---
# <a name="folder-element-xmla"></a>Elemento Folder (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene un percorso di archiviazione di file system da aggiornare per un [percorso](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) elemento durante un [ripristinare](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) o [Sincronizza](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) comando.  
  
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
|Elementi padre|[Cartelle](../../../analysis-services/xmla/xml-elements-properties/folders-element-xmla.md)|  
|Elementi figlio|[Nuova](../../../analysis-services/xmla/xml-elements-properties/new-element-xmla.md), [originale](../../../analysis-services/xmla/xml-elements-properties/original-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 Il **cartella** elemento, se specificato, viene modificata l'archiviazione posizioni degli oggetti contenuti tramite il file di backup (per **ripristinare** comandi) o il database nell'istanza di origine (per  **Sincronizzare** comandi) che corrisponde al valore del **originale** elemento al valore del **New** elemento.  
  
 Per ulteriori informazioni sul backup e ripristino degli oggetti, vedere [backup, ripristino e sincronizzazione di database &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Vedere anche
 [Elemento StorageLocation &#40;ASSL&#41;](../../../analysis-services/scripting/properties/storagelocation-element-assl.md)   
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
