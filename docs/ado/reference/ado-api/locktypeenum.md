---
title: LockTypeEnum | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- LockTypeEnum
helpviewer_keywords:
- LockTypeEnum enumeration [ADO]
ms.assetid: d2894eaf-4450-4ace-aa51-c8b875fd3010
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a4137ced62a083bb355a685222a044fdd9efacdf
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35279220"
---
# <a name="locktypeenum"></a>LockTypeEnum
Specifica il tipo di blocco applicato ai record durante la modifica.  
  
|Costante|valore|Description|  
|--------------|-----------|-----------------|  
|**adLockBatchOptimistic**|4|Indica gli aggiornamenti batch ottimistica. Obbligatorio per la modalità di aggiornamento batch.|  
|**adLockOptimistic**|3|Indica il blocco ottimistico, un record. Il provider utilizza il blocco ottimistico, bloccare i record solo quando si chiama il [aggiornamento](../../../ado/reference/ado-api/update-method.md) metodo.|  
|**adLockPessimistic**|2|Indica il blocco pessimistico, un record. Il provider non sia necessaria per garantire la corretta modifica dei record, in genere bloccando i record nell'origine dati dopo la modifica.|  
|**adLockReadOnly**|1|Indica i record di sola lettura. È possibile modificare i dati.|  
|**adLockUnspecified**|-1|Non specifica un tipo di blocco. Per i cloni, il clone viene creato con lo stesso tipo di blocco dell'originale.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Package: **com.ms.wfc.data**  
  
|Costante|  
|--------------|  
|AdoEnums.LockType.BATCHOPTIMISTIC|  
|AdoEnums.LockType.OPTIMISTIC|  
|AdoEnums.LockType.PESSIMISTIC|  
|AdoEnums.LockType.READONLY|  
|AdoEnums.LockType.UNSPECIFIED|  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Metodo Clone (ADO)](../../../ado/reference/ado-api/clone-method-ado.md)|[Proprietà LockType (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)|  
|[Metodo Open (Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|[Evento WillExecute (ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)|
