---
title: Elemento DiscretizationMethod (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DiscretizationMethod Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DiscretizationMethod
helpviewer_keywords:
- DiscretizationMethod element
ms.assetid: 4cfe015f-ad6c-47e1-8aff-c9c7677867b1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 75308b5270eb762236be22fc0838a480474898dc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200476"
---
# <a name="discretizationmethod-element-assl"></a>Elemento DiscretizationMethod (ASSL)
  Definisce il metodo da usare per la discretizzazione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionAttribute> <!-- or ScalarMiningStructureColumn -->  
   ...  
   <DiscretizationMethod>...</DiscretizationMethod>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Nessuno*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore dell'elemento `DiscretizationMethod` determina la modalità di discretizzazione dei valori per `DimensionAttribute` o `ScalarMiningStructureColumn` oppure il modo in cui tali valori vengono organizzati in un set di gruppi specifico. Per altre informazioni sui metodi di discretizzazione, vedere [metodi di discretizzazione &#40;Data Mining&#41;](../../data-mining/discretization-methods-data-mining.md).  
  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Automatico*|Equivale al metodo di discretizzazione AUTOMATIC per le colonne della struttura di data mining.|  
|*EqualAreas*|Equivale al metodo di discretizzazione EQUAL_AREAS per le colonne della struttura di data mining.|  
|*Cluster*|Equivale al metodo di discretizzazione CLUSTERS per le colonne della struttura di data mining.|  
|*Thresholds*|Equivale al metodo di discretizzazione THRESHOLDS per le colonne della struttura di data mining.|  
|*EqualRanges*|Equivale al metodo di discretizzazione EQUAL_RANGES per le colonne della struttura di data mining.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `DiscretizationMethod` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.DiscretizationMethod>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
