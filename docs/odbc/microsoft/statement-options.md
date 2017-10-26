---
title: Opzioni dell'istruzione | Documenti Microsoft
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
- custom statement options [ODBC]
- statement options [ODBC]
- ODBC driver for Oracle [ODBC], statement options
ms.assetid: cd73b769-c8b5-43e0-9f80-b3011b7a6162
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8e73ba4a1fe0bd8a7fb65b8986745f9d2edee550
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="statement-options"></a>Opzioni dell'istruzione
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 Queste opzioni consentono la personalizzazione di un'istruzione di esecuzione specifico all'interno di un'applicazione.  
  
|Opzione dell'istruzione|Note|  
|----------------------|-----------|  
|SQL_BIND_TYPE|Non può superare la memoria disponibile o 2.147.483.647 byte.|  
|SQL_CONCURRENCY|Per i valori consentiti, vedere il [combinazioni di concorrenza e il tipo di cursore](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|  
|SQL_CURSOR_TYPE|Il driver non SQL_CURSOR_DYNAMIC. Vedere [SQLSetScrollOptions](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md) per ulteriori informazioni. Per i valori consentiti, vedere il [combinazioni di concorrenza e il tipo di cursore](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|  
|SQL_GET_BOOKMARK|Restituisce un valore integer a 32 bit che rappresenta il segnalibro per il numero di record corrente. Get di sola lettura. Impossibile impostare.|  
|SQL_KEYSET_SIZE|Può essere impostata solo su 0.|  
|SQL_MAX_ROWS|Il numero massimo di righe da restituire dal risultato di un set.|  
|SQL_ROW_NUMBER|Restituisce un intero a 32 bit che specifica la posizione della riga corrente nel set di risultati. Get di sola lettura. Impossibile impostare.|  
|SQL_ROWSET_SIZE|Non può superare i 4.294.967.296 righe. Tuttavia, è necessario disporre memoria virtuale sufficiente nel computer per gestire la richiesta.|  
|SQL_USE_BOOKMARKS|Supporta l'impostazione SQL_USE_BOOKMARKS su SQL_UB_ON ed espone i segnalibri di lunghezza fissa.|

