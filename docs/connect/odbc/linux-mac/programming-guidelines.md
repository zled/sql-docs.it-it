---
title: Linee guida di programmazione | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2e3aac41bd87f52998edf366d7c3da2326de3f26
ms.contentlocale: it-it
ms.lasthandoff: 10/10/2017

---
# <a name="programming-guidelines"></a>Linee guida per la programmazione
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)] Le funzionalità di programmazione il [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 e 13.1 per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] su macOS e Linux sono basate su ODBC in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Native Client ([SQL Server Native Client (ODBC)](http://go.microsoft.com/fwlink/?LinkID=134151)). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Native Client è basato su ODBC in Windows Data Access Components ([riferimento per programmatori ODBC](http://go.microsoft.com/fwlink/?LinkID=45250)).  

Un'applicazione ODBC può usare MARS Multiple Active Result Set () e altri [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] funzionalità specifiche includendo `/usr/local/include/msodbcsql.h` dopo aver incluso le intestazioni unixODBC (`sql.h`, `sqlext.h`, `sqltypes.h`, e `sqlucode.h`). Quindi utilizzare gli stessi nomi simbolici per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]-elementi specifici che si userebbero nelle applicazioni ODBC Windows.  

## <a name="available-features"></a>Funzionalità disponibili  
Le sezioni seguenti dal [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] documentazione Native Client per ODBC ([SQL Server Native Client (ODBC)](http://go.microsoft.com/fwlink/?LinkID=134151)) sono validi quando si utilizza il driver ODBC in macOS e Linux:  

-   [La comunicazione con SQL Server (ODBC)](http://msdn.microsoft.com/library/ms131692.aspx)  
-   [Supporto del timeout connessione e la query](http://msdn.microsoft.com/library/ms130822.aspx)  
-   [Cursori](http://msdn.microsoft.com/library/ms130794(SQL.110).aspx)  
-   [Data/ora miglioramenti (ODBC)](http://msdn.microsoft.com/library/bb677319.aspx)  
-   [L'esecuzione di query (ODBC)](http://msdn.microsoft.com/library/ms131677.aspx)  
-   [Gestione degli errori e messaggi](http://msdn.microsoft.com/library/ms131289.aspx)  
-   [Autenticazione Kerberos](http://msdn.microsoft.com/library/cc280459.aspx)  
-   [Tipi definiti dall'utente CLR di grandi dimensioni (ODBC)](http://msdn.microsoft.com/library/bb677316.aspx)  
-   [Esecuzione di transazioni (ODBC) (escluse le transazioni distribuite)](http://msdn.microsoft.com/library/ms131706.aspx)  
-   [Elaborazione dei risultati (ODBC)](http://msdn.microsoft.com/library/ms130812.aspx)  
-   [Esecuzione di Stored procedure](http://msdn.microsoft.com/library/ms131440.aspx)
-   [Supporto per colonne di tipo sparse (ODBC)](http://msdn.microsoft.com/library/cc280357.aspx)
-   [Crittografia SSL](http://msdn.microsoft.com/library/ms131691.aspx)
-   [I parametri con valori di tabella](https://docs.microsoft.com/en-us/sql/relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc)
-   [UTF-8 e UTF-16 per l'API di comandi e dei dati](http://msdn.microsoft.com/library/ff878241.aspx)
-   [Utilizzo di funzioni di catalogo](http://msdn.microsoft.com/library/ms131490.aspx)  

## <a name="unsupported-features"></a>Caratteristiche non supportate

Le funzionalità seguenti non sono state verificate per funzionare correttamente in questa versione del driver ODBC su macOS e Linux:

-   Connessione del Cluster di failover
-   [Risoluzione IP di rete Transparent](https://docs.microsoft.com/en-us/sql/connect/odbc/linux/using-transparent-network-ip-resolution)
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

Il client la codifica può essere uno dei valori seguenti:
  -  UTF-8
  -  ISO-8859-1
  -  ISO-8859-2
  -  ISO-8859-3
  -  ISO-8859-4
  -  ISO-8859-5
  -  ISO-8859-6
  -  ISO-8859-7
  -  ISO-8859-8
  -  ISO-8859-9
  -  ISO-8859-13.
  -  ISO-8859-15
  
I dati SQLCHAR devono essere uno dei set di caratteri supportati. I dati SQLWCHAR devono essere in formato UTF-16LE (Little Endian).  

Se SQLDescribeParameter non specifica un tipo SQL nel server, il driver usa il tipo SQL specificato nel parametro *ParameterType* di SQLBindParameter. Se in SQLBindParameter viene specificato un tipo SQL di carattere "narrow", ad esempio SQL_VARCHAR, il driver converte i dati forniti dalla tabella codici del client sul valore predefinito [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] codici. (Il valore predefinito [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] tabella codici è in genere 1252.) Se la tabella codici del client non è supportata, verrà impostata su UTF-8. In questo caso, il driver converte quindi i dati UTF-8 per la tabella codici predefinita. Tuttavia è possibile che si verifichi una perdita di dati. Se la tabella codici 1252 non riesce a rappresentare un carattere, il driver converte il carattere in un punto interrogativo (?). Per evitare questo tipo di perdita di dati, specificare in SQLBindParameter un tipo di carattere SQL Unicode, ad esempio SQL_NVARCHAR. In questo caso, il driver converte i dati Unicode forniti nella codifica UTF-8 a UTF-16 senza perdita di dati.

È presente una differenza di conversione di codifica di testo tra Windows e diverse versioni della libreria iconv in Linux e macOS. Dati di testo che viene codificati nella tabella codici 1255 (ebraico) sono un punto di codice (0xCA) che si comporta in modo diverso durante la conversione. La conversione di questo carattere in formato Unicode in Windows genera un punto di codice UTF-16 pari a 0x05BA. La conversione in Unicode in macOS e Linux con le versioni libiconv anteriore 1.15 genera un punto di codice UTF-16 pari a 0x00CA.

Quando caratteri multibyte UTF-8 o caratteri sostitutivi UTF-16 vengono suddivisi tra buffer SQLPutData, i dati vengono danneggiati. Usare i buffer per i flussi SQLPutData che non terminano con la codifica parziale di caratteri.  

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

