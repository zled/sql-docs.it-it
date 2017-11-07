---
title: Elemento AggregationPrefix (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- AggregationPrefix Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AggregationPrefix
helpviewer_keywords:
- AggregationPrefix element
ms.assetid: 1581e0df-ae8e-41ce-9c92-f0f7cac487f2
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8ef1688e23bddf1136775474c93ae62a05bb97ab
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="aggregationprefix-element-assl"></a>Elemento AggregationPrefix (ASSL)
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
  
-   *DatabasePrefix* rappresenta il valore della **AggregationPrefix** elemento associato a un **Database** elemento.  
  
-   *CubePrefix* rappresenta il valore della **AggregationPrefix** elemento associato a un **cubo** elemento.  
  
-   *MeasureGroupPrefix* rappresenta il valore della **AggregationPrefix** elemento associato a un **MeasureGroup** elemento.  
  
-   *PartitionPrefix* rappresenta il valore della **AggregationPrefix** elemento associato a un **partizione** elemento.  
  
 La quinta parte del nome, *AggregationID*, è un ID definito dal sistema e gli utenti non hanno controllo su questa parte del nome.  
  
 Gli elementi che corrispondono ai padri di **AggregationPrefix** nel modello a oggetti oggetti AMO (Analysis Management) sono <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.MeasureGroup>, e <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

