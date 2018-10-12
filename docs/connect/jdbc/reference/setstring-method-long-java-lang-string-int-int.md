---
title: Metodo setString (long, java.lang.String, int, int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerClob.setString (long, java.lang.String, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9fb59b09-e825-46a6-ba5d-85d4a8dc143a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ba5046a2036b88c3ec55499a6e86609d8b050f7b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47611059"
---
# <a name="setstring-method-long-javalangstring-int-int"></a>Metodo setString (long, java.lang.String, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Scrive la stringa specificata nell'oggetto CLOB a partire dalla posizione specificata, in base all'offset e alla lunghezza forniti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int setString(long pos,  
                     java.lang.String str,  
                     int offset,  
                     int len)  
```  
  
#### <a name="parameters"></a>Parametri  
 *POS*  
  
 Posizione in corrispondenza della quale iniziare la scrittura nell'oggetto CLOB.  
  
 *str*  
  
 Stringa da scrivere nell'oggetto CLOB.  
  
 *offset*  
  
 Offset all'interno della stringa da cui iniziare a leggere i caratteri.  
  
 *len*  
  
 Numero di caratteri da scrivere.  
  
## <a name="return-value"></a>Valore restituito  
 Numero di caratteri scritti.  
  
## <a name="exceptions"></a>Eccezioni  
 java.sql.SQLException  
  
## <a name="remarks"></a>Remarks  
 Questo metodo setString viene specificato dal metodo setString nell'interfaccia CLOB.  
  
 I dati di tipo carattere vengono sovrascritti a partire dalla posizione specificata e possono sovrascrivere la lunghezza iniziale dell'oggetto CLOB. Se si specifica un valore posizione+1, verrà aggiunta la stringa. Se si specifica un valore posizione+2 o superiore (o zero o inferiore) verrà generato un errore di posizione.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo setString &#40;SQLServerClob&#41;](../../../connect/jdbc/reference/setstring-method-sqlserverclob.md)   
 [Metodi di SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [Membri di SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [Classe SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
