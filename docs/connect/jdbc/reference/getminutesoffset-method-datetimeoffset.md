---
title: Metodo getMinutesOffset (DateTimeOffset) | Documenti Microsoft
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
ms.topic: article
ms.assetid: 18ba844a-ea36-42de-87da-bbc222082efe
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8ffaf44dae71da5c5f370c25dab87e4d799707dd
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="getminutesoffset-method-datetimeoffset"></a>Metodo getMinutesOffset (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce l'offset, in minuti rispetto all'ora GMT, di questo oggetto DateTimeOffset.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int getMinutesOffset()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Offset in minuti.  
  
## <a name="remarks"></a>Osservazioni  
 Per un oggetto DateTimeOffset che rappresenta 8 marzo 2010, 11:35:48 -0800, getMinutesOffset restituisce il valore 480.  
  
## <a name="see-also"></a>Vedere anche  
 [Classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [Membri di DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
