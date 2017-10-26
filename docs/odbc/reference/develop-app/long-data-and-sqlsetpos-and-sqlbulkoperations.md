---
title: Dati di tipo Long e SQLSetPos e SQLBulkOperations | Documenti Microsoft
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
- long data [ODBC]
- SQLSetPos function [ODBC], long data and SQLBulkOperations
- data updates [ODBC], long data
- updating data [ODBC], long data
- SQLBulkOperations function [ODBC], long data
ms.assetid: e2fdf842-5e4c-46ca-bb21-4625c3324f28
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 308e1ad6f2d99a0a6b7e73d8a82ac62362fea9a2
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="long-data-and-sqlsetpos-and-sqlbulkoperations"></a>Dati di tipo Long e SQLSetPos e SQLBulkOperations
Come accade con i parametri nelle istruzioni SQL, dati di tipo long possono essere inviati quando l'aggiornamento di righe con **SQLBulkOperations** o **SQLSetPos** o durante l'inserimento di righe con **SQLBulkOperations**. I dati vengono inviati in parti, con più chiamate a **SQLPutData**. Le colonne per cui i dati vengono inviati in fase di esecuzione sono noti come *colonne data-at-execution*.  
  
> [!NOTE]  
>  Un'applicazione in realtà può inviare qualsiasi tipo di dati in fase di esecuzione con **SQLPutData**, anche se solo i caratteri e i dati binari possono essere inviati in parti. Tuttavia, se i dati sono sufficientemente piccoli da rientrare in un unico buffer, non è in genere utilizzare **SQLPutData**. È molto più semplice associare il buffer e consentire il driver di recuperare i dati dal buffer.  
  
 Poiché le colonne di dati long non sono in genere associate, l'applicazione deve associare la colonna prima di chiamare **SQLBulkOperations** o **SQLSetPos** e annullare l'associazione dopo la chiamata **SQLBulkOperations ** o **SQLSetPos**. La colonna deve essere associata perché **SQLBulkOperations** o **SQLSetPos** funziona solo sulle colonne associate e deve essere associato in modo che **SQLGetData** può essere utilizzato per recuperare i dati dalla colonna.  
  
 Per inviare dati in fase di esecuzione, l'applicazione effettua quanto segue:  
  
1.  Inserisce un valore a 32 bit nel buffer di set di righe anziché un valore di dati. Questo valore verrà restituito all'applicazione in un secondo momento, pertanto l'applicazione deve impostare un valore significativo, ad esempio il numero della colonna o l'handle di un file contenente dati.  
  
2.  Imposta il valore nel buffer di lunghezza/indicatore al risultato di SQL_LEN_DATA_AT_EXEC (*lunghezza*) (macro). Questo valore indica al driver che verranno inviati con i dati per il parametro **SQLPutData**. Il *lunghezza* valore utilizzato durante l'invio di dati long a un'origine dati che è necessario conoscere il numero di byte di dati long verrà inviato in modo che è possibile preallocare spazio. Per determinare se un'origine dati richiede che questo valore, l'applicazione chiama **SQLGetInfo** con l'opzione SQL_NEED_LONG_DATA_LEN. Tutti i driver devono supportare questa macro. Se l'origine dati non richiede la lunghezza in byte, il driver può ignorata.  
  
3.  Chiamate **SQLBulkOperations** o **SQLSetPos**. Il driver rileva che un buffer di lunghezza/indicatore contiene il risultato di SQL_LEN_DATA_AT_EXEC (*lunghezza*) (macro) e restituisce SQL_NEED_DATA come valore restituito della funzione.  
  
4.  Chiamate **SQLParamData** restituito in risposta a di SQL_NEED_DATA. Se i dati di tipo long devono essere inviato, **SQLParamData** restituisce SQL_NEED_DATA. Nel buffer a cui fa riferimento il *ValuePtrPtr* argomento, il driver restituisce il valore univoco che l'applicazione inserito nel buffer di set di righe. Se è presente più di una colonna data-at-execution, l'applicazione utilizza questo valore per determinare la colonna per inviare i dati; il driver non è necessario per richiedere i dati per le colonne data-at-execution in un ordine particolare.  
  
5.  Chiamate **SQLPutData** per inviare i dati di colonna per il driver. Se i dati della colonna non rientrano in un unico buffer, come accade spesso con i dati di tipo long, l'applicazione chiama **SQLPutData** ripetutamente per inviare i dati in parti; in questo caso, il driver e l'origine dati per riunire i dati. Se l'applicazione passa i dati di stringa con terminazione null, il driver o l'origine dati deve rimuovere il carattere di terminazione null come parte del processo di riassemblaggio.  
  
6.  Chiamate **SQLParamData** nuovamente per indicare che è stato inviato a tutti i dati per la colonna. Se sono presenti colonne data-at-execution per cui non sono stati inviati dati, il driver restituisce SQL_NEED_DATA e il valore univoco per la colonna data-at-execution successivo. l'applicazione torna al passaggio 5. Se i dati sono stati inviati per tutte le colonne data-at-execution, i dati per la riga viene inviati all'origine dati. **SQLParamData** restituisce SQL_SUCCESS o SQL_SUCCESS_WITH_INFO e può restituire qualsiasi SQLSTATE **SQLBulkOperations** o **SQLSetPos** può restituire.  
  
 Dopo aver **SQLBulkOperations** o **SQLSetPos** restituisce SQL_NEED_DATA e prima dell'invio di dati per l'ultima colonna data-at-execution completamente, l'istruzione è in uno stato di dati necessario. In questo stato, l'applicazione può chiamare solo **SQLPutData**, **SQLParamData**, **SQLCancel**, **SQLGetDiagField**, o **SQLGetDiagRec**; tutte le altre funzioni restituiscono SQLSTATE HY010 (funzione di errore nella sequenza). La chiamata **SQLCancel** Annulla l'esecuzione dell'istruzione e restituisce lo stato precedente. Per ulteriori informazioni, vedere [tabelle di transizione dello stato di appendice b: ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).

