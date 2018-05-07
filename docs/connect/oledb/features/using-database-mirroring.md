---
title: Uso del mirroring del Database | Documenti Microsoft
description: Uso del mirroring del database con il Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- OLE DB Driver for SQL Server, database mirroring
- data access [OLE DB Driver for SQL Server], database mirroring
- database mirroring [SQL Server], connecting clients to
- MSOLEDBSQL, database mirroring
- OLE DB Driver for SQL Server, database mirroring
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 9ba469d6f17618f06b92c257982b430c3636b916
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-database-mirroring"></a>Utilizzo del mirroring del database
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]Utilizzare [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] invece.  
  
 Il mirroring del database, introdotto in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], è una soluzione per aumentare la disponibilità del database e la ridondanza dei dati. Il Driver OLE DB per SQL Server fornisce supporto implicito per il mirroring del database, in modo lo sviluppatore non debba scrivere alcun codice o eseguire altre azioni dopo che è stato configurato per il database.  
  
 Mirroring del database, implementato in una base per ogni database, mantiene una copia di un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database di produzione su un server di standby. Tale server può essere warm standby o hot standby, a seconda della configurazione e dello stato della sessione di mirroring del database. Un server hot standby supporta il failover rapido senza perdita di transazioni di cui è stato eseguito il commit, mentre un server warm standby supporta la forzatura del servizio (con possibile perdita di dati).  
  
 Nome del database di produzione di *database principale*, e viene chiamata la copia di standby di *database mirror*. Il database principale e mirror devono risiedere in istanze separate di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (istanze del server), e devono risiedere in computer separati se possibile.  
  
 Istanza del server di produzione, chiamata di *server principale*, comunica con l'istanza del server di standby, denominato il *server mirror*. Il server principale e mirror utilizzate come partner all'interno di un mirroring del database *sessione*. Se il server principale non riesce, il server mirror può rendere il database nel database principale tramite un processo denominato *failover*. Partner_A e Partner_B, ad esempio, sono due server partner, con il database principale inizialmente su Partner_A come server principale e il database mirror che risiede in Partner_B come server mirror. Se Partner_A passa alla modalità offline, il database su Partner_B può eseguire il failover per diventare il database principale corrente. Quando Partner_A si unisce alla sessione di mirroring, diventa il server mirror e il database diventa il database mirror.  
  
 Le configurazioni del mirroring del database alternative offrono livelli diversi di prestazioni e sicurezza dei dati e supportano forme diverse di failover. Per altre informazioni, vedere [Mirroring del database &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
 È possibile utilizzare un alias quando si specifica il nome del database mirror.  
  
> [!NOTE]  
>  Per informazioni sui tentativi di connessione iniziale e tentativi di riconnessione a un database con mirroring, vedere [connettere client a una sessione di mirroring del Database &#40;SQL Server&#41;](../../../database-engine/database-mirroring/connect-clients-to-a-database-mirroring-session-sql-server.md).  
  
## <a name="programming-considerations"></a>Considerazioni sulla programmazione  
 Quando si verifica un errore nel server di database principale, l'applicazione client riceve errori in risposta a chiamate API che indicano che la connessione al database è stata persa. In questo caso qualsiasi modifica al database di cui non sia stato eseguito il commit viene persa e viene eseguito il rollback della transazione corrente. In una situazione di questo tipo l'applicazione deve chiudere la connessione (o rilasciare l'oggetto origine dati) e stabilirla nuovamente. La connessione viene reindirizzata in maniera trasparente al database mirror che ora viene utilizzato come server principale.  
  
 Quando viene stabilita una connessione, il server principale invia l'identità del proprio partner di failover al client da utilizzare quando si verifica il failover. Nei casi in cui un'applicazione ha provato a stabilire una connessione dopo che si è verificato un errore nel server principale, il client non conosce l'identità del partner di failover. Per consentire ai client di far fronte a questo scenario, una proprietà di inizializzazione e una parola chiave della stringa di connessione associata consentono al client di specificare l'identità del partner di failover. L'attributo client viene utilizzato solo in questo scenario. Se è disponibile, il server principale non viene utilizzato. Se il server partner di failover fornito dal client non si riferisce a un server utilizzato come partner di failover, la connessione viene rifiutata dal server. Per consentire alle applicazioni di adattarsi alle modifiche di configurazione, l'identità del partner di failover effettivo può essere determinata ispezionando l'attributo dopo che è stata stabilita la connessione. È consigliabile memorizzare nella cache le informazioni sul partner per aggiornare la stringa di connessione oppure escogitare una strategia per eseguire un nuovo tentativo nel caso in cui il primo tentativo di stabilire una connessione non riesca.  
  
> [!NOTE]  
>  È necessario specificare in modo esplicito il database che dovrà essere utilizzato da una connessione se si desidera utilizzare questa caratteristica in un DSN, una stringa di connessione oppure una proprietà o un attributo di connessione. Il Driver OLE DB per SQL Server non tenterà di failover al database del partner se questo non viene eseguito.  
>   
>  Il mirroring è una caratteristica del database. Nelle applicazioni che utilizzano più database potrebbe non essere possibile sfruttare questa caratteristica.  
>   
>  Per i nomi di server, inoltre, non viene fatta distinzione tra maiuscole e minuscole, mentre tale distinzione viene fatta per i nomi di database. È pertanto consigliabile assicurarsi di utilizzare la stessa combinazione tra maiuscole e minuscole nei DSN e nelle stringhe di connessione.  
  
## <a name="ole-db-driver-for-sql-server"></a>Driver OLE DB per SQL Server  
 Il Driver OLE DB per SQL Server supporta di mirroring del database tramite connessione, gli attributi della stringa. La proprietà SSPROP_INIT_FAILOVERPARTNER è stato aggiunto al set di proprietà DBPROPSET_SQLSERVERDBINIT e **FailoverPartner** (parola chiave) è un nuovo attributo di stringa di connessione per DBPROP_INIT_PROVIDERSTRING. Per altre informazioni, vedere [Using Connection String Keywords con il Driver OLE DB per SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).  
  
 La cache di failover viene gestita finché è caricato il provider, ovvero fino **CoUninitialize** viene chiamato o fino a quando l'applicazione dispone di un riferimento a un oggetto gestito dal Driver OLE DB per SQL Server, ad esempio un oggetto origine dati .  
  
 Per informazioni dettagliate sui Driver OLE DB per il supporto di SQL Server per il mirroring del database, vedere [proprietà di inizializzazione e autorizzazione](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md).  
 
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per la funzionalità di SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)   
 [Connettere client a una sessione di mirroring del database &#40;SQL Server&#41;](../../../database-engine/database-mirroring/connect-clients-to-a-database-mirroring-session-sql-server.md)   
 [Mirroring del database &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
