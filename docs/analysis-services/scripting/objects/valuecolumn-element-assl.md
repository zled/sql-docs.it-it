---
title: Elemento ValueColumn (ASSL) | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 778f59678183b39817f66ee12ed28894bd464504
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="valuecolumn-element-assl"></a>Elemento ValueColumn (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Identifica la colonna che fornisce il valore dell'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <ValueColumn xsi:type="DataItem">...</ValueColumn>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|Valore predefinito|Varies (see Remarks)|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Se il [NameColumn](../../../analysis-services/scripting/objects/namecolumn-element-assl.md) elemento **DimensionAttribute** è specificato, lo stesso **DataItem** valori vengono utilizzati come valori predefiniti per il **ValueColumn** elemento. Se il **NameColumn** elemento di **DimensionAttribute** viene omesso e [KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md) insieme di **DimensionAttribute** contiene un singolo [KeyColumn](../../../analysis-services/scripting/objects/keycolumn-element-assl.md) elemento che rappresenta una colonna con tipo di dati stringa, la stessa chiave **DataItem** valori vengono utilizzati come valori predefiniti per il **ValueColumn** elemento.  
  
 Per ulteriori informazioni sul **DataItem** tipo, inclusa una tabella di oggetti di Analysis Services Scripting Language (ASSL) e le proprietà del **DataItem** del tipo, vedere [il tipo di dati DataItem & #40; ASSL & #41; ](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
 Gli elementi che corrispondono ai padri di **NameColumn** nel modello a oggetti oggetti AMO (Analysis Management) sono <xref:Microsoft.AnalysisServices.DimensionAttribute> e <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetti & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
