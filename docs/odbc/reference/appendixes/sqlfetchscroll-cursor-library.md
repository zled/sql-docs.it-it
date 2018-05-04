---
title: SQLFetchScroll (libreria di cursori) | Documenti Microsoft
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
- SQLFetchScroll function [ODBC], Cursor Library
ms.assetid: 4417e57c-31dd-475e-8fe9-eab00a459c80
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b0c3e9709cd3aeced11116ab88c5323d4462abd2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlfetchscroll-cursor-library"></a>SQLFetchScroll (libreria di cursori)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 In questo argomento viene illustrato l'utilizzo del **SQLFetchScroll** funzione nella libreria di cursori. Per informazioni generali su **SQLFetchScroll**, vedere [funzione SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md).  
  
 La libreria di cursori implementa **SQLFetchScroll** chiamando ripetutamente **SQLFetch** nel driver. Il trasferimento dei dati recuperati dal driver per i buffer di set di righe forniti dall'applicazione. Inoltre memorizza nella cache i dati nei file di memoria e disco. Quando un'applicazione richiede un nuovo set di righe, la libreria di cursori recupera in base alle esigenze dal driver (se non è stata precedentemente recuperata) o dalla cache (se si è stato recuperato in precedenza). Infine, la libreria di cursori mantiene lo stato dei dati memorizzati nella cache e restituisce le informazioni per l'applicazione della matrice di stato di riga.  
  
 Quando si utilizza la libreria di cursori, le chiamate a **SQLFetchScroll** ReadContentAsBinHex con chiamate a **SQLFetch** o **SQLExtendedFetch**.  
  
 Quando si utilizza la libreria di cursori, le chiamate a **SQLFetchScroll** sono supportati sia per ODBC 2. *x* e per ODBC 3. *x* driver.  
  
## <a name="rowset-buffers"></a>Buffer di set di righe  
 È possibile ottimizzare il trasferimento dei dati dal driver per il buffer di set di righe fornito dall'applicazione, se la libreria di cursori:  
  
-   L'applicazione utilizza l'associazione per riga.  
  
-   Esistono inutilizzati byte tra i campi della struttura che dell'applicazione dichiara per contenere una riga di dati.  
  
-   I campi in cui **SQLFetch** o **SQLFetchScroll** restituisce la lunghezza/indicatore per una colonna segue il buffer per tale colonna e precede il buffer per la colonna successiva. Questi campi sono facoltativi.  
  
 Quando l'applicazione richiede un nuovo set di righe, la libreria di cursori recupera i dati dalla cache e dal driver in base alle esigenze. Se i vecchi e nuovi set di righe si sovrappongono, la libreria di cursori possibile ottimizzare le prestazioni riutilizzando i dati dalle sezioni dei buffer di set di righe sovrapposti. Pertanto, le modifiche non salvate ai buffer di set di righe vengono perse, a meno che non si sovrappongono i vecchi e nuovi set di righe e le modifiche sono nelle sezioni dei buffer di set di righe sovrapposte. Per salvare le modifiche, un'applicazione invia un'istruzione di aggiornamento posizionato.  
  
 Si noti che la libreria di cursori Aggiorna sempre i buffer di set di righe con i dati dalla cache quando un'applicazione chiama **SQLFetchScroll** con il *FetchOrientation* argomento impostato su SQL_FETCH_RELATIVE e il *FetchOffset* argomento impostato su 0.  
  
 La libreria di cursori supporta la chiamata **SQLSetStmtAttr** con un *attributo* di SQL_ATTR_ROW_ARRAY_SIZE per modificare le dimensioni del set di righe mentre è aperto un cursore. Le nuove dimensioni del set di righe saranno effettive la volta successiva che **SQLFetchScroll** viene chiamato.  
  
## <a name="result-set-membership"></a>Appartenenza a un Set di risultati  
 La libreria di cursori recupera dati dal driver solo quando l'applicazione lo richiede. A seconda dell'origine dati e l'impostazione dell'attributo di istruzione SQL_CONCURRENCY, questo comporta le conseguenze seguenti:  
  
-   I dati recuperati dalla libreria di cursori potrebbero essere diversi da quelli che erano disponibili al momento che dell'esecuzione dell'istruzione. Ad esempio, dopo l'apertura del cursore, le righe inserite in un punto oltre la posizione corrente del cursore possono essere recuperate da alcuni driver.  
  
-   I dati nel set di risultati potrebbero essere bloccati dall'origine dati per la libreria di cursori e pertanto non essere disponibili ad altri utenti.  
  
 Dopo che la libreria di cursori ha memorizzato nella cache di una riga di dati, in grado di rilevare le modifiche a tale riga nell'origine dati sottostante (tranne gli aggiornamenti posizionati e le eliminazioni operativo nella cache del cursore stesso). Questo errore si verifica perché, per le chiamate a **SQLFetchScroll**, la libreria di cursori recupera mai nuovamente i dati dall'origine dati. Al contrario, recupera nuovamente i dati dalla cache.  
  
## <a name="scrolling"></a>Lo scorrimento  
 La libreria di cursori supporta i seguenti tipi di istruzione fetch in **SQLFetchScroll**.  
  
|Tipo di cursore|Tipi di recupero|  
|-----------------|-----------------|  
|Forward-only|SQL_FETCH_NEXT|  
|Statico|SQL_FETCH_NEXT<br /><br /> SQL_FETCH_PRIOR<br /><br /> SQL_FETCH_FIRST<br /><br /> SQL_FETCH_LAST<br /><br /> SQL_FETCH_RELATIVE<br /><br /> SQL_FETCH_ABSOLUTE<br /><br /> SQL_FETCH_BOOKMARK|  
  
## <a name="errors"></a>Errori  
 Quando **SQLFetchScroll** viene chiamato e l'altra delle chiamate a **SQLFetch** restituisce SQL_ERROR, i ricavi di libreria di cursore come indicato di seguito. Dopo aver completato questi passaggi, la libreria di cursori continua l'elaborazione.  
  
1.  Chiamate **SQLGetDiagRec** per ottenere informazioni sull'errore dal driver e si registra come record di diagnostica in Gestione Driver.  
  
2.  Imposta il campo SQL_DIAG_ROW_NUMBER nel record di diagnostica sul valore appropriato.  
  
3.  Imposta il campo SQL_DIAG_COLUMN_NUMBER nel record di diagnostica sul valore appropriato, se applicabile; in caso contrario, imposta su 0.  
  
4.  Imposta il valore per la riga nella matrice di stato di riga da SQL_ROW_ERROR errore.  
  
 Dopo il cursore è stato chiamato libreria **SQLFetch** più volte nella sua implementazione di **SQLFetchScroll**, qualsiasi errore o avviso restituito da una delle chiamate a **SQLFetch** verrà incluso un record di diagnostica e possono essere recuperati da una chiamata a **SQLGetDiagRec**. Se i dati sono stati troncati durante recupero, i dati troncati ora si trovano nella cache della libreria di cursori. Le chiamate successive a **SQLFetchScroll** scorrere fino a una riga con dati troncati restituirà i dati troncati e non verrà generato alcun avviso perché i dati vengono recuperati dalla cache della libreria di cursori. Per tenere traccia delle lunghezza dei dati restituiti in modo che possa determinare se i dati restituiti in un buffer sono stati troncati, un'applicazione deve essere associato il buffer di lunghezza/indicatore.  
  
## <a name="bookmark-operations"></a>Operazioni di segnalibro  
 La libreria di cursori supporta la chiamata **SQLFetchScroll** con un *FetchOrientation* impostato su sql_fetch_bookmark. Supporta anche la specifica di un offset nel *FetchOffset* argomento che può essere utilizzato nell'operazione di segnalibro. Questo è l'unica operazione segnalibro che supporta la libreria di cursori. La libreria di cursori non supporta la chiamata **SQLBulkOperations**.  
  
 Se l'applicazione è impostato l'attributo di istruzione SQL_ATTR_USE_BOOKMARKS e per la colonna del segnalibro è stato associato, la libreria di cursori genera un segnalibro a lunghezza fissa e lo restituisce all'applicazione. La libreria di cursori crea e gestisce i segnalibri utilizzato; non utilizza i segnalibri mantenuti nell'origine dati. Quando **SQLFetchScroll** viene chiamato per recuperare un blocco di dati che sono già stati trasferiti dall'origine dati, recupera i dati dalla cache di libreria del cursore. Di conseguenza, il segnalibro utilizzato in una chiamata a **SQLFetchScroll** con un *FetchOrientation* di SQL_FETCH_BOOKMARK devono essere create e gestite dalla libreria di cursori.  
  
## <a name="interaction-with-other-functions"></a>Interazione con altre funzioni  
 Un'applicazione deve chiamare **SQLFetch** o **SQLFetchScroll** prima che prepara o esegue qualsiasi posizionato istruzioni update o delete.
