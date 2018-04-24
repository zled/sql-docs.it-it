---
title: FieldEnum | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FieldEnum
helpviewer_keywords:
- FieldEnum enumeration [ADO]
ms.assetid: be4eda13-d4e4-4d6b-bb0d-3310b0a96fc2
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d00710700dae843695e4d1f970e2266f1113b54b
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="fieldenum"></a>FieldEnum
Specifica i campi speciali a cui fa riferimento un [Record](../../../ado/reference/ado-api/record-object-ado.md) dell'oggetto [campi](../../../ado/reference/ado-api/fields-collection-ado.md) insieme.  
  
## <a name="remarks"></a>Osservazioni  
 Queste costanti rappresentano un "collegamento" per accedere ai campi speciali associati a un **Record**. Recuperare il [campo](../../../ado/reference/ado-api/field-object.md) dall'oggetto di **campi** raccolta, quindi ottenere il contenuto con il **campo** dell'oggetto [valore](../../../ado/reference/ado-api/value-property-ado.md) proprietà.  
  
|Costante|Value|Description|  
|--------------|-----------|-----------------|  
|**adDefaultStream**|-1|Fa riferimento al campo che contiene il valore predefinito [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto associato a un **Record**.|  
|**adRecordURL**|-2|Fa riferimento al campo che contiene la stringa URL assoluta per l'oggetto corrente **Record**.|
