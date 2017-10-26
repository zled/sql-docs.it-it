---
title: Classe SQLServerException | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af5ef257-7cf6-4db3-b1ee-07d22d82bef1
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bd894bf23d8b1643722691451ccf3ae29ec6cd54
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverexception-class"></a>Classe SQLServerException
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rappresenta un'esecuzione non riuscita o incompleta di un'istruzione SQL.  
  
 **Pacchetto:** com.microsoft.sqlserver.jdbc  
  
 **Estende:** Java.SQL.  
  
 **Implementa:** Java.IO. Serializable  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final class SQLServerException  
```  
  
## <a name="remarks"></a>Osservazioni  
 La classe SQLServerException gestisce i codici di stato SQL 92 sia XOPEN. Sono intercambiabili tramite una proprietà di connessione specificata dall'utente. Le eccezioni vengono scritte in qualsiasi file di log aperto che è stato specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerException](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [Riferimento all'API del Driver JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  

