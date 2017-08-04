---
title: Note sulla versione di SQL Server 2017 in Linux | Documenti Microsoft
description: "In questo argomento contiene le note sulla versione e tutte le funzionalità supportate per 2017 di SQL Server in esecuzione in Linux. Note sulla versione sono inclusi per RC2 e versioni precedenti."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 08/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 1314744f-fcaf-46db-800e-2918fa7e1b6c
ms.translationtype: MT
ms.sourcegitcommit: b2f5d26757bd436cfd21076b2a4899376ee60c9f
ms.openlocfilehash: 1907ef1ae99146fe7cdf2ca124af22aabdc29b35
ms.contentlocale: it-it
ms.lasthandoff: 08/04/2017

---
# <a name="release-notes-for-sql-server-2017-on-linux"></a>Note sulla versione di SQL Server 2017 su Linux

Le note sulla versione seguenti si applicano a 2017 di SQL Server in esecuzione in Linux. Questa versione supporta molte delle funzionalità del motore di database di SQL Server per Linux. L'argomento riportato di seguito viene suddiviso in sezioni per ogni versione, che iniziano con la versione più recente, RC2. Vedere le informazioni contenute in ogni sezione per le piattaforme supportate, strumenti, funzionalità e i problemi noti.

La tabella seguente elenca le versioni di SQL Server 2017 trattate in questo argomento.

| Versione | Version | Data di rilascio |
|-----|-----|-----|
| [RC2](#RC2) | 14.0.900.75 | 8-2017 |
| [RC1](#RC1) | 14.0.800.90 | 7-2017 |
| [CTP 2.1](#ctp21) | 14.0.600.250 | 5-2017 |
| [NELLA VERSIONE CTP 2.0](#ctp20) | 14.0.500.272 | 4-2017 |
| [CTP 1.4](#ctp14) | 14.0.405.198 | 3-2017 |
| [CTP 1.3](#ctp13) | 14.0.304.138 | 2-2017 |
| [CTP 1.2](#ctp12) | 14.0.200.24 | 1-2017 |
| [CTP 1.1](#ctp11) | 14.0.100.187 | 12-2016 |
| [CTP 1.0](#ctp10) | 14.0.1.246 | 11-2016 |

## <a id="RC2"></a>RC2 (agosto 2017)

La versione del motore di SQL Server per questa versione è 14.0.900.75.

### <a name="supported-platforms"></a>Piattaforme supportate

| Piattaforma | File system | Guida all'installazione |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 Workstation desktop e Server | XFS o EXT4 | [Guida all'installazione](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | EXT4 | [Guida all'installazione](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | EXT4 | [Guida all'installazione](quickstart-install-connect-ubuntu.md) | 
| Motore docker 1.8 + in Windows, Mac o Linux | N/D | [Guida all'installazione](quickstart-install-connect-docker.md) | 

> [!NOTE]
> È necessario almeno 3,25 GB di memoria per l'esecuzione di SQL Server in Linux.
> Motore di SQL Server è stato testato fino a 1,5 TB di memoria in questo momento.

### <a name="package-details"></a>Dettagli del pacchetto

Nella tabella seguente sono elencati i dettagli del pacchetto e i percorsi di download per i pacchetti RPM e Debian. Si noti che è necessario scaricare i pacchetti direttamente se si utilizza la procedura nelle guide di installazione seguenti:

- [Installare il pacchetto di SQL Server](sql-server-linux-setup.md)
- [Installare il pacchetto di ricerca Full-text](sql-server-linux-setup-full-text-search.md)
- [Installare il pacchetto di SQL Server Agent](sql-server-linux-setup-sql-agent.md)

| Pacchetto | versione del pacchetto | Download |
|-----|-----|-----|
| Pacchetto Red Hat RPM | 14.0.900.75-1 | [Pacchetto RPM motore](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.900.75-1.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.900.75-1.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.900.75-1.x86_64.rpm)</br>[Pacchetto RPM di SQL Server Agent](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.900.75-1.x86_64.rpm) | 
| Pacchetto RPM SLES | 14.0.900.75-1 | [pacchetto RPM motore MSSQL server](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.900.75-1.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.900.75-1.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.900.75-1.x86_64.rpm)</br>[Pacchetto RPM di SQL Server Agent](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.900.75-1.x86_64.rpm) | 
| Pacchetto Debian Ubuntu 16.04 | 14.0.900.75-1 | [Pacchetto Debian motore](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.900.75-1_amd64.deb)</br>[Pacchetto Debian a disponibilità elevata](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.900.75-1_amd64.deb)</br>[Pacchetto Debian di ricerca full-text](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.900.75-1_amd64.deb)</br>[Pacchetto Debian di SQL Server Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.900.75-1_amd64.deb) |

### <a name="supported-client-tools"></a>Strumenti client supportati

| Strumento | Versione minima |
|-----|-----|
| [SQL Server Management Studio (SSMS) per Windows](https://go.microsoft.com/fwlink/?linkid=847722) | 17.0 |
| [SQL Server Data Tools per Visual Studio](https://go.microsoft.com/fwlink/?linkid=846626) | 17.0 |
| [Codice di Visual Studio](https://code.visualstudio.com) con il [estensione mssql](https://aka.ms/mssql-marketplace) | Più recente |

### <a name="unsupported-features-and-services"></a>Servizi e funzionalità non supportate

Le funzionalità e i servizi seguenti non sono disponibili su Linux in questo momento. Il supporto di queste funzionalità verrà sempre abilitato durante la cadenza mensile gli aggiornamenti del programma di anteprima.

| Area | Servizio o funzionalità non supportata |
|-----|-----|
| **Motore di database** | Replica transazionale |
| &nbsp; | Replica di tipo merge |
| &nbsp; | Estensione database |
| &nbsp; | Polybase |
| &nbsp; | Query distribuita con connessioni a 3rd party |
| &nbsp; | (XP_CMDSHELL, e così via). le stored procedure estese di sistema |
| &nbsp; | Tabella filetable |
| &nbsp; | Impostare gli assembly CLR con il EXTERNAL_ACCESS o UNSAFE autorizzazione |
| &nbsp; | Estensione pool di buffer |
| **SQL Server Agent** |  Sottosistemi: CmdExec, PowerShell, agente di lettura coda, SSIS, SSAS, SSRS |
| &nbsp; | Avvisi |
| &nbsp; | Agente di lettura log |
| &nbsp; | Change Data Capture |
| &nbsp; | Backup gestito |
| **Disponibilità elevata** | Mirroring del database  |
| **Sicurezza** | Extensible Key Management |
| **Servizi** | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>Problemi noti

Nelle sezioni seguenti vengono descritti problemi noti relativi a questa versione di SQL Server 2017 RC2 in Linux.

#### <a name="general"></a>Generale

- La lunghezza del nome host in cui SQL Server è installato deve essere 15 caratteri o meno. 

    - **Risoluzione**: modificare il nome e così via/nome host e un valore 15 caratteri lunghi o meno.

- Impostare manualmente l'ora di sistema con le versioni precedenti nel tempo causerà l'esecuzione SQL Server per interrompere l'aggiornamento dell'ora di sistema interno all'interno di SQL Server.

    - **Risoluzione**: riavviare SQL Server.

- Sono supportate solo le installazioni a istanza singola.

    - **Risoluzione**: se si desidera disporre di più di un'istanza in un determinato host, è consigliabile utilizzare le macchine virtuali o i contenitori di Docker. 

- Gestione configurazione SQL Server non è possibile connettersi a SQL Server in Linux.

- La lingua predefinita di **sa** account di accesso è l'inglese.

    - **Risoluzione**: modificare la lingua del **sa** account di accesso con il **ALTER LOGIN** istruzione.

#### <a name="databases"></a>Database

- Impossibile spostare il database master con l'utilità mssql conf. Altri database di sistema possono essere spostati con mssql conf

- Quando si ripristina un database di cui è stato eseguito il backup in SQL Server in Windows, è necessario utilizzare il **WITH MOVE** clausola nell'istruzione Transact-SQL.

- Le transazioni distribuite che richiedono il servizio Microsoft Distributed Transaction Coordinator non sono supportate in SQL Server in esecuzione in Linux. SQL Server a SQL Server sono supportate le transazioni distribuite.

- Determinati algoritmi (pacchetti di crittografia) per Transport Layer Security (TLS) non funzionano correttamente con SQL Server in Linux. Quando si tenta di connettersi a SQL Server, nonché problemi di attivazione delle connessioni tra repliche di gruppi di disponibilità elevata, causando errori di connessione.

   - **Risoluzione**: modificare il **mssql.conf** script di configurazione per SQL Server in Linux per disabilitare i pacchetti di crittografia problematico, effettuando le operazioni seguenti:

      1. Aggiungere quanto segue per /var/opt/mssql/mssql.conf.

      ```
      [network]
      tlsciphers=ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:!ECDHE-ECDSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES128-GCM-SHA256:!ECDHE-ECDSA-AES256-SHA384:!ECDHE-ECDSA-AES128-SHA256:!ECDHE-ECDSA-AES256-SHA:!ECDHE-ECDSA-AES128-SHA:!ECDHE-RSA-AES256-SHA384:!ECDHE-RSA-AES128-SHA256:!ECDHE-RSA-AES256-SHA:!ECDHE-RSA-AES128-SHA:!DHE-RSA-AES256-GCM-SHA384:!DHE-RSA-AES128-GCM-SHA256:!DHE-RSA-AES256-SHA:!DHE-RSA-AES128-SHA:!DHE-DSS-AES256-SHA256:!DHE-DSS-AES128-SHA256:!DHE-DSS-AES256-SHA:!DHE-DSS-AES128-SHA:!DHE-DSS-DES-CBC3-SHA:!NULL-SHA256:!NULL-SHA
      ```

      1. Riavviare SQL Server con il comando seguente.
   
      ```
      sudo systemctl restart mssql-server
      ```

#### <a name="remote-database-files"></a>File di database remoto

- Hosting dei file di database in un server NFS non è supportata in questa versione. Include l'utilizzo di NFS per disco condiviso clustering di failover e database nelle istanze non cluster. Stiamo lavorando su come abilitare il supporto di server NFS nelle prossime versioni.

#### <a name="localization"></a>Localizzazione

- Se le impostazioni locali sono inglese (it_IT) durante l'installazione, è necessario utilizzare la codifica UTF-8 nella sessione/terminale bash. Se si utilizza la codifica ASCII, si potrebbe essere visualizzato un errore simile al seguente:

   ```
   UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
   ```

   Se non è possibile utilizzare la codifica UTF-8, eseguire l'installazione utilizzando la variabile di ambiente MSSQL_LCID per specificare il linguaggio selezionato.

   ```bash
   sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
   ```

#### <a name="full-text-search"></a>Ricerca full-text
- Non tutti i filtri sono disponibili in questa versione, inclusi i filtri per i documenti di Office. Per un elenco di filtri supportati, vedere [installare di ricerca Full-Text di SQL Server in Linux](sql-server-linux-setup-full-text-search.md#filters).

#### <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)
È possibile eseguire pacchetti SSIS in Linux. Per altre informazioni, vedere gli articoli seguenti:
-   [Post di blog annunciato il supporto SSIS per Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/).
-   [Installare SQL Server Integration Services (SSIS) in Linux](sql-server-linux-setup-ssis.md)
-   [Estrarre, trasformare e caricare i dati in Linux con SSIS](sql-server-linux-migrate-ssis.md)

Tenere presente i seguenti problemi noti con questa versione.

- Il **mssql server è** pacchetto è supportato in Ubuntu e Red Hat Enterprise Linux (RHEL) in questa versione.

- Con SSIS in aggiornamento di Linux CTP 2.1 e versioni successive, i pacchetti SSIS possono utilizzare connessioni di ODBC in Linux. Questa funzionalità è stata testata con SQL Server e i driver ODBC di MySQL, ma anche dovrebbe funzionare con qualsiasi driver ODBC Unicode che osserva la specifica ODBC. In fase di progettazione, è possibile fornire un DSN o una stringa di connessione per connettersi ai dati ODBC; è inoltre possibile utilizzare l'autenticazione di Windows. Per altre informazioni, vedere il [post del blog annuncia il supporto ODBC in Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

- Le funzionalità seguenti non sono supportate in questa versione, quando si eseguono i pacchetti SSIS in Linux:
  - Database del catalogo SSIS
  - Esecuzione del pacchetto pianificato dall'agente SQL
  - Autenticazione di Windows
  - Componenti di terze parti
  - Change Data Capture (CDC)
  - Scalabilità orizzontale SSIS
  - Azure Feature Pack per SSIS
  - Supporto di Hadoop e HDFS
  - Microsoft Connector for SAP BW

#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
Le limitazioni seguenti si applicano a SQL Server Management Studio in Windows connessi a SQL Server in Linux.

- I piani di manutenzione non sono supportati.

- Gestione dei Data Warehouse di e l'agente di raccolta dati in SQL Server Management Studio non sono supportati. 

- I componenti SSMS UI con l'autenticazione di Windows o le opzioni del registro eventi di Windows non funzionano con Linux. È comunque possibile utilizzare queste funzionalità con altre opzioni, ad esempio account di accesso SQL. 

- Impossibile modificare il numero di file di log da mantenere.

### <a name="next-steps"></a>Passaggi successivi

Per iniziare, vedere le esercitazioni di avvio rapido seguenti:

- [Installare in Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installare in SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installare in Ubuntu](quickstart-install-connect-ubuntu.md)
- [Eseguire in Docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![Grafico della barra di separazione](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a id="RC1"></a>RC1 (luglio 2017)
La versione del motore di SQL Server per questa versione è 14.0.800.90.

### <a name="supported-platforms"></a>Piattaforme supportate 

| Piattaforma | File system | Guida all'installazione |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 Workstation desktop e Server | XFS o EXT4 | [Guida all'installazione](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | EXT4 | [Guida all'installazione](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | EXT4 | [Guida all'installazione](quickstart-install-connect-ubuntu.md) | 
| Motore docker 1.8 + in Windows, Mac o Linux | N/D | [Guida all'installazione](quickstart-install-connect-docker.md) | 

> [!NOTE]
> È necessario almeno 3,25 GB di memoria per l'esecuzione di SQL Server in Linux.
> Motore di SQL Server è stato testato fino a 1 TB di memoria in questo momento.

### <a name="package-details"></a>Dettagli del pacchetto
Nella tabella seguente sono elencati i dettagli del pacchetto e i percorsi di download per i pacchetti RPM e Debian. Si noti che è necessario scaricare i pacchetti direttamente se si utilizza la procedura nelle guide di installazione seguenti:

- [Installare il pacchetto di SQL Server](sql-server-linux-setup.md)
- [Installare il pacchetto di ricerca Full-text](sql-server-linux-setup-full-text-search.md)
- [Installare il pacchetto di SQL Server Agent](sql-server-linux-setup-sql-agent.md)

| Pacchetto | versione del pacchetto | Download |
|-----|-----|-----|
| Pacchetto Red Hat RPM | 14.0.800.90-2 | [Pacchetto RPM motore](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.800.90-2.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.800.90-2.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.800.90-2.x86_64.rpm)</br>[Pacchetto RPM di SQL Server Agent](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.800.90-2.x86_64.rpm) | 
| Pacchetto RPM SLES | 14.0.800.90-2 | [pacchetto RPM motore MSSQL server](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.800.90-2.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.800.90-2.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.800.90-2.x86_64.rpm)</br>[Pacchetto RPM di SQL Server Agent](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.800.90-2.x86_64.rpm) | 
| Pacchetto Debian Ubuntu 16.04 | 14.0.800.90-2 | [Pacchetto Debian motore](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.800.90-2_amd64.deb)</br>[Pacchetto Debian a disponibilità elevata](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.800.90-2_amd64.deb)</br>[Pacchetto Debian di ricerca full-text](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.800.90-2_amd64.deb)</br>[Pacchetto Debian di SQL Server Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.800.90-2_amd64.deb) |

### <a name="supported-client-tools"></a>Strumenti client supportati

| Strumento | Versione minima |
|-----|-----|
| [SQL Server Management Studio (SSMS) per Windows](https://go.microsoft.com/fwlink/?linkid=847722) | 17.0 |
| [SQL Server Data Tools per Visual Studio](https://go.microsoft.com/fwlink/?linkid=846626) | 17.0 |
| [Codice di Visual Studio](https://code.visualstudio.com) con il [estensione mssql](https://aka.ms/mssql-marketplace) | Più recente |

### <a name="unsupported-features-and-services"></a>Servizi e funzionalità non supportate
Le funzionalità e i servizi seguenti non sono disponibili su Linux in questo momento. Il supporto di queste funzionalità verrà sempre abilitato durante la cadenza mensile gli aggiornamenti del programma di anteprima.

| Area | Servizio o funzionalità non supportata |
|-----|-----|
| **Motore di database** | Replica transazionale |
| &nbsp; | Replica di tipo merge |
| &nbsp; | Estensione database |
| &nbsp; | Polybase |
| &nbsp; | Query distribuite |
| &nbsp; | (XP_CMDSHELL, e così via). le stored procedure estese di sistema |
| &nbsp; | Tabella filetable |
| &nbsp; | Impostare gli assembly CLR con il EXTERNAL_ACCESS o UNSAFE autorizzazione |
| **SQL Server Agent** |  Sottosistemi: CmdExec, PowerShell, agente di lettura coda, SSIS, SSAS, SSRS |
| &nbsp; | Avvisi |
| &nbsp; | Agente di lettura log |
| &nbsp; | Change Data Capture |
| &nbsp; | Backup gestito |
| **Disponibilità elevata** | Mirroring del database  |
| &nbsp; | Aggiornamento in sequenza del gruppo di disponibilità |
| **Sicurezza** | Extensible Key Management |
| **Servizi** | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>Problemi noti
Nelle sezioni seguenti vengono descritti problemi noti relativi a questa versione di SQL Server 2017 RC1 in Linux.

#### <a name="general"></a>Generale
- La lunghezza del nome host in cui SQL Server è installato deve essere 15 caratteri o meno. 

    - **Risoluzione**: modificare il nome e così via/nome host e un valore 15 caratteri lunghi o meno.

- Impostare manualmente l'ora di sistema con le versioni precedenti nel tempo causerà l'esecuzione SQL Server per interrompere l'aggiornamento dell'ora di sistema interno all'interno di SQL Server.

    - **Risoluzione**: riavviare SQL Server.

- Sono supportate solo le installazioni a istanza singola.

    - **Risoluzione**: se si desidera disporre di più di un'istanza in un determinato host, è consigliabile utilizzare le macchine virtuali o i contenitori di Docker. 

- Gestione configurazione SQL Server non è possibile connettersi a SQL Server in Linux.

- La lingua predefinita di **sa** account di accesso è l'inglese.

    - **Risoluzione**: modificare la lingua del **sa** account di accesso con il **ALTER LOGIN** istruzione.

#### <a name="databases"></a>Database

- Impossibile spostare i database di sistema con l'utilità mssql conf.

- Quando si ripristina un database di cui è stato eseguito il backup in SQL Server in Windows, è necessario utilizzare il **WITH MOVE** clausola nell'istruzione Transact-SQL.

- Le transazioni distribuite che richiedono il servizio Microsoft Distributed Transaction Coordinator non sono supportate in SQL Server in esecuzione in Linux. SQL Server a SQL Server sono supportate le transazioni distribuite.

#### <a name="remote-database-files"></a>File di database remoto

- Hosting dei file di database in un server NFS non è supportata in questa versione. Include l'utilizzo di NFS per disco condiviso clustering di failover e database nelle istanze non cluster. Stiamo lavorando su come abilitare il supporto di server NFS nelle prossime versioni.

#### <a name="cross-platform-availability-groups-and-distributed-availability-groups"></a>Gruppi di disponibilità su più piattaforme e i gruppi di disponibilità distribuiti

- A causa di un problema noto, la creazione di gruppi di disponibilità con repliche in istanze ospitate in Windows e Linux non funziona in questa versione. Sono inclusi i gruppi di disponibilità distribuiti. Per risolvere il problema sarà disponibile nella compilazione prossima versione finale candidata. 

#### <a name="server-collation"></a>Regole di confronto del server

- Quando l'utilizzo di MSSQL_COLLATION override o quando si esegue un'installazione (non in lingua inglese) localizzata, è possibile SQL Server verrà raggiunto un deadlock durante il tentativo di impostare le regole di confronto di server, che genera un dump. L'installazione viene completata, tuttavia le regole di confronto del server verrà non impostato. La soluzione alternativa consiste nell'eseguire. / mssql conf set di regole di confronto e immettere il nome delle regole di confronto desiderato quando viene richiesto (il nome delle regole di confronto, vedere il log degli errori in corrispondenza della riga: "Tentativo di modificare regole di confronto predefinite..."). 
 
#### <a name="localization"></a>Localizzazione

- Se le impostazioni locali sono inglese (it_IT) durante l'installazione, è necessario utilizzare la codifica UTF-8 nella sessione/terminale bash. Se si utilizza la codifica ASCII, si potrebbe essere visualizzato un errore simile al seguente:

   ```
   UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
   ```

   Se non è possibile utilizzare la codifica UTF-8, eseguire l'installazione utilizzando la variabile di ambiente MSSQL_LCID per specificare il linguaggio selezionato.

   ```bash
   sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
   ```

#### <a name = "fci"></a>Aggiornamento dell'istanza del cluster disco condiviso

Nella versione RC1 l'agente di risorse cluster imposta il nome del server virtuale, come avviene in un'istanza del Cluster di Failover in Windows. Prima di RC1 `@@servername` su un disco condiviso cluster ha restituito il nodo specifico nome di questa operazione dopo il failover `@@servername` ha restituito un valore diverso. Nella versione RC1 serverName dell'istanza del cluster disco condiviso viene aggiornato con il nome della risorsa quando la risorsa viene aggiunto al cluster. Per questo motivo, il cluster sarà necessario riavviare SQL Server dopo il failover manuale durante l'aggiornamento, come i passaggi seguenti:

1. Aggiornare innanzitutto nodo secondario (passivo).
   - Eseguire l'aggiornamento **mssql server** pacchetto.
   - Eseguire l'aggiornamento **mssql-server-a disponibilità elevata** pacchetto.
1. Eseguire manualmente il failover al nodo aggiornato.
   `pcs resource move <resourceName>`
   - Risorsa non riesce inizialmente perché l'agente di risorse controlla serverName effettivo e previsto. ServerName previsto saranno diverso.
   - Cluster verrà riavviato la risorsa di SQL Server nello stesso nodo. Verrà aggiornato il nome del server.
1. Aggiornare l'altro nodo. 
   - Eseguire l'aggiornamento **mssql server** pacchetto.
   - Eseguire l'aggiornamento **mssql-server-a disponibilità elevata** pacchetto.
1. Rimuovere il vincolo aggiunto dallo spostamento manuale delle risorse. Vedere [cluster di Failover manualmente](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md#failManual).
2. Se si desidera, esito negativo fino al nodo primario originale. 

#### <a name="availability-group"></a>Gruppo di disponibilità

In Linux, l'aggiornamento di SQL Server 2017 CTP 2.1 in sequenza a RC1 non è supportata. Dopo aver aggiornato la replica secondaria, verrà disconnesso dalla replica primaria fino a quando non viene aggiornata la replica primaria. Microsoft prevede di risolvere il problema per una versione futura.

#### <a name="full-text-search"></a>Ricerca full-text
- Non tutti i filtri sono disponibili in questa versione, inclusi i filtri per i documenti di Office. Per un elenco di filtri supportati, vedere [installare di ricerca Full-Text di SQL Server in Linux](sql-server-linux-setup-full-text-search.md#filters).

#### <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)

- Il **mssql server è** pacchetto non è supportato in SUSE in questa versione. È attualmente supportato in Ubuntu e su Red Hat Enterprise Linux (RHEL).

- Le funzionalità seguenti non sono supportate in questa versione, quando si eseguono i pacchetti SSIS in Linux:
  - Database del catalogo SSIS
  - Esecuzione del pacchetto pianificato dall'agente SQL
  - Autenticazione di Windows
  - Componenti di terze parti
  - Change Data Capture (CDC)
  - Scalabilità orizzontale SSIS
  - Azure Feature Pack per SSIS
  - Supporto di Hadoop e HDFS
  - Microsoft Connector for SAP BW

Per ulteriori informazioni su SSIS in Linux, vedere gli articoli seguenti:
-   [Installare SQL Server Integration Services (SSIS) in Linux](sql-server-linux-setup-ssis.md)
-   [Estrarre, trasformare e caricare i dati in Linux con SSIS](sql-server-linux-migrate-ssis.md)

#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
Le limitazioni seguenti si applicano a SQL Server Management Studio in Windows connessi a SQL Server in Linux.

- I piani di manutenzione non sono supportati.

- Gestione dei Data Warehouse di e l'agente di raccolta dati in SQL Server Management Studio non sono supportati. 

- I componenti SSMS UI con l'autenticazione di Windows o le opzioni del registro eventi di Windows non funzionano con Linux. È comunque possibile utilizzare queste funzionalità con altre opzioni, ad esempio account di accesso SQL. 

- Impossibile modificare il numero di file di log da mantenere.

### <a name="next-steps"></a>Passaggi successivi

Per iniziare, vedere le esercitazioni di avvio rapido seguenti:

- [Installare in Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installare in SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installare in Ubuntu](quickstart-install-connect-ubuntu.md)
- [Eseguire in Docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![Grafico della barra di separazione](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a id="ctp21"></a>CTP 2.1 (maggio 2017)
La versione del motore di SQL Server per questa versione è 14.0.600.250.

### <a name="supported-platforms"></a>Piattaforme supportate 

| Piattaforma | File system | Guida all'installazione |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 Workstation desktop e Server | XFS o EXT4 | [Guida all'installazione](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | EXT4 | [Guida all'installazione](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | EXT4 | [Guida all'installazione](quickstart-install-connect-ubuntu.md) | 
| Motore docker 1.8 + in Windows, Mac o Linux | N/D | [Guida all'installazione](quickstart-install-connect-docker.md) | 

> [!NOTE]
> È necessario almeno 3,25 GB di memoria per l'esecuzione di SQL Server in Linux.
> Motore di SQL Server è stato testato fino a 1 TB di memoria in questo momento.

### <a name="package-details"></a>Dettagli del pacchetto
Nella tabella seguente sono elencati i dettagli del pacchetto e i percorsi di download per i pacchetti RPM e Debian. Sarà necessario scaricare i pacchetti direttamente se si utilizza la procedura nelle guide di installazione seguenti:

- [Installare il pacchetto di SQL Server](sql-server-linux-setup.md)
- [Installare il pacchetto di ricerca Full-text](sql-server-linux-setup-full-text-search.md)
- [Installare il pacchetto di SQL Server Agent](sql-server-linux-setup-sql-agent.md)

| Pacchetto | versione del pacchetto | Download |
|-----|-----|-----|
| Pacchetto Red Hat RPM | 14.0.600.250-2 | [Pacchetto RPM motore](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.600.250-2.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.600.250-2.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.600.250-2.x86_64.rpm)</br>[Pacchetto RPM di SQL Server Agent](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.600.250-2.x86_64.rpm) | 
| Pacchetto RPM SLES | 14.0.600.250-2 | [pacchetto RPM motore MSSQL server](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.600.250-2.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.600.250-2.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.600.250-2.x86_64.rpm)</br>[Pacchetto RPM di SQL Server Agent](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.600.250-2.x86_64.rpm) | 
| Pacchetto Debian Ubuntu 16.04 | 14.0.600.250-2 | [Pacchetto Debian motore](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.600.250-2_amd64.deb)</br>[Pacchetto Debian a disponibilità elevata](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.600.250-2_amd64.deb)</br>[Pacchetto Debian di ricerca full-text](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.600.250-2_amd64.deb)</br>[Pacchetto Debian di SQL Server Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.600.250-2_amd64.deb) |

### <a name="supported-client-tools"></a>Strumenti client supportati

| Strumento | Versione minima |
|-----|-----|
| [SQL Server Management Studio (SSMS) per Windows](https://go.microsoft.com/fwlink/?linkid=847722) | 17.0 |
| [SQL Server Data Tools per Visual Studio](https://go.microsoft.com/fwlink/?linkid=846626) | 17.0 |
| [Codice di Visual Studio](https://code.visualstudio.com) con il [estensione mssql](https://aka.ms/mssql-marketplace) | Versione più recente (1.12) |

### <a name="unsupported-features-and-services"></a>Servizi e funzionalità non supportate
Le funzionalità e i servizi seguenti non sono disponibili su Linux in questo momento. Il supporto di queste funzionalità verrà sempre abilitato durante la cadenza mensile gli aggiornamenti del programma di anteprima.

| Area | Servizio o funzionalità non supportata |
|-----|-----|
| **Motore di database** | Replica |
| &nbsp; | Estensione database |
| &nbsp; | Polybase |
| &nbsp; | Query distribuite |
| &nbsp; | (XP_CMDSHELL, e così via). le stored procedure estese di sistema |
| &nbsp; | Tabella filetable |
| &nbsp; | Impostare gli assembly CLR con il EXTERNAL_ACCESS o UNSAFE autorizzazione |
| **Disponibilità elevata** | Mirroring del database  |
| **Sicurezza** | Autenticazione di Active Directory |
| &nbsp; | Autenticazione di Windows |
| &nbsp; | Extensible Key Management |
| &nbsp; | Utilizzo del certificato fornito dall'utente per SSL o TLS |
| **Servizi** | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>Problemi noti
Nelle sezioni seguenti vengono descritti problemi noti con questa versione di SQL Server 2017 CTP 2.1 su Linux.

#### <a name="general"></a>Generale
- La lunghezza del nome host in cui SQL Server è installato deve essere 15 caratteri o meno. 

    - **Risoluzione**: modificare il nome e così via/nome host e un valore 15 caratteri lunghi o meno.

- Impostare manualmente l'ora di sistema con le versioni precedenti nel tempo causerà l'esecuzione SQL Server per interrompere l'aggiornamento dell'ora di sistema interno all'interno di SQL Server.

    - **Risoluzione**: riavviare SQL Server.

- Sono supportate solo le installazioni a istanza singola.

    - **Risoluzione**: se si desidera disporre di più di un'istanza in un determinato host, è consigliabile utilizzare le macchine virtuali o i contenitori di Docker. 

- Gestione configurazione SQL Server non è possibile connettersi a SQL Server in Linux.

- La lingua predefinita di **sa** account di accesso è l'inglese.

    - **Risoluzione**: modificare la lingua del **sa** account di accesso con il **ALTER LOGIN** istruzione.

#### <a name="databases"></a>Database
- Impossibile spostare i database di sistema con l'utilità mssql conf.

- Quando si ripristina un database di cui è stato eseguito il backup in SQL Server in Windows, è necessario utilizzare il **WITH MOVE** clausola nell'istruzione Transact-SQL.

- Le transazioni distribuite che richiedono il servizio Microsoft Distributed Transaction Coordinator non sono supportate in SQL Server in esecuzione in Linux. SQL Server a SQL Server sono supportate le transazioni distribuite.

#### <a name="always-on-availability-group"></a>Sempre nel gruppo di disponibilità
- `sys.fn_hadr_backup_is_preffered_replica`non funziona per `CLUSTER_TYPE=NONE` o `CLUSTER_TYPE=EXTERNAL` perché si basa sul Registro di sistema del cluster di replicate WSFC chiave che non è disponibile. Stiamo lavorando per fornire una funzionalità simile a una funzione diversa. 

#### <a name="full-text-search"></a>Ricerca full-text
- Non tutti i filtri sono disponibili in questa versione, inclusi i filtri per i documenti di Office. Per un elenco di filtri supportati, vedere [installare di ricerca Full-Text di SQL Server in Linux](sql-server-linux-setup-full-text-search.md#filters).

#### <a name="sql-agent"></a>SQL Agent
- I seguenti componenti e sottosistemi di processi di SQL Agent non sono attualmente supportati in Linux:

    - Sottosistemi: CmdExec, PowerShell, server di distribuzione repliche, Snapshot, Merge, agente di lettura coda, SSIS, SSAS, SSRS
    - Avvisi
    - Posta elettronica database
    - Agente di lettura log 
    - Change Data Capture

#### <a name="sqlpackage"></a>SqlPackage
- Utilizzando SqlPackage, è necessario specificare un percorso assoluto per i file. Utilizzando i percorsi relativi verrà eseguito il mapping di file sotto il "tmp/sqlpackage. \<codice \> /sistema/system32 "cartella. 

  - **Risoluzione**: utilizzare percorsi di file assoluti.

- SqlPackage Mostra il percorso dei file con una "c:\\" prefisso.

#### <a name="ssis"></a> SQL Server Integration Services (SSIS)
È possibile eseguire pacchetti SSIS in Linux. Per altre informazioni, vedere il [post di blog annunciato il supporto SSIS per Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/). Tenere presente i seguenti problemi noti con questa versione.

- Il **mssql server è** pacchetto è supportato solo in Ubuntu in questo momento.

- Le funzionalità seguenti non sono supportate durante l'esecuzione di pacchetti SSIS in Linux:
  - Database del catalogo SSIS
  - Pianificare l'esecuzione di pacchetti da SQL Agent
  - Autenticazione di Windows
  - Componenti di terze parti
  - Driver ODBC di terze parti
  - Gestione connessione ODBC, origine e destinazione (supportato con SSIS in Linux CTP 2.1 aggiornamento)
  - Change Data Capture (CDC)
  - Scalabilità orizzontale
  - Azure Feature Pack
  - Hadoop e HDFS supporto
  - Microsoft Connector for SAP BW

Con SSIS in Linux CTP 2.1 aggiornamento, i pacchetti SSIS possono utilizzare connessioni di ODBC in Linux. Per altre informazioni, vedere il [post del blog annuncia il supporto ODBC in Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
Le limitazioni seguenti si applicano a SQL Server Management Studio in Windows connessi a SQL Server in Linux.

- I piani di manutenzione non sono supportati.

- Gestione dei Data Warehouse di e l'agente di raccolta dati in SQL Server Management Studio non sono supportati. 

- I componenti SSMS UI con l'autenticazione di Windows o le opzioni del registro eventi di Windows non funzionano con Linux. È comunque possibile utilizzare queste funzionalità con altre opzioni, ad esempio account di accesso SQL. 

- Impossibile modificare il numero di file di log da mantenere.

### <a name="next-steps"></a>Passaggi successivi

Per iniziare, vedere le esercitazioni di avvio rapido seguenti:

- [Installare in Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installare in SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installare in Ubuntu](quickstart-install-connect-ubuntu.md)
- [Eseguire in Docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![Grafico della barra di separazione](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a id="ctp20"></a>Nella versione CTP 2.0 (aprile 2017)
La versione del motore di SQL Server per questa versione è 14.0.500.272.

### <a name="supported-platforms"></a>Piattaforme supportate 

| Piattaforma | File system | Guida all'installazione |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 Workstation desktop e Server | XFS o EXT4 | [Guida all'installazione](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | EXT4 | [Guida all'installazione](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS e 16.10 | EXT4 | [Guida all'installazione](quickstart-install-connect-ubuntu.md) | 
| Motore docker 1.8 + in Windows, Mac o Linux | N/D | [Guida all'installazione](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> È necessario almeno 3,25 GB di memoria per l'esecuzione di SQL Server in Linux.
> Motore di SQL Server è stato testato fino a 1 TB di memoria in questo momento.

### <a name="package-details"></a>Dettagli del pacchetto
Nella tabella seguente sono elencati i dettagli del pacchetto e i percorsi di download per i pacchetti RPM e Debian. Si noti che è necessario scaricare i pacchetti direttamente se si utilizza la procedura nelle guide di installazione seguenti:

- [Installare il pacchetto di SQL Server](sql-server-linux-setup.md)
- [Installare il pacchetto di ricerca Full-text](sql-server-linux-setup-full-text-search.md)
- [Installare il pacchetto di SQL Server Agent](sql-server-linux-setup-sql-agent.md)

| Pacchetto | versione del pacchetto | Download |
|-----|-----|-----|
| Pacchetto Red Hat RPM | 14.0.500.272-2 | [Pacchetto RPM motore](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.500.272-2.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.500.272-2.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.500.272-2.x86_64.rpm)</br>[Pacchetto RPM di SQL Server Agent](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.500.272-2.x86_64.rpm) | 
| Pacchetto RPM SLES | 14.0.500.272-2 | [pacchetto RPM motore MSSQL server](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.500.272-2.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.500.272-2.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.500.272-2.x86_64.rpm)</br>[Pacchetto RPM di SQL Server Agent](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.500.272-2.x86_64.rpm) | 
| Pacchetto Debian Ubuntu 16.04 | 14.0.500.272-2 | [Pacchetto Debian motore](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.500.272-2_amd64.deb)</br>[Pacchetto Debian a disponibilità elevata](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.500.272-2_amd64.deb)</br>[Pacchetto Debian di ricerca full-text](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.500.272-2_amd64.deb)</br>[Pacchetto Debian di SQL Server Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.500.272-2_amd64.deb) |
| Pacchetto Debian Ubuntu 16.10 | 14.0.500.272-2 | [Pacchetto Debian motore](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.500.272-2_amd64.deb)</br>[Pacchetto Debian a disponibilità elevata](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.500.272-2_amd64.deb)</br>[Pacchetto Debian di ricerca full-text](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.500.272-2_amd64.deb)</br>[Pacchetto Debian di SQL Server Agent](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.500.272-2_amd64.deb) |

### <a name="supported-client-tools"></a>Strumenti client supportati

| Strumento | Versione minima |
|-----|-----|
| [SQL Server Management Studio (SSMS) per Windows - Release Candidate 2](https://go.microsoft.com/fwlink/?linkid=840957) | 17.0 |
| [SQL Server Data Tools per Visual Studio - versione Release Candidate 2](https://go.microsoft.com/fwlink/?linkid=837939) | 17.0 |
| [Codice di Visual Studio](https://code.visualstudio.com) con il [estensione mssql](https://aka.ms/mssql-marketplace) | Versione più recente (0.2.1) |

> [!NOTE] 
> Le versioni di SQL Server Management Studio e SQL Server Data Tools specificate sopra sono versioni Release Candidate, pertanto non è consigliata per l'utilizzo nell'ambiente di produzione.

### <a name="unsupported-features-and-services"></a>Servizi e funzionalità non supportate
Le funzionalità e i servizi seguenti non sono disponibili su Linux in questo momento. Il supporto di queste funzionalità verrà sempre abilitato durante la cadenza mensile gli aggiornamenti del programma di anteprima.

| Area | Servizio o funzionalità non supportata |
|-----|-----|
| **Motore di database** | Replica |
| &nbsp; | Estensione database |
| &nbsp; | Polybase |
| &nbsp; | Query distribuite |
| &nbsp; | (XP_CMDSHELL, e così via). le stored procedure estese di sistema |
| &nbsp; | Tabella filetable |
| &nbsp; | Impostare gli assembly CLR con il EXTERNAL_ACCESS o UNSAFE autorizzazione |
| **Disponibilità elevata** | Mirroring del database  |
| **Sicurezza** | Autenticazione di Active Directory |
| &nbsp; | Autenticazione di Windows |
| &nbsp; | Extensible Key Management |
| &nbsp; | Utilizzo del certificato fornito dall'utente per SSL o TLS |
| **Servizi** | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Integration Services | 
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>Problemi noti
Nelle sezioni seguenti vengono descritti problemi noti con questa versione di SQL Server 2017 CTP 2.0 su Linux.

#### <a name="general"></a>Generale
- La lunghezza del nome host in cui SQL Server è installato deve essere 15 caratteri o meno. 

    - **Risoluzione**: modificare il nome e così via/nome host e un valore 15 caratteri lunghi o meno.

- Impostare manualmente l'ora di sistema con le versioni precedenti nel tempo causerà l'esecuzione SQL Server per interrompere l'aggiornamento dell'ora di sistema interno all'interno di SQL Server.

    - **Risoluzione**: riavviare SQL Server.

- Sono supportate solo le installazioni a istanza singola.

    - **Risoluzione**: se si desidera disporre di più di un'istanza in un determinato host, è consigliabile utilizzare le macchine virtuali o i contenitori di Docker. 

- Gestione configurazione SQL Server non è possibile connettersi a SQL Server in Linux.

- La lingua predefinita di **sa** account di accesso è l'inglese.

    - **Risoluzione**: modificare la lingua del **sa** account di accesso con il **ALTER LOGIN** istruzione.

#### <a name="databases"></a>Database
- Impossibile spostare i database di sistema con l'utilità mssql conf.

- Quando si ripristina un database di cui è stato eseguito il backup in SQL Server in Windows, è necessario utilizzare il **WITH MOVE** clausola nell'istruzione Transact-SQL.

- Le transazioni distribuite che richiedono il servizio Microsoft Distributed Transaction Coordinator non sono supportate in SQL Server in esecuzione in Linux. SQL Server a SQL Server sono supportate le transazioni distribuite.

#### <a name="always-on-availability-group"></a>Sempre nel gruppo di disponibilità
- Tutte le configurazioni a disponibilità elevata, vale a dire il gruppo di disponibilità viene aggiunto come risorsa a un cluster Pacemaker - creato con i pacchetti pre CTP 2.0 non sono compatibili con il nuovo pacchetto. Eliminare tutte le risorse in cluster configurate in precedenza e creare nuovi gruppi di disponibilità con `CLUSTER_TYPE=EXTERNAL`. Vedere [configurare il gruppo di disponibilità AlwaysOn per SQL Server in Linux](sql-server-linux-availability-group-configure-ha.md).
- Gruppi di disponibilità creati con `CLUSTER_TYPE=NONE` e non aggiunti come risorse nel cluster continueranno a funzionare dopo l'aggiornamento. Utilizzo per gli scenari di scalabilità di lettura. Vedere [gruppo di disponibilità in lettura a livello di Configura per SQL Server in Linux](sql-server-linux-availability-group-configure-rs.md).
- `sys.fn_hadr_backup_is_preffered_replica`non funziona per `CLUSTER_TYPE=NONE` o `CLUSTER_TYPE=EXTERNAL` perché si basa sul Registro di sistema del cluster di replicate WSFC chiave che non è disponibile. Stiamo lavorando per fornire una funzionalità simile a una funzione diversa. 

#### <a name="full-text-search"></a>Ricerca full-text
- Non tutti i filtri sono disponibili in questa versione, inclusi i filtri per i documenti di Office. Per un elenco di filtri supportati, vedere [installare di ricerca Full-Text di SQL Server in Linux](sql-server-linux-setup-full-text-search.md#filters).

- Coreano word breaker richiede alcuni secondi per caricare e genera un errore al primo utilizzo. Dopo l'errore iniziale, dovrebbe funzionare normalmente.

#### <a name="sql-agent"></a>SQL Agent
- I seguenti componenti e sottosistemi di processi di SQL Agent non sono attualmente supportati in Linux:

    - Sottosistemi: CmdExec, PowerShell, server di distribuzione repliche, Snapshot, Merge, agente di lettura coda, SSIS, SSAS, SSRS
    - Avvisi
    - Posta elettronica database
    - Agente di lettura log 
    - Change Data Capture

#### <a name="sqlpackage"></a>SqlPackage
- Utilizzando SqlPackage, è necessario specificare un percorso assoluto per i file. Utilizzando i percorsi relativi verrà eseguito il mapping di file sotto il "tmp/sqlpackage. \<codice \> /sistema/system32 "cartella. 

    - **Risoluzione**: utilizzare percorsi di file assoluti.

- SqlPackage Mostra il percorso dei file con una "c:\\" prefisso.

    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
Le limitazioni seguenti si applicano a SQL Server Management Studio in Windows connessi a SQL Server in Linux.

- I piani di manutenzione non sono supportati.

- Gestione dei Data Warehouse di e l'agente di raccolta dati in SQL Server Management Studio non sono supportati. 

- I componenti SSMS UI con l'autenticazione di Windows o le opzioni del registro eventi di Windows non funzionano con Linux. È comunque possibile utilizzare queste funzionalità con altre opzioni, ad esempio account di accesso SQL. 

- Impossibile modificare il numero di file di log da mantenere.

### <a name="next-steps"></a>Passaggi successivi

Per iniziare, vedere le esercitazioni di avvio rapido seguenti:

- [Installare in Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installare in SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installare in Ubuntu](quickstart-install-connect-ubuntu.md)
- [Eseguire in Docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![Grafico della barra di separazione](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a id="ctp14"></a>CTP 1.4 (marzo 2017)
La versione del motore di SQL Server per questa versione è 14.0.405.198.

### <a name="supported-platforms"></a>Piattaforme supportate 

| Piattaforma | File system | Guida all'installazione |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 Workstation desktop e Server | XFS o EXT4 | [Guida all'installazione](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | EXT4 | [Guida all'installazione](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS e 16.10 | EXT4 | [Guida all'installazione](quickstart-install-connect-ubuntu.md) | 
| Motore docker 1.8 + in Windows, Mac o Linux | N/D | [Guida all'installazione](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> È necessario almeno 3,25 GB di memoria per l'esecuzione di SQL Server in Linux.
> Motore di SQL Server è stato testato fino a 1 TB di memoria in questo momento.

### <a name="package-details"></a>Dettagli del pacchetto
Nella tabella seguente sono elencati i dettagli del pacchetto e i percorsi di download per i pacchetti RPM e Debian. Si noti che è necessario scaricare i pacchetti direttamente se si utilizza la procedura in seguito le guide di installazione
-   [Installare il pacchetto di SQL Server](sql-server-linux-setup.md)
-   [Installare il pacchetto di ricerca Full-text](sql-server-linux-setup-full-text-search.md)
-   [Installare il pacchetto di SQL Server Agent](sql-server-linux-setup-sql-agent.md)

| Pacchetto | versione del pacchetto | Download |
|-----|-----|-----|
| Pacchetto Red Hat RPM | 14.0.405.200-1 | [Pacchetto RPM motore](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.405.200-1.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.405.200-1.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.405.200-1.x86_64.rpm)</br>[Pacchetto RPM di SQL Server Agent](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.405.200-1.x86_64.rpm) | 
| Pacchetto RPM SLES | 14.0.405.200-1 | [pacchetto RPM motore MSSQL server](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.405.200-1.x86_64.rpm)</br>[Pacchetto RPM disponibilità elevata](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.405.200-1.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.405.200-1.x86_64.rpm)</br>[Pacchetto RPM di SQL Server Agent](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.405.200-1.x86_64.rpm) | 
| Pacchetto Debian Ubuntu 16.04 | 14.0.405.200-1 | [Pacchetto Debian motore](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.405.200-1_amd64.deb)</br>[Pacchetto Debian a disponibilità elevata](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.405.200-1_amd64.deb)</br>[Pacchetto Debian di ricerca full-text](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.405.200-1_amd64.deb)</br>[Pacchetto Debian di SQL Server Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.405.200-1_amd64.deb) |
| Pacchetto Debian Ubuntu 16.10 | 14.0.405.200-1 | [Pacchetto Debian motore](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.405.200-1_amd64.deb)</br>[Pacchetto Debian a disponibilità elevata](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.405.200-1_amd64.deb)</br>[Pacchetto Debian di ricerca full-text](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.405.200-1_amd64.deb)</br>[Pacchetto Debian di SQL Server Agent](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.405.200-1_amd64.deb) |

### <a name="supported-client-tools"></a>Strumenti client supportati

| Strumento | Versione minima |
|-----|-----|
| [SQL Server Management Studio (SSMS) per Windows - Release Candidate 2](https://go.microsoft.com/fwlink/?linkid=840957) | 17.0 |
| [SQL Server Data Tools per Visual Studio - versione Release Candidate 2](https://go.microsoft.com/fwlink/?linkid=837939) | 17.0 |
| [Codice di Visual Studio](https://code.visualstudio.com) con il [estensione mssql](https://aka.ms/mssql-marketplace) | Versione più recente (0.2.1) |

> [!NOTE] 
> Le versioni di SQL Server Management Studio e SQL Server Data Tools specificate sopra sono versioni Release Candidate, pertanto non è consigliata per l'utilizzo nell'ambiente di produzione.

### <a name="unsupported-features-and-services"></a>Servizi e funzionalità non supportate
Le funzionalità e i servizi seguenti non sono disponibili su Linux in questo momento. Il supporto di queste funzionalità verrà sempre abilitato durante la cadenza mensile gli aggiornamenti del programma di anteprima.

| Area | Servizio o funzionalità non supportata |
|-----|-----|
| **Motore di database** | Replica |
| &nbsp; | Estensione database |
| &nbsp; | Polybase |
| &nbsp; | Query distribuite |
| &nbsp; | (XP_CMDSHELL, e così via). le stored procedure estese di sistema |
| &nbsp; | Tabella filetable |
| &nbsp; | Impostare gli assembly CLR con il EXTERNAL_ACCESS o UNSAFE autorizzazione |
| **Disponibilità elevata** | Mirroring del database  |
| **Sicurezza** | Autenticazione di Active Directory |
| &nbsp; | Autenticazione di Windows |
| &nbsp; | Extensible Key Management |
| &nbsp; | Utilizzo del certificato fornito dall'utente per SSL o TLS |
| **Servizi** | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Integration Services | 
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>Problemi noti
Nelle sezioni seguenti vengono descritti problemi noti con questa versione di SQL Server 2017 CTP 1.4 in Linux.

#### <a name="general"></a>Generale
- La lunghezza del nome host in cui SQL Server è installato deve essere 15 caratteri o meno. 

    - **Risoluzione**: modificare il nome e così via/nome host e un valore 15 caratteri lunghi o meno.

- Impossibile eseguire il comando `ALTER SERVICE MASTER KEY REGENERATE`. È presente un bug noto che determinerà il SQL Server potrebbe diventare instabile. Se è necessario rigenerare la chiave Master del servizio, è necessario eseguire il backup dei file di database, disinstallare e reinstallare SQL Server e quindi ripristinare nuovamente i file di database.

- Impostare manualmente l'ora di sistema con le versioni precedenti nel tempo causerà l'esecuzione SQL Server per interrompere l'aggiornamento dell'ora di sistema interno all'interno di SQL Server.

    - **Risoluzione**: riavviare SQL Server.

- Non eseguire il mapping di alcuni nomi di fuso orario in Linux esattamente ai nomi di fuso orario di Windows.

    - **Risoluzione**: utilizzare nomi di fuso orario nella colonna TZID il ' Mapping per: tabella sezione Windows il [pagina della documentazione www.Unicode.org](http://www.unicode.org/cldr/charts/latest/supplemental/zone_tzid.html).

- Motore di SQL Server prevede che le righe nei file di testo per essere terminato con CR-LF (stile Windows formattazione riga).

- Sono supportate solo le installazioni a istanza singola.

    - **Risoluzione**: se si desidera disporre di più di un'istanza in un determinato host, è consigliabile utilizzare le macchine virtuali o i contenitori di Docker. 

- Tutti i file di log e i log degli errori vengono codificati in UTF-16.

- Gestione configurazione SQL Server non è possibile connettersi a SQL Server in Linux.

- **CREATE ASSEMBLY** non funzionerà durante il tentativo di utilizzare un file. Utilizzare il **FROM \<bit\>**  metodo invece per il momento. 

#### <a name="databases"></a>Database
- Impossibile spostare i database di sistema con l'utilità mssql conf.

- Quando si ripristina un database di cui è stato eseguito il backup in SQL Server in Windows, è necessario utilizzare il **WITH MOVE** clausola nell'istruzione Transact-SQL.

- Le transazioni distribuite che richiedono il servizio Microsoft Distributed Transaction Coordinator non sono supportate in SQL Server in esecuzione in Linux. SQL Server a SQL Server sono supportate le transazioni distribuite.

#### <a name="always-on-availability-group"></a>Sempre nel gruppo di disponibilità
- Gruppo di disponibilità AlwaysOn le risorse del cluster in Linux che sono state create con CTP 1.3 avrà esito negativo dopo l'aggiornamento a disponibilità elevata pacchetto (mssql-server-a disponibilità elevata). 

   - **Risoluzione**: prima di aggiornare il pacchetto a disponibilità elevata, impostare il parametro di risorse cluster `notify=true`. 
   
      - Nell'esempio seguente imposta il parametro di risorse cluster su una risorsa denominata **ag1** su RHEL o Ubuntu: 

      ```bash
      sudo pcs resource update ag1-master notify=true
      ```

      - Per SLES, aggiornamento configurazione risorsa gruppo di disponibilità per aggiungere `notify=true`.  

      ```bash
      crm configure edit ms-ag_cluster 
      ```

      Aggiungere `notify=true` e salvare la configurazione di risorsa.

- Gruppi di disponibilità AlwaysOn in Linux può essere soggetta a perdite di dati se le repliche sono in modalità con commit sincrono. Vedere i dettagli come appropriato per la distribuzione di Linux. 

   - [RHEL](sql-server-linux-availability-group-cluster-rhel.md)
   - [SLES](sql-server-linux-availability-group-cluster-sles.md)
   - [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)

#### <a name="full-text-search"></a>Ricerca full-text
- Non tutti i filtri sono disponibili in questa versione, inclusi i filtri per i documenti di Office. Per un elenco di filtri supportati, vedere [installare di ricerca Full-Text di SQL Server in Linux](sql-server-linux-setup-full-text-search.md#filters).

- Coreano word breaker richiede alcuni secondi per caricare e genera un errore al primo utilizzo. Dopo l'errore iniziale, dovrebbe funzionare normalmente.

#### <a name="sql-agent"></a>SQL Agent
- I seguenti componenti e sottosistemi di processi di SQL Agent non sono attualmente supportati in Linux:
    - Sottosistemi: CmdExec, PowerShell, server di distribuzione repliche, Snapshot, Merge, agente di lettura coda, SSIS, SSAS, SSRS
    - Avvisi
    - Posta elettronica database
    - Log shipping
    - Agente di lettura log 
    - Change Data Capture

#### <a name="in-memory-oltp"></a>OLTP in memoria
- Database OLTP in memoria possono essere creati solo nella directory /var/opt/mssql. Per ulteriori informazioni, visitare il [argomento OLTP In memoria](sql-server-linux-performance-get-started.md#use-in-memory-oltp).  

#### <a name="sqlpackage"></a>SqlPackage
- Utilizzando SqlPackage, è necessario specificare un percorso assoluto per i file. Utilizzando i percorsi relativi verrà eseguito il mapping di file sotto il "tmp/sqlpackage. \<codice \> /sistema/system32 "cartella. 

    - **Risoluzione**: utilizzare percorsi di file assoluti.

- SqlPackage Mostra il percorso dei file con una "c:\\" prefisso.

    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
Le limitazioni seguenti si applicano a SQL Server Management Studio in Windows connessi a SQL Server in Linux.

- I piani di manutenzione non sono supportati.

- Gestione dei Data Warehouse di e l'agente di raccolta dati in SQL Server Management Studio non è supportata. 

- I componenti SSMS UI con l'autenticazione di Windows o le opzioni del registro eventi di Windows non funzionano con Linux. È comunque possibile utilizzare queste funzionalità con altre opzioni, ad esempio account di accesso SQL. 

- Il Visualizzatore di file è limitata al "c:\\" ambito, che viene risolta var/rifiutare mssql/in Linux. Per utilizzare altri percorsi, generare script dell'operazione di interfaccia utente e sostituire l'unità c:\\ percorsi con percorsi di Linux. Quindi eseguire manualmente lo script in SSMS.

- Impossibile modificare il numero di file di log da mantenere.

### <a name="next-steps"></a>Passaggi successivi

Per iniziare, vedere le esercitazioni di avvio rapido seguenti:

- [Installare in Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installare in SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installare in Ubuntu](quickstart-install-connect-ubuntu.md)
- [Eseguire in Docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![Grafico della barra di separazione](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a id="ctp13"></a>CTP 1.3 (febbraio 2017)
La versione del motore di SQL Server per questa versione è 14.0.304.138.

### <a name="supported-platforms"></a>Piattaforme supportate 

| Piattaforma | File system | Guida all'installazione |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 Workstation desktop e Server | XFS o EXT4 | [Guida all'installazione](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | EXT4 | [Guida all'installazione](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS e 16.10 | EXT4 | [Guida all'installazione](quickstart-install-connect-ubuntu.md) | 
| Motore docker 1.8 + in Windows, Mac o Linux | N/D | [Guida all'installazione](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> È necessario almeno 3,25 GB di memoria per l'esecuzione di SQL Server in Linux.
> Motore di SQL Server è stato testato fino a 1 TB di memoria in questo momento.

### <a name="package-details"></a>Dettagli del pacchetto
Nella tabella seguente sono elencati i dettagli del pacchetto e i percorsi di download per i pacchetti RPM e Debian. Si noti che è necessario scaricare tali pacchetti direttamente se si utilizza la procedura descritta nel [Guide all'installazione](sql-server-linux-setup.md).

| Pacchetto | versione del pacchetto | Download |
|-----|-----|-----|
| Pacchetto Red Hat RPM | 14.0.304.138-1 | [pacchetto RPM motore MSSQL server](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.304.138-1.x86_64.rpm)</br>[pacchetto di elevata disponibilità RPM MSSQL-server-a disponibilità elevata](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.304.138-1.x86_64.rpm)</br>[pacchetto RPM di ricerca Full-text MSSQL-server-ft](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.304.138-1.x86_64.rpm) | 
| Pacchetto RPM SLES | 14.0.304.138-1 | [pacchetto RPM motore MSSQL server](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.304.138-1.x86_64.rpm)</br>[pacchetto di elevata disponibilità RPM MSSQL-server-a disponibilità elevata](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.304.138-1.x86_64.rpm)</br>[pacchetto RPM di ricerca Full-text MSSQL-server-ft](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.304.138-1.x86_64.rpm) | 
| Pacchetto Debian Ubuntu 16.04 | 14.0.304.138-1 | [MSSQL server motore Debian di pacchetto](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.304.138-1_amd64.deb)</br>[MSSQL-server-a disponibilità elevata elevata disponibilità Debian pacchetto](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.304.138-1_amd64.deb)</br>[MSSQL-server-fts pacchetto Debian di ricerca Full-text](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.304.138-1_amd64.deb) |
| Pacchetto Debian Ubuntu 16.10 | 14.0.304.138-1 | [MSSQL server motore Debian di pacchetto](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.304.138-1_amd64.deb)</br>[MSSQL-server-a disponibilità elevata elevata disponibilità Debian pacchetto](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.304.138-1_amd64.deb)</br>[MSSQL-server-fts pacchetto Debian di ricerca Full-text](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.304.138-1_amd64.deb) |

### <a name="supported-client-tools"></a>Strumenti client supportati

| Strumento | Versione minima |
|-----|-----|
| [SQL Server Management Studio (SSMS) per Windows - Release Candidate 2](https://go.microsoft.com/fwlink/?linkid=840957) | 17.0 |
| [SQL Server Data Tools per Visual Studio - versione Release Candidate 2](https://go.microsoft.com/fwlink/?linkid=837939) | 17.0 |
| [Codice di Visual Studio](https://code.visualstudio.com) con il [estensione mssql](https://aka.ms/mssql-marketplace) | Versione più recente (0.2.1) |

> [!NOTE] 
> Le versioni di SQL Server Management Studio e SQL Server Data Tools specificate sopra sono versioni Release Candidate, pertanto non è consigliata per l'utilizzo nell'ambiente di produzione.

### <a name="unsupported-features-and-services"></a>Servizi e funzionalità non supportate
Le funzionalità e i servizi seguenti non sono disponibili su Linux in questo momento. Il supporto di queste funzionalità verrà sempre abilitato durante la cadenza mensile gli aggiornamenti del programma di anteprima.

| Area | Servizio o funzionalità non supportata |
|-----|-----|
| **Motore di database** | Replica |
| &nbsp; | Estensione database |
| &nbsp; | Polybase |
| &nbsp; | Query distribuite |
| &nbsp; | (XP_CMDSHELL, e così via). le stored procedure estese di sistema |
| &nbsp; | Tabella filetable |
| &nbsp; | Impostare gli assembly CLR con il EXTERNAL_ACCESS o UNSAFE autorizzazione |
| **Disponibilità elevata** | Mirroring del database  |
| **Sicurezza** | Autenticazione di Active Directory |
| &nbsp; | Autenticazione di Windows |
| &nbsp; | Extensible Key Management |
| &nbsp; | Utilizzo del certificato fornito dall'utente per SSL o TLS |
| **Servizi** | SQL Server Agent |
| &nbsp; | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Integration Services | 
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>Problemi noti
Nelle sezioni seguenti vengono descritti problemi noti con questa versione di SQL Server 2017 CTP 1.3 su Linux.

#### <a name="general"></a>Generale
- La lunghezza del nome host in cui SQL Server è installato deve essere 15 caratteri o meno. 

    - **Risoluzione**: modificare il nome e così via/nome host e un valore 15 caratteri lunghi o meno.

- Impossibile eseguire il comando `ALTER SERVICE MASTER KEY REGENERATE`. È presente un bug noto che determinerà il SQL Server potrebbe diventare instabile. Se è necessario rigenerare la chiave Master del servizio, è necessario eseguire il backup dei file di database, disinstallare e reinstallare SQL Server e quindi ripristinare nuovamente i file di database.

- Impostare manualmente l'ora di sistema con le versioni precedenti nel tempo causerà l'esecuzione SQL Server per interrompere l'aggiornamento dell'ora di sistema interno all'interno di SQL Server.

    - **Risoluzione**: riavviare SQL Server.

- Non eseguire il mapping di alcuni nomi di fuso orario in Linux esattamente ai nomi di fuso orario di Windows.

    - **Risoluzione**: utilizzare nomi di fuso orario nella colonna TZID il ' Mapping per: tabella sezione Windows il [pagina della documentazione www.Unicode.org](http://www.unicode.org/cldr/charts/latest/supplemental/zone_tzid.html).

- Motore di SQL Server prevede che le righe nei file di testo per essere terminato con CR-LF (stile Windows formattazione riga).

- Sono supportate solo le installazioni a istanza singola.

    - **Risoluzione**: se si desidera disporre di più di un'istanza in un determinato host, è consigliabile utilizzare le macchine virtuali o i contenitori di Docker. 

- Tutti i file di log e i log degli errori vengono codificati in UTF-16.

- Gestione configurazione SQL Server non è possibile connettersi a SQL Server in Linux.

- **CREATE ASSEMBLY** non funzionerà durante il tentativo di utilizzare un file. Utilizzare il **FROM \<bit\>**  metodo invece per il momento. 

#### <a name="databases"></a>Database
- Non è possibile modificare i percorsi dei file di dati e di log TempDB.

- Impossibile spostare i database di sistema con l'utilità mssql conf.

- Quando si ripristina un database di cui è stato eseguito il backup in SQL Server in Windows, è necessario utilizzare il **WITH MOVE** clausola nell'istruzione Transact-SQL.

- Le transazioni distribuite che richiedono il servizio Microsoft Distributed Transaction Coordinator non sono supportate in SQL Server in esecuzione in Linux. SQL Server a SQL Server sono supportate le transazioni distribuite.

- Gruppi di disponibilità AlwaysOn in Linux può essere soggetta a perdite di dati se le repliche sono in modalità con commit sincrono. Vedere 
 
   - [RHEL](sql-server-linux-availability-group-cluster-rhel.md)
   - [SLES](sql-server-linux-availability-group-cluster-sles.md)
   - [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)

   
#### <a name="full-text-search"></a>Ricerca full-text
- Non tutti i filtri sono disponibili in questa versione, inclusi i filtri per i documenti di Office. Per un elenco di filtri supportati, vedere [installare di ricerca Full-Text di SQL Server in Linux](sql-server-linux-setup-full-text-search.md#filters).

- Coreano word breaker richiede alcuni secondi per caricare e genera un errore al primo utilizzo. Dopo l'errore iniziale, dovrebbe funzionare normalmente.

#### <a name="in-memory-oltp"></a>OLTP in memoria
- Database OLTP in memoria possono essere creati solo nella directory /var/opt/mssql. Per ulteriori informazioni, visitare il [argomento OLTP In memoria](sql-server-linux-performance-get-started.md#use-in-memory-oltp).  

#### <a name="sqlpackage"></a>SqlPackage
- Utilizzando SqlPackage, è necessario specificare un percorso assoluto per i file. Utilizzando i percorsi relativi verrà eseguito il mapping di file nel "/tmp/sqlpackage./ <code/> /sistema/system32" cartella. 

    - **Risoluzione**: utilizzare percorsi di file assoluti.

- SqlPackage Mostra il percorso dei file con una "c:\\" prefisso.

#### <a name="sqlcmdbcp--odbc"></a>SQLCMD/BCP & ODBC 
- Strumenti di riga di comando di SQL Server (mssql-tools) e il Driver ODBC (ha) dipende da una gestione Driver unixODBC personalizzato. In questo modo è in conflitto se si dispone di una gestione Driver unixODBC installate in precedenza. 

    - **Risoluzione**: in Ubuntu, il conflitto verrà risolto automaticamente. Quando viene richiesto se si desidera disinstallare Gestione Driver unixODBC esistente, digitare "y" e procedere con l'installazione. In Red Hat, sarà necessario rimuovere manualmente Gestione Driver unixODBC esistente utilizzando `yum remove unixODBC`. Si sta lavorando a risolvere questa limitazione per RHEL e SUSE e deve disporre di un aggiornamento per la prima.  
    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
Le limitazioni seguenti si applicano a SQL Server Management Studio in Windows connessi a SQL Server in Linux.

- I piani di manutenzione non sono supportati.

- Gestione dei Data Warehouse di e l'agente di raccolta dati in SQL Server Management Studio non è supportata. 

- I componenti SSMS UI con l'autenticazione di Windows o le opzioni del registro eventi di Windows non funzionano con Linux. È comunque possibile utilizzare queste funzionalità con altre opzioni, ad esempio account di accesso SQL. 

- SQL Server Agent non è ancora supportata. Pertanto, la funzionalità di SQL Server Agent in SQL Server Management Studio non funziona in Linux al momento.

- Il Visualizzatore di file è limitata al "c:\\" ambito, che viene risolta var/rifiutare mssql/in Linux. Per utilizzare altri percorsi, generare script dell'operazione di interfaccia utente e sostituire l'unità c:\\ percorsi con percorsi di Linux. Quindi eseguire manualmente lo script in SSMS.

- Impossibile modificare il numero di file di log da mantenere.

### <a name="next-steps"></a>Passaggi successivi

Per iniziare, vedere le esercitazioni di avvio rapido seguenti:

- [Installare in Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installare in SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installare in Ubuntu](quickstart-install-connect-ubuntu.md)
- [Eseguire in Docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![Grafico della barra di separazione](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a name="a-idctp12-ctp-12-january-2017"></a><a id="ctp12">CTP 1.2 (gennaio January 2017)
La versione del motore di SQL Server per questa versione è 14.0.200.24.

### <a name="supported-platforms"></a>Piattaforme supportate 

| Piattaforma | File system | Guida all'installazione |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 Workstation desktop e Server | XFS o EXT4 | [Guida all'installazione](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | EXT4 | [Guida all'installazione](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS e 16.10 | EXT4 | [Guida all'installazione](quickstart-install-connect-ubuntu.md) | 
| Motore docker 1.8 + in Windows, Mac o Linux | N/D | [Guida all'installazione](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> È necessario almeno 3,25 GB di memoria per l'esecuzione di SQL Server in Linux.
> Motore di SQL Server è stata testata fino a 256GB di memoria in questo momento.

### <a name="package-details"></a>Dettagli del pacchetto
Nella tabella seguente sono elencati i dettagli del pacchetto e i percorsi di download per i pacchetti RPM e Debian. Si noti che è necessario scaricare tali pacchetti direttamente se si utilizza la procedura descritta nel [Guide all'installazione](sql-server-linux-setup.md).

| Pacchetto | versione del pacchetto | Download |
|-----|-----|-----|
| Pacchetto RPM | 14.0.200.24-2 | [pacchetto di motore RPM 14.0.200.24-2 MSSQL server](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.200.24-2.x86_64.rpm)</br>[pacchetto di elevata disponibilità RPM 14.0.200.24-2 MSSQL server](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.200.24-2.x86_64.rpm) | 
| Pacchetto Debian | 14.0.200.24-2 | [MSSQL server 14.0.200.24-2 motore Debian pacchetto](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.200.24-2_amd64.deb) |

### <a name="supported-client-tools"></a>Strumenti client supportati

| Strumento | Versione minima |
|-----|-----|
| [SQL Server Management Studio (SSMS) per Windows - versione finale candidata 1](https://go.microsoft.com/fwlink/?LinkID=835608) | 17.0 |
| [SQL Server Data Tools per Visual Studio - versione finale candidata 1](https://go.microsoft.com/fwlink/?LinkID=835150) | 17.0 |
| [Codice di Visual Studio](https://code.visualstudio.com) con il [estensione mssql](https://aka.ms/mssql-marketplace) | Versione più recente (0,2) |

> [!NOTE] 
> Le versioni di SQL Server Management Studio e SQL Server Data Tools specificate sopra sono versioni Release Candidate, pertanto non è consigliata per l'utilizzo nell'ambiente di produzione.

### <a name="unsupported-features-and-services"></a>Servizi e funzionalità non supportate
Le funzionalità e i servizi seguenti non sono disponibili su Linux in questo momento. Il supporto di queste funzionalità verrà sempre abilitato durante la cadenza mensile gli aggiornamenti del programma di anteprima.

| Area | Servizio o funzionalità non supportata |
|-----|-----|
| **Motore di database** | Ricerca full-text |
| &nbsp; | Replica |
| &nbsp; | Estensione database |
| &nbsp; | Polybase |
| &nbsp; | Query distribuite |
| &nbsp; | (XP_CMDSHELL, e così via). le stored procedure estese di sistema |
| &nbsp; | Tabella filetable |
| &nbsp; | Impostare gli assembly CLR con il EXTERNAL_ACCESS o UNSAFE autorizzazione |
| **Disponibilità elevata** | Gruppi di disponibilità AlwaysOn |
| &nbsp; | Mirroring del database  |
| **Sicurezza** | Autenticazione di Active Directory |
| &nbsp; | Autenticazione di Windows |
| &nbsp; | Extensible Key Management |
| &nbsp; | Utilizzo del certificato fornito dall'utente per SSL o TLS |
| **Servizi** | SQL Server Agent |
| &nbsp; | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Integration Services | 
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>Problemi noti
Nelle sezioni seguenti vengono descritti problemi noti con questa versione di SQL Server 2017 CTP 1.2 in Linux.

#### <a name="general"></a>Generale
- La lunghezza del nome host in cui SQL Server è installato deve essere 15 caratteri o meno. 

    - **Risoluzione**: modificare il nome e così via/nome host e un valore 15 caratteri lunghi o meno.

- Impossibile eseguire il comando `ALTER SERVICE MASTER KEY REGENERATE`. È presente un bug noto che determinerà il SQL Server potrebbe diventare instabile. Se è necessario rigenerare la chiave Master del servizio, è necessario eseguire il backup dei file di database, disinstallare e reinstallare SQL Server e quindi ripristinare nuovamente i file di database.

- Nome della risorsa per la risorsa di SQL modificata da ocf:sql:fci a ocf:mssql:fci. Ulteriori informazioni sulla configurazione di un cluster di failover di un disco condiviso è possibile trovare [qui](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-shared-disk-cluster-red-hat-7-configure).

- Impostare manualmente l'ora di sistema con le versioni precedenti nel tempo causerà l'esecuzione SQL Server per interrompere l'aggiornamento dell'ora di sistema interno all'interno di SQL Server.

    - **Risoluzione**: riavviare SQL Server.

- Non eseguire il mapping di alcuni nomi di fuso orario in Linux esattamente ai nomi di fuso orario di Windows.

    - **Risoluzione**: utilizzare nomi di fuso orario nella colonna TZID il ' Mapping per: tabella sezione Windows il [pagina della documentazione www.Unicode.org](http://www.unicode.org/cldr/charts/latest/supplemental/zone_tzid.html).

- Motore di SQL Server prevede che le righe nei file di testo per essere terminato con CR-LF (stile Windows formattazione riga).

- Sono supportate solo le installazioni a istanza singola.

    - **Risoluzione**: se si desidera disporre di più di un'istanza in un determinato host, è consigliabile utilizzare le macchine virtuali o i contenitori di Docker. 

- Tutti i file di log e i log degli errori vengono codificati in UTF-16.

- Gestione configurazione SQL Server non è possibile connettersi a SQL Server in Linux.

- **CREATE ASSEMBLY** non funzionerà durante il tentativo di utilizzare un file. Utilizzare il **FROM \<bit\>**  metodo invece per il momento. 

#### <a name="databases"></a>Database
- Non è possibile modificare i percorsi dei file di dati e di log TempDB.

- Impossibile spostare i database di sistema con l'utilità mssql conf.

- Quando si ripristina un database di cui è stato eseguito il backup in SQL Server in Windows, è necessario utilizzare il **WITH MOVE** clausola nell'istruzione Transact-SQL.

- Le transazioni distribuite che richiedono il servizio Microsoft Distributed Transaction Coordinator non sono supportate in SQL Server in esecuzione in Linux. SQL Server a SQL Server sono supportate le transazioni distribuite.

#### <a name="in-memory-oltp"></a>OLTP in memoria
- Database OLTP in memoria possono essere creati solo nella directory /var/opt/mssql. Questi database è anche necessario che la "c:\\" notazione quando si fa riferimento. Per ulteriori informazioni, visitare il [argomento OLTP In memoria](sql-server-linux-performance-get-started.md#use-in-memory-oltp).  

#### <a name="sqlpackage"></a>SqlPackage
- Utilizzando SqlPackage, è necessario specificare un percorso assoluto per i file. Utilizzando i percorsi relativi verrà eseguito il mapping di file sotto il "tmp/sqlpackage. \<codice \> /sistema/system32 "cartella. 

    - **Risoluzione**: utilizzare percorsi di file assoluti.

- SqlPackage Mostra il percorso dei file con una "c:\\" prefisso.

#### <a name="sqlcmdbcp--odbc"></a>SQLCMD/BCP & ODBC 
- Se si dispone di una versione precedente di strumenti della riga di comando di SQL Server (mssql strumenti) e il Driver ODBC (ha), si potrebbe essere installato un unixODBC personalizzata di gestione Driver (unixODBC-utf16). Ciò potrebbe causare un potenziale conflitto come non utilizziamo non più di un gestore personalizzato del driver. 

    - **Risoluzione**: Ubuntu e SLES, il conflitto verrà risolto automaticamente. Quando viene richiesto se si desidera disinstallare Gestione Driver unixODBC esistente, digitare "y" e procedere con l'installazione. In Red Hat, sarà necessario rimuovere manualmente Gestione Driver unixODBC esistente utilizzando `yum remove unixODBC-utf16 unixODBC-utf16-devel` e ripetere l'installazione.
    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
Le limitazioni seguenti si applicano a SQL Server Management Studio in Windows connessi a SQL Server in Linux.

- I piani di manutenzione non sono supportati.

- Gestione dei Data Warehouse di e l'agente di raccolta dati in SQL Server Management Studio non è supportata. 

- I componenti SSMS UI con l'autenticazione di Windows o le opzioni del registro eventi di Windows non funzionano con Linux. È comunque possibile utilizzare queste funzionalità con altre opzioni, ad esempio account di accesso SQL. 

- SQL Server Agent non è ancora supportata. Pertanto, la funzionalità di SQL Server Agent in SQL Server Management Studio non funziona in Linux al momento.

- Il Visualizzatore di file è limitata al "c:\\" ambito, che viene risolta var/rifiutare mssql/in Linux. Per utilizzare altri percorsi, generare script dell'operazione di interfaccia utente e sostituire l'unità c:\\ percorsi con percorsi di Linux. Quindi eseguire manualmente lo script in SSMS.

### <a name="next-steps"></a>Passaggi successivi

Per iniziare, vedere le esercitazioni di avvio rapido seguenti:

- [Installare in Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installare in SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installare in Ubuntu](quickstart-install-connect-ubuntu.md)
- [Eseguire in Docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![Grafico della barra di separazione](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a name="a-idctp11-ctp-11-december-2016"></a><a id="ctp11">CTP 1.1 (dicembre 2016)
La versione del motore di SQL Server per questa versione è 14.0.100.187.

### <a name="supported-platforms"></a>Piattaforme supportate 

| Piattaforma | File system | Guida all'installazione |
|-----|-----|-----|
| Red Hat Enterprise Linux Workstation, Server e Desktop | XFS o EXT4 | [Guida all'installazione](quickstart-install-connect-red-hat.md) | 
| Ubuntu 16.04LTS e 16.10 | EXT4 | [Guida all'installazione](quickstart-install-connect-ubuntu.md) | 
| Motore docker 1.8 + in Windows, Mac o Linux | N/D | [Guida all'installazione](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> È necessario almeno 3,25 GB di memoria per l'esecuzione di SQL Server in Linux.
> Motore di SQL Server è stata testata fino a 256GB di memoria in questo momento.

### <a name="package-details"></a>Dettagli del pacchetto
Nella tabella seguente sono elencati i dettagli del pacchetto e i percorsi di download per i pacchetti RPM e Debian. Si noti che è necessario scaricare tali pacchetti direttamente se si utilizza la procedura descritta nel [Guide all'installazione](sql-server-linux-setup.md).

| Pacchetto | versione del pacchetto | Download |
|-----|-----|-----|
| Pacchetto RPM | 14.0.100.187-1 | [pacchetto di motore RPM 14.0.100.187-1 MSSQL server](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.100.187-1.x86_64.rpm)</br>[pacchetto di elevata disponibilità RPM 14.0.100.187-1 MSSQL server](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.100.187-1.x86_64.rpm) | 
| Pacchetto Debian | 14.0.100.187-1 | [MSSQL server 14.0.100.187-1 motore Debian pacchetto](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.100.187-1_amd64.deb) |

### <a name="supported-client-tools"></a>Strumenti client supportati

| Strumento | Versione minima |
|-----|-----|
| [SQL Server Management Studio (SSMS) per Windows - versione finale candidata 1](https://go.microsoft.com/fwlink/?LinkID=835608) | 17.0 |
| [SQL Server Data Tools per Visual Studio - versione finale candidata 1](https://go.microsoft.com/fwlink/?LinkID=835150) | 17.0 |
| [Codice di Visual Studio](https://code.visualstudio.com) con il [estensione mssql](https://aka.ms/mssql-marketplace) | Versione più recente (0,2) |

> [!NOTE] 
> Le versioni di SQL Server Management Studio e SQL Server Data Tools specificate sopra sono versioni Release Candidate, pertanto non è consigliata per l'utilizzo nell'ambiente di produzione.

### <a name="unsupported-features-and-services"></a>Servizi e funzionalità non supportate
Le funzionalità e i servizi seguenti non sono disponibili su Linux in questo momento. Il supporto di queste funzionalità verrà sempre abilitato durante la cadenza mensile gli aggiornamenti del programma di anteprima.

| Area | Servizio o funzionalità non supportata |
|-----|-----|
| **Motore di database** | Ricerca full-text |
| &nbsp; | Replica |
| &nbsp; | Estensione database |
| &nbsp; | Polybase |
| &nbsp; | Query distribuite |
| &nbsp; | (XP_CMDSHELL, e così via). le stored procedure estese di sistema |
| &nbsp; | Tabella filetable |
| &nbsp; | Impostare gli assembly CLR con il EXTERNAL_ACCESS o UNSAFE autorizzazione |
| **Disponibilità elevata** | Gruppi di disponibilità AlwaysOn |
| &nbsp; | Mirroring del database  |
| **Sicurezza** | Autenticazione di Active Directory |
| &nbsp; | Autenticazione di Windows |
| &nbsp; | Extensible Key Management |
| &nbsp; | Utilizzo del certificato fornito dall'utente per SSL o TLS |
| **Servizi** | SQL Server Agent |
| &nbsp; | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Integration Services | 
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>Problemi noti
Nelle sezioni seguenti vengono descritti problemi noti con questa versione di SQL Server 2017 CTP 1.1 in Linux.

#### <a name="general"></a>Generale
- La lunghezza del nome host in cui SQL Server è installato deve essere 15 caratteri o meno. 

    - **Risoluzione**: modificare il nome e così via/nome host e un valore 15 caratteri lunghi o meno.

- Impossibile eseguire il comando `ALTER SERVICE MASTER KEY REGENERATE`. È presente un bug noto che determinerà il SQL Server potrebbe diventare instabile. Se è necessario rigenerare la chiave Master del servizio, è necessario eseguire il backup dei file di database, disinstallare e reinstallare SQL Server e quindi ripristinare nuovamente i file di database.

- Nome della risorsa per la risorsa di SQL modificata da ocf:sql:fci a ocf:mssql:fci. Ulteriori informazioni sulla configurazione di un cluster di failover di un disco condiviso è possibile trovare [qui](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-shared-disk-cluster-red-hat-7-configure).

- Impostare manualmente l'ora di sistema con le versioni precedenti nel tempo causerà l'esecuzione SQL Server per interrompere l'aggiornamento dell'ora di sistema interno all'interno di SQL Server.

    - **Risoluzione**: riavviare SQL Server.

- Non eseguire il mapping di alcuni nomi di fuso orario in Linux esattamente ai nomi di fuso orario di Windows.

    - **Risoluzione**: utilizzare nomi di fuso orario nella colonna TZID il ' Mapping per: tabella sezione Windows il [pagina della documentazione www.Unicode.org](http://www.unicode.org/cldr/charts/latest/supplemental/zone_tzid.html).

- Motore di SQL Server prevede che le righe nei file di testo per essere terminato con CR-LF (stile Windows formattazione riga).

- Sono supportate solo le installazioni a istanza singola.

    - **Risoluzione**: se si desidera disporre di più di un'istanza in un determinato host, è consigliabile utilizzare le macchine virtuali o i contenitori di Docker. 

- Tutti i file di log e i log degli errori vengono codificati in UTF-16.

- Gestione configurazione SQL Server non è possibile connettersi a SQL Server in Linux.

- **CREATE ASSEMBLY** non funzionerà durante il tentativo di utilizzare un file. Utilizzare il **FROM \<bit\>**  metodo invece per il momento. 

#### <a name="databases"></a>Database
- Non è possibile modificare i percorsi dei file di dati e di log TempDB.

- Impossibile spostare i database di sistema con l'utilità mssql conf.

- Quando si ripristina un database di cui è stato eseguito il backup in SQL Server in Windows, è necessario utilizzare il **WITH MOVE** clausola nell'istruzione Transact-SQL.

- Le transazioni distribuite che richiedono il servizio Microsoft Distributed Transaction Coordinator non sono supportate in SQL Server in esecuzione in Linux. SQL Server a SQL Server sono supportate le transazioni distribuite.

#### <a name="in-memory-oltp"></a>OLTP in memoria
- Database OLTP in memoria possono essere creati solo nella directory /var/opt/mssql. Questi database è anche necessario che la "c:\" notazione quando si fa riferimento. Per ulteriori informazioni, visitare il [argomento OLTP In memoria](sql-server-linux-performance-get-started.md#use-in-memory-oltp).  

#### <a name="sqlpackage"></a>SqlPackage
- Utilizzando SqlPackage, è necessario specificare un percorso assoluto per i file. Utilizzando i percorsi relativi verrà eseguito il mapping di file sotto il "tmp/sqlpackage. \<codice \> /sistema/system32 "cartella. 

    - **Risoluzione**: utilizzare percorsi di file assoluti.

- SqlPackage Mostra il percorso dei file con una "c:\\" prefisso.

#### <a name="sqlcmdbcp--odbc"></a>SQLCMD/BCP & ODBC 
- Strumenti di riga di comando di SQL Server (mssql-tools) e il Driver ODBC (ha) dipende da una gestione Driver unixODBC personalizzato. In questo modo è in conflitto se si dispone di una gestione Driver unixODBC installate in precedenza. 

    - **Risoluzione**: in Ubuntu, il conflitto verrà risolto automaticamente. Quando viene richiesto se si desidera disinstallare Gestione Driver unixODBC esistente, digitare "y" e procedere con l'installazione. In Red Hat, sarà necessario rimuovere manualmente Gestione Driver unixODBC esistente utilizzando `yum remove unixODBC`. Si sta lavorando a risolvere questa limitazione per RHEL e SUSE e deve disporre di un aggiornamento per la prima.  
    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
Le limitazioni seguenti si applicano a SQL Server Management Studio in Windows connessi a SQL Server in Linux.

- I piani di manutenzione non sono supportati.

- Gestione dei Data Warehouse di e l'agente di raccolta dati in SQL Server Management Studio non è supportata. 

- I componenti SSMS UI con l'autenticazione di Windows o le opzioni del registro eventi di Windows non funzionano con Linux. È comunque possibile utilizzare queste funzionalità con altre opzioni, ad esempio account di accesso SQL. 

- SQL Server Agent non è ancora supportata. Pertanto, la funzionalità di SQL Server Agent in SQL Server Management Studio non funziona in Linux al momento.

- Il Visualizzatore di file è limitata al "c:\\" ambito, che viene risolta var/rifiutare mssql/in Linux. Per utilizzare altri percorsi, generare script dell'operazione di interfaccia utente e sostituire l'unità c:\\ percorsi con percorsi di Linux. Quindi eseguire manualmente lo script in SSMS.

v

![Grafico della barra di separazione](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a name="a-idctp10-ctp-10-november-2016"></a><a id="ctp10">CTP 1.0 (novembre 2016)
La versione del motore di SQL Server per questa versione è 14.0.1.246.

### <a name="supported-platforms"></a>Piattaforme supportate 

| Piattaforma | File system | Guida all'installazione |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.2 Workstation desktop e Server | XFS o EXT4 | [Guida all'installazione](quickstart-install-connect-red-hat.md) | 
| Ubuntu 16.04LTS | EXT4 | [Guida all'installazione](quickstart-install-connect-ubuntu.md) | 
| Motore docker 1.8 + in Windows, Mac o Linux | N/D | [Guida all'installazione](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> È necessario almeno 3,25 GB di memoria per l'esecuzione di SQL Server in Linux.
> Motore di SQL Server è stata testata fino a 256GB di memoria in questo momento.

### <a name="package-details"></a>Dettagli del pacchetto
Nella tabella seguente sono elencati i dettagli del pacchetto e i percorsi di download per i pacchetti RPM e Debian. Si noti che è necessario scaricare tali pacchetti direttamente se si utilizza la procedura descritta nel [Guide all'installazione](sql-server-linux-setup.md).

| Pacchetto | versione del pacchetto | Download |
|-----|-----|-----|
| Pacchetto RPM | 14.0.1.246-6 | [pacchetto di motore RPM 14.0.1.246-6 MSSQL server](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.1.246-6.x86_64.rpm)</br>[pacchetto di elevata disponibilità RPM 14.0.1.246-6 MSSQL server](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.1.246-6.x86_64.rpm) | 
| Pacchetto Debian | 14.0.1.246-6 | [MSSQL server 14.0.1.246-6 motore Debian pacchetto](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.1.246-6_amd64.deb) |

### <a name="supported-client-tools"></a>Strumenti client supportati

| Strumento | Versione minima |
|-----|-----|
| [SQL Server Management Studio (SSMS) per Windows - versione finale candidata 1](https://go.microsoft.com/fwlink/?LinkID=835608) | 17.0 |
| [SQL Server Data Tools per Visual Studio - versione finale candidata 1](https://go.microsoft.com/fwlink/?LinkID=835150) | 17.0 |
| [Codice di Visual Studio](https://code.visualstudio.com) con il [estensione mssql](https://aka.ms/mssql-marketplace) | Versione più recente (0.1.5) |

> [!NOTE] 
> Le versioni di SQL Server Management Studio e SQL Server Data Tools specificate sopra sono versioni Release Candidate, pertanto non è consigliata per l'utilizzo nell'ambiente di produzione.

### <a name="unsupported-features-and-services"></a>Servizi e funzionalità non supportate
Le funzionalità e i servizi seguenti non sono disponibili su Linux in questo momento. Il supporto di queste funzionalità verrà sempre abilitato durante la cadenza mensile gli aggiornamenti del programma di anteprima.

| Area | Servizio o funzionalità non supportata |
|-----|-----|
| **Motore di database** | Ricerca full-text |
| &nbsp; | Replica |
| &nbsp; | Estensione database |
| &nbsp; | Polybase |
| &nbsp; | Query distribuite |
| &nbsp; | (XP_CMDSHELL, e così via). le stored procedure estese di sistema |
| &nbsp; | Tabella filetable |
| &nbsp; | Impostare gli assembly CLR con il EXTERNAL_ACCESS o UNSAFE autorizzazione |
| **Disponibilità elevata** | Gruppi di disponibilità AlwaysOn |
| &nbsp; | Mirroring del database  |
| **Sicurezza** | Autenticazione di Active Directory |
| &nbsp; | Autenticazione di Windows |
| &nbsp; | Extensible Key Management |
| &nbsp; | Utilizzo del certificato fornito dall'utente per SSL o TLS |
| **Servizi** | SQL Server Agent |
| &nbsp; | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Integration Services | 
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>Problemi noti
Nelle sezioni seguenti vengono descritti problemi noti con questa versione di SQL Server 2017 CTP1 in Linux.

#### <a name="general"></a>Generale
- La lunghezza del nome host in cui SQL Server è installato deve essere 15 caratteri o meno. 

    - **Risoluzione**: modificare il nome e così via/nome host e un valore 15 caratteri lunghi o meno.

- Impostare manualmente l'ora di sistema con le versioni precedenti nel tempo causerà l'esecuzione SQL Server per interrompere l'aggiornamento dell'ora di sistema interno all'interno di SQL Server.

    - **Risoluzione**: riavviare SQL Server.

- Non eseguire il mapping di alcuni nomi di fuso orario in Linux esattamente ai nomi di fuso orario di Windows.

    - **Risoluzione**: utilizzare nomi di fuso orario nella colonna TZID il ' Mapping per: tabella sezione Windows il [pagina della documentazione www.Unicode.org](http://www.unicode.org/cldr/charts/latest/supplemental/zone_tzid.html).

- Motore di SQL Server prevede che le righe nei file di testo per essere terminato con CR-LF (stile Windows formattazione riga).

- Sono supportate solo le installazioni a istanza singola.

    - **Risoluzione**: se si desidera disporre di più di un'istanza in un determinato host, è consigliabile utilizzare le macchine virtuali o i contenitori di Docker. 

- Tutti i file di log e i log degli errori vengono codificati in UTF-16.

- Gestione configurazione SQL Server non è possibile connettersi a SQL Server in Linux.

- **CREATE ASSEMBLY** non funzionerà durante il tentativo di utilizzare un file. Utilizzare il **FROM \<bit\>**  metodo invece per il momento.

#### <a name="databases"></a>Database
- Non è possibile modificare i percorsi dei file di dati e di log TempDB.

- Impossibile spostare i database di sistema con l'utilità mssql conf.

- Quando si ripristina un database di cui è stato eseguito il backup in SQL Server in Windows, è necessario utilizzare il **WITH MOVE** clausola nell'istruzione Transact-SQL.

- Le transazioni distribuite che richiedono il servizio Microsoft Distributed Transaction Coordinator non sono supportate in SQL Server in esecuzione in Linux. SQL Server a SQL Server sono supportate le transazioni distribuite.

#### <a name="in-memory-oltp"></a>OLTP in memoria
- Database OLTP in memoria possono essere creati solo nella directory /var/opt/mssql. Questi database è anche necessario che la "c:\\" notazione quando si fa riferimento. Per ulteriori informazioni, visitare il [argomento OLTP In memoria](sql-server-linux-performance-get-started.md#use-in-memory-oltp).  

#### <a name="sqlpackage"></a>SqlPackage
- Utilizzando SqlPackage richiede di specificare un percorso assoluto per i file. Utilizzando i percorsi relativi verrà eseguito il mapping di file sotto il "tmp/sqlpackage. \<codice \> /sistema/system32 "cartella. 

    - **Risoluzione**: utilizzare percorsi di file assoluti.

- SqlPackage Mostra il percorso dei file con una "c:\\" prefisso.

#### <a name="sqlcmdbcp--odbc"></a>SQLCMD/BCP & ODBC 
- Strumenti di riga di comando di SQL Server (mssql-tools) e il Driver ODBC (ha) dipende da una gestione Driver unixODBC personalizzato. In questo modo è in conflitto se si dispone di una gestione Driver unixODBC installate in precedenza. 

    - **Risoluzione**: in Ubuntu, il conflitto verrà risolto automaticamente. Quando viene richiesto se si desidera disinstallare Gestione Driver unixODBC esistente, digitare "y" e procedere con l'installazione. In Red Hat, sarà necessario rimuovere manualmente Gestione Driver unixODBC esistente utilizzando `yum remove unixODBC`. Si sta lavorando a risolvere questa limitazione per RHEL e SUSE e deve disporre di un aggiornamento per la prima.  
    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
Le limitazioni seguenti si applicano a SQL Server Management Studio in Windows connessi a SQL Server in Linux.

- I piani di manutenzione non sono supportati.

- Gestione dei Data Warehouse di e l'agente di raccolta dati in SQL Server Management Studio non è supportata. 

- I componenti SSMS UI con l'autenticazione di Windows o le opzioni del registro eventi di Windows non funzionano con Linux. È comunque possibile utilizzare queste funzionalità con altre opzioni, ad esempio account di accesso SQL. 

- SQL Server Agent non è ancora supportata. Pertanto, la funzionalità di SQL Server Agent in SQL Server Management Studio non funziona in Linux al momento.

- Il Visualizzatore di file è limitata al "c:\\" ambito, che viene risolta var/rifiutare mssql/in Linux. Per utilizzare altri percorsi, generare script dell'operazione di interfaccia utente e sostituire l'unità c:\\ percorsi con percorsi di Linux. Quindi eseguire manualmente lo script in SSMS.

### <a name="next-steps"></a>Passaggi successivi

Per iniziare, vedere le esercitazioni di avvio rapido seguenti:

- [Installare in Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installare in SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installare in Ubuntu](quickstart-install-connect-ubuntu.md)
- [Eseguire in Docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

