---
title: Classe SQLServerResultSet | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eaffcff1-286c-459f-83da-3150778480c9
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ac9db37012a51c8ba365b22dd7e56b30ae5b5b6d
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverresultset-class"></a>Classe SQLServerResultSet
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rappresenta un set di risultati JDBC.  
  
 **Pacchetto:** com.microsoft.sqlserver.jdbc  
  
 **Implementa:** [ISQLServerResultSet](../../../connect/jdbc/reference/isqlserverresultset-interface.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final class SQLServerResultSet  
```  
  
## <a name="remarks"></a>Osservazioni  
 Esistono due tipi di set di risultati: lato client e lato server.  
  
 I set di risultati del lato client vengono utilizzati quando le dimensioni dei risultati sono tali da consentirne la conservazione nella memoria del processo client. Questi risultati sono disponibili più rapidamente e vengono lette dal [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] interamente dal database. Inoltre non impongono carico aggiuntivo sul database, evitando l'overhead correlato alla creazione di cursori sul lato server. Tuttavia, questi tipi di set di risultati non sono aggiornabili.  
  
 I set di risultati del lato server possono essere utilizzati quando le dimensioni dei risultati sono tali da non consentirne la conservazione nella memoria del processo client o quando il set di risultati deve essere aggiornabile. Con questo tipo di set di risultati, il driver JDBC crea un cursore sul lato server e recupera in modo trasparente le righe del set di risultati man mano che l'utente scorre il set stesso.  
  
 La classe SQLServerResultSet fornisce numerosi metodi che consentono di aggiornare il set di risultati con qualsiasi tipo di dati Java nativo e numerosi tipi di oggetto Java.  
  
 Questa classe supporta l'annullamento del wrapping nella classe SQLServerResultSet e interfaccia ISQLServerResultSet, interfaccia Java.SQL. ResultSet. Per ulteriori informazioni, vedere [wrapper e interfacce](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Riferimento all'API del Driver JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
