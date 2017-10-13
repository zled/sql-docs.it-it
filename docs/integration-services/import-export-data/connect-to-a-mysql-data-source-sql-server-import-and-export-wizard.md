---
title: Connettersi a un'origine dati di MySQL (SQL Server importazione / esportazione guidata) | Documenti Microsoft
ms.custom: 
ms.date: 06/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d7c5a38-18d3-4cc9-a241-04422cb250d3
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3df56fcda5b39c2895de83feac4f302686b1adf3
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="connect-to-a-mysql-data-source-sql-server-import-and-export-wizard"></a>Connettersi a un'origine dati di MySQL (SQL Server importazione / esportazione guidata)
In questo argomento viene illustrato come connettersi a un **MySQL** dell'origine dati dal **scegliere un'origine dati** o **scegliere una destinazione** pagina di SQL Server di importazione / esportazione guidata. Esistono diversi provider di dati che è possibile utilizzare per la connessione a MySQL.

> [!IMPORTANT]
> Le informazioni dettagliate sui requisiti e i prerequisiti per la connessione a un database MySQL non rientrano nell'ambito di questo articolo di Microsoft. In questo articolo si presuppone di aver già installato il software client MySQL e che sia possibile già connettersi correttamente al database MySQL di destinazione. Per altre informazioni, consultare l'amministratore del database MySQL o la documentazione di MySQL.

## <a name="get-the-mysql-connectors"></a>Recuperare i connettori di MySQL
Scaricare il provider e driver descritte in questo argomento dal [connettori MySQL](https://dev.mysql.com/downloads/connector/) pagina.

## <a name="connect-to-mysql-with-the-net-framework-data-provider-for-mysql"></a>Connessione a MySQL con .net Framework Data Provider per MySQL
Dopo aver selezionato **il Provider di dati .NET Framework per MySQL** sul **scegliere un'origine dati** o **scegliere una destinazione** pagina della procedura guidata, la pagina Visualizza un elenco raggruppato di opzioni per il provider. Molti di questi sono impostazioni familiare e i nomi non compatibili. Fortunatamente, è necessario fornire solo alcuni blocchi di informazioni. È possibile ignorare i valori predefiniti per le altre impostazioni.

> [!NOTE]
> Le opzioni di connessione per il provider di dati sono gli stessi se MySQL è l'origine o destinazione. Ovvero le opzioni disponibili sono gli stessi in entrambi i **scegliere un'origine dati** e **scegliere una destinazione** pagine della procedura guidata.

|Informazioni necessarie|.NET framework di Provider di dati per la proprietà di MySQL|
|---|---|
|Nome server|**Server**|
|Nome database|**Database**|
|Informazioni di autenticazione (accesso)|**Id utente** e **Password**|

Non è necessario immettere la stringa di connessione nella **ConnectionString** campo dell'elenco. Dopo avere immesso i singoli valori per il nome del server MySQL (**Server**) e informazioni di accesso, la procedura guidata consente di assemblare la stringa di connessione da singole proprietà e i relativi valori. 

![La connessione a MySQL con il provider .NET, 1 di 2](../../integration-services/import-export-data/media/connect-to-mysql-with-the-net-provider-1-of-2.png)

![La connessione a MySQL con il provider .NET, 2 di 2](../../integration-services/import-export-data/media/connect-to-mysql-with-the-net-provider-2-of-2.png)

## <a name="connect-to-mysql-with-the-mysql-odbc-driver"></a>La connessione a MySQL con il driver ODBC di MySQL
Driver ODBC non sono elencati nell'elenco a discesa delle origini dati. Per connettersi con un driver ODBC, selezionare innanzitutto il **il Provider di dati .NET Framework per ODBC** come origine dati nel **scegliere un'origine dati** o **scegliere una destinazione** pagina. Questo provider funge da wrapper per il driver ODBC.

Di seguito è riportata la schermata generica che viene visualizzato subito dopo aver selezionato il Provider di dati .NET Framework per ODBC.

![Connettersi a SQL con ODBC prima](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-before.jpg)

### <a name="options-to-specify-mysql-odbc-driver"></a>Opzioni per specificare (MySQL ODBC Driver)

> [!NOTE]
> Le opzioni di connessione per questo provider di dati e il driver ODBC sono gli stessi se MySQL è l'origine o destinazione. Ovvero le opzioni disponibili sono gli stessi in entrambi i **scegliere un'origine dati** e **scegliere una destinazione** pagine della procedura guidata.

Per connettersi a MySQL con il driver ODBC di MySQL, assemblare una stringa di connessione che include le seguenti impostazioni e i relativi valori. Il formato della stringa di connessione completa segue immediatamente l'elenco di impostazioni.

> [!TIP]
> Visualizzare la Guida di assemblaggio di una stringa di connessione più adatta. In alternativa, invece di fornire una stringa di connessione, fornire un DSN esistente (nome dell'origine dati) o crearne uno nuovo. Per ulteriori informazioni su queste opzioni, vedere [connettersi a un'origine dati ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

**Driver**  
Il nome del driver ODBC.

**Server**  
Il nome del server MySQL. 

**Database**  
Il nome del database MySQL.

**UID** e **PWD**   
L'id utente e password per la connessione.

### <a name="connection-string-format"></a>Formato stringa di connessione
Di seguito è riportato il formato della stringa di connessione tipica.

    ```
    Driver={MySQL ODBC 5.3 Unicode Driver};Server=<server>;Database=<database>;UID=<user id>;PWD=<password>
    ```

### <a name="enter-the-connection-string"></a>Immettere la stringa di connessione
Immettere la stringa di connessione nella **ConnectionString** campo o immettere il nome DSN nel **Dsn** nel campo di **scegliere un'origine dati** o **scegliere una destinazione** pagina. Dopo avere immesso la stringa di connessione, la procedura guidata analizza la stringa e visualizza le singole proprietà e i relativi valori nell'elenco.

L'esempio seguente usa la stringa di connessione.

    ```
    Driver={MySQL ODBC 5.3 Unicode Driver};Server=127.0.0.1;Database=world;UID=root;PWD=********
    ```

Di seguito è riportata la schermata che viene visualizzato dopo aver immesso la stringa di connessione.

![La connessione a MySQL con ODBC](../../integration-services/import-export-data/media/connect-to-mysql-with-odbc.png)

## <a name="other-data-providers-and-more-info"></a>Altri provider di dati e altre informazioni
Per informazioni sulla connessione a MySQL con un provider di dati che non è elencato, vedere [le stringhe di connessione MySQL](https://www.connectionstrings.com/mysql/). Questo sito di terze parti contiene inoltre informazioni sui provider di dati e i parametri di connessione descritti in questa pagina.

## <a name="see-also"></a>Vedere anche
[Scegliere un'origine dati](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Scegliere una destinazione](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


