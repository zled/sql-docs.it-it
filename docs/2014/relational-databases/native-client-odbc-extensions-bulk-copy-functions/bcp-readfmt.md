---
title: bcp_readfmt | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- bcp_readfmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_readfmt function
ms.assetid: 654001c8-ae9f-425c-b820-f0191bf89367
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dbf545e694ac6d5368a4abf23aba6ca0a6d32119
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37428730"
---
# <a name="bcpreadfmt"></a>bcp_readfmt
  Legge una definizione di formato di file di dati dal file di formato specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RETCODE bcp_readfmt (  
HDBC   
hdbc  
,  
LPCTSTR   
szFormatFile  
);  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *HDBC*  
 Handle di connessione ODBC abilitato per la copia bulk.  
  
 *szFormatFile*  
 Percorso e nome del file contenente i valori di formato per il file di dati.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SUCCEED o FAIL.  
  
## <a name="remarks"></a>Note  
 Dopo aver `bcp_readfmt` legge i valori di formato, effettua le chiamate appropriate a [bcp_columns](bcp-columns.md) e [bcp_colfmt](bcp-colfmt.md). L'utente può evitare di analizzare un file di formato ed effettuare queste chiamate.  
  
 Per rendere persistente un file di formato, chiamare [bcp_writefmt](bcp-writefmt.md). Le chiamate a `bcp_readfmt` può fare riferimento ai formati salvati. Per altre informazioni, vedere [bcp_init](bcp-init.md).  
  
 In alternativa, l'utilità di copia bulk (**bcp**) può salvare i formati di dati definito dall'utente nei file che possono essere utilizzati dalle `bcp_readfmt`. Per altre informazioni sul **bcp** utilità e la struttura dei **bcp** i file di formato di dati, vedere [l'importazione ed esportazione dei dati &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md).  
  
 Il `BCPDELAYREADFMT` pari al *eOption* parametro dei [bcp_control](bcp-control.md) modifica il comportamento di bcp_readfmt.  
  
> [!NOTE]  
>  Il file di formato è stato prodotto dalla versione 4.2 o versione successiva del **bcp** utilità.  
  
## <a name="example"></a>Esempio  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
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
if (bcp_init(hdbc, _T("myTable"), _T("myData.csv"),  
   _T("myErrors"),    DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_readfmt(hdbc, _T("myFmtFile.fmt")) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_exec(hdbc, &nRowsProcessed) == SUCCEED)  
   {  
   cout << nRowsProcessed << " rows copied to SQL Server\n";  
   }  
  
// Carry on.  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di copia bulk](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
