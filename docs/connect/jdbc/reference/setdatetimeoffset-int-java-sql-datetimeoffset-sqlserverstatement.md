---
title: setDateTimeOffset (int, Java.SQL. DateTimeOffset) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8b6e380-6b53-489b-be73-73fcb5258269
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b9b18af7823f8d02f80ba636fe57b5d6cd807770
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="setdatetimeoffsetint-javasqldatetimeoffset-sqlserverstatement"></a>setDateTimeOffset(int, java.sql.DateTimeOffset) (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il parametro designato sul valore DateTimeOffset specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setDateTimeOffset(int parameterIndex, DateTimeOffset dateTime)  
```  
  
#### <a name="parameters"></a>Parametri  
 *parameterIndex*  
  
 Indice della colonna da impostare.  
  
 *dateTimeOffset*  
  
 Oggetto DateTimeOffset.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Il formato di DateTimeOffset è "AAAA-MM-GG HH-MM-SS[.nnnnnnn] [+][-] HH:MM". Utilizzare la tabella seguente come riferimento.  
  
|Tipo SQL|Insert|  
|--------------|------------|  
|datetime|Unico inserimento possibile: "AAAA-MM-GG hh:mm:ss[.nnn]"|  
|smalldatetime|Unico inserimento possibile: "AAAA-MM-GG hh:mm:ss"|  
|Time|Unico inserimento possibile: "hh:mm:ss[.nnnnnnn]"|  
|Data|Unico inserimento possibile: "AAAA-MM-GG"|  
|datetime2|Unico inserimento possibile: "AAAA-MM-GG hh:mm:ss[.nnnnnnn]"|  
  
## <a name="see-also"></a>Vedere anche  
 [getDateTimeOffset &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md)   
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
