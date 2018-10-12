---
title: Metodo getDate (int, java.util.Calendar) (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getDate (int, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 150411f7-2a73-4380-b921-9698acd5d1f9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a9edc9762a1d75c90c5fb1c9564766eb38da0421
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47773679"
---
# <a name="getdate-method-int-javautilcalendar-sqlserverresultset"></a>Metodo getDate (int, java.util.Calendar) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore dell'indice della colonna designata nella riga corrente di questo oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) come oggetto java.sql.Date nel linguaggio di programmazione Java, utilizzando l'oggetto Calendar specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.Date getDate(int columnIndex,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnIndex*  
  
 Valore **int** che indica l'indice di colonna.  
  
 *licenza CAL*  
  
 Un oggetto calendario.  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto Data.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo getDate viene specificato dal metodo getDate nell'interfaccia java.sql.ResultSet.  
  
 Questo metodo restituisce una parte della data valida di un tipo di dati datetime o smalldatetime di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], con la parte dell'ora impostata sull'ora di base 00.00 (mezzanotte) di Java nel fuso orario del calendario.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getDate &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getdate-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
