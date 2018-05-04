---
title: Funzione SQLDriverToDataSource | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLDriverToDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDriverToDataSource
helpviewer_keywords:
- SQLDriverToDataSource function [ODBC]
ms.assetid: 0de28eb5-8aa9-43e4-a87f-7dbcafe800dc
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 996b2a717933f9e7da1cd16ffd39f8bf40156642
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqldrivertodatasource-function"></a>SQLDriverToDataSource (funzione)
**SQLDriverToDataSource** supporta le traduzioni per i driver ODBC. Questa funzione non viene chiamata dalle applicazioni basate su ODBC; le applicazioni richiedono traduzione attraverso **SQLSetConnectAttr**. Il driver associato il *ConnectionHandle* specificato in **SQLSetConnectAttr** chiama la DLL specificata per eseguire conversioni di tutti i dati che passano dal driver per l'origine dati. Una DLL di conversione predefinita può essere specificato nel file di inizializzazione di ODBC.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL SQLDriverToDataSource(  
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
 [Input] Il tipo di dati SQL ODBC. Questo argomento indica al driver come convertire *rgbValueIn* in un formato accettabile dall'origine dati. Per un elenco dei tipi di dati SQL validi, vedere [tipi di dati SQL](../../../odbc/reference/appendixes/sql-data-types.md).  
  
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
 Il driver chiama **SQLDriverToDataSource** per convertire tutti i dati (istruzioni SQL, parametri e così via) passando dal driver per l'origine dati. DLL di conversione non può convertire alcuni dati, in base al tipo dei dati e lo scopo della DLL di conversione. Ad esempio, una DLL che converte i dati di tipo carattere da una tabella codici a altra ignora tutti i dati numerici e binari.  
  
 Il valore di *fOption* è impostata sul valore di *vParam* specificato chiamando **SQLSetConnectAttr** con l'attributo SQL_ATTR_TRANSLATE_OPTION. È un valore a 32 bit che ha un significato specifico per una determinata DLL di conversione. Ad esempio, è possibile specificare che un determinato set di caratteri traduzione.  
  
 Se viene specificato lo stesso buffer per *rgbValueIn* e *rgbValueOut*, verrà eseguita la conversione dei dati nel buffer sul posto.  
  
 Sebbene *cbValueIn*, *cbValueOutMax*, e *pcbValueOut* sono di tipo SDWORD, **SQLDriverToDataSource** non necessariamente supporta i puntatori di grandi dimensioni.  
  
 Se **SQLDriverToDataSource** restituisce FALSE, il troncamento dei dati sono stati generati durante la conversione. Se *pcbValueOut* (il numero di byte disponibili da restituire nel buffer di output) è maggiore di *cbValueOutMax* (la lunghezza del buffer di output), quindi sono stati troncati. Il driver deve determinare se il troncamento è accettabile. Se non è possibile eseguire il troncamento, il **SQLDriverToDataSource** ha restituito FALSE a causa di un altro errore. In entrambi i casi, viene restituito un messaggio di errore specifico *szErrorMsg*.  
  
 Per ulteriori informazioni sulla conversione di dati, vedere [traduzione DLL](../../../odbc/reference/develop-app/translation-dlls.md).  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Convertendo i dati restituiti dall'origine dati|[SQLDataSourceToDriver](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|  
|Restituisce l'impostazione di un attributo di connessione|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|L'impostazione di un attributo di connessione|[Funzione SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
