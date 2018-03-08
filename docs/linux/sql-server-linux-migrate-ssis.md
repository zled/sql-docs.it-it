---
title: Estrarre, trasformare e caricare i dati in Linux con SSIS | Documenti Microsoft
description: Questo articolo viene descritto il servizio SQL Server Integration Services (SSIS) per i computer Linux
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 01/09/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.workload: On Demand
ms.openlocfilehash: 87c28ec845a59ea13acce0585bc9b249f100a4a5
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2018
---
# <a name="extract-transform-and-load-data-on-linux-with-ssis"></a>Estrarre, trasformare e caricare i dati in Linux con SSIS

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In questo articolo viene descritto come eseguire i pacchetti di SQL Server Integration Services (SSIS) in Linux. SSIS consente di risolvere i problemi di integrazione di dati complessi estrarre dati da più origini e formati, trasformazione e pulizia dei dati e caricare i dati in più destinazioni. 

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

## <a name="run-an-encrypted-password-protected-package"></a>Eseguire un pacchetto crittografato (protetto da password)
Esistono tre modi per eseguire un pacchetto SSIS che viene crittografato con una password:

1.  Impostare il valore della variabile di ambiente `SSIS_PACKAGE_DECRYPT`, come illustrato nell'esempio seguente:

    ```
    SSIS_PACKAGE_DECRYPT=test /opt/ssis/bin/dtexec /f package.dtsx
    ```

2.  Specificare il `/de[crypt]` opzione per immettere la password in modo interattivo, come illustrato nell'esempio seguente:

    ```
    /opt/ssis/bin/dtexec /f package.dtsx /de
    
    Enter decryption password:
    ```

3.  Specificare il `/de` opzione per fornire la password nella riga di comando, come illustrato nell'esempio seguente. Questo metodo è sconsigliato, perché la password di decrittografia con il comando Archivia nella cronologia dei comandi.

    ```
    opt/ssis/bin/dtexec /f package.dtsx /de test
    
    Warning: Using /De[crypt] <password> may store decryption password in command history.
    
    You can use /De[crypt] instead to enter interactive mode,
    or use environment variable SSIS_PACKAGE_DECRYPT to set decryption password.
    ```

## <a name="design-packages"></a>Progettazione di pacchetti

**Connettersi a origini dati ODBC**. Con SSIS in aggiornamento di Linux CTP 2.1 e versioni successive, i pacchetti SSIS possono utilizzare connessioni di ODBC in Linux. Questa funzionalità è stata testata con SQL Server e i driver ODBC di MySQL, ma anche dovrebbe funzionare con qualsiasi driver ODBC Unicode che osserva la specifica ODBC. In fase di progettazione, è possibile fornire un DSN o una stringa di connessione per connettersi ai dati ODBC; è inoltre possibile utilizzare l'autenticazione di Windows. Per altre informazioni, vedere il [post del blog annuncia il supporto ODBC in Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

**Percorsi**. Specificare percorsi di stile di Windows nei pacchetti SSIS. SSIS in Linux non supporta i percorsi di stile di Linux, ma esegue il mapping di percorsi di stile di Windows per i percorsi di stile di Linux in fase di esecuzione. Quindi, ad esempio, SSIS in Linux esegue il mapping di stile di Windows percorso `C:\test` al percorso di Linux stile `/test`.

## <a name="deploy-packages"></a>Distribuire i pacchetti
È possibile archiviare solo i pacchetti nel file system su Linux in questa versione. Il database del catalogo SSIS e il servizio SSIS legacy non sono disponibili in Linux per l'archiviazione e distribuzione del pacchetto.

## <a name="schedule-packages"></a>Pianificare i pacchetti
È possibile utilizzare il sistema Linux, ad esempio gli strumenti di pianificazione `cron` per pianificare i pacchetti. Per pianificare l'esecuzione del pacchetto in questa versione, è possibile utilizzare SQL Agent in Linux. Per altre informazioni, vedere [pacchetti SSIS di pianificazione in Linux con cron](sql-server-linux-schedule-ssis-packages.md).

## <a name="limitations-and-known-issues"></a>Limitazioni e problemi noti

Per informazioni dettagliate sulle limitazioni e problemi noti di SSIS in Linux, vedere [limitazioni e problemi noti per SSIS in Linux](sql-server-linux-ssis-known-issues.md).

## <a name="more-info-about-ssis-on-linux"></a>Altre informazioni su SSIS in Linux

Per ulteriori informazioni su SSIS in Linux, vedere il post di blog seguenti:

-   [SSIS in Linux è disponibile in SQL Server 2017 CTP 2.1](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)
-   [ODBC è supportato in SSIS in Linux (aggiornamento di SQL Server 2017 CTP 2.1)](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)

## <a name="more-info-about-ssis"></a>Altre informazioni su SSIS

Microsoft SQL Server Integration Services (SSIS) è una piattaforma per la compilazione di soluzioni di integrazione di dati a elevate prestazioni, inclusi l'estrazione, trasformazione e caricamento (ETL) di pacchetti per il data warehousing. Per altre informazioni su SSIS, vedere [SQL Server Integration Services](/sql/integration-services/sql-server-integration-services).

SSIS include le funzionalità seguenti:
- gli strumenti grafici e procedure guidate per la compilazione e debug dei pacchetti in Windows
- una serie di attività per eseguire funzioni di flusso di lavoro quali operazioni FTP, l'esecuzione di istruzioni SQL e l'invio di messaggi di posta elettronica
- un'ampia gamma di origini dati e destinazioni per l'estrazione e il caricamento dei dati
- un'ampia gamma di trasformazioni per la pulizia, aggregazione, l'unione e la copia dei dati
- application programming interface (API) per l'estensione SSIS con script personalizzati e i componenti personalizzati

Per informazioni introduttive su SSIS, scaricare la versione più recente di [SQL Server Data Tools (SSDT)](../integration-services/ssis-how-to-create-an-etl-package.md).

Per ulteriori informazioni su SSIS, vedere gli articoli seguenti:
- [Altre informazioni su SQL Server Integration Services](../integration-services/sql-server-integration-services.md)
- [Strumenti di gestione e sviluppo di SQL Server Integration Services (SSIS)](../integration-services/integration-services-ssis-development-and-management-tools.md)
- [Esercitazioni su SQL Server Integration Services](../integration-services/integration-services-tutorials.md)

## <a name="related-content-about-ssis-on-linux"></a>Contenuto correlato su SSIS in Linux
-   [Installare SQL Server Integration Services (SSIS) in Linux](sql-server-linux-setup-ssis.md)
-   [Configurare SQL Server Integration Services in Linux con ssis-conf](sql-server-linux-configure-ssis.md)
-   [Limitazioni e problemi noti per SSIS in Linux](sql-server-linux-ssis-known-issues.md)
-   [Esecuzione in Linux con cron del pacchetto di pianificazione di SQL Server Integration Services](sql-server-linux-schedule-ssis-packages.md)
