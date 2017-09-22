---
title: "Novità di SQL Server 2017 RC1 in Linux | Documenti Microsoft"
description: "Questo argomento sono incluse nuove funzionalità per la versione corrente di SQL Server 2017 in Linux."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 08/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 456b6f31-6b97-4e31-80ab-b40151ec4868
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 622e0ed2242ddc454028962c63b5760a6baad38a
ms.contentlocale: it-it
ms.lasthandoff: 09/21/2017

---
# <a name="whats-new-for-sql-server-2017-on-linux"></a>Novità di SQL Server 2017 su Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

In questo argomento vengono descritte le novità di SQL Server 2017 su Linux.

## <a name="rc2"></a>RC2

La versione RC2 contiene varie correzioni di bug e miglioramenti.

## <a name="rc1"></a>RC1

La versione RC1 contiene gli aggiornamenti e i miglioramenti seguenti:

- Abilitato Transparent Layer Security (TLS) per le connessioni crittografate. Per ulteriori informazioni, vedere [crittografia delle connessioni a SQL Server in Linux](sql-server-linux-encrypted-connections.md).
- Abilitato [l'autenticazione di Active Directory](sql-server-linux-active-directory-authentication.md).
- Abilitato [posta elettronica database](../relational-databases/database-mail/database-mail.md).
- Aggiunta del supporto di IPV6.
- Variabili di ambiente aggiunto per la configurazione iniziale di SQL Server. Per ulteriori informazioni, vedere [le impostazioni di configurazione SQL Server con le variabili di ambiente in Linux](sql-server-linux-configure-environment-variables.md).
- Rimosso **sqlpackage** da installato i file binari. SqlPackage sia ancora possibile eseguirlo su Linux in modalità remota da Windows.
- Condividere i set di dischi cluster resource agente che il nome della risorsa come viene effettuata su un'istanza cluster di failover di Windows SQL Server. `@@ServerName`Restituisce il nome di risorsa cluster disco condiviso di SQL Server; prima di RC1 è stato restituito il nome del nodo del cluster che la risorsa di proprietà.

## <a name="ctp-21"></a>CTP 2.1

La versione CTP 2.1 contiene gli aggiornamenti e i miglioramenti seguenti:

- Aggiunto [variabili di ambiente per configurare il servizio SQL Server](sql-server-linux-configure-environment-variables.md).
- [MSSQL-conf](sql-server-linux-configure-mssql-conf.md) è necessario disporre di due parti convenzione di denominazione per le impostazioni.
- Il [mssql scripter](https://github.com/Microsoft/sql-xplat-cli) strumento. Questa utilità consente agli sviluppatori, amministratori di database, gli amministratori di sistema di generare `CREATE` e `INSERT` script Transact-SQL da oggetti di database nel database di SQL Server, database SQL di Azure e Azure SQL DW dalla riga di comando.
- Il [strumento DBFS](https://github.com/Microsoft/dbfs). Questo è uno strumento open source che consente agli amministratori di database e gli amministratori di sistema per monitorare SQL Server più facilmente all'esposizione dei dati in tempo reale da SQL Server viste a gestione dinamica (DMV) come file virtuali in una directory virtuale in sistemi operativi Linux.
- SQL Server Integration Services (SSIS) viene ora eseguito in Linux. Inoltre, è un nuovo pacchetto che consente di eseguire pacchetti SSIS in Linux dalla riga di comando. Per altre informazioni, vedere il [post di blog annunciato il supporto SSIS per Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/). Con SSIS in Linux CTP 2.1 aggiornamento, i pacchetti SSIS possono utilizzare connessioni di ODBC in Linux. Per altre informazioni, vedere il [post del blog annuncia il supporto ODBC in Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

## <a name="ctp-20"></a>NELLA VERSIONE CTP 2.0

La versione CTP 2.0 contiene i seguenti miglioramenti e correzioni:

- Aggiunto **Log Shipping** funzionalità di SQL Server Agent.
- Messaggi localizzati di mssql-conf.
- Formattazione di percorso di Linux sono ora compatibili in tutto il motore di SQL Server. Ma sono supportate per "c:\\" percorsi con prefissi continuerà.
- Abilitato DMV **sys.dm_os_file_exists**.
- Abilitato DMV **sys.fn_trace_gettable**.
- Aggiunto [modalità di sicurezza rigidi CLR](/sql/database-engine/configure-windows/clr-strict-security).
- Grafico SQL.
- Ricompilazione dell'indice Online può essere ripristinato.
- Elaborazione delle Query adattivo.
- Aggiunta codifica UTF-8 per i file di sistema, inclusi i file di log.
- Correzione di limitazione percorso database In memoria. 
- Aggiungi nuovo tipo di cluster `CLUSTER_TYPE = EXTERNAL` per la configurazione di un gruppo di disponibilità per la disponibilità elevata.
- Correggere i listener del gruppo di disponibilità per il routing di sola lettura.
- Supporto di produzione per i clienti del programma di adozione anticipata (EAP). Effettuare l'iscrizione [qui](http://aka.ms/eapsignup).

## <a name="ctp-14"></a>CTP 1.4

La versione CTP 1.4 contiene gli aggiornamenti e i miglioramenti seguenti:

- Abilitato il [SQL Server Agent](sql-server-linux-setup-sql-agent.md).
  - Abilitare la funzionalità di processi di T-SQL.
- Fuso orario predefinito bug:
  - Supporto di fuso orario per Asia/Kolkata.
  - Funzione GETDATE () predefinito.
- Rete Async I / 0 miglioramenti:
  - Miglioramenti significativi delle prestazioni del carico di lavoro OLTP In memoria.
- Immagine di docker include ora le utilità della riga di comando di SQL Server. (sqlcmd/bcp).
- Stato abilitato il supporto di Virtual Device Interface (VDI) per i backup.
- Percorso del database TempDB può essere modificata dopo l'installazione tramite `ALTER DATABASE`.

## <a name="ctp-13"></a>CTP 1.3

La versione CTP 1.3 contiene gli aggiornamenti e i miglioramenti seguenti:

- Abilitato [ricerca Full-text](sql-server-linux-setup-full-text-search.md) funzionalità.
- Abilitato Always On [funzionalità gruppi di disponibilità](sql-server-linux-availability-group-overview.md) per la disponibilità elevata.
- Funzionalità aggiuntive in **mssql conf**:
  - Prima fase di configurazione usando **mssql conf**. Verificare l'utilizzo di mssql-conf nel [Guide all'installazione](sql-server-linux-setup.md#platforms).
  - Abilitazione di gruppi di disponibilità. Vedere il [argomento gruppi di disponibilità](sql-server-linux-availability-group-overview.md).
- Percorso di Linux native fisso supporta per i filegroup OLTP In memoria.
- DMV dm_os_host_info abilitato.

## <a name="ctp-12"></a>CTP 1.2

La versione CTP 1.2 contiene gli aggiornamenti e i miglioramenti seguenti:

- Supporto per [SUSE Linux Enterprise Server v12 SP2](quickstart-install-connect-suse.md).
- Correzioni di bug per i miglioramenti principali di motore e stabilità.
- Immagine di docker: 
  - Predefinito [emettere #1](https://github.com/Microsoft/mssql-docker/issues/1) aggiungendo Python all'immagine.
  - Rimosso `/opt/mssql/data` volume per il valore predefinito.
- Aggiornamento a .NET 4.6.2.

## <a name="ctp-11"></a>CTP 1.1

La versione CTP 1.1 contiene gli aggiornamenti e i miglioramenti seguenti:

- Supporto per Red Hat Enterprise Linux versione 7.3.
- Supporto per Ubuntu 16.10.
- Livello del sistema operativo Docker aggiornato per Ubuntu 16.04.
- Correzione di problemi di telemetria nell'immagine di Docker.
- Script di installazione di SQL Server predefinito correlati bug.
- Prestazioni migliorate per i moduli T-SQL compilati in modo nativo, inclusi:
  - **OPENJSON**, **FOR JSON**, **JSON** incorporati.
  - Colonne calcolate (solo gli indici sono consentiti su colonne calcolate persistenti, ma non su colonne calcolate non persistenti per le tabelle in memoria).
  - **CROSS APPLY** operazioni.
- Nuove funzionalità del linguaggio:
  - Funzioni stringa: **TRIM**, **CONCAT_WS**, **TRADUCI** e **STRING_AGG** con supporto per **WITHIN GROUP (ORDER BY)**.
  - **IMPORTAZIONE BULK** supporta ora il formato CSV e l'archiviazione Blob di Azure come File di origine.

In modalità di compatibilità 140:

- Migliorate le prestazioni degli aggiornamenti per gli indici columnstore non cluster nel caso, quando la riga si trova nell'archivio delta. Modificato da eliminare e inserire le operazioni di aggiornamento. Modificare inoltre la forma del piano usata dal livello in modo da limitare.
- Query in modalità batch ora supportano "concessioni di memoria cicli di commenti e suggerimenti". Ciò migliorerà la concorrenza e velocità effettiva nei sistemi che eseguono query ripetute che utilizzano la modalità batch. Questo può consentire più query da eseguire nei sistemi in caso contrario di blocco in memoria prima di avviare le query.
- Per consentire di piani paralleli per il prelievo invece contro columnstores i piani di miglioramento delle prestazioni nel parallelismo di modalità batch ignorando semplice piano per la modalità batch. 

[Miglioramenti di Service Pack 1](https://blogs.msdn.microsoft.com/sqlreleaseservices/sql-server-2016-service-pack-1-sp1-released/) in questa versione CTP1.1:
- Clonazione del database per CLR, Filestream o Filetable, gli oggetti In memoria e l'archivio Query.
- **CREARE** o **ALTER** operatori per gli oggetti di programmabilità.
- Nuovo **HINT USE** opzione per fornire suggerimenti per la query processor di query. Altre informazioni: [hint per la Query](/sql-docs/docs/t-sql/queries/hints-transact-sql-query).
- Account del servizio SQL possono ora identificare a livello di programmazione abilitare blocco di pagine in memoria e l'inizializzazione immediata dei File di autorizzazioni.
- Supporto per numero di file TempDB, dimensioni del file e le impostazioni di aumento delle dimensioni di file.
- Diagnostica estesa in showplan XML.
- Operatore Lightweight query esecuzione di profilatura.
- Nuova funzione a gestione dinamica **sys.dm_exec_query_statistics_xml**.
- Nuova funzione a gestione dinamica per le statistiche incrementali.
- Rimossa disturbate In memoria correlato la registrazione messaggi dal log degli errori.
- Diagnostica di latenza AlwaysOn migliorate.
- Pulire il rilevamento delle modifiche manuale.
- **DROP TABLE** il supporto per la replica.
- **L'istruzione BULK INSERT** in heap con **automatica TABLOCK** in TF 715.
- Parallelo **INSERT... Selezionare** modifiche per tabelle temporanee locali.

Altre informazioni su questi aggiornamenti nel [descrizione versione del Service Pack 1](https://blogs.msdn.microsoft.com/sqlreleaseservices/sql-server-2016-service-pack-1-sp1-released/).

Numerosi miglioramenti di motore di database si applicano a Windows e Linux. Per funzionalità del motore di database che non sono attualmente supportate in Linux, può essere l'unica eccezione. Per ulteriori informazioni, vedere [novità di SQL Server 2017 (motore di Database)](https://msdn.microsoft.com/library/mt775028).

## <a name="see-also"></a>Vedere anche

Per i requisiti di installazione, aree di funzionalità non supportate e problemi noti, vedere [note sulla versione di SQL Server 2017 in Linux](sql-server-linux-release-notes.md).

