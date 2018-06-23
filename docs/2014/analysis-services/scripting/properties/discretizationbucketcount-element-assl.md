---
title: Elemento DiscretizationBucketCount (ASSL) | Documenti Microsoft
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
- DiscretizationBucketCount Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DiscretizationBucketCount
helpviewer_keywords:
- DiscretizationBucketCount element
ms.assetid: 551a73ae-59e1-4079-a2d9-988df96b5e07
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e3609dcc1a5a926e4b9ecc46736a90d6620ec068
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169988"
---
# <a name="discretizationbucketcount-element-assl"></a>Elemento DiscretizationBucketCount (ASSL)
  Contiene il numero di bucket per la discretizzazione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionAttribute> <!-- or ScalarMiningStructureColumn -->  
   ...  
   <DiscretizationBucketCount>...</DiscretizationBucketCount>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Valore intero|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il valore dell'elemento `DiscretizationBucketCount` determina quanti gruppi o "bucket" vengono creati quando i valori per `DimensionAttribute` o `ScalarMiningStructureColumn` vengono discretizzati o organizzati in un set di gruppi specifico. Se l'elemento non è specificato o se per il valore dell'elemento, viene specificato zero [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] crea un numero appropriato di gruppi in base al metodo di discretizzazione. Per ulteriori informazioni sui metodi di discretizzazione, vedere [metodi di discretizzazione &#40;Data Mining&#41;](../../data-mining/discretization-methods-data-mining.md).  
  
 Gli elementi che corrispondono ai padri di `DiscretizationBucketCount` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.DimensionAttribute> e <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento DiscretizationMethod &#40;ASSL&#41;](discretizationmethod-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  