---
title: Elemento SkippedLevelsColumn (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9727a5080437352bebbfa9c7ced1cd3c88689113
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48141731"
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
  
## <a name="remarks"></a>Note  
 Il `SkippedLevelsColumn` elemento è applicabile solo agli attributi padre (in altre parole, il valore della [utilizzo](../properties/usage-element-dimensionattribute-assl.md) (elemento) per il `DimensionAttribute` padre è impostato su *padre*). L'elemento `SkippedLevelsColumn` contiene la colonna o l'attributo per l'attributo padre che archivia il numero di livelli ignorati tra ogni membro e il relativo membro padre. Questo consente alle gerarchie padre-figlio basate sull'attributo padre di ignorare i livelli tra i membri. I valori contenuti in questa colonna o attributo devono essere numeri interi non negativi. In caso contrario, si verifica un errore di elaborazione. Se l'elemento `SkippedLevelsColumn` non è specificato o non contiene alcun valore, il membro corrente ha una profondità di un livello sotto il relativo membro padre.  
  
 Per altre informazioni sul `DataItem` tipo, inclusa una tabella di oggetti di Analysis Services Scripting Language (ASSL) e le proprietà della `DataItem` tabella, vedere [tipo di dati DataItem &#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md).  
  
 L'elemento che corrisponde al padre di `SkippedLevelsColumn` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Attributes &#40;ASSL&#41;](../collections/attributes-element-assl.md)   
 [Elemento della dimensione &#40;ASSL&#41;](dimension-element-assl.md)   
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
