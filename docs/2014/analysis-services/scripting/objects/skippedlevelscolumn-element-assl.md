---
title: Elemento SkippedLevelsColumn (ASSL) | Documenti Microsoft
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
- SkippedLevelsColumn Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- SkippedLevelsColumn
helpviewer_keywords:
- SkippedLevelsColumn element
ms.assetid: 6b00a288-99c1-4735-9e6b-cd13ed4fa346
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3ae469982f39e1274759eaaea992fe456330d8fb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065685"
---
# <a name="skippedlevelscolumn-element-assl"></a>Elemento SkippedLevelsColumn (ASSL)
    
> [!NOTE]  
>  Questa caratteristica non è più utilizzata in questa versione di Microsoft SQL Server. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata.  
  
 Fornisce i dettagli di una colonna che archivia il numero di livelli ignorati (vuoti) tra ogni membro e il relativo elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <SkippedLevelsColumn xsi:type="DataItem">...</SkippedLevelsColumn>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il `SkippedLevelsColumn` elemento è applicabile solo agli attributi padre (in altre parole, il valore della [utilizzo](../properties/usage-element-dimensionattribute-assl.md) elemento per il `DimensionAttribute` padre è impostato su *padre*). L'elemento `SkippedLevelsColumn` contiene la colonna o l'attributo per l'attributo padre che archivia il numero di livelli ignorati tra ogni membro e il relativo membro padre. Questo consente alle gerarchie padre-figlio basate sull'attributo padre di ignorare i livelli tra i membri. I valori contenuti in questa colonna o attributo devono essere numeri interi non negativi. In caso contrario, si verifica un errore di elaborazione. Se l'elemento `SkippedLevelsColumn` non è specificato o non contiene alcun valore, il membro corrente ha una profondità di un livello sotto il relativo membro padre.  
  
 Per ulteriori informazioni sul `DataItem` tipo, inclusa una tabella di oggetti di Analysis Services Scripting Language (ASSL) e le proprietà del `DataItem` tabella, vedere [tipo di dati DataItem &#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md).  
  
 L'elemento che corrisponde al padre di `SkippedLevelsColumn` nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Attributi elemento &#40;ASSL&#41;](../collections/attributes-element-assl.md)   
 [Elemento della dimensione &#40;ASSL&#41;](dimension-element-assl.md)   
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  