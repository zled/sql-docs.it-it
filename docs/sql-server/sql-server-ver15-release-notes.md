---
title: Note sulla versione di SQL Server 2019 | Microsoft Docs
ms.date: 11/06/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
ms.assetid: 13942af8-5a40-4cef-80f5-918386767a47
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: = sql-server-ver15 || = sqlallproducts-allversions
ms.openlocfilehash: 2c21ac917845b8162348b93fec3b868f1f748592
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51703859"
---
# <a name="sql-server-2019-preview-release-notes"></a>Note sulla versione di anteprima di SQL Server 2019

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Questo articolo descrive le limitazioni e i problemi noti per le versioni Community Technology Preview (CTP) di [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]. Per informazioni correlate, vedere:
- [Novità di SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md)

> [!NOTE]
> Le versioni di anteprima di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] vengono rese disponibili per consentire di sperimentare le funzionalità della prossima versione. Non sono supportate o concesse in licenza per la produzione. In particolare non sono supportati gli scenari riportati di seguito:
>
> - Installazione side-by-side con altre versioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]
> - Aggiornare un'istanza esistente di SQL Server da qualsiasi versione

**Provare[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]**
- [![Download da Evaluation Center](../includes/media/download2.png)](https://go.microsoft.com/fwlink/?LinkID=862101) [Scaricare [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] per l'installazione in Windows](https://go.microsoft.com/fwlink/?LinkID=862101)
- Installazione in Linux per [Red Hat Enterprise Server](../linux/quickstart-install-connect-red-hat.md), [SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md) e [Ubuntu](../linux/quickstart-install-connect-ubuntu.md).
- [Esecuzione in SQL Server 2019 in Docker](../linux/quickstart-install-connect-docker.md).

## <a name="ctp-21-november-2018"></a>CTP 2.1 (novembre 2018)
[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1 è l'ultima versione pubblica di [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)].

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1 è disponibile solo come edizione di valutazione. Non sono disponibili altre edizioni. Il supporto per CTP 2.1 è descritto nel file license_Eval.rtf nel supporto di installazione.

Un supporto limitato può essere disponibile in una delle posizioni seguenti:

- Forum
  - [Commenti di SQL Server](https://aka.ms/sqlfeedback)
  - [Introduzione a SQL Server](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=sqlgetstarted)
  - [Transact-SQL](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=transactsql)
  - [Documentazione di SQL Server](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=sqldocumentation)

- Oppure inviando un tweet [@SQLServer](https://twitter.com/SQLServer) con [#sqlhelp](https://twitter.com/search?q=%23sqlhelp)

### <a name="documentation-ctp-21"></a>Documentazione (CTP 2.1)

- **Problema e impatto per i clienti**: la documentazione di SQL Server 2019 (15.x) è limitata e il contenuto è incluso nel set di documentazione di [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Il contenuto di articoli specifici per SQL Server 2019 (15.x) è indicato con **Si applica a**.

- **Problema e impatto per i clienti**: la documentazione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] può essere filtrata in base alla versione. Usare il controllo nell'angolo superiore sinistro di ogni pagina della documentazione per filtrare in base ai requisiti. 

- **Problema e impatto per i clienti:** non è disponibile contenuto offline per SQL Server 2019 (15.x).

### <a name="hardware-and-software-requirements"></a>Requisiti hardware e software

- **Problema e impatto per i clienti**: i requisiti hardware e software sono ancora in fase di revisione e non sono finali per la versione del prodotto.

  - **Hardware**
    - [Windows - Requisiti del processore, della memoria e del sistema operativo](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md#pmosr)
    - [Linux - Requisiti di sistema](../linux/sql-server-linux-setup.md#system)
  - **Software**
    - Windows Server 2016 o versione successiva. Per requisiti aggiuntivi, vedere [Requisiti per l'installazione di SQL Server](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)
    - Microsoft .NET Framework 4.6.2. Disponibile dall'[Area download Microsoft](https://www.microsoft.com/download/details.aspx?id=53344).
    - Per Linux, vedere [Linux - Piattaforme supportate](../linux/sql-server-linux-setup.md#supportedplatforms)

### <a name="floating-point-results"></a>Risultati a virgola mobile

- **Problema e impatto sul cliente**: l'anteprima di SQL Server 2019 usa un compilatore aggiornato per compilare SQL Server. In alcuni casi il codice compilato con il nuovo compilatore può restituire vari numerici a virgola mobile diversi dalle versioni precedenti di SQL Server. La modifica funzionale sarà limitata al nuovo livello di compatibilità (150) in una versione CTP futura.

- **Soluzione alternativa**: N/D

- **Si applica a:** SQL Server 2019 CTP 2.1

### <a name="sql-server-integration-services-ssis-page-deployment-after-switching-db-to-single-user-mode-and-then-switching-back"></a>Distribuzione di pacchetti SQL Server Integration Services (SSIS) dopo il passaggio del database alla modalità utente singolo e il ritorno alla modalità multiutente

- **Problema e impatto per i clienti**: dopo il passaggio di SSISB dalla modalità utente singolo nuovamente alla modalità multiutente, potrebbe essere segnalato l'errore seguente quando si distribuisce un pacchetto:

  `Cannot continue the execution because the session is in the kill state.`

- **Soluzione alternativa**: arrestare e riavviare l'istanza di SQL Server e passare di nuovo SSISDB alla modalità multiutente. 

- **Si applica a**: anteprima di SQL Server 2019 CTP 2.1


### <a name="udf-inlining"></a>Inlining di funzioni definite dall'utente 

- **Problema e impatto per i clienti**: esistono scenari anomali in cui le chiamate annidate a funzioni definite dall'utente inline non convalidano correttamente la sicurezza.
  
- **Soluzione alternativa**: disabilitare l'inlining di funzioni definite dall'utente per tali funzioni definite dall'utente tramite l'impostazione `INLINE = OFF`.

- **Si applica a:** SQL Server 2019 CTP 2.1

### <a name="lightweight-query-profiling-infrastructure"></a>Infrastruttura leggera di profilatura query

- **Problema e impatto per i clienti**: l'esecuzione del comando `ALTER DATABASE SCOPED CONFIGURATION SET LIGHTWEIGHT_QUERY_PROFILING = ON` restituisce un errore di sintassi. Tutti gli scenari che dipendono dall'esecuzione di questo comando avranno esito negativo.

  > [!NOTE]
  > Attualmente l'infrastruttura leggera di profilatura query (LWP) non è controllabile a livello di singoli databasee per impostazione predefinita resta abilitata per tutti i database. Per altre informazioni su LWP, vedere [Novità di SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

- **Soluzione alternativa:** nessuna soluzione alternativa per le versioni CTP di [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)].

- **Si applica a**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1 e CTP 2.0.

### <a name="utf-8-collations"></a>Regole di confronto UTF-8

- **Problema e impatto per i clienti**: le regole di confronto che supportano UTF-8 non possono essere usate con altre funzionalità [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. UTF-8 non è supportato quando sono in uso le caratteristiche [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] seguenti:

  - Replica di SQL Server
  - Server collegato
  - OLTP in memoria
  - Tabella esterna per PolyBase

    Si noti anche che attualmente non è disponibile il supporto dell'interfaccia utente per la scelta di regole di confronto con supporto UTF-8 in Azure Data Studio o SSDT. La versione più recente di SSMS supporta la scelta di regole di confronto con UTF-8 nell'interfaccia utente.

- **Soluzione alternativa:** nessuna soluzione alternativa per le versioni CTP di [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)].

- **Si applica a**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1 e CTP 2.0.

### <a name="sql-graph"></a>SQL Graph

- **Problema e impatto per i clienti**: gli strumenti che dipendono da DacFx, come import-export, non funzionano per le nuove funzionalità dei grafi Edge Constraints (Vincoli di arco) o Merge DML (Unisci DML). La creazione di script in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] potrebbe non funzionare.

- **Soluzione alternativa**: la creazione di script [!INCLUDE[tsql](../includes/tsql-md.md)] e l'esecuzione di tali script sul server mediante [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] o SQLCMD funziona correttamente. L'esportazione o l'importazione di oggetti database che creano vincoli di arco, usano la nuova sintassi DML di unione o creano tabelle o viste derivate su oggetti grafo non funzionano. Gli utenti devono creare manualmente questi oggetti nel database usando gli script [!INCLUDE[tsql](../includes/tsql-md.md)]. 

- **Si applica a:** [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1 e 2.0.

### <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted con enclave sicuri

- **Problema e impatto per i clienti**: i calcoli avanzati sono in attesa di varie ottimizzazioni delle prestazioni, includono funzionalità limitate (nessuna indicizzazione e altro) e sono attualmente disabilitati per impostazione predefinita.

- **Soluzione alternativa**: per abilitare i calcoli avanzati, eseguire `DBCC traceon(127,-1)`. Per informazioni dettagliate, vedere [Enable rich computations](../relational-databases/security/encryption/configure-always-encrypted-enclaves.md#configure-a-secure-enclave) (Abilitare i calcoli avanzati).

- **Si applica a:** [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1 e 2.0.

### <a name="sql-server-integration-service---fuzzy-lookup-transformation"></a>Servizio di integrazione di SQL Server - Trasformazione Ricerca Fuzzy

- **Problema e impatto per i clienti**: la trasformazione Ricerca Fuzzy avrà esito negativo con l'errore seguente se viene impostata per riutilizzare l'indice:

  `The specified delimiters do not match the delimiters used to build the pre-existing match index "...". This error occurs when the delimiters used to tokenize fields do not match. This can have unknown effects on the matching behavior or results.`

- **Soluzione alternativa**: N/D

- **Altre informazioni**: N/D  

- **Si applica a**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP2.1

## <a name="ctp-20-september-2018"></a>CTP 2.0 (settembre 2018)

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.0 è la prima versione pubblica di [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)].

### <a name="sql-server-integration-services-ssis-transfer-database-task"></a>SQL Server Integration Services (SSIS) - Attività Trasferisci database

- **Problema e impatto per i clienti**: quando un elemento `Transfer Database Task` è configurato per il trasferimento di un database in modalità `Database Online`, l'operazione potrebbe non riuscire e restituire l'errore seguente:

  >Impossibile eseguire il metodo Execute sull'attività. Codice di errore restituito: 0x80131500 (Si è verificato un errore durante il trasferimento dei dati. Per informazioni dettagliate, vedere l'eccezione interna. Il metodo Execute deve essere eseguito correttamente e indicare il risultato tramite un parametro di output.

- **Soluzione alternativa**: eseguire `DBCC TRACEON (7416,-1)` sul server e riprovare.

- **Si applica a:** [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.0.

[!INCLUDE[get-help-options-msft-only](../includes/paragraph-content/get-help-options.md)]

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)
