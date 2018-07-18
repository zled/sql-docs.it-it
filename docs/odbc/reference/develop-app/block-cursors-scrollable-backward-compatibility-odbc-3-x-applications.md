---
title: Blocco e la compatibilità di cursori scorrevoli per ODBC 3. x | Documenti Microsoft
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
- compatibility [ODBC], cursors
- backward compatibility [ODBC], cursors
- SQLExtendedFetch function [ODBC], block cursors
- cursors [ODBC], compatibility issues
- SQLFetchScroll function [ODBC], block cursors
ms.assetid: 82f6cf68-cfde-4417-9788-d6382ca14bf8
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9b4551000dd009230864ff2a4a18b8d649294987
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility-for-odbc-3x-applications"></a>Cursori a blocchi, i cursori scorrevoli e la compatibilità con le applicazioni ODBC 3. x
L'esistenza di entrambi **SQLFetchScroll** e **SQLExtendedFetch** rappresenta il primo clear suddiviso in ODBC tra l'interfaccia API (Application Programming), ovvero il set di funzioni di le chiamate dell'applicazione e il servizio Provider interfaccia SPI (), ovvero il set di funzioni il driver implementa. La divisione è necessario per conciliare il requisito in ODBC 3. *x*, che usa **SQLFetchScroll**, per allineare con gli standard e di essere compatibile con ODBC 2. *x*, che usa **SQLExtendedFetch**.  
  
 ODBC 3*x* API, ovvero il set di funzioni l'applicazione chiama, include **SQLFetchScroll** e relativi attributi di istruzione. ODBC 3*x* SPI, ovvero il set di funzioni implementa il driver, include **SQLFetchScroll**, **SQLExtendedFetch**e i relativi attributi di istruzione. Poiché ODBC non impone formalmente la divisione tra l'API e l'indice, è possibile per ODBC 3*x* alle applicazioni di chiamare **SQLExtendedFetch** e relativi attributi di istruzione. Tuttavia, non è necessario per ODBC 3*x* applicazioni per eseguire questa operazione. Per ulteriori informazioni sulle API e SPI, vedere l'introduzione a [architettura ODBC](../../../odbc/reference/odbc-architecture.md).  
  
 Per informazioni su come ODBC 3. *x* gestione Driver mapping delle chiamate a ODBC 2. *x* e ODBC 3. *x* driver e le funzioni e l'istruzione gli attributi di un'applicazione ODBC 3. *x* driver deve implementare per il blocco e i cursori scorrevoli, vedere [il Driver cosa](../../../odbc/reference/appendixes/what-the-driver-does.md) nell'appendice g: Driver le linee guida per la compatibilità con le versioni precedenti.  
  
 Nella tabella seguente sono riepilogate le funzioni e gli attributi delle istruzioni un'applicazione ODBC 3. *x* applicazione deve utilizzare con i cursori scorrevoli e di blocco. Vengono anche elencate le differenze tra ODBC 2. *x* e ODBC 3. *x* in quest'area che ODBC 3. *x* applicazioni devono tenere in considerazione per essere compatibile con ODBC 2. *x* driver.  
  
|Funzione o<br /><br /> attributo di istruzione|Commenti|  
|-----------------------------------------|--------------|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|Punta al segnalibro da utilizzare con **SQLFetchScroll**.<br /><br /> Quando un'applicazione configura questa impostazione in un ODBC 2. *x* driver, questo deve puntare a un segnalibro a lunghezza fissa.|  
|VENGONO IMPOSTATI SQL_ATTR_ROW_STATUS_PTR|Punti nella matrice di stato di riga vengono immesse **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**, e **SQLSetPos**.<br /><br /> Se un'applicazione imposta questa in una di ODBC 2. *x* driver e chiama **SQLBulkOperation** con un *operazione* di SQL_ADD prima di chiamare **SQLFetchScroll**,  **SQLFetch**, o **SQLExtendedFetch**, SQLSTATE HY011 (Impossibile impostare l'attributo ora) viene restituito.<br /><br /> Quando un'applicazione chiama **SQLFetch** in un'API ODBC 2. *x* driver, **SQLFetch** viene eseguito il mapping a **SQLExtendedFetch** e pertanto restituisce i valori in questa matrice.|  
|SQL_ATTR_ROWS_FETCHED_PTR|Punta al buffer in cui **SQLFetch** e **SQLFetchScroll** restituire il numero di righe recuperate.<br /><br /> Quando un'applicazione chiama **SQLFetch** in un'API ODBC 2. *x* driver, **SQLFetch** viene eseguito il mapping a **SQLExtendedFetch** e pertanto restituisce un valore di questo buffer.|  
|SQL_ATTR_ROW_ARRAY_SIZE|Imposta le dimensioni del set di righe.<br /><br /> Se un'applicazione chiama **SQLBulkOperations** con un *operazione* di SQL_ADD in un'API ODBC 2. *x* SQL_ROWSET_SIZE driver verrà utilizzato per la chiamata, non SQL_ATTR_ROW_ARRAY_SIZE, poiché la chiamata viene eseguito il mapping a **SQLSetPos** con un *operazione* di SQL_ADD, che usa SQL_ROWSET_SIZE.<br /><br /> La chiamata **SQLSetPos** con un *operazione* di SQL_ADD o **SQLExtendedFetch** in un database ODBC 2. *x* driver utilizza SQL_ROWSET_SIZE.<br /><br /> La chiamata **SQLFetch** o **SQLFetchScroll** in un database ODBC 2. *x* driver utilizza SQL_ATTR_ROW_ARRAY_SIZE.|  
|**SQLBulkOperations**|Esegue operazioni di inserimento e inserisce un segnalibro. Quando **SQLBulkOperations** con un *operazione* di SQL_ADD viene chiamato in un ODBC 2. *x* driver, questo viene mappato a **SQLSetPos** con un *operazione* di SQL_ADD. Di seguito sono indicati i dettagli di implementazione:<br /><br /> -Quando si lavora con un ODBC 2. *x* driver, in modo implicito allocato ARD che è associata a un'applicazione deve utilizzare il *StatementHandle*; non è possibile allocare ARD un'altra per l'aggiunta di righe, poiché le operazioni di descrittore esplicita sono non è supportato in un'API ODBC 2. *x* driver. Un'applicazione deve utilizzare **SQLBindCol** da associare alla ARD, non **SQLSetDescField** o **SQLSetDescRec**.<br />-Quando si chiama un'applicazione ODBC 3. *x* driver, un'applicazione può chiamare **SQLBulkOperations** con un *operazione* di SQL_ADD prima di chiamare **SQLFetch** o **SQLFetchScroll**. Quando si chiama un'API ODBC 2. *x* driver, un'applicazione deve chiamare **SQLFetchScroll** prima di chiamare **SQLBulkOperations** con un'operazione di SQL_ADD.|  
|**SQLFetch**|Restituisce il set di righe successivo. Di seguito sono indicati i dettagli di implementazione:<br /><br /> -Quando un'applicazione chiama **SQLFetch** in un'API ODBC 2. *x* driver, questo viene mappato a **SQLExtendedFetch**.<br />-Quando un'applicazione chiama **SQLFetch** in un'applicazione ODBC 3. *x* driver, viene restituito il numero di righe specificato con l'attributo di istruzione SQL_ATTR_ROW_ARRAY_SIZE.|  
|**SQLFetchScroll**|Restituisce il set di righe specificato. Di seguito sono indicati i dettagli di implementazione:<br /><br /> -Quando un'applicazione chiama **SQLFetchScroll** in un'API ODBC 2. *x* driver, restituisce SQLSTATE 01S01 (errore nella riga) prima di ogni errore che si applica a una singola riga. Ciò avviene perché solo ODBC 3*x* Driver Manager esegue il mapping a **SQLExtendedFetch** e **SQLExtendedFetch** restituisce il valore SQLSTATE. Quando un'applicazione chiama **SQLFetchScroll** in un'applicazione ODBC 3. *x* driver, non restituisce mai 01S01 SQLSTATE (errore nella riga).<br />-Quando un'applicazione chiama **SQLFetchScroll** in un'API ODBC 2. *x* driver con *FetchOrientation* impostato su SQL_FETCH_BOOKMARK, il *FetchOffset* argomento deve essere impostato su 0. SQLSTATE HYC00 (funzionalità facoltativa non implementata) viene restituito se recupero basato su offset segnalibro viene eseguito un tentativo con un ODBC 2. *x* driver.|  
  
> [!NOTE]  
>  ODBC 3. *x* applicazioni non devono utilizzare **SQLExtendedFetch** o l'attributo di istruzione SQL_ROWSET_SIZE. Al contrario, dovrebbero usare **SQLFetchScroll** e l'attributo di istruzione SQL_ATTR_ROW_ARRAY_SIZE. ODBC 3. *x* applicazioni non devono utilizzare **SQLSetPos** con un *operazione* di SQL_ADD è invece necessario utilizzare **SQLBulkOperations** con un *Operazione* di SQL_ADD.
