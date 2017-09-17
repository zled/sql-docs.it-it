---
title: setString (long, lang) metodo | Documenti Microsoft
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
- SQLServerClob.setString (long, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1b2190e9-5ace-497a-8554-0e913ea9b0cb
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0b1bcd2dc8f6e6509099eb4529e57335942c9d6d
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setstring-method-long-javalangstring"></a>Metodo setString (long, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Scrive il determinato **stringa** nell'oggetto CLOB a partire dalla posizione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int setString(long pos,  
                     java.lang.String s)  
```  
  
#### <a name="parameters"></a>Parametri  
 *POS*  
  
 Posizione in corrispondenza della quale iniziare la scrittura nell'oggetto CLOB.  
  
 *s*  
  
 Il **stringa** da scrivere nell'oggetto Clob.  
  
## <a name="return-value"></a>Valore restituito  
 Numero di caratteri scritti.  
  
## <a name="exceptions"></a>Eccezioni  
 java.sql.SQLException  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setString viene specificato dal metodo setString nell'interfaccia Java.SQL. Clob.  
  
 I dati di tipo carattere vengono sovrascritti a partire dalla posizione specificata e possono superare la lunghezza iniziale dell'oggetto CLOB. Se si specifica un valore posizione+1, verrà aggiunta la stringa. Se si specifica un valore posizione+2 o superiore (o zero o inferiore) verrà generato un errore di posizione.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo setString &#40; SQLServerClob &#41;](../../../connect/jdbc/reference/setstring-method-sqlserverclob.md)   
 [Metodi di SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [Membri di SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [Classe SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
