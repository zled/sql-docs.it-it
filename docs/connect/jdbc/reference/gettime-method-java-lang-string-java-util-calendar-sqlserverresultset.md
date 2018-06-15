---
title: Metodo getTime (lang, java.util.Calendar) | Documenti Microsoft
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
- SQLServerResultSet.getTime (java.lang.String, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 13b51f77-cec9-45fc-862e-3d2bb2d718d7
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1f8ce9d623a940c2e55a17e376d872d388a13ede
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32839446"
---
# <a name="gettime-method-javalangstring-javautilcalendar-sqlserverresultset"></a>Metodo getTime (lang, java.util.Calendar) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore del nome della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come oggetto java.SQL. Time nel linguaggio linguaggio di programmazione, utilizzando l'oggetto di calendario specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.Time getTime(java.lang.String colName,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Parametri  
 *ColName*  
  
 Oggetto **stringa** che contiene il nome della colonna.  
  
 *licenza CAL*  
  
 Un oggetto di calendario.  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto di tempo.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getTime viene specificato dal metodo getTime nell'interfaccia Java.SQL. ResultSet.  
  
 Questo metodo restituisce una parte di ora valido di un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] tipo di dati datetime o smalldatetime, con la parte della data impostata sulla data di base di Java 1970/01/01 nel fuso orario del calendario.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getTime &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/gettime-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
