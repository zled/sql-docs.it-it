---
title: Database di sistema | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: databases
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- system databases [SQL Server]
- displaying system database data
- modifying system data
- viewing system database data
ms.assetid: 30468a7c-4225-4d35-aa4a-ffa7da4f1282
caps.latest.revision: "25"
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7985a4fa9d1fa3dd4fc11553d640c4ef0ad0c6a2
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="system-databases"></a>Database di sistema.
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] include i database di sistema seguenti.  
  
|Database di sistema|Description|  
|---------------------|-----------------|  
|[Database master](../../relational-databases/databases/master-database.md)|Registra tutte le informazioni di sistema per un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Database msdb](../../relational-databases/databases/msdb-database.md)|Utilizzato da SQL Server Agent per la pianificazione di avvisi e processi.|  
|[Database model](../../relational-databases/databases/model-database.md)|Utilizzato come modello per tutti i database creati in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le modifiche apportate al database **model** , ad esempio per quanto riguarda dimensioni, regole di confronto, modello di recupero e altre opzioni del database, vengono applicate a tutti i database creati successivamente.|  
|[Database Resource](../../relational-databases/databases/resource-database.md)|Database di sola lettura che contiene gli oggetti di sistema inclusi in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Gli oggetti di sistema sono fisicamente mantenuti nel database **Resource** ma appaiono logicamente nello schema **sys** di ogni database.|  
|[Database tempdb](../../relational-databases/databases/tempdb-database.md)|Area di lavoro per l'archiviazione di oggetti temporanei o set di risultati intermedi.|  
  
## <a name="modifying-system-data"></a>modifica dei dati di sistema  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non supporta l'aggiornamento diretto delle informazioni da parte degli utenti in oggetti di sistema, ad esempio tabelle di sistema, stored procedure di sistema e viste del catalogo. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] offre, tuttavia, un set completo di strumenti di amministrazione che consentono agli utenti di amministrare completamente il sistema e gestire tutti gli utenti e gli oggetti di un database. tra cui:  
  
-   Utilità di amministrazione, ad esempio [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
-   API SQL-SMO. Consente ai programmatori di includere nelle proprie applicazioni funzionalità complete di amministrazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] . Possono utilizzare stored procedure di sistema e istruzioni DDL [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 Questi strumenti  proteggono le applicazioni dalle modifiche negli oggetti di sistema. Talvolta, ad esempio, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve modificare le tabelle di sistema nelle nuove versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per garantire il supporto per nuove funzionalità aggiunte alla versione. Le applicazioni che eseguono istruzioni SELECT che fanno riferimento diretto alle tabelle di sistema spesso si basano sul formato precedente delle tabelle. Può capitare che, per eseguire l'aggiornamento a una nuova versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , le aziende debbano prima riscrivere le applicazioni che eseguono la selezione dalle tabelle di sistema. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tratta stored procedure di sistema, DDL e SQL-SMO come interfacce pubblicate e fa il possibile per mantenerne la compatibilità con le versioni precedenti.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non supporta i trigger definiti nelle tabelle di sistema, in quanto potrebbero modificare il funzionamento del sistema.  
  
> [!NOTE]  
>  I database di sistema non possono trovarsi in directory di condivisione UNC.  
  
## <a name="viewing-system-database-data"></a>visualizzazione dei dati di database di sistema  
 È sconsigliabile definire istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] che eseguono query dirette sulle tabelle di sistema, a meno che non si tratti dell'unico modo per ottenere le informazioni richieste dall'applicazione. Le applicazioni devono invece ottenere le informazioni di sistema e del catalogo utilizzando gli elementi seguenti:  
  
-   Viste del catalogo di sistema  
  
-   SQL-SMO  
  
-   Interfaccia di Strumentazione gestione Windows (WMI, Windows Management Instrumentation)  
  
-   Funzioni, metodi, attributi o proprietà del catalogo dell'API dei dati utilizzata dall'applicazione, ad esempio ADO, OLE DB o ODBC  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] Funzioni predefinite e stored procedure di sistema.  
  
## <a name="related-tasks"></a>Related Tasks  
 [Backup e ripristino di database di sistema &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [Nascondere oggetti di sistema in Esplora oggetti](http://msdn.microsoft.com/library/c01d8804-838c-4f75-b78c-80e41e4fffdc)  
  
## <a name="related-content"></a>Contenuto correlato  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
 [Database](../../relational-databases/databases/databases.md)  
  
  
