---
title: Con le istruzioni SQL | Documenti Microsoft
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
ms.assetid: fe28f48a-e1bc-48ff-a5e7-c24cd6e5ecc7
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 361448b1b27a735f54202a3ec6bbbec8f16ccc72
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="using-statements-with-sql"></a>Utilizzo di istruzioni SQL
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Quando si lavora con i dati in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database utilizzando il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] e istruzioni SQL inline, diverse classi che è possibile utilizzare. in base al tipo di istruzione SQL che si desidera eseguire.  
  
 Se l'istruzione SQL non contiene parametri IN, utilizzare il [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) classe, ma contiene parametri, utilizzare il [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) classe.  
  
> [!NOTE]  
>  Se è necessario utilizzare istruzioni SQL che contengono entrambi IN e i parametri OUT, è necessario implementarle come stored procedure e chiamarle utilizzando la [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) classe. Per ulteriori informazioni sull'utilizzo di stored procedure, vedere [istruzioni Using con Stored procedure](../../connect/jdbc/using-statements-with-stored-procedures.md).  
  
 Nelle sezioni seguenti vengono descritti i diversi scenari di utilizzo dei dati in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database tramite istruzioni SQL.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Uso di un'istruzione SQL senza parametri](../../connect/jdbc/using-an-sql-statement-with-no-parameters.md)|Descrive come utilizzare istruzioni SQL che non contengono parametri.|  
|[Uso di istruzioni SQL con parametri](../../connect/jdbc/using-an-sql-statement-with-parameters.md)|Descrive come utilizzare istruzioni SQL che contengono parametri.|  
|[Uso di un'istruzione SQL per modificare gli oggetti di database](../../connect/jdbc/using-an-sql-statement-to-modify-database-objects.md)|Descrive come utilizzare istruzioni SQL per modificare gli oggetti di database.|  
|[Uso di un'istruzione SQL per modificare i dati](../../connect/jdbc/using-an-sql-statement-to-modify-data.md)|Descrive come utilizzare istruzioni SQL per modificare i dati in un database.|  
  
## <a name="see-also"></a>Vedere anche  
 [Uso delle istruzioni con il driver JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  
