---
title: Estrarre, trasformare e caricare i dati in Linux con SSIS | Documenti Microsoft
description: 
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 9dab69c7-73af-4340-aef0-de057356b791
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: aa4ac0cca739ea57a28beb399325d55b38502217
ms.contentlocale: it-it
ms.lasthandoff: 10/02/2017

---
# <a name="extract-transform-and-load-data-on-linux-with-ssis"></a>Estrarre, trasformare e caricare i dati in Linux con SSIS

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

In questo argomento viene descritto come eseguire i pacchetti di SQL Server Integration Services (SSIS) in Linux. SSIS consente di risolvere i problemi di integrazione di dati complessi estrarre dati da più origini e formati, trasformazione e pulizia dei dati e caricare i dati in più destinazioni. 

Pacchetti SSIS in esecuzione in Linux possono connettersi a Microsoft SQL Server in esecuzione su Windows locale o nel cloud, in Linux o in Docker. Anche possano connettersi a Database SQL di Azure, Azure SQL Data Warehouse, origini dati ODBC, file flat e altre origini dati, incluse le origini ADO.NET, i file XML e servizi OData.

Per ulteriori informazioni sulle funzionalità di SSIS, vedere [SQL Server Integration Services](../integration-services/sql-server-integration-services.md).

## <a name="prerequisites"></a>Prerequisiti

Per eseguire pacchetti SSIS in un computer Linux, è prima necessario installare SQL Server Integration Services. SSIS non è incluso nell'installazione di SQL Server per i computer Linux. Per istruzioni sull'installazione, vedere [installare SQL Server Integration Services](sql-server-linux-setup-ssis.md).

È inoltre necessario disporre di un computer Windows per creare e gestire pacchetti. Gli strumenti di gestione e Progettazione SSIS sono applicazioni di Windows che non sono attualmente disponibili per i computer Linux. 

## <a name="run-an-ssis-package"></a>Eseguire un pacchetto SSIS

Per eseguire un pacchetto SSIS in un computer Linux, eseguire le operazioni seguenti:

1.  Copiare il pacchetto SSIS nel computer Linux.
2.  Eseguire il comando seguente:
    ```
    $ dtexec /F \<package name \> /DE <protection password>
    ```

## <a name="other-common-ssis-tasks"></a>Altre attività comuni di SSIS

-   **Progettare pacchetti**.

    -   **Connettersi a origini dati ODBC**. Con SSIS in aggiornamento di Linux CTP 2.1 e versioni successive, i pacchetti SSIS possono utilizzare connessioni di ODBC in Linux. Questa funzionalità è stata testata con SQL Server e i driver ODBC di MySQL, ma anche dovrebbe funzionare con qualsiasi driver ODBC Unicode che osserva la specifica ODBC. In fase di progettazione, è possibile fornire un DSN o una stringa di connessione per connettersi ai dati ODBC; è inoltre possibile utilizzare l'autenticazione di Windows. Per altre informazioni, vedere il [post del blog annuncia il supporto ODBC in Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

    -   **Percorsi**. Specificare percorsi di stile di Windows nei pacchetti SSIS. SSIS in Linux non supporta i percorsi di stile di Linux, ma esegue il mapping di percorsi di stile di Windows per i percorsi di stile di Linux in fase di esecuzione. Quindi, ad esempio, SSIS in Linux esegue il mapping di stile di Windows percorso `C:\test` al percorso di Linux stile `/test`.

-   **Distribuire i pacchetti**. È possibile archiviare solo i pacchetti nel file system su Linux in questa versione. Il database del catalogo SSIS e il servizio SSIS legacy non sono disponibili in Linux per l'archiviazione e distribuzione del pacchetto.

-   **Pianificare i pacchetti**. È possibile utilizzare il sistema Linux, ad esempio gli strumenti di pianificazione `cron` per pianificare i pacchetti. Per pianificare l'esecuzione del pacchetto in questa versione, è possibile utilizzare SQL Agent in Linux. Per altre informazioni, vedere [pacchetti SSIS di pianificazione in Linux con cron](sql-server-linux-schedule-ssis-packages.md).

## <a name="limitations-and-known-issues"></a>Limitazioni e problemi noti

### <a name="general-limitations-and-known-issues"></a>Problemi noti e limitazioni generali

Le funzionalità seguenti non sono supportate in questa versione di SSIS in Linux:
  - Database del catalogo SSIS
  - Esecuzione del pacchetto pianificato dall'agente SQL
  - Autenticazione di Windows
  - Componenti di terze parti
  - Change Data Capture (CDC)
  - Scalabilità orizzontale SSIS
  - Azure Feature Pack per SSIS
  - Supporto di Hadoop e HDFS
  - Microsoft Connector for SAP BW

Per altre limitazioni e problemi noti con SSIS in Linux, vedere il [note sulla versione](sql-server-linux-release-notes.md#ssis).

### <a name="components"></a>Componenti supportati e non supportati

I seguenti componenti di Integration Services predefiniti sono supportati in Linux. Alcuni di essi hanno limitazioni sulla piattaforma Linux, come descritto nelle tabelle seguenti.

Componenti predefiniti ai quali non sono elencati di seguito non sono supportati in Linux.

#### <a name="supported-control-flow-tasks"></a>Attività flusso di controllo è supportato
- Inserimento bulk - attività
- Attività Flusso di dati
- Attività Profiling dati
- Attività Esegui SQL
- Attività Esegui istruzione T-SQL
- Attività Espressione
- Attività FTP
- Attività Servizio Web
- Attività XML

#### <a name="control-flow-tasks-supported-with-limitations"></a>Attività flusso di controllo è supportata con limitazioni

| Attività | Limitazioni |
|------------|---|
| Execute Process Task | Supporta solo modalità in-process. |
| Attività File system | Il *spostamento directory* e *impostare attributi di file* azioni non sono supportate. |
| attività Script | Supporta solo l'API di .NET Framework standard. |
| Invia messaggi - attività | Supporta solo modalità utente anonimo. |
| Attività Trasferisci Database | I percorsi UNC non sono supportati. |
| | |

#### <a name="supported-control-flow-containers"></a>Contenitori del flusso di controllo è supportato
- Sequenza - contenitore
- Contenitore Ciclo For
- Contenitore Ciclo Foreach

#### <a name="supported-data-flow-sources-and-destinations"></a>Flusso di dati supportati origini e destinazioni
- Origine File non elaborato e destinazione
- Origine XML

#### <a name="data-flow-sources-and-destinations-supported-with-limitations"></a>Origini flusso di dati e destinazioni supportate con limitazioni

| Componente | Limitazioni |
|------------|---|
| Destinazione e l'origine ADO.NET | Supporta solo il provider di dati SQLClient. |
| Origine File flat e destinazione | Supporta solo i percorsi dei file di stile di Windows, a cui viene applicata la regola di mapping del percorso predefinito. Ad esempio `D:\home\ssis\travel.csv` diventa `/home/ssis/travel.csv`. |
| Origine OData | Supporta solo l'autenticazione di base. |
| Destinazione e l'origine ODBC | Supporta i driver ODBC Unicode a 64 bit in Linux. Dipende da Gestione driver UnixODBC in Linux. |
| Origine OLE DB e destinazione | Supporta solo SQL Server Native Client 11.0 e il Provider Microsoft OLE DB per SQL Server. |
| | |

#### <a name="supported-data-flow-transformations"></a>Trasformazioni del flusso di dati supportati
- Aggregate
- Controllo
- Server di distribuzione di dati bilanciati
- Mappa caratteri
- Suddivisione condizionale
- Copia colonna
- Conversione dati
- Colonna derivata
- Esportazione colonna
- Raggruppamento fuzzy
- Ricerca fuzzy
- Importa colonna
- Ricerca
- Merge
- Merge Join
- Multicast
- Pivot
- Conteggio righe
- Dimensione a modifica lenta
- Sort
- Ricerca termini
- Union All
- UnPivot

#### <a name="data-flow-transformations-supported-with-limitations"></a>Trasformazioni di flusso di dati supportate con restrizioni

| Componente | Limitazioni |
|------------|---|
| Comando OLE DB - trasformazione | Stesse limitazioni di origine OLE DB e di destinazione. |
| componente script | Supporta solo l'API di .NET Framework standard. |
| | |

### <a name="supported-and-unsupported-log-providers"></a>Provider di log supportati e non supportati
Tutti i provider di log SSIS predefiniti sono supportati in Linux tranne il provider del registro eventi di Windows.

Il provider di log di SQL Server supporta solo l'autenticazione di SQL. non supporta l'autenticazione di Windows.

I provider di log SSIS per file di testo, per i file XML e per SQL Server Profiler scrivono l'output in un file specificato. Le considerazioni seguenti si applicano al percorso del file:
-   Se non si fornisce un percorso, il provider di log scritto nella directory corrente dell'host. Se l'utente corrente non dispone dell'autorizzazione di scrittura nella directory corrente dell'host, il provider di log genera un errore.
-   È possibile utilizzare una variabile di ambiente in un percorso di file. Se si specifica una variabile di ambiente, viene visualizzato il testo specificato nel percorso del file. Ad esempio, se si specifica `%TMP%/log.txt`, il provider di log aggiunge il testo letterale `/%TMP%/log.txt` nella directory host corrente.

## <a name="more-info-about-ssis-on-linux"></a>Altre informazioni su SSIS in Linux

Per ulteriori informazioni su SSIS in Linux, vedere il post di blog seguenti:

-   [SSIS in Linux è disponibile in SQL Server 2017 CTP 2.1](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)
-   [ODBC è supportato in SSIS in Linux (aggiornamento di SQL Server 2017 CTP 2.1)](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)

## <a name="more-info-about-ssis"></a>Altre informazioni su SSIS

Microsoft SQL Server Integration Services (SSIS) è una piattaforma per la compilazione di soluzioni di integrazione di dati a elevate prestazioni, inclusi l'estrazione, trasformazione e caricamento (ETL) di pacchetti per il data warehousing. Per altre informazioni su SSIS, vedere [SQL Server Integration Services](/sql/integration-services/sql-server-integration-services.md).

SSIS include le funzionalità seguenti:
- gli strumenti grafici e procedure guidate per la compilazione e debug dei pacchetti in Windows
- una serie di attività per eseguire funzioni di flusso di lavoro quali operazioni FTP, l'esecuzione di istruzioni SQL e l'invio di messaggi di posta elettronica
- un'ampia gamma di origini dati e destinazioni per l'estrazione e il caricamento dei dati
- un'ampia gamma di trasformazioni per la pulizia, aggregazione, l'unione e la copia dei dati
- application programming interface (API) per l'estensione SSIS con script personalizzati e i componenti personalizzati

Per informazioni introduttive su SSIS, scaricare la versione più recente di [SQL Server Data Tools (SSDT)](../integration-services/ssis-how-to-create-an-etl-package.md).

## <a name="see-also"></a>Vedere anche
- [Altre informazioni su SQL Server Integration Services](../integration-services/sql-server-integration-services.md)
- [Strumenti di gestione e sviluppo di SQL Server Integration Services (SSIS)](../integration-services/integration-services-ssis-development-and-management-tools.md)
- [Esercitazioni su SQL Server Integration Services](../integration-services/integration-services-tutorials.md)

