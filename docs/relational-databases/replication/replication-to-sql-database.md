---
title: Replica nel database SQL | Microsoft Docs
ms.custom: 
ms.date: 06/29/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Database replication
- replication, SQL Database
ms.assetid: e8484da7-495f-4dac-b38e-bcdc4691f9fa
caps.latest.revision: "15"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c06ca9a84504ca2ce9958e39e352a7ad93c9a56d
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="replication-to-sql-database"></a>Replica nel database SQL
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  <a name="includessnoversionincludesssnoversion-mdmd-replication-can-be-configured-to-includesssdsfullincludessssdsfull-mdmd"></a>La replica di[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può essere configurata in [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)].  
 -  
 - **Configurazioni supportate:**  
 -  
 --  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può essere un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in esecuzione in locale o un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in esecuzione in una macchina virtuale di Azure nel cloud. Per altre informazioni, vedere [Panoramica di SQL Server in Macchine virtuali di Azure](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-infrastructure-services/).  
 -  
 --   [!INCLUDE[ssSDS](../../includes/sssds-md.md)] deve essere un sottoscrittore push di un server di pubblicazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
 -  
 --  Il database di distribuzione e gli agenti di replica non possono essere inseriti in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
 -  
 --   Sono supportate la replica snapshot e la replica transazionale unidirezionale. Non sono supportate la replica transazionale peer-to-peer e la replica di tipo merge.  
 -  
 -## Versioni  
 - Il server di pubblicazione e il database di distribuzione devono eseguire almeno una delle versioni seguenti:  
 -  
 --   [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
 -  
 --   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP1 CU3  
 -  
 --   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] RTM CU10  
 -  
 --   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP2 CU8  
 -  
 --   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] previsto in SP3  
 -  
 - Il tentativo di configurare la replica con una versione precedente può causare l'errore numero MSSQL_REPL20084 (il processo non è riuscito a connettersi al Sottoscrittore) e MSSQL_REPL40532 (Non è possibile aprire il server \<nome> richiesto dall'account di accesso. Accesso non riuscito).  
 -  
 - Il sottoscrittore [!INCLUDE[ssSDS](../../includes/sssds-md.md)] deve disporre almeno della versione 12 e può essere in qualsiasi area.  
 -  
 - Per usare tutte le funzionalità di [!INCLUDE[ssSDS](../../includes/sssds-md.md)] è necessario usare le versioni più recenti di [SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx) e [SQL Server Data Tools](https://msdn.microsoft.com/library/mt204009.aspx).  
 -  
 -## Osservazioni  
 - La replica può essere configurata tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o eseguendo istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] nel server di pubblicazione. Non è possibile configurare la replica tramite il portale di [!INCLUDE[ssSDS](../../includes/sssds-md.md)] .  
 -  
 - La replica può usare solo account di accesso per l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per la connessione a [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
 -  
 - La tabella replicata deve includere una chiave primaria.  
 -  
 - È necessario avere una sottoscrizione di Azure esistente e un [!INCLUDE[ssSDS](../../includes/sssds-md.md)] esistente versione 12.  
 -  
 - Una singola pubblicazione in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può supportare sia sottoscrittori [!INCLUDE[ssSDS](../../includes/sssds-md.md)] che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (in locale e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in una macchina virtuale di Azure).  
 -  
 - La gestione, il monitoraggio e la risoluzione dei problemi della replica devono essere eseguiti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]in locale.  
 -  
 - Sono supportate solo sottoscrizioni push a [!INCLUDE[ssSDS](../../includes/sssds-md.md)] .  
 -  
 - È supportato solo `@subscriber_type = 0` in **sp_addsubscription** per il database SQL.  
 -  
 - [!INCLUDE[ssSDS](../../includes/sssds-md.md)] non supporta la replica bidirezionale, immediata, aggiornabile o peer-to-peer.      
 -  
 -## Architettura della replica  
 - ![replication-to-sql-database](../../relational-databases/replication/media/replication-to-sql-database.png "replication-to-sql-database")  
 -  
 -## Scenari  
 -  
 -#### Scenario di replica tipico  
 -  
 -1.  Creare una pubblicazione di replica transazionale in un database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] locale.  
 -  
 -2.  Nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] locale usare **Creazione guidata nuova sottoscrizione** o istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] per creare un push alla sottoscrizione in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
 -  
 -3.  Il set di dati iniziale è generalmente uno snapshot creato dall'agente snapshot e distribuito e applicato dall'agente di distribuzione. È anche possibile ottenerlo mediante un backup o altri strumenti, come [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
 -  
 -#### Scenario di migrazione dei dati  
 -  
 -1.  Usare la replica transazionale per replicare i dati da un database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] locale a [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
 -  
 -2.  Reindirizzare le applicazioni client o di livello intermedio per aggiornare la copia di [!INCLUDE[ssSDS](../../includes/sssds-md.md)] .  
 -  
 -3.  Interrompere l'aggiornamento della versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] della tabella e rimuovere la pubblicazione.  
 -  
 -## Limitazioni  
 - Le opzioni seguenti non sono supportate per le sottoscrizioni di [!INCLUDE[ssSDS](../../includes/sssds-md.md)] :  
 -  
 --   Copia associazioni filegroup  
 -  
 --   Copia schemi di partizionamento delle tabelle  
 -  
 --   Copia schemi di partizionamento dell'indice  
 -  
 --   Copia statistiche definite dall'utente  
 -  
 --   Copia associazioni predefinite  
 -  
 --   Copia associazioni regola  
 -  
 --   Copia indici full-text  
 -  
 --   Copia XSD per colonna XML  
 -  
 --   Copia indici XML  
 -  
 --   Copia autorizzazioni  
 -  
 --   Copia indici spaziali  
 -  
 --   Copia indici filtrati  
 -  
 --   Copia attributo di compressione dati  
 -  
 --   Copia attributo di colonna di tipo sparse  
 -  
 --   Converti tipo filestream in tipi di dati MAX  
 -  
 --   Converti tipo hierarchyId in tipi di dati MAX  
 -  
 --   Converti tipo spaziale in tipi di dati MAX  
 -  
 --   Copia proprietà estese  
 -  
 --   Copia autorizzazioni  
 -  
 - Limitazioni da determinare:  
 -  
 --   Copia regola di confronto  
 -  
 --   Esecuzione in una transazione serializzata della stored procedure  
 -  
 -## Esempi  
 - Creare una pubblicazione e una sottoscrizione push. Per altre informazioni, vedere:  
 -  
 --   [Creazione di una Pubblicazione](../../relational-databases/replication/publish/create-a-publication.md)  
 -  
 --   [Creare una sottoscrizione push ](../../relational-databases/replication/create-a-push-subscription.md) con il [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] nome di server logico come sottoscrittore (ad esempio **N'azuresqldbdns.database.windows.net'**) e il [!INCLUDE[ssSDS](../../includes/sssds-md.md)] nome come database di destinazione (ad esempio  **AdventureWorks**).  
 -  
 -## Vedere anche  
 - [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 - [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 - [Tipi di replica](../../relational-databases/replication/types-of-replication.md)   
 - [Monitoraggio &#40;replica&#41;](../../relational-databases/replication/monitor/monitoring-replication.md)   
 - [Inizializzare una sottoscrizione](../../relational-databases/replication/initialize-a-subscription.md)  
