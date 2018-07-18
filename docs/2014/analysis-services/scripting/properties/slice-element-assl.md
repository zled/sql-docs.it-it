---
title: Slice (ASSL) elemento | Microsoft Docs
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
- Slice Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Slice
helpviewer_keywords:
- Slice element
ms.assetid: 2c8c4107-c641-4724-bfa5-0c47e0ec8888
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 299f84167ec64c4bdd795c56a608e76f61d348b0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37178888"
---
# <a name="slice-element-assl"></a>Elemento Slice (ASSL)
  Contiene un'espressione MDX (Multidimensional Expressions) che definisce la sezione contenuta in una partizione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Partition>  
      ...  
   <Slice>...</Slice>  
   ...  
</Partition>  
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
|Elemento padre|[Partizione](../objects/partition-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 L'elemento `Slice` contiene un'espressione di tupla o un'espressione set MDX che identifica la parte del cubo per cui la partizione archivia informazioni. L'espressione MDX è simile al [StrToSet](/sql/mdx/strtoset-mdx) MDX è utilizzabile con la parola chiave CONSTRAINED, in quanto l'espressione non può includere funzioni MDX o definite dall'utente.  
  
 L'elemento che corrisponde al padre di `Slice` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
