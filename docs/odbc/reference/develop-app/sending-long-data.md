---
title: L'invio di dati Long | Documenti Microsoft
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
- long data [ODBC]
- sending long data [ODBC]
ms.assetid: ea989084-a8e6-4737-892e-9ec99dd49caf
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3a15a3fdd69a1578392d34adac08b297269df7cf
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32913966"
---
# <a name="sending-long-data"></a>L'invio di dati Long
Definiscono DBMS *dati long* come qualsiasi carattere o dati binari in una determinata dimensione, ad esempio 254 caratteri. Che non sia possibile archiviare l'intero elemento di dati long in memoria, ad esempio quando l'elemento rappresenta un documento di testo lungo o una bitmap. Poiché tali dati non possono essere archiviati in un unico buffer, la invia al driver in parti con l'origine dati **SQLPutData** quando viene eseguita l'istruzione. Parametri per il quale i dati vengono inviati in fase di esecuzione sono noti come *parametri data-at-execution*.  
  
> [!NOTE]  
>  Un'applicazione può inviare effettivamente qualsiasi tipo di dati in fase di esecuzione con **SQLPutData**, anche se solo i caratteri e i dati binari possono essere inviati in parti. Tuttavia, se i dati sono sufficientemente piccoli da rientrare in un unico buffer, non è in genere utilizzare **SQLPutData**. È molto più semplice associare il buffer e consentire il driver di recuperare i dati dal buffer.  
  
 Per inviare dati in fase di esecuzione, l'applicazione esegue le azioni seguenti:  
  
1.  Passa un valore a 32 bit che identifica il parametro di *ParameterValuePtr* argomento in **SQLBindParameter** anziché passare l'indirizzo di un buffer. Questo valore non viene analizzato dal driver. Verrà restituito all'applicazione in un secondo momento, pertanto consigliabile significato particolare per l'applicazione. Ad esempio, potrebbe essere il numero del parametro o l'handle di un file contenente dati.  
  
2.  Passa l'indirizzo di un buffer di lunghezza/indicatore nel *StrLen_or_IndPtr* argomento di **SQLBindParameter**.  
  
3.  Archivia SQL_DATA_AT_EXEC o il risultato di SQL_LEN_DATA_AT_EXEC (*lunghezza*) (macro) nel buffer di lunghezza/indicatore. Entrambi questi valori indicano al driver che verranno inviati con i dati per il parametro **SQLPutData**. SQL_LEN_DATA_AT_EXEC (*lunghezza*) viene utilizzata per inviare dati di tipo long a un'origine dati che è necessario conoscere il numero di byte di dati long verrà inviato in modo che è possibile preallocare spazio. Per determinare se un'origine dati richiede questo valore, l'applicazione chiama **SQLGetInfo** con l'opzione SQL_NEED_LONG_DATA_LEN. Tutti i driver devono supportare questa macro. Se l'origine dati non richiede la lunghezza in byte, il driver può ignorata.  
  
4.  Chiamate **SQLExecute** o **SQLExecDirect**. Il driver rileva che un buffer di lunghezza/indicatore contiene il valore SQL_DATA_AT_EXEC o il risultato di SQL_LEN_DATA_AT_EXEC (*lunghezza*) (macro) e restituisce SQL_NEED_DATA come valore restituito della funzione.  
  
5.  Chiamate **SQLParamData** restituito in risposta a di SQL_NEED_DATA. Se i dati di tipo long devono essere inviato, **SQLParamData** restituisce SQL_NEED_DATA. Nel buffer a cui fa riferimento il *ValuePtrPtr* argomento, il driver restituisce il valore che identifica il parametro data-at-execution. Se è presente più di un parametro data-at-execution, l'applicazione deve utilizzare questo valore per determinare quale parametro per inviare i dati; il driver non è necessario per richiedere i dati per i parametri data-at-execution in un ordine particolare.  
  
6.  Chiamate **SQLPutData** per inviare i dati dei parametri del driver. Se i dati del parametro non rientrano in un singolo buffer, come accade spesso con i dati di tipo long, l'applicazione chiama **SQLPutData** ripetutamente per inviare i dati in parti; in questo caso, il driver e l'origine dati per riunire i dati. Se l'applicazione passa i dati di stringa con terminazione null, il driver o l'origine dati deve rimuovere il carattere di terminazione null come parte del processo di riassemblaggio.  
  
7.  Chiamate **SQLParamData** nuovamente per indicare che è stato inviato a tutti i dati per il parametro. Se sono presenti parametri data-at-execution per cui non sono stati inviati dati, il driver restituisce SQL_NEED_DATA e il valore che identifica il parametro successivo. l'applicazione torna al passaggio 6. Se i dati sono stati inviati per tutti i parametri data-at-execution, viene eseguita l'istruzione. **SQLParamData** restituisce SQL_SUCCESS o SQL_SUCCESS_WITH_INFO e può restituiscono qualsiasi valore o diagnostico che **SQLExecute** o **SQLExecDirect** può restituire.  
  
 Dopo aver **SQLExecute** o **SQLExecDirect** restituisce SQL_NEED_DATA e prima dell'invio di dati per l'ultimo parametro data-at-execution completamente, l'istruzione è in uno stato di dati necessario. Mentre un'istruzione si trova in uno stato di dati necessario, l'applicazione può chiamare solo **SQLPutData**, **SQLParamData**, **SQLCancel**, **SQLGetDiagField**, o **SQLGetDiagRec**; tutte le altre funzioni restituiscono SQLSTATE HY010 (funzione di errore nella sequenza). La chiamata **SQLCancel** Annulla l'esecuzione dell'istruzione e restituisce lo stato precedente. Per ulteriori informazioni, vedere [tabelle di transizione dello stato di appendice b: ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Per un esempio di invio dei dati in fase di esecuzione, vedere il [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md) descrizione della funzione.
