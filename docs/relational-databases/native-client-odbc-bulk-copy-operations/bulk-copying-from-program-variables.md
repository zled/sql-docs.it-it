---
title: Copia bulk da variabili di programma | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-bulk-copy-operations
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], program variables
- bcp_bind function
- mapping data types [ODBC]
- SQL Server Native Client ODBC driver, bulk copy
- data types [ODBC], bulk copying
- ODBC, bulk copy operations
- program variables [ODBC]
ms.assetid: e4284a1b-7534-4b34-8488-b8d05ed67b8c
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5f00c8542691fcbdd66e5a35151161b3a901f439
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="bulk-copying-from-program-variables"></a>Copia bulk da variabili di programma
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  È possibile eseguire una copia bulk direttamente dalle variabili di programma. Dopo aver allocato le variabili per contenere i dati per una riga e una chiamata [bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) per avviare la copia bulk, chiamare [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) per ogni colonna specificare il percorso e il formato della variabile di programma da associare con la colonna. Completare ogni variabile con i dati, quindi chiamare [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) per inviare una riga di dati al server. Ripetere il processo di compilazione le variabili e la chiamata **bcp_sendrow** fino a quando tutte le righe sono state inviate al server, quindi chiamare [bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md) per specificare che l'operazione è stata completata.  
  
 Il **bcp_bind * * * pData* parametro contiene l'indirizzo della variabile da associare alla colonna. I dati di ogni colonna possono essere archiviati in due modi:  
  
-   Allocando una variabile in modo da contenere i dati.  
  
-   Allocando una variabile indicatore seguita immediatamente dalla variabile dati.  
  
 La variabile indicatore indica la lunghezza dei dati per le colonne a lunghezza variabile e indica inoltre i valori NULL se la colonna ammette valori NULL. Se solo una variabile di dati viene utilizzata, l'indirizzo di questa variabile viene archiviato nel **bcp_bind * * * pData* parametro. Se viene utilizzata una variabile indicatore, l'indirizzo della variabile indicatore verrà archiviato nel **bcp_bind * * * pData* parametro. Le funzioni di copia bulk calcolano il percorso della variabile dati aggiungendo il **bcp_bind * * * cbIndicator* e *pData* parametri.  
  
 **bcp_bind** supporta tre metodi per la gestione di dati a lunghezza variabile:  
  
-   Utilizzare *cbData* con solo una variabile di dati. Inserire la lunghezza dei dati in *cbData*. Ogni volta che la lunghezza dei dati per BULK copia, chiamare [bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)reimpostare *cbData*. Se viene utilizzato uno degli altri due metodi, specificare SQL_VARLEN_DATA per *cbData*. Se tutti i valori di dati specificati per una colonna sono NULL, specificare SQL_NULL_DATA per *cbData*.  
  
-   Utilizzare variabili indicatore. Non appena un nuovo valore dei dati viene spostato nella variabile dati, archiviare la lunghezza del valore nella variabile indicatore. Se viene utilizzato uno degli altri due metodi, specificare 0 per *cbIndicator*.  
  
-   Utilizzare i puntatori ai caratteri di terminazione. Caricamento di **bcp_bind * * * pTerm* parametro con l'indirizzo dello schema di bit che termina i dati. Se viene utilizzato uno degli altri due metodi, specificare NULL per *pTerm*.  
  
 Tutte e tre questi metodi possono essere utilizzati sulla stessa **bcp_bind** chiamare, nel qual caso in cui viene utilizzata la specifica che comporta la quantità minima di dati da copiare.  
  
 Il **bcp_bind * * * tipo* gli identificatori di tipo dati di parametro utilizza DB-Library, non identificatori di tipo dati ODBC. Gli identificatori di tipo di dati DB-Library vengono definiti in SQLNCLI. h per l'utilizzo con ODBC **bcp_bind** (funzione).  
  
 Le funzioni di copia bulk non supportano tutti i tipi di dati C ODBC. Ad esempio, le funzioni di copia bulk non supportano la struttura ODBC SQL_C_TYPE_TIMESTAMP, pertanto usare [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md) o [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) per convertire i dati ODBC SQL_TYPE_TIMESTAMP in una variabile SQL_C_CHAR. Se si utilizza quindi **bcp_bind** con un *tipo* parametro di SQLCHARACTER per associare la variabile a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime** convertono le funzioni di copia bulk di colonna, il clausola di escape timestamp nella variabile carattere nel formato datetime appropriato.  
  
 Nella tabella seguente sono elencati i tipi di dati consigliati da utilizzare nel mapping da un tipo di dati SQL ODBC a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.  
  
|Tipo di dati SQL ODBC|Tipo di dati C ODBC|bcp_bind *tipo* parametro|Tipo di dati di SQL Server|  
|-----------------------|----------------------|--------------------------------|--------------------------|  
|SQL_CHAR|SQL_C_CHAR|SQLCHARACTER|**character**<br /><br /> **char**|  
|SQL_VARCHAR|SQL_C_CHAR|SQLCHARACTER|**varchar**<br /><br /> **caratteri diversi**<br /><br /> **char varying**<br /><br /> **sysname**|  
|SQL_LONGVARCHAR|SQL_C_CHAR|SQLCHARACTER|**text**|  
|SQL_WCHAR|SQL_C_WCHAR|SQLNCHAR|**nchar**|  
|SQL_WVARCHAR|SQL_C_WCHAR|SQLNVARCHAR|**nvarchar**|  
|SQL_WLONGVARCHAR|SQL_C_WCHAR|SQLNTEXT|**ntext**|  
|SQL_DECIMAL|SQL_C_CHAR|SQLCHARACTER|**decimal**<br /><br /> **DEC**<br /><br /> **money**<br /><br /> **smallmoney**|  
|SQL_NUMERIC|SQL_C_NUMERIC|SQLNUMERICN|**numeric**|  
|SQL_BIT|SQL_C_BIT|SQLBIT|**bit**|  
|SQL_TINYINT (con segno)|SQL_C_SSHORT|SQLINT2|**smallint**|  
|SQL_TINYINT (senza segno)|SQL_C_UTINYINT|SQLINT1|**tinyint**|  
|SQL_SMALL_INT (con segno)|SQL_C_SSHORT|SQLINT2|**smallint**|  
|SQL_SMALL_INT (senza segno)|SQL_C_SLONG|SQLINT4|**int**<br /><br /> **integer**|  
|SQL_INTEGER (con segno)|SQL_C_SLONG|SQLINT4|**int**<br /><br /> **integer**|  
|SQL_INTEGER (senza segno)|SQL_C_CHAR|SQLCHARACTER|**decimal**<br /><br /> **DEC**|  
|SQL_BIGINT (con segno e senza segno)|SQL_C_CHAR|SQLCHARACTER|**bigint**|  
|SQL_REAL|SQL_C_FLOAT|SQLFLT4|**real**|  
|SQL_FLOAT|SQL_C_DOUBLE|SQLFLT8|**float**|  
|SQL_DOUBLE|SQL_C_DOUBLE|SQLFLT8|**float**|  
|SQL_BINARY|SQL_C_BINARY|SQLBINARY|**binary**<br /><br /> **timestamp**|  
|SQL_VARBINARY|SQL_C_BINARY|SQLBINARY|**varbinary**<br /><br /> **La variabile binario**|  
|SQL_LONGVARBINARY|SQL_C_BINARY|SQLBINARY|**image**|  
|SQL_TYPE_DATE|SQL_C_CHAR|SQLCHARACTER|**datetime**<br /><br /> **smalldatetime**|  
|SQL_TYPE_TIME|SQL_C_CHAR|SQLCHARACTER|**datetime**<br /><br /> **smalldatetime**|  
|SQL_TYPE_TIMESTAMP|SQL_C_CHAR|SQLCHARACTER|**datetime**<br /><br /> **smalldatetime**|  
|SQL_GUID|SQL_C_GUID|SQLUNIQUEID|**uniqueidentifier**|  
|SQL_INTERVAL_|SQL_C_CHAR|SQLCHARACTER|**char**|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non hanno effettuato **tinyint**senza segno **smallint**, o senza segno **int** tipi di dati. Per evitare la perdita di valori di dati durante la migrazione di questi tipi di dati, creare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella con il tipo di dati integer successivo più grande. Per impedire agli utenti di aggiungere in un secondo momento valori non compresi nell'intervallo consentito dal tipo di dati originale, applicare una regola alla colonna [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per limitare i valori consentiti all'intervallo supportato dal tipo di dati originale:  
  
```  
CREATE TABLE Sample_Ints(STinyIntCol   SMALLINT,  
USmallIntCol INT)  
GO  
CREATE RULE STinyInt_Rule  
AS   
@range >= -128 AND @range <= 127  
GO  
CREATE RULE USmallInt_Rule  
AS   
@range >= 0 AND @range <= 65535  
GO  
sp_bindrule STinyInt_Rule, 'Sample_Ints.STinyIntCol'  
GO  
sp_bindrule USmallInt_Rule, 'Sample_Ints.USmallIntCol'  
GO  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non supporta direttamente i tipi di dati di intervallo. Un'applicazione può, tuttavia, archiviare le sequenze di escape di intervallo come stringhe di caratteri in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] colonna di tipo carattere. Tali valori potranno essere letti dall'applicazione per un utilizzo futuro ma non potranno essere utilizzati nelle istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Le funzioni di copia bulk utilizzabile per caricare rapidamente i dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che è stato letto da un'origine dati ODBC. Utilizzare [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md) per associare le colonne del set di risultati a variabili di programma, quindi utilizzare **bcp_bind** per associare le stesse variabili di programma a un'operazione di copia bulk. La chiamata [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md) o **SQLFetch** viene quindi recuperata una riga di dati dall'origine dati ODBC nelle variabili di programma e chiamare il metodo [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) copia bulk dei dati dalle variabili di programma a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Un'applicazione può utilizzare il [bcp_colptr](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colptr.md) funzione ogni volta che è necessario modificare l'indirizzo della variabile dati specificata in origine il **bcp_bind** *pData* parametro. Un'applicazione può utilizzare il [bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) funzione ogni volta che è necessario modificare la lunghezza dei dati specificata in origine il **bcp_bind * * * cbData* parametro.  
  
 Non è possibile leggere dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nelle variabili di programma con la copia bulk; non c'è niente una funzione "bcp_readrow". È possibile solo inviare i dati dall'applicazione al server.  
  
## <a name="see-also"></a>Vedere anche  
 [L'esecuzione di operazioni di copia Bulk &#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
