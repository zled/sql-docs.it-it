---
title: Metodo (lungo byte) Position | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerBlob.position (byte[], long)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 787412c2-4342-49c8-9ca2-7a9ddcd3277c
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 83ad2523dc9948af642ab3ac7fbd62e6bac789a4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32841376"
---
# <a name="position-method-byte-long"></a>posizione (lungo byte) (metodo)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce la posizione di un modello specificato nell'oggetto BLOB in base il determinato **byte** criterio e all'indice iniziale della matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public long position(byte[] bPattern,  
                     long start)  
```  
  
#### <a name="parameters"></a>Parametri  
 *bPattern*  
  
 Modello da cercare.  
  
 *start*  
  
 Indice iniziale in corrispondenza del quale eseguire la ricerca.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **lungo** valore della posizione in cui il modello è stato trovato oppure -1 se non è stato trovato.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo di posizione è specificato dal metodo posizione nell'interfaccia Java.SQL. BLOB.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo Position &#40;SQLServerBlob&#41;](../../../connect/jdbc/reference/position-method-sqlserverblob.md)   
 [Metodi di SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [Membri di SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [Classe SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
