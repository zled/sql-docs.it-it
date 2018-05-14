---
title: Elemento Isolation (ASSL) | Documenti Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b8233ce2fc5d987dac6511fee978e45b213601a2
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="isolation-element-assl"></a>Elemento Isolation (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
|Value|Description|  
|-----------|-----------------|  
|*ReadCommitted*|Specifica che le istruzioni non possono leggere i dati modificati da altre transazioni ma di cui non è stato eseguito il commit. In questo modo vengono evitate letture dirty. Le altre transazioni possono modificare dati tra singole istruzioni all'interno della transazione corrente. Ciò comporta letture non ripetibili o dati fantasma. Il valore corrisponde al valore predefinito per l'elemento **Isolation** .|  
|*Snapshot*|Specifica che i dati letti da qualsiasi istruzione in una transazione rappresenteranno la versione consistente dal punto di vista transazionale dei dati presenti all'avvio della transazione. La transazione può rilevare solo le modifiche ai dati di cui è stato eseguito il commit prima dell'avvio della transazione. Le modifiche ai dati apportate da altre transazioni dopo l'avvio della transazione corrente non sono visibili alle istruzioni in esecuzione nella transazione corrente. Di conseguenza, è come se le istruzioni di una transazione ottenessero uno snapshot dei dati di cui è stato eseguito il commit corrispondente ai dati presenti all'avvio della transazione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
