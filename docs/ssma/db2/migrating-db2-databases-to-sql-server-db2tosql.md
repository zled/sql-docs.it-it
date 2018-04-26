---
title: Database DB2 la migrazione a SQL Server (DB2ToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-db2
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 14d2e655-af7e-4aa5-ba28-0e3d0d025518
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d1cab931b4a0dae12dd6b5871b71da7d8e65051f
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="migrating-db2-databases-to-sql-server-db2tosql"></a>Migrazione di database DB2 a SQL Server (DB2ToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant (SSMA) per DB2 è un ambiente completo che consente di eseguire rapidamente la migrazione di database DB2 per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure. Tramite SSMA per DB2, è possibile esaminare gli oggetti di database e i dati, valutare i database per la migrazione, eseguire la migrazione di oggetti di database [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure, quindi eseguire la migrazione dei dati per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure. Si noti che è possibile eseguire la migrazione di schemi SYS e sistema DB2.  
  
## <a name="recommended-migration-process"></a>Consiglia di processo di migrazione  
Per completare la migrazione oggetti e i dati dal database di DB2 per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure, procedere come segue:  
  
1.  [Nuovo progetto SSMA](http://msdn.microsoft.com/en-us/66437b45-4686-4fc7-a91b-ebde45e0f1b0).  
  
    Dopo aver creato il progetto, è possibile impostare le opzioni di mapping dei tipi, migrazione e conversione del progetto. Per informazioni sulle impostazioni di progetto, vedere [impostazioni del progetto di &#40;conversione&#41; &#40;DB2ToSQL&#41; ](../../ssma/db2/project-settings-conversion-db2tosql.md) e le relative sezioni. Per informazioni su come personalizzare i mapping dei tipi di dati, vedere [Mapping DB2 e tipi di dati di SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md).  
  
2.  [Connettersi al database DB2](http://msdn.microsoft.com/en-us/5eb5801d-f0c3-4127-97c0-0b1ef49f4844).  
  
3.  [La connessione a SQL Server](http://msdn.microsoft.com/en-us/b59803cb-3cc6-41cc-8553-faf90851410e).  
  
4.  [Mapping degli schemi di DB2 agli schemi di SQL Server](http://msdn.microsoft.com/en-us/05ff7bd4-e60b-4f48-a893-bc2346aa9a8a).  
  
5.  Facoltativamente, [report di valutazione](http://msdn.microsoft.com/en-us/9e13eba0-e3cf-4205-974f-c00f982061de) per valutare gli oggetti di database per la conversione e stimare il tempo di conversione.  
  
6.  [Convertire gli schemi di DB2](http://msdn.microsoft.com/en-us/7947efc3-ca86-4ec5-87ce-7603059c75a0).  
  
7.  [Caricare gli oggetti di database convertito in SQL Server](http://msdn.microsoft.com/en-us/f4ea1ced-9f9f-4a9d-88ab-81dbab64adc3).  
  
    È possibile farlo in uno dei modi seguenti:  
  
    -   Salvare uno script ed eseguirlo in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
    -   Sincronizzare gli oggetti di database.  
  
8.  [La migrazione dei dati DB2 in SQL Server](http://msdn.microsoft.com/en-us/86cbd39f-6dac-409a-9ce1-7dd54403f84b).  
  
9. Se necessario, aggiornare le applicazioni di database.  
  
## <a name="see-also"></a>Vedere anche  
[Installazione di SSMA per DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-for-db2-db2tosql.md)  
[Guida introduttiva di SSMA per DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/getting-started-with-ssma-for-db2-db2tosql.md)  
  
