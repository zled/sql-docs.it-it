---
title: Metodo getTimestamp (int, java.util.Calendar) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getTimestamp (int, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f2dd5688-7344-437a-8716-7024fb8e9c31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c6d4908025700c6dda9a5636991ba3f799e628e8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47667410"
---
# <a name="gettimestamp-method-int-javautilcalendar-sqlserverresultset"></a>Metodo getTimestamp (int, java.util.Calendar) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore dell'indice della colonna designata nella riga corrente di questo oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) come oggetto java.sql.Timestamp nel linguaggio di programmazione Java, utilizzando un oggetto Calendar.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.Timestamp getTimestamp(int columnIndex,  
                                       java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnIndex*  
  
 Valore **int** che indica l'indice di colonna.  
  
 *licenza CAL*  
  
 Un oggetto calendario.  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto di Timestamp.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo getTimestamp viene specificato dal metodo getTimestamp nell'interfaccia ResultSet.  
  
 Questo metodo restituisce valori solo dalle colonne datetime e smalldatetime di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getTimestamp &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/gettimestamp-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
