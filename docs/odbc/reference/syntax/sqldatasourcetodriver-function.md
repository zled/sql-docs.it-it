---
title: Funzione SQLDataSourceToDriver | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLDataSourceToDriver
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDataSourceToDriver
helpviewer_keywords:
- SQLDataSourceToDriver function [ODBC]
ms.assetid: 0d87fcac-30a0-4303-ad8f-a5b53f4b428d
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4d09d649bc53a08ff7389413882bb338d9713ffc
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqldatasourcetodriver-function"></a>SQLDataSourceToDriver (funzione)
**SQLDataSourceToDriver** supportstranslations per driver ODBC. Questa funzione non viene chiamata dalle applicazioni basate su ODBC; le applicazioni richiedono traduzione attraverso **SQLSetConnectAttr**. Il driver associato il *ConnectionHandle* specificato in **SQLSetConnectAttr** chiama la DLL specificata per eseguire conversioni di tutti i dati che passano dall'origine dati per il driver. Una DLL di conversione predefinita può essere specificato nel file di inizializzazione di ODBC.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL SQLDataSourceToDriver(  
     UDWORD     fOption,  
     SWORD      fSqlType,  
     PTR        rgbValueIn,  
     SDWORD     cbValueIn,  
     PTR        rgbValueOut,  
     SDWORD     cbValueOutMax,  
     SDWORD *   pcbValueOut,  
     UCHAR *    szErrorMsg,  
     SWORD      cbErrorMsgMax,  
     SWORD *    pcbErrorMsg);  
```  
  
## <a name="arguments"></a>Argomenti  
 *fOption*  
 [Input] Valore dell'opzione.  
  
 *fSqlType*  
 [Input] Il tipo di dati SQL. Questo argomento indica al driver come convertire *rgbValueIn* in un formato accettabile per l'applicazione. Per un elenco dei tipi di dati SQL validi, vedere il [tipi di dati SQL](../../../odbc/reference/appendixes/sql-data-types.md) sezione Appendice d: tipo di dati.  
  
 *rgbValueIn*  
 [Input] Valore da convertire.  
  
 *cbValueIn*  
 [Input] Lunghezza di *rgbValueIn*.  
  
 *rgbValueOut*  
 [Output] Risultato della conversione.  
  
> [!NOTE]  
>  DLL di conversione non null terminare questo valore.  
  
 *cbValueOutMax*  
 [Input] Lunghezza di *rgbValueOut*.  
  
 *pcbValueOut*  
 [Output] Il numero totale di byte (escluso il byte di terminazione null) disponibile per restituire *rgbValueOut*.  
  
 Per dati carattere o binario, se è maggiore di o uguale a *cbValueOutMax*, i dati in *rgbValueOut* viene troncato a *cbValueOutMax* byte.  
  
 Per tutti gli altri tipi di dati, il valore di *cbValueOutMax* viene ignorato e la DLL di conversione si presuppone che le dimensioni di *rgbValueOut* è la dimensione del tipo di dati C predefinito del tipo di dati SQL specificato con *fSqlType*.  
  
 Il *pcbValueOut* argomento può essere un puntatore null.  
  
 *szErrorMsg*  
 [Output] Puntatore alla risorsa di archiviazione per un messaggio di errore. Si tratta di una stringa vuota, a meno che la conversione non riuscita.  
  
 *cbErrorMsgMax*  
 [Input] Lunghezza di *szErrorMsg*.  
  
 *pcbErrorMsg*  
 [Output] Puntatore al numero totale di byte (escluso il byte di terminazione null) disponibile per restituire *szErrorMsg*. Se questo è maggiore o uguale a *cbErrorMsg*, i dati in *szErrorMsg* viene troncato a *cbErrorMsgMax* meno il carattere di terminazione null. Il *pcbErrorMsg* argomento può essere un puntatore null.  
  
## <a name="returns"></a>Valori di codice restituiti  
 TRUE se la conversione ha avuto esito positivo, FALSE se la conversione non è riuscita.  
  
## <a name="comments"></a>Commenti  
 Il driver chiama **SQLDataSourceToDriver** tradurre alldata (dati del set di risultati, i nomi di tabella, i conteggi delle righe, i messaggi di errore e così via) di passaggio dei dati di origine al driver. DLL di conversione non può convertire alcuni dati, in base al tipo dei dati e lo scopo della traduzione DLL. ad esempio, una DLL che converte i dati di tipo carattere da una tabella codici a altra ignora tutti i dati numerici e binari.  
  
 Il valore di *fOption* è impostata sul valore di *vParam* specificato chiamando **SQLSetConnectAttr** con l'attributo SQL_ATTR_TRANSLATE_OPTION. È un valore a 32 bit che ha un significato specifico per una determinata DLL di conversione. Ad esempio, è possibile specificare che un determinato set di caratteri traduzione.  
  
 Se viene specificato lo stesso buffer per *rgbValueIn* e *rgbValueOut*, verrà eseguita la conversione dei dati nel buffer sul posto.  
  
 Sebbene *cbValueIn*, *cbValueOutMax*, e *pcbValueOut* sono di tipo SDWORD, **SQLDataSourceToDriver** non necessariamente supporta i puntatori di grandi dimensioni.  
  
 Se **SQLDataSourceToDriver** restituisce FALSE, il troncamento dei dati sono stati generati durante la conversione. Se *pcbValueOut* (il numero di byte disponibili da restituire nel buffer di output) è maggiore di *cbValueOutMax* (la lunghezza del buffer di output), quindi sono stati troncati. Il driver deve determinare se il troncamento è stato accettato. Se non è possibile eseguire il troncamento, il **SQLDataSourceToDriver** ha restituito FALSE a causa di un altro errore. In entrambi i casi, viene restituito un messaggio di errore specifico *szErrorMsg*.  
  
 Per ulteriori informazioni sulla conversione di dati, vedere [traduzione DLL](../../../odbc/reference/develop-app/translation-dlls.md).  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Conversione di dati inviati all'origine dati|[SQLDriverToDataSource](../../../odbc/reference/syntax/sqldrivertodatasource-function.md)|  
|Restituisce l'impostazione di un attributo di connessione|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|L'impostazione di un attributo di connessione|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
