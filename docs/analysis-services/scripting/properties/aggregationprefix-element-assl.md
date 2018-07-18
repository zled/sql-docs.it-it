---
title: Elemento AggregationPrefix (ASSL) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b23721728f8e196c47ab326024a6f514631c3b6f
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="aggregationprefix-element-assl"></a>Elemento AggregationPrefix (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce il prefisso comune da usare per i nomi di aggregazione in tutto l'elemento padre associato.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Cube> <!-- or Database, MeasureGroup, Partition -->  
   ...  
   <AggregationPrefix>...</AggregationPrefix>  
   ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Cubo](../../../analysis-services/scripting/objects/cube-element-assl.md), [Database](../../../analysis-services/scripting/objects/database-element-assl.md), [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [partizione](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 I prefissi di aggregazione generano nomi di aggregazione in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]e generare i nomi delle tabelle nel database relazionale per aggregazioni archiviate in una partizione OLAP (ROLAP) relazionali.  
  
 Un nome di aggregazione completamente espanso contiene le parti seguenti:  
  
 *\<DatabasePrefix >\<CubePrefix >\<MeasureGroupPrefix >\<PartitionPrefix >\<AggregationID >*  
  
 Le prime quattro parti del nome di aggregazione costituiscono il prefisso di aggregazione. L'utente fornisce le prime quattro parti:  
  
-   *DatabasePrefix* rappresenta il valore di **AggregationPrefix** associato all'elemento un **Database** elemento.  
  
-   *CubePrefix* rappresenta il valore di **AggregationPrefix** associato all'elemento un **cubo** elemento.  
  
-   *MeasureGroupPrefix* rappresenta il valore di **AggregationPrefix** associato all'elemento un **MeasureGroup** elemento.  
  
-   *PartitionPrefix* rappresenta il valore di **AggregationPrefix** associato all'elemento un **partizione** elemento.  
  
 La quinta parte del nome, *AggregationID*, è un ID definito dal sistema e gli utenti non hanno controllo su questa parte del nome.  
  
 Gli elementi che corrispondono ai padri di **AggregationPrefix** nel modello a oggetti oggetti AMO (Analysis Management) sono <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.MeasureGroup>, e <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
