---
title: bcp_bind | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-extensions-bulk-copy-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: bcp_bind
apilocation: sqlncli11.dll
apitype: DLLExport
helpviewer_keywords: bcp_bind function
ms.assetid: 6e335a5c-64b2-4bcf-a88f-35dc9393f329
caps.latest.revision: "47"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9efa0570e0ffe698fccb7decb6eafbf5877842db
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="bcpbind"></a>bcp_bind
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Vengono associati dati provenienti da una variabile di programma a una colonna di tabella per eseguire la copia bulk in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RETCODE bcp_bind (  
        HDBC hdbc,   
        LPCBYTE pData,  
        INT cbIndicator,  
        DBINT cbData,  
        LPCBYTE pTerm,  
        INT cbTerm,  
        INT eDataType,  
        INT idxServerCol);  
```  
  
## <a name="arguments"></a>Argomenti  
 *HDBC*  
 Handle di connessione ODBC abilitato per la copia bulk.  
  
 *pData*  
 Puntatore ai dati copiati. Se *eDataType* è SQLTEXT, SQLNTEXT, SQLXML, SQLUDT, SQLCHARACTER, SQLVARCHAR, SQLVARBINARY, SQLBINARY, SQLNCHAR o SQLIMAGE, *pData* può essere NULL. Un valore NULL *pData* indica che i valori di dati long verranno inviati a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in blocchi mediante [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md). L'utente deve solo impostare *pData* su NULL se la colonna corrispondente al campo associato dell'utente è una colonna BLOB in caso contrario **bcp_bind** avrà esito negativo.  
  
 Se presenti nei dati, gli indicatori vengono visualizzati in memoria direttamente prima dei dati. Il *pData* punta alla variabile dell'indicatore in questo caso e la larghezza dell'indicatore di parametro di *cbIndicator* parametro, viene utilizzato dalla copia bulk di dati utente indirizzo correttamente.  
  
 *cbIndicator*  
 Lunghezza, espressa in byte, di un indicatore di lunghezza o Null per i dati della colonna. Valori di lunghezza di indicatore validi sono 0 (nel caso in cui non venga utilizzato un indicatore), 1, 2, 4 o 8. Gli indicatori vengono visualizzati in memoria direttamente prima di qualsiasi dato. La definizione del tipo di struttura seguente, ad esempio, potrebbe essere utilizzata per inserire valori integer in una tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mediante la copia bulk:  
  
```  
typedef struct tagBCPBOUNDINT  
    {  
    int iIndicator;  
    int Value;  
    } BCPBOUNDINT;  
```  
  
 Nel caso di esempio, il *pData* parametro viene impostato per l'indirizzo di un'istanza dichiarata della struttura, l'indirizzo di BCPBOUNDINT *iIndicator* membro della struttura. Il *cbIndicator* parametro viene impostato per la dimensione di un numero intero (sizeof e *cbData* parametro verrebbe impostato nuovamente le dimensioni di un numero intero (sizeof. Per la copia bulk il valore di una riga nel server che contiene un valore NULL per la colonna associata, il valore dell'istanza *iIndicator* membro deve essere impostato su SQL_NULL_DATA.  
  
 *cbData*  
 Numero di byte dei dati nella variabile di programma che non include la lunghezza di un carattere di terminazione o di un indicatore di lunghezza o Null.  
  
 Impostazione *cbData* su SQL_NULL_DATA indica che tutte le righe copiate nel server contengono un valore NULL per la colonna.  
  
 Impostazione *cbData* su SQL_VARLEN_DATA indica che il sistema utilizzerà un carattere di terminazione di stringa o altro metodo, per determinare la lunghezza dei dati copiati.  
  
 Per tipi di dati a lunghezza fissa, ad esempio numeri interi, il tipo di dati indica la lunghezza dei dati al sistema. Pertanto, per i tipi di dati a lunghezza fissa, *cbData* può essere SQL_VARLEN_DATA o la lunghezza dei dati.  
  
 Per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] caratteri e i tipi di dati binari, *cbData* può essere SQL_VARLEN_DATA, SQL_NULL_DATA, un valore positivo o 0. Se *cbData* è SQL_VARLEN_DATA, il sistema utilizza un indicatore di lunghezza o null (se presente) o una sequenza di caratteri di terminazione per determinare la lunghezza dei dati. Se vengono forniti entrambi, il sistema utilizza quello che comporta la copia del minori numero di dati. Se *cbData* è SQL_VARLEN_DATA, il tipo di dati della colonna è un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] carattere o binario e né un indicatore di lunghezza né una sequenza di caratteri di terminazione è specificata, il sistema restituisce un messaggio di errore.  
  
 Se *cbData* è 0 o un valore positivo, il sistema utilizza *cbData* come la lunghezza dei dati. Tuttavia, se, oltre a un valore positivo *cbData* valore, viene fornita un carattere di terminazione o di un indicatore di lunghezza sequenza, il sistema determina la lunghezza dei dati tramite il metodo che comporta la quantità minima di dati da copiare.  
  
 Il *cbData* valore del parametro rappresenta il numero di byte di dati. Se i dati di tipo carattere vengono rappresentati come caratteri wide Unicode, un numero positivo *cbData* valore del parametro rappresenta il numero di caratteri moltiplicato per la dimensione in byte di ogni carattere.  
  
 *pTerm*  
 Puntatore al modello di byte, se presente, che contrassegna la fine di questa variabile di programma. Le stringhe ANSI e MBCS C, ad esempio, presentano generalmente un carattere di terminazione di 1 byte (\0).  
  
 Se non è presente alcun carattere di terminazione per la variabile, impostare *pTerm* su NULL.  
  
 È possibile utilizzare una stringa vuota ("") per definire il carattere di terminazione Null C come carattere di terminazione della variabile di programma. Poiché la stringa vuota con terminazione null costituisce un singolo byte (il carattere di terminazione stesso), impostare *cbTerm* su 1. Ad esempio, per indicare che la stringa in *szName* è con terminazione null e che per indicare la lunghezza deve essere utilizzato il carattere di terminazione:  
  
```  
bcp_bind(hdbc, szName, 0,  
   SQL_VARLEN_DATA, "", 1,  
   SQLCHARACTER, 2)  
```  
  
 Un modulo di versione di questo esempio potrebbe indicare che 15 da copiati i caratteri di *szName* variabile alla seconda colonna della tabella associata:  
  
```  
bcp_bind(hdbc, szName, 0, 15,   
   NULL, 0, SQLCHARACTER, 2)  
```  
  
 L'API della copia bulk esegue la conversione dei caratteri da Unicode a MBCS in base alle necessità. Verificare che la stringa di byte del carattere di terminazione e la lunghezza della stringa di byte siano impostate correttamente. Ad esempio, per indicare che la stringa in *szName* è una stringa di caratteri wide Unicode terminata dal valore di carattere di terminazione null di Unicode:  
  
```  
bcp_bind(hdbc, szName, 0,   
   SQL_VARLEN_DATA, L"",  
   sizeof(WCHAR), SQLNCHAR, 2)  
```  
  
 Se il limite [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la colonna è un carattere wide, in cui viene eseguita alcuna conversione [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md). Se la colonna di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è un tipo di carattere MBCS, la conversione da carattere wide a carattere multibyte viene eseguita quando i dati vengono inviati a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *cbTerm*  
 Numero dei byte presenti nel carattere di terminazione per la variabile di programma, se presente. Se non è presente alcun carattere di terminazione per la variabile, impostare *cbTerm* su 0.  
  
 *eDataType*  
 Tipo di dati C della variabile di programma. I dati della variabile di programma vengono convertiti nel tipo della colonna di database. Se questo parametro è 0, non viene eseguita alcuna conversione.  
  
 Il *eDataType* parametro viene enumerato in base il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] token dei tipi di dati in SQLNCLI. h, non gli enumeratori tipo di dati C ODBC. È ad esempio possibile specificare un numero intero a due byte, SQL_C_SHORT di tipo ODBC, utilizzando il tipo specifico di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQLINT2.  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]stato introdotto il supporto per i token tipo dati SQLXML e SQLUDT nel ***eDataType*** parametro.  
  
 *idxServerCol*  
 Posizione ordinale della colonna nella tabella di database in cui vengono copiati i dati. La prima colonna di una tabella è la colonna 1. La posizione ordinale di una colonna è indicata da [SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md).  
  
## <a name="returns"></a>Valori di codice restituiti  
 SUCCEED o FAIL.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare **bcp_bind** per copiare i dati da una variabile di programma in una tabella in modo rapido ed efficace [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Chiamare [bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) prima di chiamare questa o qualsiasi altra funzione di copia bulk. La chiamata **bcp_init** imposta il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la tabella di destinazione per la copia bulk. Quando si chiama **bcp_init** per l'utilizzo con **bcp_bind** e [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md), **bcp_init** *szDataFile*parametro, che indica il file di dati è impostato su NULL. il **bcp_init * * * eDirection* parametro è impostato su DB_IN.  
  
 Rendere un apposito **bcp_bind** chiamato per ogni colonna di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella in cui si desidera copiare. Dopo aver necessari **bcp_bind** chiamate sono state apportate, quindi chiamare **bcp_sendrow** per inviare una riga di dati da variabili di programma a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La riassociazione della colonna non è supportata.  
  
 Ogni volta che si desidera [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per eseguire il commit delle righe già ricevute, chiamare [bcp_batch](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md). Ad esempio, chiamare **bcp_batch** una volta per ogni 1000 righe inserite o in un altro intervallo.  
  
 Quando non sono presenti altre righe da inserire, chiamare [bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md). In caso contrario, viene generato un errore.  
  
 Controllare le impostazioni di parametro, specificate con [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md), non hanno effetto sui **bcp_bind** trasferimenti di righe.  
  
 Se *pData* per una colonna è impostata su NULL perché il relativo valore verrà fornito dalle chiamate a [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md), tutte le colonne successive con *eDataType* impostato su SQLTEXT, SQLNTEXT, SQLXML, SQLUDT, SQLCHARACTER, SQLVARCHAR, SQLVARBINARY, SQLBINARY, SQLNCHAR o SQLIMAGE deve essere associate con *pData* impostato su NULL e i relativi valori devono anche essere forniti dalle chiamate a **bcp_moretext**.  
  
 Per i nuovi tipi di valori di grandi dimensioni, ad esempio **varchar (max)**, **varbinary (max)**, o **nvarchar (max)**, è possibile utilizzare SQLCHARACTER, SQLVARCHAR, SQLVARBINARY, SQLBINARY, e SQLNCHAR come indicatori di tipo nel *eDataType* parametro.  
  
 Se *cbTerm* è diverso da 0, qualsiasi valore (1, 2, 4 o 8) è valido per il prefisso (*cbIndicator*). In questo caso, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client verrà cercare il carattere di terminazione, calcolare la lunghezza dei dati rispetto al carattere di terminazione (*si*) e impostare il *cbData* sul valore più piccolo di i e il valore di prefisso.  
  
 Se *cbTerm* è 0 e *cbIndicator* (prefisso) non è 0, *cbIndicator* deve essere 8. Al prefisso a 8 byte possono essere assegnati i valori seguenti:  
  
-   0xFFFFFFFFFFFFFFFF indica un valore Null per il campo  
  
-   0xFFFFFFFFFFFFFFFE viene trattato come valore di prefisso speciale utilizzato per inviare dati in blocchi al server in modo efficace. Il formato dei dati con questo prefisso speciale è:  
  
-   < SPECIAL_PREFIX > \<0 o più BLOCCHI di dati >< ZERO_CHUNK > dove:  
  
-   SPECIAL_PREFIX è 0xFFFFFFFFFFFFFFFE  
  
-   DATA_CHUNK è un prefisso a 4 byte che contiene la lunghezza del blocco, seguita dai dati effettivi la cui lunghezza viene specificata nel prefisso a 4 byte.  
  
-   ZERO_CHUNK è un valore a 4 byte che contiene tutti zeri (00000000) che indicano la fine dei dati.  
  
-   Qualsiasi altra lunghezza a 8 byte valida viene trattata come una lunghezza dei dati normale.  
  
 La chiamata [bcp_columns](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) quando si utilizza **bcp_bind** genera un errore.  
  
## <a name="bcpbind-support-for-enhanced-date-and-time-features"></a>Supporto di bcp_bind per le caratteristiche avanzate di data e ora  
 Per informazioni sui tipi utilizzati con il *eDataType* parametro per i tipi di data/ora, vedere [modifiche di copia Bulk per avanzate di data e ora tipi &#40; OLE DB e ODBC &#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).  
  
 Per ulteriori informazioni, vedere [data e ora miglioramenti &#40; ODBC &#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="example"></a>Esempio  
  
```  
#include sql.h  
#include sqlext.h  
#include odbcss.h  
// Variables like henv not specified.  
HDBC      hdbc;  
char         szCompanyName[MAXNAME];  
DBINT      idCompany;  
DBINT      nRowsProcessed;  
DBBOOL      bMoreData;  
char*      pTerm = "\t\t";  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source; return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bcp.   
if (bcp_init(hdbc, "comdb..accounts_info", NULL, NULL  
   DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Bind program variables to table columns.   
if (bcp_bind(hdbc, (LPCBYTE) &idCompany, 0, sizeof(DBINT), NULL, 0,  
   SQLINT4, 1)    == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_bind(hdbc, (LPCBYTE) szCompanyName, 0, SQL_VARLEN_DATA,  
   (LPCBYTE) pTerm, strnlen(pTerm, sizeof(pTerm)), SQLCHARACTER, 2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
while (TRUE)  
   {  
   // Retrieve and process program data.   
   if ((bMoreData = getdata(&idCompany, szCompanyName)) == TRUE)  
      {  
      // Send the data.   
      if (bcp_sendrow(hdbc) == FAIL)  
         {  
         // Raise error and return.  
         return;  
         }  
      }  
   else  
      {  
      // Break out of loop.  
      break;  
      }  
   }  
  
// Terminate the bulk copy operation.  
if ((nRowsProcessed = bcp_done(hdbc)) == -1)  
   {  
   printf_s("Bulk-copy unsuccessful.\n");  
   return;  
   }  
  
printf_s("%ld rows copied.\n", nRowsProcessed);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di copia bulk](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
