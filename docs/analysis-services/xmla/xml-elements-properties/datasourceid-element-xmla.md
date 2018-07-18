---
title: Elemento DataSourceID (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 883fa5df355874516ffd6f0cac01ff50d727d737
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37979143"
---
# <a name="datasourceid-element-xmla"></a>Elemento DataSourceID (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Identifica un'origine dati utilizzata da un [posizione](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) elemento durante una [Backup](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [Restore](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md), o [Sincronizza](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) comando.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Location>  
   ...  
   <DataSourceID>...</DataSourceID>  
   ...  
</Location>  
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
|Elementi padre|[Percorso](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il **DataSourceID** elemento contiene il nome dell'origine dati nell'istanza di origine che identifica l'istanza remota in cui deve essere eseguito il backup, ripristinati o sincronizzati informazioni sulle partizioni remote.  
  
 Per altre informazioni sul backup e ripristino di partizioni remote, vedere [backup, ripristino e sincronizzazione di database &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Vedere anche
 [Elemento ConnectionString &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/connectionstring-element-xmla.md)   
 [Elemento DataSourceType &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/datasourcetype-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
