---
title: La migrazione da Oracle database in SQL Server (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 04/22/2018
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1d196dd6-4322-4c98-bb72-602c57d96134
caps.latest.revision: 9
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: f20b7271932cbbcc0538fc9923e45b2fc029f646
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2018
ms.locfileid: "38983203"
---
# <a name="migrating-oracle-databases-to-sql-server-oracletosql"></a>Migrazione di database Oracle a SQL Server (OracleToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant (SSMA) per Oracle è un ambiente completo che consente di eseguire rapidamente la migrazione di database Oracle a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], database SQL di Azure o Azure SQL Data Warehouse. Tramite SSMA per Oracle, è possibile esaminare gli oggetti di database e i dati, valutare i database per la migrazione, eseguire la migrazione di oggetti di database [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], database SQL di Azure o Azure SQL Data Warehouse, quindi eseguire la migrazione dei dati a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], database SQL di Azure o Azure SQL Data Data warehouse. Si noti che è possibile eseguire la migrazione di schemi SYS e di sistema Oracle.
  
## <a name="recommended-migration-process"></a>Processo di migrazione consigliato  
Per completare la migrazione oggetti e i dati dal database Oracle a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], database SQL di Azure o Azure SQL Data Warehouse, usare la procedura seguente:
  
1.  [Creare un nuovo progetto SSMA](http://msdn.microsoft.com/ee5d94c0-c7a6-4779-bd32-729bdaf61e1b).  
  
    Dopo aver creato il progetto, è possibile impostare conversione del progetto, la migrazione e le opzioni di mapping dei tipi. Per informazioni sulle impostazioni del progetto, vedere [impostazione delle opzioni progetto &#40;OracleToSQL&#41;](../../ssma/oracle/setting-project-options-oracletosql.md). Per informazioni su come personalizzare i mapping dei tipi di dati, vedere [Mapping di Oracle e SQL Server Data Types &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md).  
  
2.  [Connettersi al server di database Oracle](http://msdn.microsoft.com/e276cdbf-3ebc-4ba8-b40d-a7a42befa2b6).  
  
3.  [Connettersi a un'istanza di SQL Server](http://msdn.microsoft.com/1b2a8059-1829-4904-a82f-9c06de1e245f).  
  
4.  [Eseguire il mapping degli schemi di database Oracle a schemi di database di SQL Server](http://msdn.microsoft.com/0edeaa08-9c5d-4e3a-bc15-b9a1f0c8a9dc).  
  
5.  Facoltativamente [creazione di report di valutazione](http://msdn.microsoft.com/4de9bcf6-1346-4740-87f9-7f24a8226357) per valutare gli oggetti di database per la conversione e stimare il tempo di conversione.  
  
6.  [Convertire gli schemi del database Oracle in schemi di SQL Server](http://msdn.microsoft.com/e021182d-31da-443d-b110-937f5db27272).  
  
7.  [Caricare gli oggetti di database convertiti in SQL Server](http://msdn.microsoft.com/a8ae33b2-1883-4785-922b-ea0e31c0b37a).  
  
    È possibile eseguire questa operazione in uno dei modi seguenti:  
  
    -   Salvare uno script ed eseguirlo in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
    -   Sincronizzare gli oggetti di database.  
  
8.  [La migrazione dei dati a SQL Server](http://msdn.microsoft.com/e23c5268-41ed-4e55-9fe7-a11376202a13).  
  
9. Se necessario, aggiornare le applicazioni di database.  
  
## <a name="see-also"></a>Vedere anche  
[Installazione di SSMA per Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-oracletosql.md)  
[Introduzione a SSMA per Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/getting-started-with-ssma-for-oracle-oracletosql.md)  
  
