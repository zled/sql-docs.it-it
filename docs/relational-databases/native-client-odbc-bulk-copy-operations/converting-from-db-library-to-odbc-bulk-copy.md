---
title: La conversione da DB-Library a copia Bulk ODBC | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-bulk-copy-operations
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- converting DB-Library to ODBC bulk copy
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], DB-Library bulk copy
- ODBC, bulk copy operations
- DB-Library bulk copy
ms.assetid: 0bc15bdb-f19f-4537-ac6c-f249f42cf07f
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: abdb8b529914a3ebb09ed0d5d933c30e0ef43f9d
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="converting-from-db-library-to-odbc-bulk-copy"></a>Conversione della copia bulk da DB-Library a ODBC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Conversione di un programma di copia bulk di DB-Library in ODBC è facile quanto supportate da funzioni di copia di massa di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client sono simili alle funzioni di copia bulk DB-Library, con le eccezioni seguenti:  
  
-   Nelle applicazioni DB-Library un puntatore a una struttura DBPROCESS viene passato come primo parametro delle funzioni di copia bulk. Nelle applicazioni ODBC il puntatore DBPROCESS viene sostituito da un handle di connessione ODBC.  
  
-   Chiamata di applicazioni DB-Library **BCP_SETL** prima della connessione per abilitare le operazioni di copia bulk in una struttura DBPROCESS. Le applicazioni ODBC chiamano invece [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) prima della connessione per abilitare le operazioni bulk su un handle di connessione:  
  
    ```  
    SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP,  
        (void *)SQL_BCP_ON, SQL_IS_INTEGER);  
    ```  
  
-   Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client non supportano i gestori di messaggi ed errori di DB-Library, è necessario chiamare **SQLGetDiagRec** per ottenere gli errori e i messaggi generati dalle funzioni di copia bulk ODBC. Le versioni ODBC delle funzioni di copia bulk restituiscono i codici restituiti standard di copia bulk SUCCEED o FAILED, non codici restituiti di tipo ODBC, come SQL_SUCCESS o SQL_ERROR.  
  
-   I valori specificati per DB-Library [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)*varlen* parametro vengono interpretati in modo diverso rispetto a ODBC **bcp_bind * * * cbData* parametro.  
  
    |Condizione indicata|DB-Library *varlen* valore|ODBC *cbData* valore|  
    |-------------------------|--------------------------------|-------------------------|  
    |Valori Null forniti|0|-1 (SQL_NULL_DATA)|  
    |Dati variabili forniti|-1|-10 (SQL_VARLEN_DATA)|  
    |Carattere di lunghezza zero o stringa binaria|ND|0|  
  
     In DB-Library, un *varlen* valore -1 indica che vengono forniti dati di lunghezza variabile, in ODBC *cbData* viene interpretato in modo da indicare che vengono forniti solo valori NULL. Modificare qualsiasi DB-Library *varlen* specifiche di -1 su SQL_VARLEN_DATA e qualsiasi *varlen* specifiche 0 su SQL_NULL_DATA.  
  
-   DB-Library  **bcp_colfmt * * * file_collen* e ODBC [bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)*cbUserData * presentano lo stesso problema come il **bcp_bind * * * varlen*e *cbData* parametri indicati in precedenza. Modificare qualsiasi DB-Library *file_collen* specifiche di -1 su SQL_VARLEN_DATA e qualsiasi *file_collen* specifiche 0 su SQL_NULL_DATA.  
  
-   Il *iValue* parametro di ODBC [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) funzione è un puntatore void. In DB-Library, *iValue* è un numero intero. Il cast dei valori per ODBC *iValue* a void *.  
  
-   Il **bcp_control** opzione BCPMAXERRS specifica il numero di righe singole con errori prima di un'operazione di copia bulk ha esito negativo. L'impostazione predefinita per BCPMAXERRS è 0 (esito negativo sul primo errore) nella versione DB-Library di **bcp_control** e 10 nella versione di ODBC. Nelle applicazioni DB-Library che dipendono dall'impostazione predefinita pari a 0 per terminare un'operazione di copia bulk devono essere modificate per chiamare ODBC **bcp_control** per impostare su 0 BCPMAXERRS.  
  
-   ODBC **bcp_control** funzione supporta le seguenti opzioni non supportate dalla versione DB-Library di **bcp_control**:  
  
    -   BCPODBC  
  
         Se impostato su TRUE, specifica che **datetime** e **smalldatetime** valori salvati in formato carattere avrà il prefisso di sequenza escape timestamp ODBC e il suffisso. Si applica solo alle operazioni BCP_OUT.  
  
         Bcpodbc è impostato su FALSE, un **datetime** valore convertito in una stringa di caratteri viene restituito come:  
  
        ```  
        1997-01-01 00:00:00.000  
        ```  
  
         Bcpodbc è impostato su TRUE, lo stesso **datetime** valore viene restituito come:  
  
        ```  
        {ts '1997-01-01 00:00:00.000' }  
        ```  
  
    -   BCPKEEPIDENTITY  
  
         Quando è impostato su TRUE, specifica che le funzioni di copia bulk inseriscono i valori dei dati forniti per le colonne con vincoli di identità. Se questa impostazione non è disponibile, per le righe inserite vengono generati nuovi valori Identity.  
  
    -   BCPHINTS  
  
         Specifica le varie ottimizzazioni della copia bulk. Questa opzione non può essere utilizzata nella versione 6.5 o nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   BCPFILECP  
  
         Specifica la tabella codici del file di copia bulk.  
  
    -   BCPUNICODEFILE  
  
         Specifica che un file di copia bulk in modalità carattere è un file Unicode.  
  
-   ODBC **bcp_colfmt** funzione non supporta il *file_type* indicatore di SQLCHAR perché è in conflitto con il typedef di ODBC SQLCHAR. Utilizzare invece SQLCHARACTER per **bcp_colfmt**.  
  
-   Nelle versioni ODBC delle funzioni di copia bulk, il formato per l'utilizzo di **datetime** e **smalldatetime** valori in stringhe di caratteri è il formato ODBC yyyy-mm-dd hh:mm:ss. **smalldatetime** valori utilizzano il formato ODBC yyyy-mm-dd hh:mm:ss.  
  
     Le versioni DB-Library di funzioni di copia bulk accettano **datetime** e **smalldatetime** valori nelle stringhe di caratteri con diversi formati:  
  
    -   Il formato predefinito è *mmm gg aaaa hh: mmxx* in *xx* AM o PM.  
  
    -   **DateTime** e **smalldatetime** in qualsiasi formato supportato da DB-Library stringhe di caratteri **dbconvert** (funzione).  
  
    -   Quando il **Usa impostazioni internazionali** in DB-Library è selezionata la casella di **opzioni** scheda della finestra di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilità di rete del Client, le funzioni di copia bulk di DB-Library accettano anche le date in locale formato di data definito per le impostazioni locali del Registro di sistema di computer client.  
  
     Le funzioni di copia bulk di DB-Library non accettano ODBC **datetime** e **smalldatetime** formati.  
  
     Se l'attributo dell'istruzione SQL_SOPT_SS_REGIONALIZE è impostato su SQL_RE_ON, le funzioni di copia bulk ODBC accettano il formato di data locale definito per le impostazioni locali del Registro di sistema del computer client.  
  
-   In caso di output **money** valori in formato carattere, ODBC bulk copia funzioni forniscono quattro cifre di precisione e nessun separatore virgola; Le versioni DB-Library solo forniscono a due cifre di precisione e includono i separatori virgola.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di operazioni di copia Bulk &#40; ODBC &#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)   
 [Funzioni di copia bulk](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
