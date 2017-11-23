---
title: Database master (SQL Server PDW)
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c71617c0-6689-4f52-81c6-58f4cf7c7377
caps.latest.revision: "8"
ms.workload: not set
ms.openlocfilehash: 59acb3fb8c5c1913e8b4d656e9895b2810e19497
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="master-database"></a>Database master
Il database master di SQL Server PDW archivia informazioni di accesso a livello di dispositivo e il catalogo del database. È un database master di SQL Server che si trova nel nodo di controllo. Di conseguenza, fornisce una funzionalità simile a SQL Server PDW come master consente a SQL Server.  
  
Per ulteriori informazioni sui database di sistema, vedere [database di sistema](system-databases.md).  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
Nell'elenco seguente descrive le operazioni che non è possibile eseguire nel database master di SQL Server PDW.  
  
Si *non è possibile:*  
  
-   Eseguire un backup differenziale del database master.  
  
-   Creare oggetti utente nel database master.  
  
-   Modificare le regole di confronto del database master.  
  
-   Modificare il proprietario del database master.  
  
-   Eliminare o rinominare master.  
  
-   Modificare le autorizzazioni allo schema.  
  
-   Eseguire **SHRINKLOG DBCC**.  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Attività|Description|  
|--------|---------------|  
|Creare un backup completo del database master.|Esempio:<br /><br />`BACKUP DATABASE master TO backup_directory;`<br /><br />Per ulteriori informazioni, vedere [BACKUP DATABASE](../t-sql/statements/backup-database-parallel-data-warehouse.md).|  
|Ripristinare il database master|Per ripristinare il database master, utilizzare il [ripristinare il Master Database](restore-the-master-database.md) pagina dello strumento Configuration Manager.|  
|Consente di visualizzare informazioni sul catalogo di database.|`SELECT * FROM master.sys.databases;`|  
|Visualizzare le informazioni di accesso e autorizzazione a livello di sistema.|`SELECT * FROM master.sys.server_permissions;`<br /><br />`SELECT * FROM master.sys.server_principals;`<br /><br />`SELECT * FROM master.sys.sql_logins;`|  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
