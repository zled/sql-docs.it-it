---
title: Migrazione di Oracle database a SQL Server (OracleToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d196dd6-4322-4c98-bb72-602c57d96134
caps.latest.revision: "9"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Active
ms.openlocfilehash: c3b6bc1f359cd54c1380fbe193fb007e1e337a3d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="migrating-oracle-databases-to-sql-server-oracletosql"></a>Migrazione di database Oracle a SQL Server (OracleToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Migration Assistant (SSMA) per Oracle è un ambiente completo che consente di eseguire rapidamente la migrazione di database Oracle a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure. Tramite SSMA per Oracle, è possibile esaminare gli oggetti di database e i dati, valutare i database per la migrazione, eseguire la migrazione di oggetti di database [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure, quindi eseguire la migrazione dei dati per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure. Si noti che è possibile eseguire la migrazione di schemi SYS e sistema Oracle.  
  
## <a name="recommended-migration-process"></a>Consiglia di processo di migrazione  
Per completare la migrazione oggetti e i dati dal database Oracle a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure, procedere come segue:  
  
1.  [Creare un nuovo progetto SSMA](http://msdn.microsoft.com/en-us/ee5d94c0-c7a6-4779-bd32-729bdaf61e1b).  
  
    Dopo aver creato il progetto, è possibile impostare le opzioni di mapping dei tipi, migrazione e conversione del progetto. Per informazioni sulle impostazioni del progetto, vedere [OracleToSQL impostazione delle opzioni progetto &#40; &#41;](../../ssma/oracle/setting-project-options-oracletosql.md). Per informazioni su come personalizzare i mapping dei tipi di dati, vedere [OracleToSQL Mapping Oracle e tipi di dati di SQL Server &#40; &#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md).  
  
2.  [Connettersi al server di database Oracle](http://msdn.microsoft.com/en-us/e276cdbf-3ebc-4ba8-b40d-a7a42befa2b6).  
  
3.  [Connettersi a un'istanza di SQL Server](http://msdn.microsoft.com/en-us/1b2a8059-1829-4904-a82f-9c06de1e245f).  
  
4.  [Eseguire il mapping degli schemi di database Oracle a schemi di database di SQL Server](http://msdn.microsoft.com/en-us/0edeaa08-9c5d-4e3a-bc15-b9a1f0c8a9dc).  
  
5.  Facoltativamente, [creare report di valutazione](http://msdn.microsoft.com/en-us/4de9bcf6-1346-4740-87f9-7f24a8226357) per valutare gli oggetti di database per la conversione e stimare il tempo di conversione.  
  
6.  [Convertire gli schemi di database Oracle in schemi di SQL Server](http://msdn.microsoft.com/en-us/e021182d-31da-443d-b110-937f5db27272).  
  
7.  [Caricare gli oggetti di database convertito in SQL Server](http://msdn.microsoft.com/en-us/a8ae33b2-1883-4785-922b-ea0e31c0b37a).  
  
    È possibile farlo in uno dei modi seguenti:  
  
    -   Salvare uno script ed eseguirlo in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
    -   Sincronizzare gli oggetti di database.  
  
8.  [La migrazione dei dati a SQL Server](http://msdn.microsoft.com/en-us/e23c5268-41ed-4e55-9fe7-a11376202a13).  
  
9. Se necessario, aggiornare le applicazioni di database.  
  
## <a name="see-also"></a>Vedere anche  
[Installazione di SSMA per OracleToSQL Oracle &#40; &#41;](../../ssma/oracle/installing-ssma-for-oracle-oracletosql.md)  
[Introduzione a SSMA per OracleToSQL Oracle &#40; &#41;](../../ssma/oracle/getting-started-with-ssma-for-oracle-oracletosql.md)  
  
