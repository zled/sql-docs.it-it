---
title: Restituiscono codici di ODBC | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- return codes [ODBC]
- diagnostic information [ODBC], return codes
ms.assetid: e893b719-4392-476f-911a-5ed6da6f7e94
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 12751f87c9f9832567dc04ba7df7659e80e66897
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32913216"
---
# <a name="return-codes-odbc"></a>Codici restituiti ODBC
Ogni funzione ODBC restituisce un codice, noto come relativo *codice restituito,* che indica l'esito positivo o negativo della funzione complessivo. La logica del programma si basa generalmente sui codici restituiti.  
  
 Ad esempio, il codice seguente chiama **SQLFetch** per recuperare le righe in un set di risultati. Controlla il codice restituito della funzione per determinare se (SQL_NO_DATA), è stata raggiunta la fine del set di risultati se le informazioni di avviso è state restituite (SQL_SUCCESS_WITH_INFO) o se si è verificato un errore (SQL_ERROR).  
  
```  
SQLRETURN   rc;  
SQLHSTMT    hstmt;  
  
while ((rc=SQLFetch(hstmt)) != SQL_NO_DATA) {  
   if (rc == SQL_SUCCESS_WITH_INFO) {  
      // Call function to display warning information.  
   } else if (rc == SQL_ERROR) {  
      // Call function to display error information.  
      break;  
   }  
   // Process row.  
}  
```  
  
 Il codice restituito SQL_INVALID_HANDLE indica sempre un errore di programmazione e non dovrebbe essere mai rilevato in fase di esecuzione. Tutti gli altri codici restituiti forniscono informazioni di runtime, anche se SQL_ERROR potrebbe indicare un errore di programmazione.  
  
 Nella tabella seguente definisce i codici restituiti.  
  
|Codice restituito|Description|  
|-----------------|-----------------|  
|SQL_SUCCESS|Funzione completata. L'applicazione chiama **SQLGetDiagField** per recuperare informazioni aggiuntive da record di intestazione.|  
|SQL_SUCCESS_WITH_INFO|Funzione è stata completata correttamente, possibilmente con un errore non irreversibile (avviso). L'applicazione chiama **SQLGetDiagRec** o **SQLGetDiagField** per recuperare informazioni aggiuntive.|  
|SQL_ERROR|Funzione non riuscita. L'applicazione chiama **SQLGetDiagRec** o **SQLGetDiagField** per recuperare informazioni aggiuntive. Il contenuto di tutti gli argomenti di output per la funzione è indefinito.|  
|SQL_INVALID_HANDLE|Funzione non riuscita a causa di un handle di ambiente, connessione, istruzione o descrittore non valido. Ciò indica un errore di programmazione. Nessuna informazione aggiuntiva disponibile da **SQLGetDiagRec** o **SQLGetDiagField**. Questo codice viene restituito solo quando l'handle è un puntatore null o è di tipo non corretto, ad esempio quando un handle di istruzione viene passato un argomento che richiede un handle di connessione.|  
|SQL_NO_DATA|Nessun altro dato era disponibile. L'applicazione chiama **SQLGetDiagRec** o **SQLGetDiagField** per recuperare informazioni aggiuntive. Uno o più record di stato definito dal driver nella classe 02xxx possono essere restituiti. **Nota:** In ODBC 2. *x*, questo restituito il codice è stato denominato SQL_NO_DATA_FOUND.|  
|SQL_NEED_DATA|Sono necessari più dati, ad esempio l'invio di dati del parametro in fase di esecuzione o sono necessarie informazioni di connessione aggiuntive. L'applicazione chiama **SQLGetDiagRec** o **SQLGetDiagField** per recuperare informazioni aggiuntive, se presente.|  
|SQL_STILL_EXECUTING|Una funzione che è stata avviata in modo asincrono è ancora in esecuzione. L'applicazione chiama **SQLGetDiagRec** o **SQLGetDiagField** per recuperare informazioni aggiuntive, se presente.|
