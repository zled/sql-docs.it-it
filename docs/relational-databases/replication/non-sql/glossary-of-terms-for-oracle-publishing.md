---
title: "Glossario dei termini per la pubblicazione Oracle | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pubblicazione Oracle [replica di SQL Server], glossario"
ms.assetid: e21dfa4b-6144-4be7-9cbf-ca2709b2bd9f
caps.latest.revision: 32
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 32
---
# Glossario dei termini per la pubblicazione Oracle
  In caso di configurazione e amministrazione della pubblicazione Oracle, è consigliabile avere familiarità con i termini Oracle seguenti. Per un elenco completo dei termini Oracle, vedere la documentazione online Oracle.  
  
 Tabelle organizzate a indice (IOT, Index Organized Table)  
 Una tabella i cui dati sono fisicamente ordinati su disco in ordine di indice. è simile a un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tabella con un indice cluster. Una tabella organizzata a indice viene replicata in un Sottoscrittore come una tabella con indice cluster.  
  
 Istanza  
 Un database Oracle è associato a un'istanza, che include la memoria e i processi in background che supportano il database. Un'istanza di Oracle è sempre mappata a un singolo database, mentre un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] può contenere più database. In alcuni casi, un database Oracle può disporre di più istanze.  
  
 Listener Oracle  
 Gestisce il traffico di rete in ingresso per un'istanza di database Oracle. Durante la configurazione della connettività di rete per un database Oracle, si specifica il protocollo con cui viene inviato il traffico e la porta su cui il listener resta in attesa di traffico. Il listener viene in genere configurato per l'esecuzione sullo stesso computer dell'istanza di database Oracle e può essere configurato per una o più istanze.  
  
 ROWID  
 Puntatore alla posizione di una riga specifica in un database. Poiché il recupero di righe mediante ROWID risulta più veloce rispetto all'utilizzo di un indice o un'analisi di tabella, ROWID viene temporaneamente utilizzato nella replica durante l'elaborazione delle modifiche alle tabelle pubblicate.  
  
 Sequenza  
 Oggetto di database utilizzato per generare numeri univoci. Le sequenze vengono utilizzate nella replica per ordinare le modifiche apportate alle tabelle pubblicate.  
  
 SQL\*Plus  
 Applicazione utilizzata per l'accesso e l'esecuzione di query in database Oracle. È simile a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **sqlcmd**.  
  
 Sinonimo  
 Alias di un oggetto. Lo speciale sinonimo public **MSSQLSERVERDISTRIBUTOR** viene creato automaticamente quando viene configurato un server di pubblicazione Oracle. Il sinonimo fa riferimento il **HREPL_Distributor** tabella e fornisce un puntatore logico per il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] server di distribuzione che il server di pubblicazione dei servizi.  
  
 Dopo la pubblicazione di un database Oracle, i successivi tentativi di configurare questo server di pubblicazione per l'utilizzo di un diverso server di distribuzione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avranno esito negativo, poiché questo sinonimo public identifica lo specifico server di distribuzione già configurato per il server di pubblicazione.  
  
 Spazio di tabella  
 Unità di archiviazione di database approssimativamente equivalente a un filegroup in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Nome del servizio TNS  
 TNS (Transparent Network Substrate) è un livello di comunicazione utilizzato dai database Oracle. Il nome del servizio TNS è il nome con cui un'istanza di database Oracle viene riconosciuta in una rete. Il nome del servizio TNS viene assegnato durante la configurazione della connettività per il database Oracle. Il nome del servizio TNS viene utilizzato nella replica per identificare il server di pubblicazione e stabilire connessioni.  
  
 Schema utente  
 Uno schema utente può essere considerato come un utente di database proprietario di un determinato set di oggetti di database. Lo schema utente di amministrazione della replica possiede tutti gli oggetti creati dal [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] processo di replica nel database Oracle, ad eccezione del **MSSQLSERVERDISTRIBUTOR** sinonimo public.  
  
## Vedere anche  
 [Configurazione di un server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Oggetti creati nel server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/objects-created-on-the-oracle-publisher.md)   
 [Server di pubblicazione non SQL Server](../../../relational-databases/replication/non-sql/non-sql-server-publishers.md)   
 [Panoramica della pubblicazione Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  