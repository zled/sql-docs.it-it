---
title: Elemento Collation (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Collation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Collation
helpviewer_keywords:
- Collation element
ms.assetid: 9b6dbe19-543e-43e6-abe9-1e8b4dfaa275
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 410baddd86da9d6100cd3ef7342501fed955b847
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48178071"
---
# <a name="collation-element-assl"></a>Elemento Collation (ASSL)
  Determina le regole di confronto usate dall’elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Database> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Collation>...</Collation>  
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
|Elementi padre|[Cubo](../objects/cube-element-assl.md), [Database](../objects/database-element-assl.md), [DataItem](../data-type/dataitem-data-type-assl.md), [dimensione](../objects/dimension-element-assl.md), [MiningModel](../objects/miningmodel-element-assl.md), [MiningStructure](../objects/miningstructure-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 La `Collation` stringa consiste nell'identificatore delle impostazioni locali (LCID) e nel flag di confronto, separati da un carattere di sottolineatura. Ad esempio, Latin1_General_CI_AS è una stringa accettabile.  
  
 Gli elementi che corrispondono ai padri di `Collation` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.DataItem>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.MiningModel> e <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
