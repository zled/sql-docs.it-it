---
title: Utilizzo delle matrici di parametri | Documenti Microsoft
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
helpviewer_keywords:
- arrays of parameter values [ODBC]
- parameter arrays [ODBC]
ms.assetid: 5a28be88-e171-4f5b-bf4d-543c4383c869
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fe2d85bd347477c0acc775a4f071968d6d8b15d6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-arrays-of-parameters"></a>Utilizzo delle matrici di parametri
L'utilizzo delle matrici di parametri, l'applicazione chiama **SQLSetStmtAttr** con un *attributo* argomento di SQL_ATTR_PARAMSET_SIZE per specificare il numero di set di parametri. Chiama **SQLSetStmtAttr** con un *attributo* argomento di SQL_ATTR_PARAMS_PROCESSED_PTR per specificare l'indirizzo di una variabile in cui il driver può restituire il numero di set di parametri elaborati, inclusi i set di errore. Chiama **SQLSetStmtAttr** con un *attributo* argomento di SQL_ATTR_PARAM_STATUS_PTR in modo che punti a una matrice in cui si desidera ottenere informazioni sullo stato per ogni riga di valori di parametro. Il driver archivia questi indirizzi nella struttura che viene mantenuta per l'istruzione.  
  
> [!NOTE]  
>  In ODBC 2. *x*, **SQLParamOptions** è stato chiamato per specificare più valori per un parametro. In ODBC 3. *x*, la chiamata a **SQLParamOptions** è stato sostituito dalle chiamate a **SQLSetStmtAttr** per impostare gli attributi SQL_ATTR_PARAMSET_SIZE e SQL_ATTR_PARAMS_PROCESSED_ARRAY .  
  
 Prima di eseguire l'istruzione, l'applicazione imposta il valore di ogni elemento di ogni matrice associato. Quando viene eseguita l'istruzione, il driver utilizza le informazioni memorizzata per recuperare i valori dei parametri e li inviano a origine dati. Se possibile, il driver deve inviare questi valori come matrici. Sebbene l'utilizzo di matrici di parametri è meglio implementata tramite l'istruzione SQL con tutti i parametri nella matrice con una singola chiamata all'origine dati, questa funzionalità non è ampiamente disponibile in DBMS oggi. Tuttavia, possono simulare i driver tramite l'esecuzione di un'istruzione SQL più volte, ciascuna con un singolo set di parametri.  
  
 Prima di un'applicazione utilizza le matrici di parametri, è necessario assicurarsi che siano supportati per i driver utilizzati dall'applicazione. Questa operazione può essere eseguita in due modi:  
  
-   Utilizzare solo i driver che supportano le matrici di parametri. L'applicazione può codificare i nomi dei driver oppure l'utente in modo che venga usare solo questi driver. Applicazioni personalizzate e le applicazioni verticali in genere utilizzano un set limitato di driver.  
  
-   Verificare il supporto di matrici di parametri in fase di esecuzione. Un driver supporta matrici di parametri se è possibile impostare l'attributo di istruzione SQL_ATTR_PARAMSET_SIZE su un valore maggiore di 1. Applicazioni generiche e le applicazioni verticali comunemente verificare il supporto di matrici di parametri in fase di esecuzione.  
  
 La disponibilità di conteggi delle righe e set di risultati in esecuzione con parametri può essere determinata chiamando **SQLGetInfo** con le opzioni SQL_PARAM_ARRAY_ROW_COUNTS e SQL_PARAM_ARRAY_SELECTS. Per **inserire**, **aggiornamento**, e **eliminare** istruzioni, l'opzione SQL_PARAM_ARRAY_ROW_COUNTS indica se il numero di riga singola (uno per ogni set di parametri) disponibile (SQL_PARC_BATCH) o se i conteggi delle righe vengono raggruppate in un unico (SQL_PARC_NO_BATCH). Per **selezionare** istruzioni, l'opzione SQL_PARAM_ARRAY_SELECTS indica se un set di risultati è disponibile per ogni set di parametri (SQL_PAS_BATCH) o se solo un set di risultati è disponibile (SQL_PAS_NO_BATCH). Se il driver non supporta istruzioni di creazione di set di risultati deve essere eseguito con una matrice di parametri, SQL_PARAM_ARRAY_SELECTS restituisce SQL_PAS_NO_SELECT. Si tratta di dati specifici dell'origine se le matrici di parametri possono essere utilizzate con altri tipi di istruzioni, soprattutto perché l'utilizzo di parametri in queste istruzioni sarebbe specifici dell'origine dati e non seguirà la grammatica SQL ODBC.  
  
 La matrice a cui fa riferimento l'attributo di istruzione SQL_ATTR_PARAM_OPERATION_PTR può essere utilizzata per ignorare le righe di parametri. Se un elemento della matrice è impostato su SQL_PARAM_IGNORE, il set di parametri corrispondente a tale elemento verrà esclusi i **SQLExecute** o **SQLExecDirect** chiamare. La matrice a cui fa riferimento l'attributo SQL_ATTR_PARAM_OPERATION_PTR è allocata e compilata l'applicazione e letti dal driver. Se le righe recuperate vengono utilizzate come parametri di input, è possono utilizzare i valori della matrice di stato di riga nella matrice di operazione del parametro.  
  
## <a name="error-processing"></a>Errore di elaborazione  
 Se si verifica un errore durante l'esecuzione dell'istruzione, la funzione di esecuzione restituisce un errore e imposta la variabile di numeri di riga per il numero della riga contenente l'errore. Si tratta di dati specifici dell'origine se tutte le righe ad eccezione del fatto venga eseguito il set di errore o se tutte le righe prima (ma non dopo) vengono eseguiti l'errore impostato. Poiché l'elaborazione di set di parametri, il driver imposta il buffer specificato dall'attributo di istruzione SQL_ATTR_PARAMS_PROCESSED_PTR per il numero della riga in fase di elaborazione. Se tutti i set con la differenza che vengono eseguiti il set di errore, il driver imposta il buffer per SQL_ATTR_PARAMSET_SIZE dopo l'elaborazione di tutte le righe.  
  
 Se è stato impostato il tipo di istruzione sql_attr_param_status_ptr, **SQLExecute** o **SQLExecDirect** restituisce il *matrice di stato* che fornisce lo stato di ogni set di parametri. Matrice di stato del parametro è allocata dall'applicazione e compilata dal driver. Gli elementi indicano se l'istruzione SQL è stata eseguita correttamente per la riga di parametri o se si è verificato un errore durante l'elaborazione di set di parametri. Se si è verificato un errore, il driver imposta il valore corrispondente nella matrice di stato del parametro per SQL_PARAM_ERROR e viene restituito SQL_SUCCESS_WITH_INFO. L'applicazione può controllare la matrice di stato per determinare quali righe sono state elaborate. Utilizza il numero di riga, l'applicazione può spesso per risolvere il problema e riprendere l'elaborazione.  
  
 Utilizzo di matrice di stato del parametro è determinato dalle opzioni di SQL_PARAM_ARRAY_ROW_COUNTS e SQL_PARAM_ARRAY_SELECTS restituite da una chiamata a **SQLGetInfo**. Per **inserire**, **aggiornamento**, e **eliminare** istruzioni, la matrice di stato del parametro viene compilato con informazioni sullo stato se viene restituito SQL_PARC_BATCH per SQL_PARAM_ARRAY_ ROW_COUNTS, ma non se SQL_PARC_NO_BATCH viene restituito. Per **selezionare** istruzioni, la matrice di stato del parametro viene inserita se SQL_PAS_BATCH viene restituito per SQL_PARAM_ARRAY_SELECT, ma non viene restituito SQL_PAS_NO_BATCH o SQL_PAS_NO_SELECT.  
  
## <a name="data-at-execution-parameters"></a>Parametri data-at-Execution  
 Se uno dei valori nella matrice di lunghezza/indicatore SQL_DATA_AT_EXEC o il risultato di SQL_LEN_DATA_AT_EXEC (*lunghezza*) (macro), i dati per tali valori vengono inviati con **SQLPutData** nel modo consueto. Gli aspetti seguenti di questo processo tenere commento speciali perché non sono immediatamente evidenti:  
  
-   Quando il driver restituisce SQL_NEED_DATA, deve impostare l'indirizzo della variabile di numeri di riga per riga per cui necessita di dati. Come nel caso a valore singolo, l'applicazione non può prevedere l'ordine in cui il driver richiederà i valori dei parametri all'interno di un singolo set di parametri. Se si verifica un errore durante l'esecuzione di un parametro data-at-execution, il buffer specificato dall'attributo di istruzione SQL_ATTR_PARAMS_PROCESSED_PTR viene impostato sul numero di riga in cui l'errore si è verificato, lo stato per la riga nella matrice di stato di riga specificata da il tipo di istruzione sql_attr_param_status_ptr è impostata su SQL_PARAM_ERROR e la chiamata a **SQLExecute**, **SQLExecDirect**, **SQLParamData**, o  **SQLPutData** restituisce SQL_ERROR. Il contenuto del buffer è indefinito se **SQLExecute**, **SQLExecDirect**, o **SQLParamData** restituire SQL_STILL_EXECUTING.  
  
-   Poiché il driver non interpreta il valore di *ParameterValuePtr* argomento di **SQLBindParameter** per i parametri data-at-execution, se l'applicazione fornisce un puntatore a una matrice,  **SQLParamData** non estrarre e restituire un elemento della matrice per l'applicazione. Al contrario, restituisce che il valore scalare l'applicazione fosse fornita. Ciò significa che il valore restituito da **SQLParamData** è l'applicazione non è sufficiente specificare il parametro per il quale deve inviare i dati, l'applicazione deve anche considerare il numero di riga corrente.  
  
     Se solo alcuni degli elementi della matrice di parametri sono parametri data-at-execution, l'applicazione deve passare l'indirizzo di una matrice in *ParameterValuePtr* che contiene elementi per tutti i parametri. Questa matrice viene interpretata in genere per i parametri che non sono parametri data-at-execution. Per i parametri data-at-execution, il valore che **SQLParamData** fornisce all'applicazione, che potrebbe essere in genere usata per identificare i dati che richiede il driver in questo caso, è sempre l'indirizzo della matrice.
