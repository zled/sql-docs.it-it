---
title: Elemento IsKey (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- IsKey Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- IsKey
helpviewer_keywords:
- IsKey element
ms.assetid: 523b26c8-5cce-415d-a360-9a0d8724b872
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 525d5de1fb6935c2056dc026b57229535e7557cb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48199011"
---
# <a name="iskey-element-assl"></a>Elemento IsKey (ASSL)
  Indica se la colonna fornisce la chiave del case in una [MiningStructure](../objects/miningstructure-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ScalarMiningStructureColumn>  
   ...  
   <IsKey>...</IsKey>  
   ...  
</ScalarMiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Boolean|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Una o più colonne possono essere designate come colonne chiave per ogni livello di una struttura della tabella nidificata.  
  
 L'elemento che corrisponde al padre di `IsKey` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
