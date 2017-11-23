---
title: 'Appendice b: tabelle di transizione dello stato di ODBC | Documenti Microsoft'
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- state transitions [ODBC]
- transitioning states [ODBC], about state transitions
- state transitions [ODBC], about state transitions
ms.assetid: 15088dbe-896f-4296-b397-02bb3d0ac0fb
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2a191cb539aec61150f30d8c083dfba7dd2d2069
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="appendix-b-odbc-state-transition-tables"></a>Appendice b: tabelle di transizione dello stato di ODBC
Le tabelle in questa appendice illustrano come le funzioni ODBC causano transizioni di ambiente, connessione, istruzione e gli stati del descrittore. Lo stato dell'ambiente, una connessione, istruzione o un descrittore determina in genere quando le funzioni che utilizzano il corrispondente tipo di handle (ambiente di connessione, istruzione o descrittore) possono essere chiamate. Gli stati di ambiente, connessione, l'istruzione e descrittore sovrappongano approssimativamente come illustrato nelle figure seguenti. Ad esempio, la sovrapposizione esatto della connessione stati C5 e C6 e istruzione indica S1 tramite S12 dati dipende dall'origine, poiché le transazioni iniziano in momenti diversi da origini dati diverse e varia a seconda dello stato di descrittore D1i (allocati in modo implicito descrittore) durante lo stato D1e (allocati in modo esplicito descrittore) lo stato dell'istruzione a cui è associato il descrittore, è indipendentemente dallo stato di qualsiasi istruzione. Per una descrizione di ogni stato, vedere [transizioni di ambiente](../../../odbc/reference/appendixes/environment-transitions.md), [connessione transizioni](../../../odbc/reference/appendixes/connection-transitions.md), [istruzione transizioni](../../../odbc/reference/appendixes/statement-transitions.md), e [descrittore transizioni ](../../../odbc/reference/appendixes/descriptor-transitions.md), più avanti in questa appendice.  
  
 Gli stati di connessione e dell'ambiente si sovrappongono come indicato di seguito:  
  
 ![Sovrapposizione degli stati di connessione e dell'ambiente](../../../odbc/reference/appendixes/media/app01.gif "il server app01")  
  
 Gli stati di connessione e l'istruzione si sovrappongono come indicato di seguito:  
  
 ![Istruzione e connessione stati sovrapposizione](../../../odbc/reference/appendixes/media/app02.gif "app02")  
  
 Gli stati del descrittore e dell'istruzione si sovrappongono come indicato di seguito:  
  
 ![Istruzione e descrittore stati sovrapposizione](../../../odbc/reference/appendixes/media/app03.gif "app03")  
  
 Gli stati di connessione e descrittore si sovrappongono come indicato di seguito:  
  
 ![Connessione e descrittore stati sovrapposizione](../../../odbc/reference/appendixes/media/app04.gif "app04")  
  
 Ogni voce in una tabella di transizione può essere uno dei valori seguenti:  
  
-   **--**-Lo stato rimane invariato dopo l'esecuzione della funzione.  
  
-   **E**  
     ***n***,  **C*n***,  **S*n***, o  **D*n** *, lo stato di ambiente, connessione, istruzione o descrittore passa allo stato specificato.  
  
-   **(QUALI)**  , Ovvero un handle non valido passato alla funzione. Se l'handle è stato un handle null oppure un handle valido di tipo errato, ad esempio, un handle di connessione è stato passato quando è richiesto un handle di istruzione, la funzione non restituisca SQL_INVALID_HANDLE; in caso contrario, il comportamento è indefinito e probabilmente irreversibile. Questo errore viene visualizzato solo quando è il risultato della chiamata della funzione nello stato specificato solo possibile. Questo errore non modifica lo stato e viene sempre rilevato da Gestione Driver, come indicato dalle parentesi.  
  
-   **NS** : stato successivo. La transizione di istruzione è lo stesso come se l'istruzione non ha subito gli stati asincroni. Ad esempio, si supponga che un'istruzione che crea un set di risultati è in stato S11 dallo stato S1 perché **SQLExecDirect** restituito SQL_STILL_EXECUTING. La notazione NS nello stato S11 significa che le transizioni per l'istruzione siano uguali a quelli per un'istruzione nello stato S1 che crea un set di risultati. Se **SQLExecDirect** restituisce un errore, l'istruzione rimane nello stato S1; se ha esito positivo, l'istruzione passa allo stato S5; se necessita di dati, l'istruzione viene spostato in modo da indicare S8; e se è ancora in esecuzione, rimane in stato S11.  
  
-   ***XXXXX*** o  **(*XXXXX*) * *: un valore SQLSTATE è correlata alla tabella di transizione. SQLSTATE rilevate da Gestione Driver vengono racchiusi tra parentesi. La funzione ha restituito SQL_ERROR e SQLSTATE specificato, ma non modifica lo stato. Ad esempio, se **SQLExecute** viene chiamato prima **SQLPrepare**, restituisce SQLSTATE HY010 (funzione di errore nella sequenza).  
  
> [!NOTE]  
>  Le tabelle non vengono visualizzati gli errori non correlati alle tabelle che non modificano lo stato di transizione. Ad esempio, quando **SQLAllocHandle** viene chiamato con stato ambiente E1 e restituisce SQLSTATE HY001 (errore di allocazione della memoria), l'ambiente rimane nello stato E1; ciò non è indicato nella tabella di transizione dell'ambiente per  **SQLAllocHandle**.  
  
 Se l'ambiente, connessione, l'istruzione o descrittore possa passare allo più stato, ogni possibile stato viene visualizzato e uno o più piè di pagina illustrano le condizioni in cui ogni transizione viene eseguita. Note seguenti possono essere visualizzata una tabella.  
  
|Piè di pagina|Significato|  
|--------------|-------------|  
|b|Prima o dopo. Il cursore è posizionato prima dell'inizio del set di risultati o dopo la fine del set di risultati.|  
|c|Funzione corrente. La funzione corrente era in esecuzione in modo asincrono.|  
|d|Bisogno di dati. La funzione ha restituito SQL_NEED_DATA.|  
|e|Errore. La funzione ha restituito SQL_ERROR.|  
|i|Riga non valida. Il cursore è posizionato su una riga nel risultato set e la riga era state eliminate o si è verificato un errore in un'operazione della riga. Se la matrice di stato di riga esiste già, il valore della matrice di stato di riga per la riga è SQL_ROW_DELETED o SQL_ROW_ERROR. (La matrice di stato di riga a cui punta l'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR.)|  
|nf|Non è stato trovato. La funzione ha restituito SQL_NO_DATA. Non si applica quando **SQLExecDirect**, **SQLExecute**, o **SQLParamData** restituisce SQL_NO_DATA dopo l'esecuzione di una ricerca istruzioni update o delete.|  
|np|Non è preparato. L'istruzione non è stato preparato.|  
|rif Nr|Nessun risultato. L'istruzione non fornirà o non ha creato un set di risultati.|  
|o|Altra funzione. Un'altra funzione era in esecuzione in modo asincrono.|  
|p|Preparato. L'istruzione è stata preparata.|  
|r|Risultati. L'istruzione verrà o ha creato un set di risultati (eventualmente vuota).|  
|s|Esito positivo. La funzione ha restituito SQL_SUCCESS_WITH_INFO o SQL_SUCCESS.|  
|v|Riga valida. Il cursore è posizionato su una riga nel set di risultati e la riga era stata inserita, aggiornate correttamente, o un'altra operazione nella riga è stata completata correttamente. Se la matrice di stato di riga esiste già, il valore della matrice di stato di riga per la riga è SQL_ROW_ADDED, SQL_ROW_SUCCESS o SQL_ROW_UPDATED. (La matrice di stato di riga a cui punta l'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR.)|  
|x|In esecuzione. La funzione ha restituito SQL_STILL_EXECUTING.|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
 In questo esempio, la riga di transizione ambiente tabella per **SQLFreeHandle** quando *HandleType* è impostato su SQL_HANDLE_ENV come indicato di seguito.  
  
|E0<br /><br /> Non allocato|E1<br /><br /> Allocato|E2<br /><br /> Connessione|  
|------------------------|----------------------|-----------------------|  
|(QUALI)|E0|(HY010)|  
  
 Se **SQLFreeHandle** viene chiamato con stato ambiente E0 *HandleType* impostato su SQL_HANDLE_ENV, gestione Driver non restituisca SQL_INVALID_HANDLE. Se viene chiamato con stato E1 *HandleType* impostato su SQL_HANDLE_ENV, l'ambiente passa allo stato E0 se la funzione ha esito positivo e rimane in stato E1 se la funzione ha esito negativo. Se viene chiamato con stato E2 *HandleType* impostato su SQL_HANDLE_ENV, gestione Driver sempre restituisce SQL_ERROR e SQLSTATE HY010 (funzione di errore nella sequenza) e l'ambiente rimane nello stato E2.  
  
 Per comprendere le tabelle di transizione di stato, è necessario capire quale elemento (ambiente di connessione, istruzione o descrittore) fanno riferimento. Si supponga che una funzione accetta l'handle di un elemento di tipo X. La tabella di transizione dello stato di X per tale funzione viene descritta la funzione, con l'handle di un elemento di tipo X, influisce su tale elemento come chiamante. Ad esempio, **SQLDisconnect** accetta un handle di connessione. La tabella di transizione dello stato di connessione per **SQLDisconnect** viene descritto come **SQLDisconnect** influisce sullo stato della connessione per il quale viene chiamato.  
  
 Si supponga che una funzione accetta l'handle di un elemento di tipo Y, in cui non è uguale a X Y. La tabella di transizione dello stato di X per tale funzione viene descritto come chiamare la funzione, con un handle di tipo X associata con l'elemento di tipo Y, interessa l'elemento di tipo Y. Ad esempio, l'istruzione tabella transizione dello stato per **SQLDisconnect** viene descritto come **SQLDisconnect** influisce sullo stato di un'istruzione quando viene chiamato con l'handle di connessione alla quale il l'istruzione è associato.  
  
 Questa appendice contiene gli argomenti seguenti.  
  
-   [Transizioni di ambiente](../../../odbc/reference/appendixes/environment-transitions.md)  
  
-   [Transizioni di connessione](../../../odbc/reference/appendixes/connection-transitions.md)  
  
-   [Transizioni di istruzione](../../../odbc/reference/appendixes/statement-transitions.md)  
  
-   [Transizioni dei descrittori](../../../odbc/reference/appendixes/descriptor-transitions.md)
