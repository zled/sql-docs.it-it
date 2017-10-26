---
title: Con le istruzioni SQL | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe28f48a-e1bc-48ff-a5e7-c24cd6e5ecc7
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5cba782d32a60b2bbdcf61276db6a1989f82c50b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="using-statements-with-sql"></a>Utilizzo di istruzioni SQL
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Quando si lavora con i dati in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database utilizzando il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] e istruzioni SQL inline, diverse classi che è possibile utilizzare. in base al tipo di istruzione SQL che si desidera eseguire.  
  
 Se l'istruzione SQL non contiene parametri IN, utilizzare il [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) classe, ma contiene parametri, utilizzare il [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) classe.  
  
> [!NOTE]  
>  Se è necessario utilizzare istruzioni SQL che contengono entrambi IN e i parametri OUT, è necessario implementarle come stored procedure e chiamarle utilizzando la [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) classe. Per ulteriori informazioni sull'utilizzo di stored procedure, vedere [istruzioni Using con Stored procedure](../../connect/jdbc/using-statements-with-stored-procedures.md).  
  
 Nelle sezioni seguenti vengono descritti i diversi scenari di utilizzo dei dati in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database tramite istruzioni SQL.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Utilizzando un'istruzione SQL senza parametri](../../connect/jdbc/using-an-sql-statement-with-no-parameters.md)|Descrive come utilizzare istruzioni SQL che non contengono parametri.|  
|[Utilizzo di un'istruzione SQL con parametri](../../connect/jdbc/using-an-sql-statement-with-parameters.md)|Descrive come utilizzare istruzioni SQL che contengono parametri.|  
|[Utilizzo di un'istruzione SQL per modificare gli oggetti di Database](../../connect/jdbc/using-an-sql-statement-to-modify-database-objects.md)|Descrive come utilizzare istruzioni SQL per modificare gli oggetti di database.|  
|[Modificare i dati tramite un'istruzione SQL](../../connect/jdbc/using-an-sql-statement-to-modify-data.md)|Descrive come utilizzare istruzioni SQL per modificare i dati in un database.|  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle istruzioni con il Driver JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  

