---
title: Metodo (CLOB, long) Position | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerClob.position (java.sql.Clob, long)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b2fb34d5-1d34-4764-a795-712d9c6aa313
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2a99157558ef3a4728e122a90021ff98640c28d1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47823399"
---
# <a name="position-method-javasqlclob-long"></a>Metodo position (java.sql.Clob, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce la posizione del carattere dell'oggetto CLOB specificato in tale oggetto in base alla posizione di inizio specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public long position(java.sql.Clob searchstr,  
                     long start)  
```  
  
#### <a name="parameters"></a>Parametri  
 *searchstr*  
  
 Sottostringa da cercare.  
  
 *start*  
  
 Posizione in corrispondenza della quale iniziare la ricerca. La prima posizione è 1.  
  
## <a name="return-value"></a>Valore restituito  
 Posizione in cui viene visualizzata la sottostringa oppure -1 se non è presente. La prima posizione è 1.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo di posizione viene specificato dal metodo di posizione nell'interfaccia CLOB.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo Position &#40;SQLServerClob&#41;](../../../connect/jdbc/reference/position-method-sqlserverclob.md)   
 [Metodi di SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [Membri di SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [Classe SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
