---
title: La migrazione dei database di Sybase ASE a SQL Server - database SQL di Azure | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: ed7952d4-8331-44d7-bccf-3440e17238b2
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 63dc9188d93def41a5116386f93bf29e3b744e8e
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="migrating-sybase-ase-databases-to-sql-server---azure-sql-db-sybasetosql"></a>Migrazione di database di Sybase ASE a SQL Server: database SQL di Azure (SybaseToSQL)
SQL Server Migration Assistant (SSMA) per Sybase è un ambiente completo che consente di rapidamente la migrazione dei database di Sybase Adaptive Server Enterprise (ASE) a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure. Tramite SSMA per Sybase, è possibile esaminare gli oggetti di database e i dati, valutare i database per la migrazione, eseguire la migrazione di oggetti di database [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure, quindi eseguire la migrazione dei dati per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure.  
  
## <a name="recommended-migration-process"></a>Consiglia di processo di migrazione  
Per completare la migrazione oggetti e i dati dal database ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure, procedere come segue:  
  
1.  [Creare un nuovo progetto SSMA](http://msdn.microsoft.com/en-us/11091d95-c488-48c3-891a-743cac94ac93).  
  
    Dopo aver creato il progetto, è possibile impostare le opzioni di mapping dei tipi, migrazione e conversione del progetto. Per informazioni sulle impostazioni del progetto, vedere [impostazione delle opzioni progetto &#40; SybaseToSQL &#41; ](../../ssma/sybase/setting-project-options-sybasetosql.md). Per informazioni sulla personalizzazione dei mapping dei tipi di dati, vedere [Mapping Sybase ASE e tipi di dati di SQL Server &#40; SybaseToSQL &#41; ](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
2.  [Connettersi al server di database Sybase ASE](http://msdn.microsoft.com/en-us/a45a2330-9175-4c9e-af38-ef920e350614).  
  
3.  [Connettersi a un'istanza di SQL Server](http://msdn.microsoft.com/en-us/dd368a1a-45b0-40e9-b4d3-5cdb48c26606) o [connettersi a un'istanza di database SQL di Azure](http://msdn.microsoft.com/en-us/9e77e4b0-40c0-455c-8431-ca5d43849aa7).  
  
4.  [Eseguire il mapping degli schemi di database ASE a SQL Server / database SQL di Azure degli schemi di database](http://msdn.microsoft.com/en-us/2c927003-c49d-4fe1-8e3e-5b2899166268).  
  
5.  Facoltativamente, [creare report di valutazione](http://msdn.microsoft.com/en-us/eb996b7c-1eef-4f73-b5e6-2fa6faf7336c) per valutare gli oggetti di database per la conversione e stimare il tempo di conversione.  
  
6.  [Convertire gli schemi di database Sybase ASE in SQL Server / schemi di database SQL di Azure](http://msdn.microsoft.com/en-us/509cb65d-2f54-427a-83d7-37919cc4e3e3).  
  
7.  [Caricare gli oggetti di database convertito in SQL Server / database SQL di Azure](http://msdn.microsoft.com/en-us/4c59256f-99a8-4351-9559-a455813dbd06).  
  
    È possibile tramite salvare uno script ed eseguirlo in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure oppure è possibile sincronizzare gli oggetti di database.  
  
8.  [La migrazione dei dati a SQL Server / database SQL di Azure](http://msdn.microsoft.com/en-us/54a39f5e-9250-4387-a3ae-eae47c799811).  
  
9. Se necessario, aggiornare le applicazioni di database.  
  
## <a name="see-also"></a>Vedere anche  
[L'installazione di SSMA per Sybase &#40; SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
[Introduzione a SSMA per Sybase &#40; SybaseToSQL &#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)  
  

