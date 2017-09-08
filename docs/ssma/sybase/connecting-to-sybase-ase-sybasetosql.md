---
title: Connessione a Sybase ASE (SybaseToSQL) | Documenti Microsoft
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
helpviewer_keywords:
- Connecting to Sybase ASE
ms.assetid: a45a2330-9175-4c9e-af38-ef920e350614
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4cbdcd08cc4186dd4fa6d7d8fcffebdfd1139799
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="connecting-to-sybase-ase-sybasetosql"></a>Connessione a Sybase ASE (SybaseToSQL)
Per eseguire la migrazione dei database Sybase Adaptive Server Enterprise (ASE) [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, è necessario connettersi al Server adattivo che contiene i database che si desidera eseguire la migrazione. Quando ci si connette, SSMA Ottiene i metadati relativi a tutti i database nel Server adattivo e visualizza i metadati del database nel riquadro di esplorazione dei metadati di Sybase. SSMA archivia le informazioni relative al server di database, ma non archivia le password.  
  
La connessione a ASE rimane attiva finché non si chiude il progetto. Quando si riapre il progetto, è necessario riconnettersi alla ASE se si desidera una connessione attiva al server.  
  
I metadati relativi a Adaptive Server non viene aggiornato automaticamente. In alternativa, se si desidera aggiornare i metadati nel Visualizzatore metadati Sybase, è necessario aggiornare manualmente i metadati, come descritto nella sezione "Aggiornamento di metadati di Sybase ASE" più avanti in questo argomento.  
  
## <a name="required-ase-permissions"></a>Autorizzazioni necessarie ASE  
L'account utilizzato per connettersi a ASE deve disporre di almeno **pubblica** accesso al database master e a qualsiasi database di origine per eseguire la migrazione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. Inoltre, per selezionare le autorizzazioni per le tabelle incluse nella migrazione, l'utente deve disporre delle autorizzazioni SELECT su tabelle di sistema seguenti:  
  
-   .dbo.sysobjects [source_db]  
  
-   .dbo.syscolumns [source_db]  
  
-   .dbo.sysusers [source_db]  
  
-   .dbo.systypes [source_db]  
  
-   .dbo.sysconstraints [source_db]  
  
-   .dbo.syscomments [source_db]  
  
-   .dbo.sysindexes [source_db]  
  
-   .dbo.sysreferences [source_db]  
  
-   master.dbo.sysdatabases  
  
## <a name="establishing-a-connection-to-ase"></a>Stabilire una connessione a ASE  
Quando ci si connette a un Server adattiva, SSMA legge i metadati del database nel server di database e quindi aggiunge i metadati del file di progetto. Questi metadati vengono utilizzati da SSMA durante la conversione di oggetti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o sintassi SQL Azure, e quando esegue la migrazione di dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. È possibile esplorare i metadati nel riquadro Visualizzatore metadati Sybase e le proprietà di singoli oggetti di database.  
  
> [!IMPORTANT]  
> Prima di provare a connettersi al server di database, assicurarsi che il server di database è in esecuzione e può accettare connessioni.  
  
**Per connettersi a Sybase ASE**  
  
1.  Nel **File** dal menu **Connetti Sybase**.  
  
    Se si è connessi in precedenza per Sybase, il nome di comando sarà **riconnessione per Sybase**.  
  
2.  Nel **Provider** selezionare uno dei provider installati nel computer di connettersi al server di Sybase.  
  
3.  Nel **modalità** selezionare **modalità Standard** o **modalità avanzata**.  
  
    Utilizzare la modalità standard per specificare il nome del server, porta, nome utente e password. Utilizzare la modalità avanzata per fornire una stringa di connessione. Questa modalità è in genere utilizzata solo per la risoluzione dei problemi o l'utilizzo con il supporto tecnico.  
  
4.  Se si seleziona **modalità Standard**, specificare i valori seguenti:  
  
    1.  Nel **nome Server** immettere o selezionare il nome o indirizzo IP del server di database.  
  
    2.  Se il server di database non è configurato per accettare le connessioni sull'impostazione predefinita la porta (5000), immettere il numero di porta utilizzato per le connessioni di Sybase nel **porta Server** casella.  
  
    3.  Nel **nome utente** , immettere un account di Sybase che disponga delle autorizzazioni necessarie.  
  
    4.  Nel **Password** immettere la password per il nome utente specificato.  
  
5.  Se si seleziona **modalità avanzata**, specificare una stringa di connessione nel **stringa di connessione** casella.  
  
    Esempi di stringhe di connessione diverse sono i seguenti:  
  
    1.  **Stringhe di connessione per il Provider OLE DB Sybase:**  
  
        Per Sybase ASE OLE DB 12,5, una stringa di connessione di esempio è la seguente:  
  
        `Server Name=sybserver;User ID=MyUserID;Password=MyP@$$word;Provider=Sybase.ASEOLEDBProvider;`  
  
        Per Sybase ASE OLE DB 15, una stringa di connessione di esempio è la seguente:  
  
        `Server=sybserver;User ID=MyUserID;Password=MyP@$$word;Provider= ASEOLEDB;Port=5000;`  
  
    2.  **Stringa di connessione del Provider ODBC Sybase:**  
  
        `Driver=Adaptive Server Enterprise;Server=sybserver;uid=MyUserID;pwd=MyP@$$word;Port=5000;`  
  
    3.  **Stringa di connessione per il Provider ADO.NET Sybase:**  
  
        `Server=sybserver;Port=5000;uid=MyUserID;pwd=MyP@$$word;`  
  
    Per ulteriori informazioni, vedere [Connetti per Sybase &#40; SybaseToSQL &#41; ](../../ssma/sybase/connect-to-sybase-sybasetosql.md).  
  
## <a name="reconnecting-to-sybase-ase"></a>La riconnessione per Sybase ASE  
La connessione al server di database rimane attiva finché non si chiude il progetto. Quando si riapre il progetto, sarà necessario riconnettere se si desidera una connessione attiva al Server adattivo. È possibile lavorare offline fino a quando non si desidera aggiornare i metadati, caricare gli oggetti di database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, e la migrazione dei dati.  
  
## <a name="refreshing-sybase-ase-metadata"></a>Aggiornamento dei metadati di Sybase ASE  
I metadati sui database ASE non vengono aggiornati automaticamente. I metadati nel Visualizzatore metadati Sybase sono uno snapshot dei metadati quando si è connessi prima Adaptive Server o l'ultima volta che si aggiorna manualmente i metadati. È possibile aggiornare manualmente i metadati per un singolo database, un unico schema di database o tutti i database.  
  
**Per aggiornare i metadati**  
  
1.  Assicurarsi di essere connessi al Server adattivo.  
  
2.  Nel Visualizzatore metadati Sybase, selezionare la casella di controllo accanto al database o schema di database che si desidera aggiornare.  
  
3.  Database o i singoli database o lo schema del database e quindi scegliere **aggiornamento dal Database**.  
  
4.  Se viene chiesto di verificare l'oggetto corrente, fare clic su **Sì**.  
  
## <a name="next-step"></a>Passaggio successivo  
  
-   Il passaggio successivo del processo di migrazione consiste nel [connettersi a un'istanza di SQL Server](http://msdn.microsoft.com/en-us/dd368a1a-45b0-40e9-b4d3-5cdb48c26606) / [connessione a un'istanza di SQL Azure](http://msdn.microsoft.com/en-us/9e77e4b0-40c0-455c-8431-ca5d43849aa7)  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database di Sybase ASE a SQL Server: database SQL di Azure &#40; SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  

