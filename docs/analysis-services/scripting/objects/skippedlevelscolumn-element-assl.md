---
title: Elemento SkippedLevelsColumn (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: SkippedLevelsColumn Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: SkippedLevelsColumn
helpviewer_keywords: SkippedLevelsColumn element
ms.assetid: 6b00a288-99c1-4735-9e6b-cd13ed4fa346
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 58fe89ee107684bc96dfa79566569709d92aa683
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="skippedlevelscolumn-element-assl"></a>Elemento SkippedLevelsColumn (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
    
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il **SkippedLevelsColumn** elemento è applicabile solo agli attributi padre (in altre parole, il valore del [utilizzo](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md) elemento per il **DimensionAttribute** padre è impostato per *padre*). L'elemento **SkippedLevelsColumn** contiene la colonna o l'attributo per l'attributo padre che archivia il numero di livelli ignorati tra ogni membro e il relativo membro padre. Questo consente alle gerarchie padre-figlio basate sull'attributo padre di ignorare i livelli tra i membri. I valori contenuti in questa colonna o attributo devono essere numeri interi non negativi. In caso contrario, si verifica un errore di elaborazione. Se l'elemento **SkippedLevelsColumn** non è specificato o non contiene alcun valore, il membro corrente ha una profondità di un livello sotto il relativo membro padre.  
  
 Per ulteriori informazioni sul **DataItem** tipo, inclusa una tabella di oggetti di Analysis Services Scripting Language (ASSL) e le proprietà del **DataItem** tabella, vedere [il tipo di dati DataItem &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
 L'elemento che corrisponde all'elemento padre **SkippedLevelsColumn** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Attributi elemento &#40; ASSL &#41;](../../../analysis-services/scripting/collections/attributes-element-assl.md)   
 [Elemento Dimension &#40; ASSL &#41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)   
 [Oggetti &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
