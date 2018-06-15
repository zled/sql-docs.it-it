---
title: FieldEnum | Documenti Microsoft
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
- FieldEnum
helpviewer_keywords:
- FieldEnum enumeration [ADO]
ms.assetid: be4eda13-d4e4-4d6b-bb0d-3310b0a96fc2
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1c9633fff954251a6a7e1d6153b86ad0b4545b3f
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35278662"
---
# <a name="fieldenum"></a>FieldEnum
Specifica i campi speciali a cui fa riferimento un [Record](../../../ado/reference/ado-api/record-object-ado.md) dell'oggetto [campi](../../../ado/reference/ado-api/fields-collection-ado.md) insieme.  
  
## <a name="remarks"></a>Remarks  
 Queste costanti rappresentano un "collegamento" per accedere ai campi speciali associati a un **Record**. Recuperare il [campo](../../../ado/reference/ado-api/field-object.md) dall'oggetto di **campi** raccolta, quindi ottenere il contenuto con il **campo** dell'oggetto [valore](../../../ado/reference/ado-api/value-property-ado.md) proprietà.  
  
|Costante|valore|Description|  
|--------------|-----------|-----------------|  
|**adDefaultStream**|-1|Fa riferimento al campo che contiene il valore predefinito [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto associato a un **Record**.|  
|**adRecordURL**|-2|Fa riferimento al campo che contiene la stringa URL assoluta per l'oggetto corrente **Record**.|
