---
title: Connettersi a un'origine dati Oracle (SQL Server importazione / esportazione guidata) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0bd1f5a-34dd-4be3-9ac8-f9f87727781b
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e589e7f7a0262d258342bf887ec84c57d57dc978
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="connect-to-an-oracle-data-source-sql-server-import-and-export-wizard"></a>Connettersi a un'origine dati Oracle (SQL Server importazione / esportazione guidata)
In questo argomento viene illustrato come connettersi a un **Oracle** dell'origine dati dal **scegliere un'origine dati** o **scegliere una destinazione** pagina di SQL Server di importazione / esportazione guidata. Esistono diversi provider di dati che è possibile utilizzare per connettersi a Oracle.

> [!IMPORTANT]
> Le informazioni dettagliate sui requisiti e i prerequisiti per la connessione a un database Oracle non rientrano nell'ambito di questo articolo di Microsoft. In questo articolo si presuppone di aver già installato il software client Oracle e che sia possibile già connettersi correttamente al database Oracle di destinazione. Per altre informazioni, consultare l'amministratore del database Oracle o la documentazione di Oracle.

## <a name="connect-to-oracle-with-the-net-framework-data-provider-for-oracle"></a>Connettersi a Oracle con .net Framework Provider di dati per Oracle
Dopo aver selezionato **il Provider di dati .NET Framework per Oracle** sul **scegliere un'origine dati** o **scegliere una destinazione** pagina della procedura guidata, la pagina Visualizza un elenco raggruppato di opzioni per il provider. Molti di questi sono impostazioni familiare e i nomi non compatibili. Fortunatamente, è necessario fornire solo due o tre tipi di informazioni. È possibile ignorare i valori predefiniti per le altre impostazioni.

> [!NOTE]
> Le opzioni di connessione per il provider di dati sono gli stessi se Oracle è l'origine o destinazione. Ovvero le opzioni disponibili sono gli stessi in entrambi i **scegliere un'origine dati** e **scegliere una destinazione** pagine della procedura guidata.

|Informazioni necessarie|.NET framework Data Provider for proprietà Oracle|
|---|---|
|Nome server|**Data Source**|
|Informazioni di autenticazione (accesso)|**ID utente** e **Password**; in alternativa, **la sicurezza integrata**|

Non è necessario immettere la stringa di connessione nella **ConnectionString** campo dell'elenco. Dopo avere immesso i singoli valori per il nome del server Oracle (**origine dati**) e informazioni di accesso, la procedura guidata consente di assemblare la stringa di connessione da singole proprietà e i relativi valori. 

![Connettersi a Oracle con il provider .NET](../../integration-services/import-export-data/media/connect-to-oracle-with-net-provider.jpg)

## <a name="connect-to-oracle-with-the-microsoft-odbc-driver-for-oracle"></a>Connettersi a Oracle con il driver ODBC di Microsoft per Oracle
Driver ODBC non sono elencati nell'elenco a discesa delle origini dati. Per connettersi con un driver ODBC, selezionare innanzitutto il **il Provider di dati .NET Framework per ODBC** come origine dati nel **scegliere un'origine dati** o **scegliere una destinazione** pagina. Questo provider funge da wrapper per il driver ODBC.

Di seguito è riportata la schermata generica che viene visualizzato subito dopo aver selezionato il Provider di dati .NET Framework per ODBC.

![Connettersi a Oracle con ODBC prima](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-before.jpg)

### <a name="options-to-specify-odbc-driver-for-oracle"></a>Opzioni per specificare (Driver ODBC per Oracle)

> [!NOTE]
> Le opzioni di connessione per questo provider di dati e il driver ODBC sono gli stessi se Oracle è l'origine o destinazione. Ovvero le opzioni disponibili sono gli stessi in entrambi i **scegliere un'origine dati** e **scegliere una destinazione** pagine della procedura guidata.

Per connettersi a Oracle con il Driver ODBC per Oracle, assemblare una stringa di connessione che include le seguenti impostazioni e i relativi valori. Il formato della stringa di connessione completa segue immediatamente l'elenco di impostazioni.

> [!TIP]
> Visualizzare la Guida di assemblaggio di una stringa di connessione più adatta. In alternativa, invece di fornire una stringa di connessione, fornire un DSN esistente (nome dell'origine dati) o crearne uno nuovo. Per ulteriori informazioni su queste opzioni, vedere [connettersi a un'origine dati ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

**Driver**  
Il nome del driver ODBC, **Microsoft ODBC per Oracle**.

**Server**  
Il nome del server Oracle. 

**UID** e **Pwd**   
L'id utente e password per la connessione.

### <a name="connection-string-format"></a>Formato stringa di connessione
Di seguito è riportato il formato della stringa di connessione tipica.

    ```
    Driver={Microsoft ODBC for Oracle};Server=myServerAddress;Uid=myUsername;Pwd=myPassword;
    ```

### <a name="enter-the-connection-string"></a>Immettere la stringa di connessione
Immettere la stringa di connessione nella **ConnectionString** campo o immettere il nome DSN nel **Dsn** nel campo di **scegliere un'origine dati** o **scegliere una destinazione** pagina. Dopo avere immesso la stringa di connessione, la procedura guidata analizza la stringa e visualizza le singole proprietà e i relativi valori nell'elenco.

Di seguito è riportata la schermata che viene visualizzato dopo aver immesso la stringa di connessione.

![Connettersi a Oracle con ODBC](../../integration-services/import-export-data/media/connect-to-oracle-with-odbc.jpg)

## <a name="whats-my-oracle-server-name"></a>Che cos'è il nome del server Oracle?
Eseguire una delle query seguenti per ottenere il nome del server Oracle.

`SELECT host_name FROM v$instance`

o

`SELECT sys_context('USERENV','SERVER_HOST') FROM dual`

## <a name="other-data-providers-and-more-info"></a>Altri provider di dati e altre informazioni
Per informazioni su come connettersi a Oracle con un provider di dati che non è elencato, vedere [stringhe di connessione Oracle](https://www.connectionstrings.com/oracle/). Questo sito di terze parti contiene inoltre informazioni sui provider di dati e i parametri di connessione descritti in questa pagina.

## <a name="see-also"></a>Vedere anche
[Scegliere un'origine dati](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Scegliere una destinazione](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


