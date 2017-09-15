---
title: Esecuzione ODBC preparato | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- prepared execution [ODBC]
- SQL statements [ODBC], prepared execution
- SQL statements [ODBC], executing
ms.assetid: f08c8a98-31ee-48b2-9dbf-6f31c2166dbb
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d6b2437d1958e2583dabb75c0a4c26a2ed472975
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="prepared-execution-odbc"></a>Esecuzione preparata ODBC
Esecuzione preparata è un modo efficiente per eseguire un'istruzione più volte. L'istruzione viene innanzitutto compilata, o *preparati,* in un piano di accesso. Il piano di accesso viene quindi eseguito uno o più volte in un secondo momento. Per ulteriori informazioni sui piani di accesso, vedere [l'elaborazione di un'istruzione SQL](../../../odbc/reference/processing-a-sql-statement.md).  
  
 L'esecuzione preparata viene comunemente utilizzata dalle applicazioni personalizzate e verticale per eseguire ripetutamente la stessa istruzione SQL con parametri. Ad esempio, il codice seguente prepara un'istruzione per aggiornare i prezzi delle diverse parti. Viene quindi eseguita l'istruzione più volte con valori di parametro diversi ogni volta.  
  
```  
SQLREAL       Price;  
SQLUINTEGER   PartID;  
SQLINTEGER    PartIDInd = 0, PriceInd = 0;  
  
// Prepare a statement to update salaries in the Employees table.  
SQLPrepare(hstmt, "UPDATE Parts SET Price = ? WHERE PartID = ?", SQL_NTS);  
  
// Bind Price to the parameter for the Price column and PartID to  
// the parameter for the PartID column.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_FLOAT, SQL_REAL, 7, 0,  
                  &Price, 0, &PriceInd);  
SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 10, 0,  
                  &PartID, 0, &PartIDInd);  
  
// Repeatedly execute the statement.  
while (GetPrice(&PartID, &Price)) {  
   SQLExecute(hstmt);  
}  
```  
  
 L'esecuzione preparata è più veloce rispetto a esecuzione diretta per le istruzioni eseguite più volte, sopratutto perché l'istruzione viene compilata solo una volta. le istruzioni eseguite direttamente vengono compilate ogni volta che vengono eseguite. L'esecuzione preparata anche possibile fornire che una riduzione del traffico di rete perché il driver può inviare un identificatore del piano di accesso all'origine dati ogni volta che l'istruzione viene eseguita, anziché un'intera istruzione SQL, se l'accesso all'origine dati supporta prevede gli identificatori.  
  
 L'applicazione può recuperare i metadati per il gruppo di risultati dopo l'istruzione viene preparata e prima che venga eseguito. Tuttavia, restituzione dei metadati per preparati, non eseguite istruzioni è costose per alcuni driver e dovrebbero essere evitate dalla applicazioni interoperative, se possibile. Per ulteriori informazioni, vedere [metadati dei Set di risultati](../../../odbc/reference/develop-app/result-set-metadata.md).  
  
 L'esecuzione preparata non deve essere utilizzata per le istruzioni eseguite una sola volta. Per tali istruzioni, è leggermente più lento rispetto a esecuzione diretta perché richiede una chiamata di funzione ODBC aggiuntiva.  
  
> [!IMPORTANT]  
>  Eseguire il commit o il rollback di una transazione, in modo esplicito chiamando **SQLEndTran** o per lavorare in modalità autocommit, a causa di alcune origini dati eliminare i piani di accesso per tutte le istruzioni in una connessione. Per ulteriori informazioni, vedere le opzioni SQL_CURSOR_COMMIT_BEHAVIOR e SQL_CURSOR_ROLLBACK_BEHAVIOR il [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) descrizione della funzione.  
  
 Preparare ed eseguire un'istruzione, l'applicazione:  
  
1.  Chiamate **SQLPrepare** e lo passa a una stringa contenente l'istruzione SQL.  
  
2.  Imposta i valori dei parametri. I parametri effettivamente possono essere impostati prima o dopo la preparazione dell'istruzione. Per ulteriori informazioni, vedere [parametri dell'istruzione](../../../odbc/reference/develop-app/statement-parameters.md), più avanti in questa sezione.  
  
3.  Chiamate **SQLExecute** ed esegue un'elaborazione aggiuntiva che è necessaria, ad esempio il recupero dei dati.  
  
4.  Ripetere i passaggi da 2 e 3 in base alle esigenze.  
  
5.  Quando **SQLPrepare** viene chiamato, il driver:  
  
    -   Modifica l'istruzione SQL per l'utilizzo di grammatica SQL dell'origine dati senza analizzare l'istruzione. Questo include sostituendo le sequenze di escape descritte in [sequenze di Escape ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md). L'applicazione può recuperare il modulo di un'istruzione SQL modificato chiamando **SQLNativeSql**. Se è impostato l'attributo di istruzione SQL_ATTR_NOSCAN, le sequenze di escape non vengono sostituite.  
  
    -   Invia l'istruzione per l'origine dati per la preparazione.  
  
    -   Archivia l'identificatore del piano di accesso restituito per un'esecuzione successiva (se l'elaborazione ha avuto esito positivo) o restituisce eventuali errori (se le operazioni di preparazione non riuscita). Gli errori sono errori di sintassi, ad esempio SQLSTATE 42000 (sintassi o violazione di accesso) e gli errori semantici, ad esempio 42S02 SQLSTATE (Base tabella o vista non trovato).  
  
        > [!NOTE]  
        >  Alcuni driver non restituire errori a questo punto, ma invece restituirle quando viene eseguita l'istruzione o quando vengono chiamate le funzioni di catalogo. Di conseguenza, **SQLPrepare** può sembrare che hanno avuto esito positivo quando in realtà non è riuscito.  
  
6.  Quando **SQLExecute** viene chiamato, il driver:  
  
    -   Recupera i valori di parametro corrente e li converte in base alle esigenze. Per ulteriori informazioni, vedere [parametri dell'istruzione](../../../odbc/reference/develop-app/statement-parameters.md), più avanti in questa sezione.  
  
    -   Invia l'identificatore del piano di accesso e i valori di parametro convertito all'origine dati.  
  
    -   Restituisce gli eventuali errori. Si tratta di errori di runtime in genere, ad esempio SQLSTATE 24000 (stato del cursore non valido). Tuttavia, alcuni driver restituire errori sintattici e semantici a questo punto.  
  
 Se l'origine dati non supporta la preparazione, il driver deve emulare, per quanto possibile. Ad esempio, il driver potrebbe non eseguire alcuna operazione quando **SQLPrepare** viene chiamato e quindi eseguire l'esecuzione diretta dell'istruzione quando **SQLExecute** viene chiamato.  
  
 Se l'origine dati supporta il controllo senza l'esecuzione della sintassi, il driver potrebbe inviare l'istruzione per il controllo quando **SQLPrepare** viene chiamato e inviare l'istruzione per l'esecuzione quando **SQLExecute** è chiamato.  
  
 Se il driver non è possibile emulare preparazione dell'istruzione, archivia l'istruzione quando **SQLPrepare** viene chiamato e inviata per l'esecuzione quando **SQLExecute** viene chiamato.  
  
 Poiché non è perfetto, preparazione dell'istruzione emulata **SQLExecute** può restituire eventuali errori in genere restituiti da **SQLPrepare**.
