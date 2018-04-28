---
title: setDateTimeOffset (int, Java.SQL. DateTimeOffset) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8b6e380-6b53-489b-be73-73fcb5258269
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e2f2c0e6fcdd299f6d1b0d18615e72dbfc4ff76f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
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
  
 *DateTimeOffset*  
  
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
 [getDateTimeOffset &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md)   
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
