---
title: Elemento NameColumn (ASSL) | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 83037e86aaa9afe53aa4fbfb08305be63c4f9cf1
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34035592"
---
# <a name="namecolumn-element-assl"></a>Elemento NameColumn (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Identifica la colonna che fornisce il nome dell'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionAttribute> <!-- or ScalarMiningStructureColumn -->  
   ...  
   <NameColumn xsi:type="DataItem">...</NameColumn>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|Valore predefinito|Vedere la tabella riportata di seguito.|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
|Predecessore o padre|Valore predefinito|  
|------------------------|-------------------|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|Varies (see Remarks)|  
|[ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|Nessuno|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md), [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Se il [KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md) insieme di **DimensionAttribute** contiene un singolo [KeyColumn](../../../analysis-services/scripting/objects/keycolumn-element-assl.md) elemento che rappresenta una colonna con tipo di dati stringa, la stessa chiave **DataItem** valori vengono utilizzati come valori predefiniti per il **NameColumn** elemento.  
  
 Per ulteriori informazioni sul **DataItem** tipo, inclusa una tabella di oggetti di Analysis Services Scripting Language (ASSL) e le proprietà del **DataItem** del tipo, vedere [il tipo di dati DataItem & #40; ASSL & #41; ](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
 Gli elementi che corrispondono ai padri di **NameColumn** nel modello a oggetti oggetti AMO (Analysis Management) sono <xref:Microsoft.AnalysisServices.DimensionAttribute> e <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetti & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
