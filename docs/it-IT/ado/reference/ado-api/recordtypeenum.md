---
title: RecordTypeEnum | Documenti Microsoft
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
- RecordTypeEnum
helpviewer_keywords:
- RecordTypeEnum enumeration [ADO]
ms.assetid: f557e537-015d-4ba7-8a41-a6f00b366a91
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e5c7678d492e41396d3b0893aab66a3bb531e1b7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="recordtypeenum"></a>RecordTypeEnum
Specifica il tipo di [Record](../../../ado/reference/ado-api/record-object-ado.md) oggetto.  
  
|Costante|Value|Description|  
|--------------|-----------|-----------------|  
|**adSimpleRecord**|0|Indica un *semplice* record (non contiene nodi figlio).|  
|**adCollectionRecord**|1|Indica un *raccolta* record (contiene nodi figlio).|  
|**adRecordUnknown**|-1|Indica che il tipo dell'oggetto **Record** è sconosciuto.|  
|**adStructDoc**|2|Indica uno speciale tipo di *raccolta* documenti strutturati record che rappresenta COM.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Queste costanti non dispongono di equivalenti ADO/WFC.  
  
## <a name="applies-to"></a>Si applica a  
 [Proprietà RecordType (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)
