---
title: Note sulla versione di SQL Server 2012 SP4 | Microsoft Docs
ms.prod: sql-server-2012
ms.technology: server-general
ms.custom: 
ms.date: 10/05/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67cb8b3e-3d82-47f4-840d-0f12a3bff565
caps.latest.revision: "0"
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b09784b129109f907c19a56a2a6fadcba119e73d
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="sql-server-2012-sp4-release-notes"></a>Note sulla versione di SQL Server 2012 SP4
In questo argomento vengono riassunti i miglioramenti inclusi in SQL Server 2012 SP4. Vengono anche descritti i problemi da esaminare o risolvere prima di installare il Service Pack 4. Le note sulla versione sono disponibili solo online, non nel supporto di installazione. Questo argomento viene aggiornato periodicamente, in caso di rilevamento di nuovi problemi. Per un elenco dettagliato delle correzioni nel Service Pack 4, vedere [Informazioni sulla versione di SQL Server 2012 Service Pack 4](https://go.microsoft.com/fwlink/?linkid=846937).  

> Il Service Pack 4 include tutti gli aggiornamenti cumulativi di SQL Server 2012 SP3.
  
##<a name="download-pages"></a>Pagine di download
I collegamenti seguenti consentono di accedere ai principali pacchetti di download per SQL Server 2012 SP3. Le pagine per il download includono informazioni sui requisiti di sistema e istruzioni di base per l'installazione.
- [Installazione della patch di SQL Server 2012 SP4](https://go.microsoft.com/fwlink/?linkid=846829)
- [SQL Server 2012 SP4 Express](https://go.microsoft.com/fwlink/?linkid=846905)
- [Microsoft SQL Server 2012 SP4 Feature Pack](https://go.microsoft.com/fwlink/?linkid=846907)

##  <a name="sp4-performance-and-scale-improvements"></a>Miglioramenti in termini di prestazioni e scalabilità del Service Pack 4

- **Procedura di pulizia dell'agente di distribuzione migliorata**: un database di distribuzione di dimensioni eccessive è la causa di una situazione di blocco e di deadlock. Grazie a una procedura di pulizia migliorata è possibile eliminare scenari di blocco e di deadlock di questo genere. 
- **Scalabilità dinamica degli oggetti in memoria**: partizione dinamica di oggetti in memoria in base al numero di nodi e di core per ridimensionare l'hardware moderno. Obiettivo della promozione dinamica è impedire potenziali colli di bottiglia ed eseguire automaticamente la partizione di un oggetto in memoria thread-safe. È possibile promuovere dinamicamente gli oggetti in memoria non partizionati perché siano partizionati in base al nodo. Il numero delle partizioni corrisponde al numero di nodi NUMA. Gli oggetti in memoria partizionati in base al nodo possono essere ulteriormente promossi perché siano partizionati in base alla CPU, nel caso in cui il numero delle partizioni sia corrispondente al numero delle CPU.
- **Abilitazione di 8 TB per pool di buffer**: abilitazione dello spazio degli indirizzi virtuali a 128 TB per pool di buffer
- **Pulizia di Rilevamento modifiche**: miglioramento delle prestazioni di pulizia di Rilevamento modifiche ed efficienza delle tabelle lato Rilevamento modifiche. 

## <a name="sp4-supportability-and-diagnostics-improvements"></a>Miglioramenti al supporto e alla diagnostica del Service Pack 4

- **Supporto per dump completi per gli agenti di replica**: oggi, se gli agenti di replica incontrano un'eccezione non gestita, il comportamento predefinito prevede la creazione di un breve dump dei sintomi dell'eccezione. Tale comportamento richiede passaggi complessi per la risoluzione dei problemi correlati alle eccezioni non gestite. Il Supporto Package 4 introduce una nuova chiave del Registro di sistema che supporta la creazione di un dump completo per gli agenti di replica.
- **Diagnostica avanzata nel file XML dello showplan**: il file XML dello showplan è stato migliorato per contenere informazioni su flag di traccia abilitati, frazioni di memoria per l'ottimizzazione del join annidato dei cicli, tempo di CPU e tempo trascorso. 
- **Migliore correlazione tra la diagnostica di XEvent e delle DMV**: i campi query_hash e query_plan_hash vengono usati per identificare una query in modo univoco. Nelle DMV sono definiti come varbinary (8), mentre in XEvent come UINT64. Poiché in SQL Server non esiste un "bigint senza segno", il cast non sempre funziona. Questo miglioramento introduce nuove colonne azione/filtro di XEvent equivalenti ai campi query_hash e query_plan_hash ad eccezione del fatto che tali valori sono definiti come INT64. In questo modo è possibile correlare le query tra XEvent e le viste a gestione dinamica. 
- **Migliore diagnostica di concessione/utilizzo memoria**: nuovo evento XEvent query_memory_grant_usage (backport da Server 2016 SP1)
- **Aggiunta della traccia di protocollo ai passaggi di negoziazione SSL**: aggiungere informazioni di traccia bit su negoziazione riuscita/non riuscita, ad esempio il protocollo, può essere utile per risolvere problemi di connettività,ad esempio durante la distribuzione di TLS 1.2
- **Impostazione del livello di compatibilità corretto per il database di distribuzione**: dopo l'installazione del Service Pack il livello di compatibilità del database di distribuzione viene impostato su 90. La modifica del livello era dovuta a un problema nella stored procedure sp_vupgrade_replication. Il Service Pack è stato modificato e ora imposta il livello di compatibilità corretto per il database di distribuzione. 
- **Nuovo comando DBCC per la clonazione di un database**: è stato aggiunto un nuovo comando DBCC per la clonazione del database che consente agli utenti esperti, ad esempio CSS, di risolvere problemi di database di produzione esistenti clonando lo schema e i metadati e non i dati. La chiamata viene eseguita con DBCC clonedatabase ('source_database_name', 'clone_database_name'). È consigliabile non usare i database clonati in ambienti di produzione. Per vedere se un database è stato generato da una chiamata per la clonazione del database, è possibile usare il comando seguente, selezionare DATABASEPROPERTYEX('clonedb', 'isClone'). Il valore restituito pari a 1 è true e il valore 0 è false. 
- **Informazioni sul file TempDB e sulle dimensioni nel log degli errori di SQL**: se le dimensioni e l'aumento automatico sono diversi per i file di dati TempDB durante l'avvio, viene stampato il numero di file e attivato un avviso.
- **Messaggi di supporto per l'inizializzazione immediata dei file nel log degli errori di SQL Server**: nel log degli errori viene indicato se l'inizializzazione immediata dei file di database è abilitata/disabilitata
- **Nuova DMF in sostituzione a DBCC INPUTBUFFER**: in sostituzione a DBCC INPUTBUFFER è stata introdotta sys.dm_input_buffer, una nuova funzione a gestione dinamica che usa session_id come parametro
- **Miglioramento di eventi XEvent in caso di errore di routing di lettura per un gruppo di disponibilità**: attualmente l'evento XEvent read_only_rout_fail viene generato solo in presenza di un elenco di routing. Nessuno dei server contenuto in questo elenco è tuttavia disponibile per le connessioni. Questo miglioramento aggiunge informazioni in caso di risoluzione dei problemi e interessa anche gli elementi di codice in cui è attivo XEvent. 
- **Gestione migliorata di Service Broker in caso di failover del gruppo di disponibilità**: attualmente quando Service Broker è abilitato in un database del gruppo di disponibilità, durante un failover del gruppo di disponibilità tutte le connessioni a Service Broker che hanno avuto origine nella replica primaria vengono lasciate aperte. Questo miglioramento chiude tutte le connessioni aperte durante un failover del gruppo di disponibilità.
- **[Partizionamento soft-NUMA automatico](https://msdn.microsoft.com/library/ms345357(SQL.120).aspx)** : con SQL 2014 SP2 viene introdotta la configurazione soft-NUMA automatica quando il flag di traccia 8079 è abilitato al livello server. Quando il flag di traccia 8079 viene abilitato durante l'avvio, SQL Server 2014 SP2 interroga il layout di hardware e configura automaticamente soft-NUMA nei sistemi che segnalano 8 o più CPU per nodo NUMA. Il comportamento soft-NUMA automatico supporta l'Hyper-Threading (HT/processore logico). Il partizionamento e la creazione di nodi aggiuntivi ridimensionano l'elaborazione in background aumentando il numero di listener tramite scalabilità e le funzionalità di crittografia e di rete. È consigliabile testare le prestazioni del carico di lavoro con la configurazione soft-NUMA automatica prima di attivarlo nell'ambiente di produzione.

## <a name="see-also"></a>Vedere anche
- [Installare gli aggiornamenti dei servizi di SQL Server 2012](https://msdn.microsoft.com/library/hh479746(v=sql.110).aspx)
- [Identificazione della versione e dell'edizione di SQL Server](https://support.microsoft.com/en-us/help/321185)

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
