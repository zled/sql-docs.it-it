---
title: Elemento Isolation (ASSL) | Documenti Microsoft
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
- Isolation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Isolation element
ms.assetid: 28c98c6f-668e-4547-8d25-127cc3995a7d
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: cdcbf79ccd1281c9f3dbaa109b3c77214ced22bf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063698"
---
# <a name="isolation-element-assl"></a>Elemento Isolation (ASSL)
  Indica il livello di isolamento per un elemento derivato dal [DataSource](../data-type/datasource-data-type-assl.md) tipo di dati.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DataSource>  
   ...  
   <Isolation>...</Isolation>  
   ...  
</DataSource>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*ReadCommitted*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Origine dati](../data-type/datasource-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il valore per l'elemento è limitato a una delle stringhe della tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*ReadCommitted*|Specifica che le istruzioni non possono leggere i dati modificati da altre transazioni ma di cui non è stato eseguito il commit. In questo modo vengono evitate letture dirty. Le altre transazioni possono modificare dati tra singole istruzioni all'interno della transazione corrente. Ciò comporta letture non ripetibili o dati fantasma. Il valore corrisponde al valore predefinito per l'elemento `Isolation`.|  
|*Snapshot*|Specifica che i dati letti da qualsiasi istruzione in una transazione rappresenteranno la versione consistente dal punto di vista transazionale dei dati presenti all'avvio della transazione. La transazione può rilevare solo le modifiche ai dati di cui è stato eseguito il commit prima dell'avvio della transazione. Le modifiche ai dati apportate da altre transazioni dopo l'avvio della transazione corrente non sono visibili alle istruzioni in esecuzione nella transazione corrente. Di conseguenza, è come se le istruzioni di una transazione ottenessero uno snapshot dei dati di cui è stato eseguito il commit corrispondente ai dati presenti all'avvio della transazione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  