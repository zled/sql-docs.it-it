---
title: Metodo compareTo (DateTimeOffset) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e4cf2ea4-0fe9-40ce-ba79-f2a2b616997e
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4d30f5d823a7f060c9920e74a5a4e5bed55b2821
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="compareto-method-datetimeoffset"></a>Metodo compareTo (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Confronta questo **DateTimeOffset** oggetto a un altro **DateTimeOffset** oggetto in base all'ora GMT.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int compareTo(DateTimeOffset other)  
```  
  
#### <a name="parameters"></a>Parametri  
 Oggetto [DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) valore da confrontare con l'istanza corrente.  
  
## <a name="return-value"></a>Valore restituito  
 Nella tabella seguente viene descritto il valore restituito del metodo:  
  
|Valore restituito|Description|  
|------------------|-----------------|  
|0|Entrambi **DateTimeOffset** oggetti rappresentano lo stesso punto nel tempo.|  
|numero negativo|Questo **DateTimeOffset** oggetto rappresenta un punto nel tempo che precede *altri*.|  
|numero positivo|Questo **DateTimeOffset** oggetto rappresenta un punto nel tempo successivo *altri*.|  
  
## <a name="remarks"></a>Osservazioni  
 Quando due **DateTimeOffset** oggetti dispongono della stessa ora GMT, non vi è alcun ordinamento aggiuntivo degli oggetti basati sull'offset.  
  
## <a name="see-also"></a>Vedere anche  
 [Classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [Membri di DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
