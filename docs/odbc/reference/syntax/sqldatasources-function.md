---
title: Funzione SQLDataSources | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLDataSources
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLDataSources
helpviewer_keywords: SQLDataSources function [ODBC]
ms.assetid: 3f63b1b4-e70e-44cd-96c6-6878d50d0117
caps.latest.revision: "22"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8aee3d9e1caa424f4792fb1fae0551adcacfcdc3
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqldatasources-function"></a>SQLDataSources (funzione)
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: 92 ISO  
  
 **Riepilogo**  
 **SQLDataSources** restituisce informazioni su un'origine dati. Questa funzione è implementata solo da Gestione Driver.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLDataSources(  
     SQLHENV          EnvironmentHandle,  
     SQLUSMALLINT     Direction,  
     SQLCHAR *        ServerName,  
     SQLSMALLINT      BufferLength1,  
     SQLSMALLINT *    NameLength1Ptr,  
     SQLCHAR *        Description,  
     SQLSMALLINT      BufferLength2,  
     SQLSMALLINT *    NameLength2Ptr);  
```  
  
## <a name="arguments"></a>Argomenti  
 *EnvironmentHandle*  
 [Input] Handle di ambiente.  
  
 *Direzione*  
 [Input] Determina l'origine dati di gestione Driver restituisce informazioni su. I possibili valori sono i seguenti:  
  
 SQL_FETCH_NEXT (per recuperare il nome dell'origine dati successivo nell'elenco), SQL_FETCH_FIRST (per il recupero dall'inizio dell'elenco), SQL_FETCH_FIRST_USER (per il DSN utente fetch il primo) o SQL_FETCH_FIRST_SYSTEM (per recuperare il primo DSN di sistema).  
  
 Quando *direzione* è impostato su SQL_FETCH_FIRST, le chiamate successive a **SQLDataSources** con *direzione* impostato su SQL_FETCH_NEXT restituire DSN utente e di sistema. Quando *direzione* è impostato su SQL_FETCH_FIRST_USER, tutte le chiamate successive a **SQLDataSources** con *direzione* impostato su SQL_FETCH_NEXT restituire solo i DSN utente. Quando *direzione* è impostato su SQL_FETCH_FIRST_SYSTEM, tutte le chiamate successive a **SQLDataSources** con *direzione* impostato su SQL_FETCH_NEXT restituire solo i DSN di sistema.  
  
 *ServerName*  
 [Output] Puntatore a un buffer in cui restituire il nome dell'origine dati.  
  
 Se *ServerName* è NULL, *NameLength1Ptr* continuerà a restituire il numero totale di caratteri (escluso il carattere di terminazione null per i dati di tipo carattere) disponibile da restituire nel buffer a cui fa riferimento *ServerName*.  
  
 *BufferLength1*  
 [Input] Lunghezza di **ServerName* buffer, in caratteri, questo non è necessario essere più lungo di SQL_MAX_DSN_LENGTH più il carattere di terminazione null.  
  
 *NameLength1Ptr*  
 [Output] Puntatore a un buffer in cui restituire il numero totale di caratteri (escluso il carattere di terminazione null) disponibile per restituire \* *ServerName*. Se il numero di caratteri disponibili da restituire è maggiore o uguale a *BufferLength1*, il nome dell'origine dati in \* *ServerName* viene troncato a *BufferLength1* meno la lunghezza di un carattere di terminazione null.  
  
 *Descrizione*  
 [Output] Puntatore a un buffer in cui si desidera restituire la descrizione del driver associato all'origine dati. Ad esempio, file dBASE o SQL Server.  
  
 Se *descrizione* è NULL, *NameLength2Ptr* continuerà a restituire il numero totale di caratteri (escluso il carattere di terminazione null per i dati di tipo carattere) disponibile da restituire nel buffer a cui fa riferimento *Descrizione*.  
  
 *BufferLength2*  
 [Input] Lunghezza in caratteri del **descrizione* buffer.  
  
 *NameLength2Ptr*  
 [Output] Puntatore a un buffer in cui restituire il numero totale di caratteri (escluso il carattere di terminazione null) disponibile per restituire \* *descrizione*. Se il numero di caratteri disponibili da restituire è maggiore o uguale a *BufferLength2*, la descrizione del driver nella \* *descrizione* viene troncato a *BufferLength2*  meno la lunghezza di un carattere di terminazione null.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLDataSources** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato può essere ottenuto chiamando **SQLGetDiagRec** con un *HandleType*impostato su SQL_HANDLE_ENV e *gestire* di *EnvironmentHandle*. Nella tabella seguente sono elencati i valori SQLSTATE normalmente restituiti dal **SQLDataSources** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|(DM) messaggio informativo di gestione Driver specifico. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01004|Stringa di dati corretto troncato|(DM) buffer \* *ServerName* non sia abbastanza grande per restituire il nome di origine di dati completo. Pertanto, il nome è stato troncato. Viene restituita la lunghezza del nome di origine tutti i dati \* *NameLength1Ptr*. (Funzione restituisce SQL_SUCCESS_WITH_INFO).<br /><br /> (DM) buffer \* *descrizione* non sia abbastanza grande per restituire la descrizione completa del driver. Pertanto, la descrizione è stata troncata. Viene restituita la lunghezza della descrizione dell'origine dati non troncato **NameLength2Ptr*. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|HY000|Errore generale|(DM) di un errore per cui si è verificato alcun errore SQLSTATE specifico per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel  *\*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Impossibile allocare la memoria che è necessario per supportare l'esecuzione o il completamento della funzione (DM) il Driver Manager.|  
|HY010|Errore nella sequenza (funzione)|(DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per il *StatementHandle* e restituito SQL_PARAM_DATA_ È DISPONIBILE. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY090|Lunghezza di stringa o di buffer non valida|(DM) il valore specificato per l'argomento *BufferLength1* era minore di 0.<br /><br /> (DM) il valore specificato per l'argomento *BufferLength2* era minore di 0.|  
|HY103|Codice di recupero non valido|(DM) il valore specificato per l'argomento *direzione* non è uguale a SQL_FETCH_FIRST, SQL_FETCH_FIRST_USER, SQL_FETCH_FIRST_SYSTEM o SQL_FETCH_NEXT.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
  
## <a name="comments"></a>Commenti  
 Poiché **SQLDataSources** viene implementato in Gestione Driver, è supportata per tutti i driver indipendentemente dalla conformità agli standard del driver specifico.  
  
 Un'applicazione può chiamare **SQLDataSources** più volte per recuperare tutti i nomi di origine dati. Gestione Driver recupera informazioni dalle informazioni di sistema. Quando non sono presenti più nomi di origine dati, gestione Driver restituisce SQL_NO_DATA. Se **SQLDataSources** viene chiamato con SQL_FETCH_NEXT immediatamente dopo che viene restituito SQL_NO_DATA, verrà restituito il primo nome origine dati. Per informazioni su come un'applicazione utilizza le informazioni restituite da **SQLDataSources**, vedere [scelta di un'origine dati o il Driver](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 Se viene passato SQL_FETCH_NEXT **SQLDataSources** alla prima chiamata, verrà restituito il primo nome origine dati.  
  
 Il driver determina la modalità di mapping dei nomi delle origini dati alle origini dei dati effettivi.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Individuazione e l'elenco di valori necessari per connettersi a un'origine dati|[Funzione SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Connessione a un'origine dati|[Funzione SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Connessione a un'origine dati tramite una connessione stringa o una finestra di dialogo|[Funzione SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Restituzione di attributi e le descrizioni di driver|[Funzione SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
