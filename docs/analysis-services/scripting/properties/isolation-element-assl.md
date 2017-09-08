---
title: Elemento Isolation (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Isolation Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Isolation element
ms.assetid: 28c98c6f-668e-4547-8d25-127cc3995a7d
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: cc61e20927d2a547a8d86e80a61e53c60e523bb2
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="isolation-element-assl"></a>Elemento Isolation (ASSL)
  Indica il livello di isolamento per un elemento derivato dal [DataSource](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md) tipo di dati.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DataSource>  
   ...  
   <Isolation>...</Isolation>  
   ...  
</DataSource>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*ReadCommitted*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Origine dati](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore per l'elemento è limitato a una delle stringhe della tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*ReadCommitted*|Specifica che le istruzioni non possono leggere i dati modificati da altre transazioni ma di cui non è stato eseguito il commit. In questo modo vengono evitate letture dirty. Le altre transazioni possono modificare dati tra singole istruzioni all'interno della transazione corrente. Ciò comporta letture non ripetibili o dati fantasma. Il valore corrisponde al valore predefinito per l'elemento **Isolation** .|  
|*Snapshot*|Specifica che i dati letti da qualsiasi istruzione in una transazione rappresenteranno la versione consistente dal punto di vista transazionale dei dati presenti all'avvio della transazione. La transazione può rilevare solo le modifiche ai dati di cui è stato eseguito il commit prima dell'avvio della transazione. Le modifiche ai dati apportate da altre transazioni dopo l'avvio della transazione corrente non sono visibili alle istruzioni in esecuzione nella transazione corrente. Di conseguenza, è come se le istruzioni di una transazione ottenessero uno snapshot dei dati di cui è stato eseguito il commit corrispondente ai dati presenti all'avvio della transazione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
