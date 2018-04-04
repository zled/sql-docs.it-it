---
title: 'Appendice b: le tabelle di transizione di stato di ODBC | Documenti Microsoft'
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- state transitions [ODBC]
- transitioning states [ODBC], about state transitions
- state transitions [ODBC], about state transitions
ms.assetid: 15088dbe-896f-4296-b397-02bb3d0ac0fb
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2dabd364fb0a7415a4cf05035d06f5a1dd5838e5
ms.sourcegitcommit: 6bd21109abedf64445bdb3478eea5aaa7553fa46
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2018
---
# <a name="appendix-b-odbc-state-transition-tables"></a>Appendice b: le tabelle di transizione di stato di ODBC
Le tabelle in questa appendice illustrano come le funzioni ODBC causano transizioni di ambiente, connessione, istruzione e gli stati del descrittore. Lo stato dell'ambiente, connessione, istruzione o descrittore determina in genere quando possono essere chiamate le funzioni che utilizzano il tipo di handle (ambiente di connessione, istruzione o descrittore) corrispondente. Gli stati di ambiente, connessione, l'istruzione e descrittore sovrappongano approssimativamente come illustrato nelle figure seguenti. Ad esempio, la sovrapposizione esatto della connessione stati C5 e C6 e istruzione indica S1 tramite S12 dati dipende dall'origine, poiché le transazioni iniziano in momenti diversi da origini dati diverse e lo stato di descrittore D1i (allocati in modo implicito descrittore) a seconda dei casi lo stato dell'istruzione a cui è associato il descrittore, mentre stato D1e (allocati in modo esplicito descrittore) è indipendentemente dallo stato di qualsiasi istruzione. Per una descrizione di ogni stato, vedere [transizioni di ambiente](../../../odbc/reference/appendixes/environment-transitions.md), [connessione transizioni](../../../odbc/reference/appendixes/connection-transitions.md), [istruzione transizioni](../../../odbc/reference/appendixes/statement-transitions.md), e [descrittore transizioni ](../../../odbc/reference/appendixes/descriptor-transitions.md), più avanti in questa appendice.  
  
 Gli stati di connessione e dell'ambiente si sovrappongono nel modo seguente:  
  
 ![Sovrapposizione degli stati della connessione e dell'ambiente](../../../odbc/reference/appendixes/media/app01.gif "il server app01")  
  
 Gli stati di connessione e l'informativa si sovrappongono nel modo seguente:  
  
 ![Connessione e delle istruzioni stati sovrapposizione](../../../odbc/reference/appendixes/media/app02.gif "app02")  
  
 Gli stati del descrittore e dell'istruzione si sovrappongono nel modo seguente:  
  
 ![Istruzione e descrittore stati sovrapposizione](../../../odbc/reference/appendixes/media/app03.gif "app03")  
  
 Gli stati di connessione e descrittore si sovrappongono nel modo seguente:  
  
 ![Connessione e descrittore stati sovrapposizione](../../../odbc/reference/appendixes/media/app04.gif "app04")  
  
 Ogni voce in una tabella di transizione può essere uno dei valori seguenti:  
  
-   **--** -Lo stato rimane invariato dopo l'esecuzione della funzione.  
  
-   **E**  
     ***n*** , **C*n * * *, **S*n * **, oppure **1!d * n***  : consente di spostare lo stato di ambiente, connessione, istruzione o descrittore per il stato specificato.  
  
-   **(QUALI)**  , Ovvero un handle non valido passato alla funzione. Se l'handle è stato un handle null oppure un handle valido di tipo errato, ad esempio, è stato passato un handle di connessione quando era obbligatorio un handle di istruzione, ovvero la funzione non restituisca SQL_INVALID_HANDLE; in caso contrario, il comportamento è indefinito e probabilmente irreversibile. Questo errore viene visualizzato solo quando è solo possibile risultato della chiamata di funzione nello stato specificato. Questo errore non modifica lo stato e viene sempre rilevato da Gestione Driver, come indicato dalle parentesi.  
  
-   **NS** : stato successivo. La transizione di istruzione è lo stesso come se l'istruzione non ha effettuato tramite gli stati asincroni. Ad esempio, si supponga che un'istruzione che crea un set di risultati entra in stato S11 dallo stato S1 perché **SQLExecDirect** restituito SQL_STILL_EXECUTING. La notazione NS nello stato S11 significa che le transizioni per l'istruzione sono le stesse per un'istruzione nello stato S1 che crea un set di risultati. Se **SQLExecDirect** restituisce un errore, l'istruzione rimane nello stato S1; se ha esito positivo, l'istruzione viene spostato in modo da indicare S5; se i dati necessari, l'istruzione viene spostato in modo da indicare S8; e se è ancora in esecuzione, rimane nello stato S11.  
  
-   ***XXXXX*** oppure **(*XXXXX*)** , ovvero un valore SQLSTATE è correlata alla tabella delle transizioni; SQLSTATE rilevate da Gestione Driver sono racchiusi tra parentesi. La funzione ha restituito SQL_ERROR e il valore SQLSTATE specificato, ma non modifica lo stato. Ad esempio, se **SQLExecute** viene chiamato prima **SQLPrepare**, restituisce SQLSTATE HY010 (funzione di errore nella sequenza).  
  
> [!NOTE]  
>  Le tabelle non verranno visualizzati gli errori non correlati alle tabelle che non modificano lo stato di transizione. Ad esempio, quando **SQLAllocHandle** viene chiamata in stato dell'ambiente E1 ed restituisce SQLSTATE HY001 (errore di allocazione della memoria), l'ambiente rimane nello stato E1; questa opzione non è mostrata nella tabella di transizione dell'ambiente per  **SQLAllocHandle**.  
  
 Se l'ambiente, connessione, l'istruzione o descrittore possibile spostare in più Stati, ogni possibile stato viene visualizzato e uno o più piè di pagina illustrano le condizioni in cui ogni transizione viene eseguita. Le note seguenti può essere visualizzata alcuna tabella.  
  
|Piè di pagina|Significato|  
|--------------|-------------|  
|b|Prima o dopo. Il cursore era posizionato prima dell'inizio del set di risultati o dopo la fine del set di risultati.|  
|c|Funzione corrente. La funzione corrente era in esecuzione in modo asincrono.|  
|d|I dati devono essere. La funzione ha restituito SQL_NEED_DATA.|  
|e|Errore. La funzione ha restituito SQL_ERROR.|  
|i|Riga non valida. Il cursore era posizionato su una riga nel risultato set e la riga era state eliminate o si è verificato un errore in un'operazione della riga. Se la matrice di stato di riga esiste già, il valore nella matrice di stato di riga per la riga è SQL_ROW_DELETED o SQL_ROW_ERROR. (La matrice di stato di riga a cui punta l'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR.)|  
|nf|Non è stato trovato. La funzione ha restituito SQL_NO_DATA. Non si applica quando **SQLExecDirect**, **SQLExecute**, o **SQLParamData** restituisce SQL_NO_DATA dopo l'esecuzione di una ricerca istruzioni update o delete.|  
|np|Non è preparato. L'istruzione non è stato preparato.|  
|rif Nr|Nessun risultato. L'istruzione non o non è stato creato un set di risultati.|  
|o|Altra funzione. Un'altra funzione era in esecuzione in modo asincrono.|  
|p|Preparato. L'istruzione è stata preparata.|  
|r|Risultati. L'istruzione verrà o è stato creato un set di risultati (eventualmente vuota).|  
|s|Esito positivo. La funzione ha restituito SQL_SUCCESS_WITH_INFO o SQL_SUCCESS.|  
|v|Riga valida. Il cursore era posizionato su una riga nel set di risultati e la riga fosse stata inserita correttamente, è stato aggiornato, o un'altra operazione nella riga era stata completata correttamente. Se la matrice di stato di riga esiste già, il valore nella matrice di stato di riga per la riga è stata SQL_ROW_ADDED, SQL_ROW_SUCCESS o SQL_ROW_UPDATED. (La matrice di stato di riga a cui punta l'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR.)|  
|x|In esecuzione. La funzione ha restituito SQL_STILL_EXECUTING.|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
 In questo esempio, la riga di transizione ambiente tabella per **SQLFreeHandle** quando *HandleType* è SQL_HANDLE_ENV come indicato di seguito.  
  
|E0<br /><br /> Non allocato|E1<br /><br /> Allocato|E2<br /><br /> Connessione|  
|------------------------|----------------------|-----------------------|  
|(IH)|E0|(HY010)|  
  
 Se **SQLFreeHandle** viene chiamato con stato ambiente E0 *HandleType* impostato su SQL_HANDLE_ENV, gestione Driver non restituisca SQL_INVALID_HANDLE. Se viene chiamato con stato E1 *HandleType* impostato su SQL_HANDLE_ENV, l'ambiente passa allo stato E0 se la funzione ha esito positivo e rimane in stato E1 se la funzione ha esito negativo. Se viene chiamato con stato E2 *HandleType* impostato su SQL_HANDLE_ENV, gestione Driver sempre restituisce SQL_ERROR e SQLSTATE HY010 (funzione di errore nella sequenza) e l'ambiente rimane nello stato E2.  
  
 Per comprendere le tabelle di transizione di stato, è necessario capire quale elemento (ambiente di connessione, istruzione o descrittore) fanno riferimento. Si supponga che una funzione accetta l'handle di un elemento di tipo X. La tabella di transizione di stato X per tale funzione viene descritto come chiamare la funzione, con l'handle di un elemento di tipo X, interessa quell'elemento. Ad esempio **SQLDisconnect** accetta un handle di connessione. La tabella di transizione dello stato di connessione per **SQLDisconnect** descrive come **SQLDisconnect** influisce sullo stato della connessione per il quale viene chiamato.  
  
 Si supponga che una funzione accetta l'handle di un elemento di tipo Y, dove Y non è uguale a X. La tabella di transizione di stato X per tale funzione viene descritto come chiamare la funzione, con un handle di tipo X che è associata all'elemento di tipo Y, interessa l'elemento di tipo Y. Ad esempio, l'istruzione transizione tabella di stato per **SQLDisconnect** descrive come **SQLDisconnect** influisce sullo stato di un'istruzione quando viene chiamato con l'handle di connessione con il quale il istruzione è associata.  
  
 Questa appendice contiene gli argomenti seguenti.  
  
-   [Transizioni di ambiente](../../../odbc/reference/appendixes/environment-transitions.md)  
  
-   [Transizioni di connessione](../../../odbc/reference/appendixes/connection-transitions.md)  
  
-   [Transizioni di istruzione](../../../odbc/reference/appendixes/statement-transitions.md)  
  
-   [Transizioni dei descrittori](../../../odbc/reference/appendixes/descriptor-transitions.md)
