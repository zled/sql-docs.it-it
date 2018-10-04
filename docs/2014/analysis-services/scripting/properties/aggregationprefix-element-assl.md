---
title: Elemento AggregationPrefix (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AggregationPrefix Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationPrefix
helpviewer_keywords:
- AggregationPrefix element
ms.assetid: 1581e0df-ae8e-41ce-9c92-f0f7cac487f2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c6cb7355644a437b7427dcd366c5f102f469135a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48121541"
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
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Cubo](../objects/cube-element-assl.md), [Database](../objects/database-element-assl.md), [MeasureGroup](../objects/group-element-assl.md), [partizione](../objects/partition-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 I prefissi di aggregazione generano nomi di aggregazione nel [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]e generare i nomi delle tabelle nel database relazionale per aggregazioni archiviate in una partizione OLAP (ROLAP) relazionali.  
  
 Un nome di aggregazione completamente espanso contiene le parti seguenti:  
  
 *\<DatabasePrefix >\<CubePrefix >\<MeasureGroupPrefix >\<PartitionPrefix >\<AggregationID >*  
  
 Le prime quattro parti del nome di aggregazione costituiscono il prefisso di aggregazione. L'utente fornisce le prime quattro parti:  
  
-   *DatabasePrefix* rappresenta il valore della `AggregationPrefix` elemento associato a un `Database` elemento.  
  
-   *CubePrefix* rappresenta il valore della `AggregationPrefix` elemento associato a un `Cube` elemento.  
  
-   *MeasureGroupPrefix* rappresenta il valore della `AggregationPrefix` elemento associato a un `MeasureGroup` elemento.  
  
-   *PartitionPrefix* rappresenta il valore della `AggregationPrefix` elemento associato a un `Partition` elemento.  
  
 La parte del nome del quinta *AggregationID*, è un ID definito dal sistema e gli utenti non dispongono di alcun controllo su questa parte del nome.  
  
 Gli elementi che corrispondono agli elementi padre di `AggregationPrefix` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.MeasureGroup> e <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
