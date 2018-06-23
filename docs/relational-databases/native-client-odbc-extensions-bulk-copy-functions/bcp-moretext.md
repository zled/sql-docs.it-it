---
title: bcp_moretext | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- bcp_moretext
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_moretext function
ms.assetid: 23e98015-a8e4-4434-9b3f-9c7350cf965f
caps.latest.revision: 39
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: edfe93e41d5a9398649550b10b11f6db64ca7afc
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2018
ms.locfileid: "35695772"
---
# <a name="bcpmoretext"></a>bcp_moretext
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Invia parte di un valore del tipo di dati Long a lunghezza variabile a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RETCODE bcp_moretext (  
        HDBC hdbc,  
        DBINT cbData,  
        LPCBYTE pData);  
```  
  
## <a name="arguments"></a>Argomenti  
 *HDBC*  
 Handle di connessione ODBC abilitato per la copia bulk.  
  
 *cbData*  
 È il numero di byte di dati copiati in SQL Server dai dati di cui fanno riferimento *pData*. Un valore di SQL_NULL_DATA indica NULL.  
  
 *pData*  
 Puntatore al blocco di dati Long a lunghezza variabile supportati da inviare a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="returns"></a>Valori di codice restituiti  
 SUCCEED o FAIL.  
  
## <a name="remarks"></a>Remarks  
 Questa funzione può essere utilizzata in combinazione con [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) e [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) long, copiare i valori di dati a lunghezza variabile a SQL Server in un numero di blocchi più piccoli. **bcp_moretext** può essere usato con colonne che dispongono dei seguenti tipi di dati di SQL Server: **testo**, **ntext**, **immagine**, **varchar (max)** , **nvarchar (max)**, **varbinary (max)**, tipo definito dall'utente (UDT) e XML. **bcp_moretext** non supporto le conversioni di dati, i dati forniti devono corrispondere al tipo di dati della colonna di destinazione.  
  
 Se **bcp_bind** viene chiamato con un valore non NULL *pData* parametro per i tipi di dati supportati da **bcp_moretext**, **bcp_sendrow** invia l'intero valore dei dati, indipendentemente dalla lunghezza. Se, tuttavia **bcp_bind** ha un valore NULL *pData* parametro per i tipi di dati supportati **bcp_moretext** può essere usato per copiare i dati immediatamente dopo una corretta restituzione da **bcp_sendrow** che indica che qualsiasi colonna associata contenente dati presenti è stati elaborati.  
  
 Se si utilizza **bcp_moretext** per l'invio di una colonna di tipo di dati supportati in una riga, è necessario anche utilizzarlo per inviare tutte le altre colonne di tipo di dati supportati nella riga. Non è possibile ignorare alcuna colonna. I tipi di dati supportati sono SQLTEXT, SQLNTEXT, SQLIMAGE, SQLUDT e SQLXML. Anche SQLCHARACTER, SQLVARCHAR, SQNCHAR, SQLBINARY e SQLVARBINARY rientrano in questa categoria se la colonna è di tipo varchar(max), nvarchar(max) o varbinary(max), rispettivamente.  
  
 Una chiamata a **bcp_bind** oppure [bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) imposta la lunghezza totale di tutte le parti di dati da copiare nella colonna di SQL Server. Un tentativo di inviare più byte rispetto a quanto specificato nella chiamata a SQL Server **bcp_bind** oppure **bcp_collen** genera un errore. Questo errore può essere causato, ad esempio, in un'applicazione che ha utilizzato **bcp_collen** per impostare la lunghezza dei dati disponibili per un Server SQL **testo** colonna a 4500, quindi chiamato **bcp_moretext** cinque volte durante il indicando in ogni chiamata che i dati di lunghezza del buffer pari a 1000 byte.  
  
 Se una riga copiata contiene più di una colonna a lunghezza variabile lunga **bcp_moretext** invia i dati a quello minimo numero esegue un confronto ordinale di colonna, seguita da quella successiva più basso numerato esegue un confronto ordinale di colonna e così via. Una corretta impostazione della lunghezza totale dei dati previsti è importante. Non è possibile segnalare, al di fuori dell'impostazione della lunghezza, che tutti i dati per una colonna sono stati ricevuti dalla copia bulk.  
  
 Quando si **var(max)** valori vengono inviati al server tramite bcp_sendrow e bcp_moretext, non è necessario chiamare bcp_collen per impostare la lunghezza della colonna. Al contrario, solo per questi tipi, il valore termina con bcp_sendrow chiamante con una lunghezza pari a zero.  
  
 Un'applicazione chiama in genere **bcp_sendrow** e **bcp_moretext** all'interno di cicli per inviare un numero di righe di dati. Di seguito è riportata una descrizione di come eseguire questa operazione per una tabella che contiene due **testo** colonne:  
  
```  
while (there are still rows to send)  
{  
bcp_sendrow(...);  
  
for (all the data in the first varbinary(max) column)  
bcp_moretext(...);  
bcp_moretext(hdbc, 0, NULL);  
  
for (all the data in the second varbinary(max) column)  
bcp_moretext(...);  
bcp_moretext(hdbc, 0, NULL);  
  
}  
  
```  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato come utilizzare **bcp_moretext** con **bcp_bind** e **bcp_sendrow**:  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
DBINT      idRow = 5;  
char*      pPart1 = "This text value isn't very long,";  
char*      pPart2 = " but it's broken into three parts";  
char*      pPart3 = " anyhow.";  
DBINT      cbAllParts;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, "comdb..articles", NULL, NULL, DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Bind program variables to table columns.   
if (bcp_bind(hdbc, (LPCBYTE) &idRow, 0, SQL_VARLEN_DATA, NULL, 0,  
   SQLINT4, 1)    == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
cbAllParts = (DBINT) (strnlen(pPart1, sizeof(pPart1) + 1) + strnlen(pPart2, sizeof(pPart2) + 1) + strnlen(pPart3, sizeof(pPart3) + 1));  
if (bcp_bind(hdbc, NULL, 0, cbAllParts, NULL, 0, SQLTEXT, 2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Send this row, with the text value broken into three chunks.   
if (bcp_sendrow(hdbc) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart1, sizeof(pPart1) + 1), pPart1) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart2, sizeof(pPart2) + 1), pPart2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart3, sizeof(pPart3) + 1), pPart3) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// All done. Get the number of rows processed (should be one).  
nRowsProcessed = bcp_done(hdbc);  
  
// Carry on.  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di copia bulk](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
