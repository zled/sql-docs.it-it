---
title: Connettersi a un'origine di dati SQL Server (SQL Server importazione / esportazione guidata) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 386cedbb-fae5-45ce-9363-c4a417f80a2f
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 17910c8e30dee98f39e977896fb67774b54a798d
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard"></a>Connettersi a un'origine di dati SQL Server (SQL Server importazione / esportazione guidata)
In questo argomento viene illustrato come connettersi a un **Microsoft SQL Server** dell'origine dati dal **scegliere un'origine dati** o **scegliere una destinazione** pagina di SQL Server di importazione / esportazione guidata. Esistono diversi provider di dati che è possibile utilizzare per connettersi a SQL Server.

> [!TIP]
> Se si è in una rete con più server, può risultare più semplice immettere il nome del server anziché espandere l'elenco a discesa di server. Se si sceglie l'elenco a discesa, potrebbe richiedere molto tempo per eseguire una query della rete per tutti i server disponibili e i risultati non possono includere anche il server desiderato.

## <a name="connect-to-sql-server-with-the-net-framework-data-provider-for-sql-server"></a>Connettersi a SQL Server con il provider di dati .NET Framework per SQL Server 
Dopo aver selezionato **il Provider di dati .NET Framework per SQL Server** sul **scegliere un'origine dati** o **scegliere una destinazione** pagina della procedura guidata, la pagina Visualizza un elenco raggruppato di opzioni per il provider. Molti di questi sono impostazioni familiare e i nomi non compatibili. Fortunatamente, per connettersi a qualsiasi database dell'organizzazione, in genere è necessario fornire solo alcuni blocchi di informazioni. È possibile ignorare i valori predefiniti per le altre impostazioni.

> [!NOTE]
> Le opzioni di connessione per il provider di dati sono gli stessi se SQL Server è l'origine o destinazione. Ovvero le opzioni disponibili sono gli stessi in entrambi i **scegliere un'origine dati** e **scegliere una destinazione** pagine della procedura guidata.

|Informazioni necessarie|.NET framework di Provider di dati per la proprietà di SQL Server|
|---|---|
|Nome server|**Data Source**|
|Informazioni di autenticazione (accesso)|**La sicurezza integrata di**; in alternativa, **ID utente** e **Password**<br/>Se si desidera visualizzare un elenco a discesa di database nel server, è innanzitutto necessario specificare le informazioni sull'account di accesso valido.|
|Nome database|**Catalogo iniziale**|

![Connettersi a SQL con il provider .NET](../../integration-services/import-export-data/media/connect-to-sql-with-net-provider.jpg)

### <a name="options-to-specify-net-framework-data-provider-for-sql-server"></a>Opzioni per specificare (Provider di dati .NET Framework per SQL Server)

> [!NOTE]
> Le opzioni di connessione per il provider di dati sono gli stessi se SQL Server è l'origine o destinazione. Ovvero le opzioni disponibili sono gli stessi in entrambi i **scegliere un'origine dati** e **scegliere una destinazione** pagine della procedura guidata.

**Data Source**  
 Immettere il nome o indirizzo IP del server di origine o destinazione oppure selezionare un server dall'elenco a discesa.  
 
 Per specificare una porta TCP non standard, immettere una virgola dopo il nome del server o indirizzo IP, quindi immettere il numero di porta.
 
 **Catalogo iniziale**  
 Immettere il nome del database di origine o destinazione oppure selezionare un database dall'elenco a discesa.  
  
 **Sicurezza integrata**  
 Specificare **True** per la connessione con autenticazione integrata di Windows (scelta consigliata) o **False** per la connessione con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione. Se si specifica **False**, è necessario immettere un ID utente e una password. Il valore predefinito è **False**.  
  
 **ID utente**  
 Immettere un nome utente se si utilizza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione.  
  
 **Password**  
 Immettere la password, se si utilizza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione.  

## <a name="connect-to-sql-server-with-the-odbc-driver-for-sql-server"></a>Connettersi a SQL Server con il driver ODBC per SQL Server 
Driver ODBC non sono elencati nell'elenco a discesa delle origini dati. Per connettersi con un driver ODBC, selezionare innanzitutto il **il Provider di dati .NET Framework per ODBC** come origine dati. Questo provider funge da wrapper per il driver ODBC.

> [!TIP]
> **Ottenere il driver più recente**. Scaricare il [Microsoft ODBC Driver 13 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339).

Di seguito è riportata la schermata generica che viene visualizzato subito dopo aver selezionato il Provider di dati .NET Framework per ODBC.

![Connettersi a SQL con ODBC prima](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-before.jpg)

### <a name="options-to-specify-odbc-driver-for-sql-server"></a>Opzioni per specificare (driver ODBC per SQL Server)

> [!NOTE]
> Le opzioni di connessione per il driver ODBC sono gli stessi se SQL Server è l'origine o destinazione. Ovvero le opzioni disponibili sono gli stessi in entrambi i **scegliere un'origine dati** e **scegliere una destinazione** pagine della procedura guidata.

Per connettersi a SQL Server con il driver ODBC, assemblare una stringa di connessione che include le seguenti impostazioni e i relativi valori. Il formato della stringa di connessione completa segue immediatamente l'elenco di impostazioni.

> [!TIP]
> Visualizzare la Guida di assemblaggio di una stringa di connessione più adatta. In alternativa, invece di fornire una stringa di connessione, fornire un DSN esistente (nome dell'origine dati) o crearne uno nuovo. Per ulteriori informazioni su queste opzioni, vedere [connettersi a un'origine dati ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

**Driver**  
Il nome del driver ODBC. Il nome è diverso per versioni diverse del driver.

**Server**  
Il nome del Server SQL.

**Database**  
Nome del database.  

**Trusted_Connection**; in alternativa, **Uid** e **Pwd**  
Specificare **Trusted_Connection = Yes** per la connessione con autenticazione integrata di Windows; in alternativa, specificare **Uid** (id utente) e **Pwd** (password) per la connessione con autenticazione di SQL Server.

### <a name="connection-string-format"></a>Formato stringa di connessione
Di seguito è riportato il formato della stringa di connessione che utilizza l'autenticazione integrata di Windows.

    `Driver={ODBC Driver 13 for SQL Server};server=<server>;database=<database>;trusted_connection=Yes;`

Di seguito è riportato il formato della stringa di connessione che utilizza l'autenticazione di SQL Server anziché l'autenticazione integrata di Windows.

     `Driver={ODBC Driver 13 for SQL Server};server=<server>;database=<database>;uid=<user id>;pwd=<password>;`

### <a name="enter-the-connection-string"></a>Immettere la stringa di connessione
Immettere la stringa di connessione nella **ConnectionString** campo o immettere il nome DSN nel **Dsn** nel campo di **scegliere un'origine dati** o **scegliere una destinazione** pagina. Dopo avere immesso la stringa di connessione, la procedura guidata analizza la stringa e visualizza le singole proprietà e i relativi valori nell'elenco.

L'esempio seguente usa la stringa di connessione.

    `Driver={ODBC Driver 13 for SQL Server};server=localhost;database=WideWorldImporters;trusted_connection=Yes;`

Di seguito è riportata la schermata che viene visualizzato dopo aver immesso la stringa di connessione.

![Connettersi a SQL con ODBC dopo](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-after.jpg)

## <a name="connect-to-sql-server-with-the-microsoft-ole-db-provider-for-sql-server-or-sql-server-native-client"></a>Connettersi a SQL Server con il Provider Microsoft OLE DB per SQL Server o SQL Server Native Client

> [!IMPORTANT]
> Il Provider Microsoft OLE DB per SQL Server e SQL Server Native Client non sono supportati nelle versioni di SQL Server dopo SQL Server 2012. In alternativa, usare il driver ODBC. Per ulteriori informazioni sulla transizione per il driver ODBC, vedere il post di blog seguenti.
>   -   [Microsoft sta allineando con ODBC per l'accesso ai dati relazionali nativi](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/)
>   -   [Introdurre i nuovi driver ODBC di Microsoft per SQL Server](https://blogs.msdn.microsoft.com/sqlnativeclient/2013/01/23/introducing-the-new-microsoft-odbc-drivers-for-sql-server/)

## <a name="other-data-providers-and-more-info"></a>Altri provider di dati e altre informazioni
Per informazioni su come connettersi a SQL Server con un provider di dati che non è elencato, vedere [le stringhe di connessione di SQL Server](https://www.connectionstrings.com/sql-server/). Questo sito di terze parti contiene inoltre informazioni sui provider di dati e i parametri di connessione descritti in questa pagina.

## <a name="see-also"></a>Vedere anche
[Scegliere un'origine dati](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Scegliere una destinazione](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


