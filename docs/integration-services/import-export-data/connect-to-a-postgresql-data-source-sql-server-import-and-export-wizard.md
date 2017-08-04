---
title: Connettersi a un'origine dati PostgreSQL (SQL Server importazione / esportazione guidata) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7a75a72-b267-444f-9eb8-d23eb333fc35
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4c82ae7eedc3e18e7591cf7ab30a507920695247
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="connect-to-a-postgresql-data-source-sql-server-import-and-export-wizard"></a>Connettersi a un'origine dati PostgreSQL (SQL Server importazione / esportazione guidata)
In questo argomento viene illustrato come connettersi a un **PostgreSQL** dell'origine dati dal **scegliere un'origine dati** o **scegliere una destinazione** pagina di SQL Server di importazione / esportazione guidata. 

> [!IMPORTANT]
> Le informazioni dettagliate sui requisiti e i prerequisiti per la connessione a un database PostgreSQL esulano dall'ambito di questo articolo di Microsoft. In questo articolo si presuppone di aver già installato il software client PostgreSQL e che sia possibile già connettersi correttamente al database PostgreSQL di destinazione. Per altre informazioni, consultare la documentazione di PostgreSQL o l'amministratore del database PostgreSQL.

## <a name="get-the-postgresql-odbc-driver"></a>Ottenere il driver ODBC PostgreSQL

### <a name="install-the-odbc-driver-with-stack-builder"></a>Installare il driver ODBC con il generatore di Stack
Eseguire il generatore di Stack per aggiungere il driver ODBC PostgreSQL (psqlODBC) per l'installazione di PostgreSQL.

![Installare PostgreSQL ODBC con il generatore di Stack](../../integration-services/import-export-data/media/install-postgresql-odbc-with-stack-builder.png)

### <a name="or-download-the-latest-odbc-driver"></a>In alternativa, scaricare il driver ODBC
In alternativa, scaricare il programma di installazione di Windows per la versione più recente del driver ODBC PostgreSQL (psqlODBC) direttamente da questo sito FTP - [https://www.postgresql.org/ftp/odbc/versions/msi/](https://www.postgresql.org/ftp/odbc/versions/msi/). Estrarre i file dal file ZIP ed eseguire il file con estensione msi.

## <a name="connect-to-postgresql-with-the-postgresql-odbc-driver-psqlodbc"></a>Connettersi a PostgreSQL con il driver ODBC PostgreSQL (psqlODBC)
Driver ODBC non sono elencati nell'elenco a discesa delle origini dati. Per connettersi con un driver ODBC, selezionare innanzitutto il **il Provider di dati .NET Framework per ODBC** come origine dati nel **scegliere un'origine dati** o **scegliere una destinazione** pagina. Questo provider funge da wrapper per il driver ODBC.

Di seguito è riportata la schermata generica che viene visualizzato subito dopo aver selezionato il Provider di dati .NET Framework per ODBC.

![Connettersi a PostgreSQL con ODBC prima](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-before.jpg)

### <a name="options-to-specify-postgresql-odbc-driver"></a>Opzioni per specificare (driver ODBC PostgreSQL)

> [!NOTE]
> Le opzioni di connessione per questo provider di dati e il driver ODBC sono gli stessi se PostgreSQL è l'origine o destinazione. Ovvero le opzioni disponibili sono gli stessi in entrambi i **scegliere un'origine dati** e **scegliere una destinazione** pagine della procedura guidata.

Per connettersi a PostgreSQL con il driver ODBC PostgreSQL, assemblare una stringa di connessione che include le seguenti impostazioni e i relativi valori. Il formato della stringa di connessione completa segue immediatamente l'elenco di impostazioni.

> [!TIP]
> Visualizzare la Guida di assemblaggio di una stringa di connessione più adatta. In alternativa, invece di fornire una stringa di connessione, fornire un DSN esistente (nome dell'origine dati) o crearne uno nuovo. Per ulteriori informazioni su queste opzioni, vedere [connettersi a un'origine dati ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

**Driver**  
Il nome del driver ODBC, ovvero **PostgreSQL ODBC Driver(UNICODE)** o **PostgreSQL ODBC Driver(ANSI)**.

**Server**  
Il nome del server PostgreSQL. 

**Porta**  
La porta da utilizzare per la connessione al server PostgreSQL.

**Database**  
Il nome del database PostgreSQL.

**UID** e **Pwd**   
Il **Uid** (id utente) e **Pwd** (password) per la connessione.

### <a name="connection-string-format"></a>Formato stringa di connessione
Di seguito è riportato il formato della stringa di connessione tipica. 

    Driver={PostgreSQL ODBC Driver(UNICODE)};Server=<server>;Port=<port>;Database=<database>;UID=<user id>;PWD=<password>

### <a name="enter-the-connection-string"></a>Immettere la stringa di connessione
Immettere la stringa di connessione nella **ConnectionString** campo o immettere il nome DSN nel **Dsn** nel campo di **scegliere un'origine dati** o **scegliere una destinazione** pagina. Dopo avere immesso la stringa di connessione, la procedura guidata analizza la stringa e visualizza le singole proprietà e i relativi valori nell'elenco.

L'esempio seguente usa la stringa di connessione.

    Driver={PostgreSQL ODBC Driver(UNICODE)};Server=127.0.0.1;Port=5432;Database=postgres;UID=postgres;PWD=********

Di seguito è riportata la schermata che viene visualizzato dopo aver immesso la stringa di connessione.

![Connettersi a PostgreSQL con ODBC](../../integration-services/import-export-data/media/connect-to-postgresql-with-odbc.png)

## <a name="other-data-providers-and-more-info"></a>Altri provider di dati e altre informazioni
Per informazioni su come connettersi a PostgreSQL con un provider di dati che non è elencato, vedere [le stringhe di connessione PostgreSQL](https://www.connectionstrings.com/postgresql/). Questo sito di terze parti contiene inoltre informazioni sui provider di dati e i parametri di connessione descritti in questa pagina.

## <a name="see-also"></a>Vedere anche
[Scegliere un'origine dati](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Scegliere una destinazione](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


