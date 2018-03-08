---
title: Linee guida per programmatori (Driver ODBC per SQL Server) | Documenti Microsoft
ms.custom: 
ms.date: 01/11/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: fd8952f28f389fa5f1b8f82072998676c5a4196e
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2018
---
# <a name="programming-guidelines"></a>Linee guida per la programmazione

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Le funzionalità di programmazione il [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] su macOS e Linux sono basate su ODBC in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Native Client ([SQL Server Native Client (ODBC)](http://go.microsoft.com/fwlink/?LinkID=134151)). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Native Client è basato su ODBC in Windows Data Access Components ([riferimento per programmatori ODBC](http://go.microsoft.com/fwlink/?LinkID=45250)).  

Un'applicazione ODBC può usare MARS Multiple Active Result Set () e altri [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] funzionalità specifiche includendo `/usr/local/include/msodbcsql.h` dopo aver incluso le intestazioni unixODBC (`sql.h`, `sqlext.h`, `sqltypes.h`, e `sqlucode.h`). Quindi utilizzare gli stessi nomi simbolici per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]-elementi specifici che si utilizzerebbe nelle applicazioni ODBC Windows.

## <a name="available-features"></a>Funzionalità disponibili  
Le sezioni seguenti dal [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] documentazione Native Client per ODBC ([SQL Server Native Client (ODBC)](http://go.microsoft.com/fwlink/?LinkID=134151)) sono validi quando si utilizza il driver ODBC in macOS e Linux:  

-   [Comunicazione con SQL Server (ODBC)](http://msdn.microsoft.com/library/ms131692.aspx)  
-   [Supporto del timeout connessione e la query](http://msdn.microsoft.com/library/ms130822.aspx)  
-   [Cursori](http://msdn.microsoft.com/library/ms130794(SQL.110).aspx)  
-   [Data/ora miglioramenti (ODBC)](http://msdn.microsoft.com/library/bb677319.aspx)  
-   [Esecuzione di query (ODBC)](http://msdn.microsoft.com/library/ms131677.aspx)  
-   [Gestione di errori e messaggi](http://msdn.microsoft.com/library/ms131289.aspx)  
-   [Autenticazione Kerberos](http://msdn.microsoft.com/library/cc280459.aspx)  
-   [Tipi CLR definiti dall'utente di grandi dimensioni (ODBC)](http://msdn.microsoft.com/library/bb677316.aspx)  
-   [Esecuzione di transazioni (ODBC) (escluse le transazioni distribuite)](http://msdn.microsoft.com/library/ms131706.aspx)  
-   [Risultati dell'elaborazione (ODBC)](http://msdn.microsoft.com/library/ms130812.aspx)  
-   [Esecuzione delle stored procedure](http://msdn.microsoft.com/library/ms131440.aspx)
-   [Supporto per colonne di tipo sparse (ODBC)](http://msdn.microsoft.com/library/cc280357.aspx)
-   [Crittografia SSL](http://msdn.microsoft.com/library/ms131691.aspx)
-   [I parametri con valori di tabella](https://docs.microsoft.com/en-us/sql/relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc)
-   [UTF-8 e UTF-16 per l'API di comandi e dei dati](http://msdn.microsoft.com/library/ff878241.aspx)
-   [Uso delle funzioni catalogo](http://msdn.microsoft.com/library/ms131490.aspx)  

## <a name="unsupported-features"></a>Caratteristiche non supportate

Le funzionalità seguenti non sono state verificate per funzionare correttamente in questa versione del driver ODBC su macOS e Linux:

-   Connessione del Cluster di failover
-   [La risoluzione IP di rete Transparent](https://docs.microsoft.com/en-us/sql/connect/odbc/linux/using-transparent-network-ip-resolution) (prima del Driver ODBC 17)
-   [Driver avanzate funzionalità di traccia](https://blogs.msdn.microsoft.com/mattn/2012/05/15/enabling-advanced-driver-tracing-for-the-sql-native-client-odbc-drivers/)

Le funzionalità seguenti non sono disponibili in questa versione del driver ODBC in macOS e Linux: 

-   Transazioni distribuite (attributo SQL_ATTR_ENLIST_IN_DTC non è supportato)  
-   Mirroring del database  
-   FILESTREAM  
-   Profilatura delle prestazioni del driver ODBC, descritti in [SQLSetConnectAttr](http://go.microsoft.com/fwlink/?LinkId=234099)e gli attributi di connessione relativi alle prestazioni seguenti:  
    -   SQL_COPT_SS_PERF_DATA  
    -   SQL_COPT_SS_PERF_DATA_LOG  
    -   SQL_COPT_SS_PERF_DATA_LOG_NOW  
    -   SQL_COPT_SS_PERF_QUERY  
    -   SQL_COPT_SS_PERF_QUERY_INTERVAL  
    -   SQL_COPT_SS_PERF_QUERY_LOG  
-   SQLBrowseConnect  
-   Tipi di intervallo C, ad esempio SQL_C_INTERVAL_YEAR_TO_MONTH (documentati in [gli identificatori di tipo di dati e i descrittori](http://msdn.microsoft.com/library/ms716351(VS.85).aspx))
-   Il valore SQL_CUR_USE_ODBC dell'attributo SQL_ATTR_ODBC_CURSORS della funzione SQLSetConnectAttr.

## <a name="character-set-support"></a>Supporto del Set di caratteri

Per ODBC Driver 13 e 13.1, i dati SQLCHAR devono essere UTF-8. Altre codifiche non sono supportati.

Per ODBC Driver 17, i dati SQLCHAR in uno dei seguenti gruppi/codifiche di caratteri sono supportati:

|Nome|Description|
|-|-|
|UTF-8|Unicode|
|CP437|Alfabeto latino MS-DOS Stati Uniti|
|CP850|MS-DOS Latin 1|
|CP874|Latin/Thai|
|CP932|Giapponese Shift-JIS|
|CP936|Cinese semplificato, GBK|
|CP949|Coreano, EUC-KR|
|CP950|Cinese tradizionale, Big5|
|CP1251|Cirillico|
|CP1253|Greco|
|CP1256|Arabo|
|CP1257|Baltico|
|CP1258|Vietnamita|
|ISO-8859-1 / CP1252|Latino 1|
|ISO-8859-2 / CP1250|Alfabeto latino-2|
|ISO-8859-3|Alfabeto latino-3|
|ISO-8859-4|Alfabeto latino-4|
|ISO-8859-5|Latin/Cyrillic|
|ISO-8859-6|Alfabeto latino/arabo|
|ISO-8859-7|Alfabeto latino/greco|
|ISO-8859-8 / CP1255|Ebraico|
|ISO-8859-9 / CP1254|Turco|
|ISO-8859-13|Latin-7|
|ISO-8859-15|Alfabeto latino 9|

Al momento della connessione, il driver rileva le impostazioni locali correnti del processo che viene caricato. Se utilizza una delle codifiche descritte sopra, il driver utilizza la codifica per i dati SQLCHAR (carattere "narrow"); in caso contrario, il valore predefinito UTF-8. Poiché tutti i processi avviati nelle impostazioni locali "C" per impostazione predefinita (e pertanto che il driver per impostazione predefinita in UTF-8), se un'applicazione deve utilizzare una delle codifiche descritte sopra, è necessario utilizzare il **setlocale** per impostare in modo appropriato prima che le impostazioni locali (funzione) la connessione; specificare le impostazioni locali desiderate in modo esplicito, o utilizzando una stringa vuota, ad esempio `setlocale(LC_ALL, "")` per utilizzare le impostazioni locali dell'ambiente.

Pertanto, in un tipico Linux o Mac ambiente in cui la codifica è UTF-8, gli utenti di ODBC Driver 17 l'aggiornamento da 13 o 13.1 non rispetterà eventuali differenze. Tuttavia, le applicazioni che utilizzano una codifica non UTF-8 nell'elenco precedente tramite `setlocale()` necessario utilizzare la codifica per i dati da e verso il driver anziché UTF-8.

I dati SQLWCHAR devono essere in formato UTF-16LE (Little Endian).

Quando si associano parametri di input con SQLBindParameter, se un carattere "narrow" SQL digitare, ad esempio SQL_VARCHAR è specificato, il driver converte i dati forniti dal client di codifica per il valore predefinito (in genere la tabella codici 1252) [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] codifica. Per i parametri di output, il driver converte dalla codifica specificata nelle informazioni di regole di confronto associate ai dati al client la codifica. Tuttavia, è possibile perdita di dati---caratteri nella codifica di origine non rappresentabile nella codifica di destinazione verranno convertito in un punto interrogativo ('? ').

Per evitare la perdita di dati durante l'associazione dei parametri di input, specificare un tipo di carattere SQL Unicode, ad esempio SQL_NVARCHAR. In questo caso, il driver converte dal client la codifica UTF-16, che può rappresentare tutti i caratteri Unicode. Inoltre, la colonna di destinazione o il parametro sul server deve inoltre essere un tipo di Unicode (**nchar**, **nvarchar**, **ntext**) o a uno con delle regole di confronto/codifica, che può rappresenta tutti i caratteri di dati di origine. Per evitare la perdita di dati con i parametri di output, specificare un tipo SQL Unicode e un Unicode C tipo (SQL_C_WCHAR), causando il driver restituire dati come UTF-16; o C "narrow" digitare e verificare che il client la codifica può rappresentare tutti i caratteri dei dati di origine (questo è sempre possibile con UTF-8).

Per ulteriori informazioni sulle regole di confronto e le codifiche, vedere [Collation and Unicode Support](../../../relational-databases/collations/collation-and-unicode-support.md).

Esistono alcune differenze di conversione di codifica tra Windows e diverse versioni della libreria iconv in Linux e macOS. Dati di testo nella tabella codici 1255 (ebraico) sono un punto di codice (0xCA) che si comporta in modo diverso durante la conversione in Unicode. In Windows, questo carattere converte il punto di codice UTF-16 pari a 0x05BA. In macOS e Linux con libiconv versioni precedenti a 1.15, viene convertito in 0x00CA. In Linux con le librerie iconv che non supportano la revisione 2003 del Big5/CP950 (denominato `BIG5-2003`), caratteri aggiunti con la revisione non verranno convertiti correttamente.

In ODBC Driver 13 e 13.1 quando caratteri multibyte UTF-8 o surrogati UTF-16 vengono suddivisi tra buffer SQLPutData, comporta il danneggiamento dei dati. Usare i buffer per i flussi SQLPutData che non terminano con la codifica parziale di caratteri. Questa limitazione è stato rimosso con 17 Driver ODBC.

## <a name="additional-notes"></a>Note aggiuntive  

1.  È possibile effettuare una connessione amministrativa dedicata (DAC) utilizzando [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] l'autenticazione e **host, porta**. Un membro del ruolo Sysadmin deve prima individuare la porta DAC. Vedere [connessione di diagnostica per gli amministratori di Database](https://docs.microsoft.com/en-us/sql/database-engine/configure-windows/diagnostic-connection-for-database-administrators#dac-port) per individuare la modalità. Ad esempio, se la porta DAC è 33000, è Impossibile connettersi a esso con `sqlcmd` come indicato di seguito:  

    ```
    sqlcmd –U <user> -P <pwd> -S <host>,33000
    ```

    > [!NOTE]  
    > Le connessioni DAC devono utilizzare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] l'autenticazione.  
    
2.  Gestione driver UnixODBC restituisce "Identificatore di opzione o di attributo non valido" per tutti gli attributi di istruzione quando questi vengono passati tramite SQLSetConnectAttr. In Windows, quando SQLSetConnectAttr riceve un valore di attributo di istruzione, fa in modo il driver imposti questo valore in tutte le istruzioni attive che sono elementi figlio dell'handle di connessione.  

## <a name="see-also"></a>Vedere anche  
[Domande frequenti](../../../connect/odbc/linux-mac/frequently-asked-questions-faq-for-odbc-linux.md)

[Problemi noti in questa versione del driver](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)

[Note sulla versione](../../../connect/odbc/linux-mac/release-notes.md)
