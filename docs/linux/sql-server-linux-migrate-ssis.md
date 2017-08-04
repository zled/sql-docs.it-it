---
title: Estrarre, trasformare e caricare i dati in Linux con SSIS | Documenti Microsoft
description: 
author: sanagama
ms.author: sanagama
manager: jhubbard
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 9dab69c7-73af-4340-aef0-de057356b791
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: d7317cad5aa1e77653431c128ce1549bc4349e18
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="extract-transform-and-load-data-on-linux-with-ssis"></a>Estrarre, trasformare e caricare i dati in Linux con SSIS

In questo argomento viene descritto come eseguire i pacchetti di SQL Server Integration Services (SSIS) in Linux. SSIS risolve i problemi di integrazione di dati complessi per il caricamento di dati da più origini e formati, trasformazione e pulizia dei dati e l'aggiornamento di più destinazioni. 

Pacchetti SSIS in esecuzione in Linux possono connettersi a Microsoft SQL Server in esecuzione su Windows locale o nel cloud, in Linux o in Docker. Inoltre, possono essere connessi al Database SQL di Azure, Azure SQL Data Warehouse e origini dati ODBC.

È possibile utilizzare SSIS per eseguire i pacchetti in Linux quando è disponibile anche un computer Windows per creare e gestire pacchetti. Gli strumenti di gestione e Progettazione SSIS sono applicazioni di Windows. 

## <a name="prerequisites"></a>Prerequisiti

Per eseguire pacchetti SSIS in un computer Linux, è prima necessario installare SQL Server Integration Services. Per istruzioni sull'installazione, vedere [installare SQL Server Integration Services](sql-server-linux-setup-ssis.md).

## <a name="run-an-ssis-package"></a>Eseguire un pacchetto SSIS

Per eseguire un pacchetto SSIS in un computer Linux, eseguire le operazioni seguenti:

1.  Copiare il pacchetto SSIS nel computer Linux.
2.  Eseguire il comando seguente:
    ```
    $ dtexec /F \<package name \> /DE <protection password>
    ```

## <a name="more-about-ssis-on-linux"></a>Ulteriori informazioni su SSIS in Linux

**Connessioni ODBC**. Con SSIS in aggiornamento di Linux CTP 2.1 e versioni successive, i pacchetti SSIS possono utilizzare connessioni di ODBC in Linux. Questa funzionalità è stata testata con SQL Server e i driver ODBC di MySQL, ma anche dovrebbe funzionare con qualsiasi driver ODBC Unicode che osserva la specifica ODBC. In fase di progettazione, è possibile fornire un DSN o una stringa di connessione per connettersi ai dati ODBC; è inoltre possibile utilizzare l'autenticazione di Windows. Per altre informazioni, vedere il [post del blog annuncia il supporto ODBC in Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

**Percorsi**. SSIS in Linux non supporta i percorsi di stile di Linux, ma esegue il mapping di percorsi di stile di Windows per i percorsi di stile di Linux in fase di esecuzione. Specificare percorsi di stile di Windows nei pacchetti SSIS. Quindi, ad esempio, SSIS in Linux esegue il mapping di stile di Windows percorso `C:\test` al percorso di Linux stile `/test`.

**Distribuzione di pacchetti**. È possibile archiviare solo i pacchetti nel file system su Linux in questa versione. Il database del catalogo SSIS e il servizio SSIS legacy non sono disponibili in Linux per l'archiviazione e distribuzione del pacchetto.

**Pianificazione dei pacchetti**. Per pianificare l'esecuzione del pacchetto in questa versione, è possibile utilizzare SQL Agent in Linux.

**Altre limitazioni e problemi noti**. Le funzionalità seguenti non sono supportate in questa versione, quando si eseguono i pacchetti SSIS in Linux:
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

Per ulteriori informazioni su SSIS in Linux, vedere il post di blog seguenti:

-   [SSIS in Linux è disponibile in SQL Server 2017 CTP 2.1](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)
-   [ODBC è supportato in SSIS in Linux (aggiornamento di SQL Server 2017 CTP 2.1)](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)

## <a name="more-about-ssis"></a>Ulteriori informazioni su SSIS

Microsoft SQL Server Integration Services (SSIS) è una piattaforma per la compilazione di soluzioni di integrazione di dati a elevate prestazioni, inclusi l'estrazione, trasformazione e caricamento (ETL) di pacchetti per il data warehousing. Per altre informazioni su SSIS, vedere [SQL Server Integration Services](/sql/integration-services/sql-server-integration-services.md).

SSIS include le funzionalità seguenti:
- gli strumenti grafici e procedure guidate per la compilazione e debug dei pacchetti in Windows
- una serie di attività per eseguire funzioni di flusso di lavoro quali operazioni FTP, l'esecuzione di istruzioni SQL e l'invio di messaggi di posta elettronica
- un'ampia gamma di origini dati e destinazioni per l'estrazione e il caricamento dei dati
- un'ampia gamma di trasformazioni per la pulizia, aggregazione, l'unione e la copia dei dati
- application programming interface (API) per l'estensione SSIS con script personalizzati e i componenti personalizzati

Per informazioni introduttive su SSIS, scaricare la versione più recente di [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md). Seguire l'esercitazione [SSIS come creare un pacchetto ETL](https://msdn.microsoft.com/en-us/library/ms169917.aspx).

## <a name="see-also"></a>Vedere anche
- [Altre informazioni su SQL Server Integration Services](https://msdn.microsoft.com/en-us/library/ms141026.aspx)
- [Strumenti di gestione e sviluppo di SQL Server Integration Services (SSIS)](https://msdn.microsoft.com/en-us/library/ms140028.aspx)
- [Esercitazioni su SQL Server Integration Services](https://msdn.microsoft.com/en-us/library/jj720568.aspx)

