---
title: 'Eseguire la migrazione di database MySQL a SQL Server: database SQL di Azure | Documenti Microsoft'
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-mysql
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 8006f9a0-394d-4238-8dc5-44255134628b
caps.latest.revision: "12"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 3e2f0f13d57b242e9f17b7241a1311df17b39612
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="migrating-mysql-databases-to-sql-server---azure-sql-db-mysqltosql"></a>Migrazione di database MySQL a SQL Server: database SQL di Azure (MySQLToSql)
SQL Server Migration Assistant (SSMA) per MySQL è un ambiente completo che consente di eseguire rapidamente la migrazione di database MySQL a SQL Server o SQL Azure. Tramite SSMA per MySQL, è possibile esaminare i dati e oggetti di database, valutare database per la migrazione, eseguire la migrazione di oggetti di database a SQL Server o SQL Azure e quindi la migrazione dei dati in SQL Server o SQL Azure.  
  
## <a name="recommended-migration-process"></a>Consiglia di processo di migrazione  
Per eseguire la migrazione dati e oggetti di database MySQL a SQL Server o SQL Azure, utilizzare la procedura seguente:  
  
1.  [Utilizzo di progetti SSMA &#40; MySQLToSQL &#41; ](../../ssma/mysql/working-with-ssma-projects-mysqltosql.md).  
  
    Dopo aver creato il progetto, è possibile impostare le opzioni di mapping dei tipi, migrazione e conversione del progetto. Per ulteriori informazioni sulle impostazioni del progetto, vedere [impostazione delle opzioni progetto &#40; MySQLToSQL &#41; ](../../ssma/mysql/setting-project-options-mysqltosql.md). Per informazioni su come personalizzare i mapping dei tipi di dati, vedere [Mapping MySQL e tipi di dati di SQL Server &#40; MySQLToSQL &#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
2.  [Connessione a MySQL &#40; MySQLToSQL &#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
3.  [Connessione a SQL Server &#40; MySQLToSQL &#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
4.  [Mapping tra i database MySQL e gli schemi di SQL Server &#40; MySQLToSQL &#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
5.  [Connessione a database SQL di Azure &#40; MySQLToSQL &#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
  
6.  Facoltativamente, [valutazione database MySQL per conversione &#40; MySQLToSQL &#41; ](../../ssma/mysql/assessing-mysql-databases-for-conversion-mysqltosql.md) per valutare gli oggetti di database per la conversione e stimare il tempo di conversione.  
  
7.  [Conversione di database MySQL &#40; MySQLToSQL &#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
8.  [Sincronizzazione](http://msdn.microsoft.com/en-us/ac993a6d-0283-4823-8793-6b217677dfa3)  
  
9. È possibile farlo in uno dei modi seguenti:  
  
    -   Salvare uno script ed eseguirlo in SQL Server o SQL Azure.  
  
    -   Sincronizzare gli oggetti di database.  
  
10. [La migrazione dei dati di MySQL in SQL Server - database SQL di Azure &#40; MySQLToSQL &#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
11. Se necessario, aggiornare le applicazioni di database.  
  
> [!NOTE]  
> È possibile eseguire la migrazione di schemi di MySQL e Information_schema.  
  
## <a name="see-also"></a>Vedere anche  
[L'installazione di SSMA per MySQL &#40; MySqlToSql &#41;](../../ssma/mysql/installing-ssma-for-mysql-mysqltosql.md)  
[Introduzione a SSMA per MySQL &#40; MySQLToSQL &#41;](../../ssma/mysql/getting-started-with-ssma-for-mysql-mysqltosql.md)  
  
