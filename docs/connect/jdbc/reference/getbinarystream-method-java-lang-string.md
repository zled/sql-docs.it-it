---
title: Metodo (lang) getBinaryStream | Documenti Microsoft
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
apiname:
- SQLServerResultSet.getBinaryStream (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 149609b5-a6de-4e23-a440-7061775d0899
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 455c307c61112fc10992c74ca15af498aa09c5f5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="getbinarystream-method-javalangstring"></a>Metodo getBinaryStream (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore del nome della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come flusso binario di byte non interpretati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.io.InputStream getBinaryStream(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnName*  
  
 Oggetto **stringa** che contiene il nome della colonna.  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto InputStream.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getBinaryStream viene specificato dal metodo getBinaryStream nell'interfaccia Java.SQL. ResultSet.  
  
 Questo metodo può essere utilizzato solo con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] tipi di dati di binary, varbinary, varbinary (max) e immagine. Se si tenta di utilizzarlo con altri tipi di dati genererà un'eccezione.  
  
 Una volta ottenuto il valore come flusso tramite questo metodo, tale valore può essere letto in blocchi dal flusso. Questo metodo è particolarmente adatto per il recupero di valori LONGVARBINARY di grandi dimensioni.  
  
> [!NOTE]  
>  Prima di ottenere il valore di qualsiasi altra colonna, è necessario leggere tutti i dati nel flusso restituito. La chiamata successiva a un metodo di richiamo chiude in modo implicito il flusso. Inoltre, un flusso restituito 0 quando viene chiamato il metodo InputStream.available, se vi è dati disponibile o meno.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getBinaryStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getbinarystream-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
