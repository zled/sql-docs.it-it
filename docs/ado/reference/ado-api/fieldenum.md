---
title: FieldEnum | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- FieldEnum
helpviewer_keywords:
- FieldEnum enumeration [ADO]
ms.assetid: be4eda13-d4e4-4d6b-bb0d-3310b0a96fc2
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1a8533cd43964bf7bd2a456ff2cadce1be00b223
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="fieldenum"></a>FieldEnum
Specifica i campi speciali a cui fa riferimento un [Record](../../../ado/reference/ado-api/record-object-ado.md) dell'oggetto [campi](../../../ado/reference/ado-api/fields-collection-ado.md) insieme.  
  
## <a name="remarks"></a>Osservazioni  
 Queste costanti rappresentano un "collegamento" per accedere ai campi speciali associati a un **Record**. Recuperare il [campo](../../../ado/reference/ado-api/field-object.md) dall'oggetto di **campi** raccolta, quindi ottenere il contenuto con il **campo** dell'oggetto [valore](../../../ado/reference/ado-api/value-property-ado.md) proprietà.  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adDefaultStream**|-1|Fa riferimento al campo che contiene il valore predefinito [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto associato a un **Record**.|  
|**adRecordURL**|-2|Fa riferimento al campo che contiene la stringa URL assoluta per l'oggetto corrente **Record**.|

