---
title: Funzione SQLDrivers | Documenti Microsoft
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
apiname: SQLDrivers
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLDrivers
helpviewer_keywords: SQLDrivers function [ODBC]
ms.assetid: 6b5b7514-e9cb-4cfd-8b7a-ab51dfab9efa
caps.latest.revision: "23"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ad4afa4a54b63b759b03774f77ed7ec0371ff931
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqldrivers-function"></a>Funzione SQLDrivers
**Conformità**  
 Introdotta: versione ODBC 2.0 aderenza: ODBC  
  
 **Riepilogo**  
 **SQLDrivers** Elenca le descrizioni di driver e parole chiave di attributo del driver. Questa funzione è implementata solo da Gestione Driver.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLDrivers(  
     SQLHENV         EnvironmentHandle,  
     SQLUSMALLINT    Direction,  
     SQLCHAR *       DriverDescription,  
     SQLSMALLINT     BufferLength1,  
     SQLSMALLINT *   DescriptionLengthPtr,  
     SQLCHAR *       DriverAttributes,  
     SQLSMALLINT     BufferLength2,  
     SQLSMALLINT *   AttributesLengthPtr);  
```  
  
## <a name="arguments"></a>Argomenti  
 *EnvironmentHandle*  
 [Input] Handle di ambiente.  
  
 *Direzione*  
 [Input] Determina se il Driver Manager recupera la descrizione del driver successiva nell'elenco (SQL_FETCH_NEXT) o se la ricerca ha inizio dall'inizio dell'elenco (SQL_FETCH_FIRST).  
  
 *DriverDescription*  
 [Output] Puntatore a un buffer in cui si desidera restituire la descrizione del driver.  
  
 Se *DriverDescription* è NULL, *DescriptionLengthPtr* continuerà a restituire il numero totale di caratteri (escluso il carattere di terminazione null per i dati di tipo carattere) disponibile per restituire il buffer a cui puntava *DriverDescription*.  
  
 *BufferLength1*  
 [Input] Lunghezza di **DriverDescription* buffer, in caratteri.  
  
 *DescriptionLengthPtr*  
 [Output] Puntatore a un buffer in cui restituire il numero totale di caratteri (escluso il carattere di terminazione null) disponibile per restituire \* *DriverDescription*. Se il numero di caratteri disponibili da restituire è maggiore o uguale a *BufferLength1*, la descrizione del driver nella \* *DriverDescription* viene troncato a  *BufferLength1* meno la lunghezza di un carattere di terminazione null.  
  
 *DriverAttributes*  
 [Output] Puntatore a un buffer in cui restituire l'elenco di coppie di valore dell'attributo del driver (vedere "Commenti").  
  
 Se *DriverAttributes* è NULL, *AttributesLengthPtr* continuerà a restituire il numero totale di byte (escluso il carattere di terminazione null per i dati di tipo carattere) disponibile da restituire nel buffer a cui puntava *DriverAttributes*.  
  
 *BufferLength2*  
 [Input] Lunghezza di \* *DriverAttributes* buffer, in caratteri. Se il  *\*DriverDescription* valore è una stringa Unicode (quando si chiama **SQLDriversW**), il *BufferLength* argomento deve essere un numero pari.  
  
 *AttributesLengthPtr*  
 [Output] Puntatore a un buffer in cui restituire il numero totale di byte (escluso il byte di terminazione null) disponibile per restituire \* *DriverAttributes*. Se il numero di byte disponibili da restituire è maggiore o uguale a *BufferLength2*, l'elenco di coppie di valore di attributo in \* *DriverAttributes* viene troncato a  *BufferLength2* meno la lunghezza del carattere di terminazione null.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLDrivers** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato può essere ottenuto chiamando **SQLGetDiagRec** con un *HandleType* di Impostato su SQL_HANDLE_ENV e *gestire* di *EnvironmentHandle*. Nella tabella seguente sono elencati i valori SQLSTATE normalmente restituiti dal **SQLDrivers** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|(DM) messaggio informativo di gestione Driver specifico. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01004|Stringa di dati corretto troncato|(DM) buffer \* *DriverDescription* non sia abbastanza grande per restituire la descrizione completa del driver. Pertanto, la descrizione è stata troncata. Viene restituita la lunghezza della descrizione del driver completo \* *DescriptionLengthPtr*. (Funzione restituisce SQL_SUCCESS_WITH_INFO).<br /><br /> (DM) buffer \* *DriverAttributes* non sia abbastanza grande per restituire l'elenco completo di coppie valore dell'attributo. Pertanto, l'elenco è stato troncato. Viene restituita la lunghezza dell'elenco di coppie valore attributo non troncato **AttributesLengthPtr*. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel  *\*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Impossibile allocare la memoria che è necessario per supportare l'esecuzione o il completamento della funzione (DM) il Driver Manager.|  
|HY010|Errore nella sequenza (funzione)|(DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** è stato chiamato per il *StatementHandle* e restituito SQL_PARAM_DATA_ È DISPONIBILE. Questa funzione è stata chiamata prima che i dati sono stati recuperati per tutti i parametri con flusso.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY090|Lunghezza di stringa o di buffer non valida|(DM) il valore specificato per l'argomento *BufferLength1* era minore di 0.<br /><br /> (DM) il valore specificato per l'argomento *BufferLength2* è minore di 0 o uguale a 1.|  
|HY103|Codice di recupero non valido|(DM) il valore specificato per l'argomento *direzione* non è uguale a SQL_FETCH_FIRST o SQL_FETCH_NEXT.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
  
## <a name="comments"></a>Commenti  
 **SQLDrivers** restituisce la descrizione del driver nel \* *DriverDescription* buffer. Restituisce informazioni aggiuntive sul driver nel \* *DriverAttributes* buffer come un elenco di coppie valore-parola chiave. Tutte le parole chiave elencate nelle informazioni di sistema per il driver verranno restituiti per tutti i driver, ad eccezione di **CreateDSN**, che viene usato per richiedere la creazione di origini dati e sono pertanto facoltativi. Ogni coppia è terminata con un byte null e l'elenco completo è terminato con un byte null (ovvero, due byte null contrassegnano la fine dell'elenco). Ad esempio, un driver basati su file usando la sintassi C potrebbe restituire il seguente elenco di attributi ("\0" rappresenta un carattere null):  
  
```  
FileUsage=1\0FileExtns=*.dbf\0\0  
```  
  
 Se \* *DriverAttributes* è non sufficientemente grande da contenere l'intero elenco, l'elenco viene troncato, **SQLDrivers** restituisce SQLSTATE 01004 (dati troncati) e la lunghezza dell'elenco (escluso il byte finali di terminazione null) viene restituito in **AttributesLengthPtr*.  
  
 Parole chiave di attributo driver vengono aggiunti dalle informazioni di sistema quando viene installato il driver. Per ulteriori informazioni, vedere [installazione dei componenti ODBC](../../../odbc/reference/install/installing-odbc-components.md).  
  
 Un'applicazione può chiamare **SQLDrivers** più volte per recuperare tutte le descrizioni dei driver. Gestione Driver recupera informazioni dalle informazioni di sistema. Quando sono non presenti più descrizioni dei driver, **SQLDrivers** restituisce SQL_NO_DATA. Se **SQLDrivers** viene chiamato con SQL_FETCH_NEXT immediatamente dopo che viene restituito SQL_NO_DATA, restituisce la prima descrizione del driver. Per informazioni su come un'applicazione utilizza le informazioni restituite da **SQLDrivers**, vedere [scelta di un'origine dati o il Driver](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 Se viene passato SQL_FETCH_NEXT **SQLDrivers** alla prima chiamata, **SQLDrivers** restituisce il primo nome origine dati.  
  
 Poiché **SQLDrivers** viene implementato in Gestione Driver, è supportata per tutti i driver indipendentemente dalla conformità agli standard del driver specifico.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Individuazione e l'elenco di valori necessari per connettersi a un'origine dati|[Funzione SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Connessione a un'origine dati|[Funzione SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Restituisce i nomi delle origini dati|[Funzione SQLDataSources](../../../odbc/reference/syntax/sqldatasources-function.md)|  
|Connessione a un'origine dati tramite una connessione stringa o una finestra di dialogo|[Funzione SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
