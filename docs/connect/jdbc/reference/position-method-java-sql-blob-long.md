---
title: Position (Java.SQL. BLOB, long) (metodo) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerBlob.position (java.sql.Blob.long)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ebd005e5-f6c5-4789-87f9-d2fdacd35060
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c7c3f740409e7a8d7a5cbc8989ae8aa074703305
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="position-method-javasqlblob-long"></a>Metodo position (java.sql.Blob, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce la posizione di un modello specificato nell'oggetto BLOB in base al modello specificato e all'indice iniziale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public long position(java.sql.Blob pattern,  
                     long start)  
```  
  
#### <a name="parameters"></a>Parametri  
 *modello*  
  
 Modello da cercare.  
  
 *inizio*  
  
 Indice iniziale in corrispondenza del quale eseguire la ricerca.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **lungo** valore della posizione in cui il modello è stato trovato oppure -1 se non è stato trovato.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo di posizione è specificato dal metodo posizione nell'interfaccia Java.SQL. BLOB.  
  
## <a name="see-also"></a>Vedere anche  
 [Posizionare metodo &#40; SQLServerBlob &#41;](../../../connect/jdbc/reference/position-method-sqlserverblob.md)   
 [Metodi di SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [Membri di SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [Classe SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
