---
title: Metodo getString (java.lang.String) (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getString (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8a98c8a8-61d0-40c9-9335-25a87b732dc3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a153811c723875da51e747a4d9cff24a57ace75
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47642889"
---
# <a name="getstring-method-javalangstring-sqlserverresultset"></a>Metodo getString (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore del nome di colonna designato nella riga corrente di questo oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) come oggetto **String** nel linguaggio di programmazione Java.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getString(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnName*  
  
 Valore **String** contenente il nome della colonna.  
  
## <a name="return-value"></a>Valore restituito  
 Valore **String**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo getString viene specificato dal metodo getString nell'interfaccia ResultSet.  
  
 Tutte le colonne in SQL Server possono essere restituite come valore String. Pertanto, possono essere restituite una rappresentazione **String** di tutti i tipi numerici e basati su caratteri e una rappresentazione stringa esadecimale di colonne binarie quali binary, varbinary, varbinary(max), image, timestamp e uniqueidentifier.  
  
 I tipi dipendenti dai percorsi quali money, smallmoney, datetime, smalldatetime, float, real, decimal e numeric restituiranno il formato canonico toString() per il valore sottostante del tipo.  
  
 I tipi definiti dall'utente vengono restituiti come valori **String** esadecimali.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getString &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getstring-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
