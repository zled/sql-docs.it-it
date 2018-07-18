---
title: Elemento MergePartitions (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 937ea7bb52e1b1ab4be992b5a8415edd51e680a9
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34573953"
---
# <a name="mergepartitions-element-xmla"></a>Elemento MergePartitions (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Unisce i dati di una o più partizioni di origine in una partizione di destinazione e quindi elimina le partizioni di origine.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <MergePartitions>  
      <Sources>...</Sources>  
      <Target>...</Target>  
   </MergePartitions>  
</Command>  
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
|Elementi padre|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|[Origini](../../../analysis-services/xmla/xml-elements-properties/sources-element-xmla.md), [destinazione](../../../analysis-services/xmla/xml-elements-properties/target-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 Tutti i riferimenti nell'oggetto di **origini** e **destinazione** elementi devono puntare alle partizioni distinte nello stesso gruppo di misure. In caso contrario si verifica un errore.  
  
## <a name="see-also"></a>Vedere anche
 [I comandi &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
