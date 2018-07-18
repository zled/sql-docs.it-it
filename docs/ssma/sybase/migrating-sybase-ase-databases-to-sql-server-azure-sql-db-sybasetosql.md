---
title: La migrazione dei database di Sybase ASE a SQL Server - database SQL di Azure | Microsoft Docs
ms.custom: ''
ms.date: 11/30/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: ed7952d4-8331-44d7-bccf-3440e17238b2
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: a021ac1cfc442943b15ade737c54d0b9e227ef03
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2018
ms.locfileid: "38982213"
---
# <a name="migrating-sap-ase-databases-to-sql-server---azure-sql-database-sybasetosql"></a>La migrazione dei database di SAP ASE a SQL Server - Database SQL di Azure (SybaseToSQL)
SQL Server Migration Assistant (SSMA) per SAP Adaptive Server Enterprise (ASE) è un ambiente completo che consente di rapidamente la migrazione dei database SAP ASE a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o Database SQL di Azure. Tramite SSMA per ASE SAP, è possibile esaminare gli oggetti di database e i dati, valutare i database per la migrazione, eseguire la migrazione di oggetti di database [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o Database SQL di Azure e quindi eseguire la migrazione dei dati a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o Database SQL di Azure.  
  
## <a name="recommended-migration-process"></a>Processo di migrazione consigliato  
Per completare la migrazione oggetti e i dati dal database SAP ASE a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o Database SQL di Azure, procedere come segue:  
  
1.  [Creare un nuovo progetto SSMA](http://msdn.microsoft.com/11091d95-c488-48c3-891a-743cac94ac93).  
  
    Dopo aver creato il progetto, è possibile impostare conversione del progetto, la migrazione e le opzioni di mapping dei tipi. Per informazioni sulle impostazioni del progetto, vedere [impostazione delle opzioni progetto &#40;SybaseToSQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md). Per informazioni sulla personalizzazione dei mapping dei tipi di dati, vedere [Mapping di Sybase ASE e SQL Server Data Types &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
2.  [Connettersi al server di database SAP ASE](http://msdn.microsoft.com/a45a2330-9175-4c9e-af38-ef920e350614).  
  
3.  [Connettersi a un'istanza di SQL Server](http://msdn.microsoft.com/dd368a1a-45b0-40e9-b4d3-5cdb48c26606) oppure [Connetti a un'istanza di Database SQL di Azure](http://msdn.microsoft.com/9e77e4b0-40c0-455c-8431-ca5d43849aa7).  
  
4.  [Eseguire il mapping di schemi di database SAP ASE a SQL Server / Database SQL di Azure degli schemi di database](http://msdn.microsoft.com/2c927003-c49d-4fe1-8e3e-5b2899166268).  
  
5.  Facoltativamente [creazione di report di valutazione](http://msdn.microsoft.com/eb996b7c-1eef-4f73-b5e6-2fa6faf7336c) per valutare gli oggetti di database per la conversione e stimare il tempo di conversione.  
  
6.  [Convertire gli schemi del database SAP ASE in SQL Server / schemi di Database SQL di Azure](http://msdn.microsoft.com/509cb65d-2f54-427a-83d7-37919cc4e3e3).  
  
7.  [Caricare gli oggetti di database convertiti in SQL Server / Database SQL di Azure](http://msdn.microsoft.com/4c59256f-99a8-4351-9559-a455813dbd06).  
  
    Uno salvare uno script ed eseguirlo in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o Database SQL di Azure o sincronizzare gli oggetti di database.  
  
8.  [La migrazione dei dati a SQL Server / Database SQL di Azure](http://msdn.microsoft.com/54a39f5e-9250-4387-a3ae-eae47c799811).  
  
9. Se necessario, aggiornare le applicazioni del database.  
  
## <a name="see-also"></a>Vedere anche  
[Installazione di SSMA per ASE SAP &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
[Introduzione a SSMA per ASE SAP &#40;SybaseToSQL&#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)  
  
