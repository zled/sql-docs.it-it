---
title: "Tipo di proprietà (flusso ADO) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Stream::Type
- _Stream::get_Type
- _Stream::put_Type
helpviewer_keywords: Type property [ADO Stream]
ms.assetid: f6a17e8c-7a28-48d0-bded-76b9e0cf7639
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: c935ffe744d73e31483f030a6efd122773909755
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="type-property-ado-stream"></a>Proprietà Type (flusso ADO)
Indica il tipo di dati contenuti nel [flusso](../../../ado/reference/ado-api/stream-object-ado.md) (binario o testo).  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un [StreamTypeEnum](../../../ado/reference/ado-api/streamtypeenum.md) valore che specifica il tipo di dati contenuti nel **flusso** oggetto. Il valore predefinito è **adTypeText**. Tuttavia, se i dati binari vengono inizialmente scritti in una nuova, vuota **flusso**, **tipo** verrà modificato in **adTypeBinary**.  
  
## <a name="remarks"></a>Osservazioni  
 Il **tipo** proprietà è di lettura/scrittura solo quando la posizione corrente si trova all'inizio del **flusso** ([posizione](../../../ado/reference/ado-api/position-property-ado.md) è 0) e di sola lettura in qualsiasi altra posizione.  
  
 Il**tipo** proprietà determina quali metodi devono essere utilizzati per leggere e scrivere il **flusso**. Per il testo **flussi**, utilizzare [ReadText](../../../ado/reference/ado-api/readtext-method.md) e [WriteText](../../../ado/reference/ado-api/writetext-method.md). Per i dati binari **flussi**, utilizzare [lettura](../../../ado/reference/ado-api/read-method.md) e [scrivere](../../../ado/reference/ado-api/write-method.md).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà RecordType (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)   
 [Proprietà Type (ADO)](../../../ado/reference/ado-api/type-property-ado.md)
