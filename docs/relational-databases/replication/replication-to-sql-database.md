---
title: "Replica nel database SQL | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/29/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Replica del database SQL"
  - "replica, database SQL"
ms.assetid: e8484da7-495f-4dac-b38e-bcdc4691f9fa
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# Replica nel database SQL
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la replica può essere configurata per [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)].  
  
 **Configurazioni supportate:**  
  
-   Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può essere un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in esecuzione in locale o un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in esecuzione in una macchina virtuale di Azure nel cloud. Per ulteriori informazioni, vedere [SQL Server in macchine virtuali di Azure Panoramica](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-infrastructure-services/).  
  
-   [!INCLUDE[ssSDS](../../includes/sssds-md.md)] deve essere un server di sottoscrizione push di un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server di pubblicazione.  
  
-   Database di distribuzione e gli agenti di replica non possono essere collocati [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
-   Sono supportate la replica snapshot e la replica transazionale unidirezionale. Non sono supportate la replica transazionale peer-to-peer e la replica di tipo merge.  
  
## Versioni  
 Il server di pubblicazione e il database di distribuzione devono eseguire almeno una delle versioni seguenti:  
  
-   [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP1 CU3  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] RTM CU10  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP2 CU8  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] previsto in SP3  
  
 Tentare di configurare la replica con una versione precedente può causare errori numero MSSQL_REPL20084 (il processo Impossibile connettersi al sottoscrittore.) e MSSQL_REPL40532 (Impossibile aprire il server \< nome> richiesto dall'account di accesso. Accesso non riuscito).  
  
 Il [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Sottoscrittore deve essere almeno la versione 12 e può essere in qualsiasi area.  
  
 Per utilizzare tutte le funzionalità di [!INCLUDE[ssSDS](../../includes/sssds-md.md)] è necessario utilizzare le versioni più recenti di [SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx) e [SQL Server Data Tools](https://msdn.microsoft.com/library/mt204009.aspx).  
  
## Osservazioni  
 La replica può essere configurata tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o eseguendo [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni nel server di pubblicazione. Non è possibile configurare la replica tramite il [!INCLUDE[ssSDS](../../includes/sssds-md.md)] portale.  
  
 La replica è possibile utilizzare solo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gli account di accesso per connettersi a [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 La tabella replicata deve includere una chiave primaria.  
  
 È necessario disporre di una sottoscrizione di Azure esistente e di un oggetto esistente [!INCLUDE[ssSDS](../../includes/sssds-md.md)] versione 12.  
  
 Una singola pubblicazione su [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può supportare sia [!INCLUDE[ssSDS](../../includes/sssds-md.md)] e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (on-premise e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in una macchina virtuale di Azure) i sottoscrittori.  
  
 Gestione delle repliche, monitoraggio e risoluzione dei problemi deve essere eseguita da locale [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Solo le sottoscrizioni a push [!INCLUDE[ssSDS](../../includes/sssds-md.md)] sono supportati.  
  
 Solo `@subscriber_type = 0` è supportato in **sp_addsubscription** per il Database SQL.  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] non supporta la replica bidirezionale, immediata, aggiornabile o peer-to.  
  
## Architettura della replica  
 ![replication-to-sql-database](../../relational-databases/replication/media/replication-to-sql-database.png "replication-to-sql-database")  
  
## Scenari  
  
#### Scenario di replica tipico  
  
1.  Creare una pubblicazione transazionale in un locale [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.  
  
2.  Presso la sede [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzare il **Creazione guidata nuova sottoscrizione** o [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni per creare un push alla sottoscrizione a [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
3.  Il set di dati iniziale è generalmente uno snapshot creato dall'agente snapshot e distribuito e applicato dall'agente di distribuzione. Il set di dati iniziale possono inoltre essere specificato tramite un backup o altri mezzi, ad esempio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
#### Scenario di migrazione dei dati  
  
1.  Utilizzare la replica transazionale per replicare i dati da un locale [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
2.  Reindirizzare le applicazioni client o di livello intermedio per aggiornare il [!INCLUDE[ssSDS](../../includes/sssds-md.md)] copia.  
  
3.  Interrompere l'aggiornamento di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versione della tabella e rimuovere la pubblicazione.  
  
## Limitazioni  
 Le opzioni seguenti non sono supportate per [!INCLUDE[ssSDS](../../includes/sssds-md.md)] sottoscrizioni:  
  
-   Copia associazioni filegroup  
  
-   Copia schemi di partizionamento delle tabelle  
  
-   Copia schemi di partizionamento dell'indice  
  
-   Copia statistiche definite dall'utente  
  
-   Copia associazioni predefinite  
  
-   Copia associazioni regola  
  
-   Copia indici full-text  
  
-   Copia XSD per colonna XML  
  
-   Copia indici XML  
  
-   Copia autorizzazioni  
  
-   Copia indici spaziali  
  
-   Copia indici filtrati  
  
-   Copia attributo di compressione dati  
  
-   Copia attributo di colonna di tipo sparse  
  
-   Converti tipo FILESTREAM in tipi di dati MAX  
  
-   Converti tipo hierarchyId in tipi di dati MAX  
  
-   Converti tipo spaziale in tipi di dati MAX  
  
-   Copia proprietà estese  
  
-   Copia autorizzazioni  
  
 Limitazioni da determinare:  
  
-   Copia regole di confronto  
  
-   Esecuzione in una transazione serializzata della stored procedure  
  
## Esempi  
 Creare una pubblicazione e una sottoscrizione push. Per altre informazioni, vedere:  
  
-   [Creazione di una pubblicazione](../../relational-databases/replication/publish/create-a-publication.md)  
  
-   [Creare una sottoscrizione Push](../../relational-databases/replication/create-a-push-subscription.md) utilizzando il [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] nome del server logico come server di sottoscrizione (ad esempio **N'azuresqldbdns.database.windows.net'**) e [!INCLUDE[ssSDS](../../includes/sssds-md.md)] nome come database di destinazione (ad esempio **AdventureWorks**).  
  
## Vedere anche  
 [Creazione di una pubblicazione](../../relational-databases/replication/publish/create-a-publication.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Tipi di replica](../../relational-databases/replication/types-of-replication.md)   
 [Monitoraggio & #40; Replica & #41;](../../relational-databases/replication/monitor/monitoring-replication.md)   
 [Inizializzazione di una sottoscrizione](../../relational-databases/replication/initialize-a-subscription.md)  
  
  