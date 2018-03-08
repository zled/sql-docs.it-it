---
title: L'esecuzione posizionato istruzioni Update e Delete | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- positioned deletes [ODBC]
- cursor library [ODBC], positioned update or delete
- positioned updates [ODBC]
- ODBC cursor library [ODBC], positioned update or delete
ms.assetid: 1d64f309-2a6e-4ad1-a6b5-e81145549c56
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c201b69b2f4a756233c65ad1a1f2730b04e3d79f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="executing-positioned-update-and-delete-statements"></a>L'esecuzione di istruzioni di eliminazione e aggiornamento posizionato
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 Dopo il recuperata di un blocco di dati con un'applicazione **SQLFetchScroll**, è possibile aggiornare o eliminare i dati nel blocco. Per eseguire un aggiornamento posizionato o eliminazione, l'applicazione:  
  
1.  Chiamate **SQLSetPos** per posizionare il cursore sulla riga deve essere aggiornato o eliminato.  
  
2.  Costruisce un aggiornamento posizionato o l'istruzione delete con la sintassi seguente:  
  
     **AGGIORNAMENTO** *-nome della tabella*  
  
     **IMPOSTARE** *colonna identificatore*  **=**  {*espressione* &#124; **NULL**}  
  
     [**,** *colonna identificatore*  **=**  {*espressione* &#124; **NULL**}]  
  
     **WHERE CURRENT OF** *-nome del cursore*  
  
     **DELETE FROM** *-nome della tabella* **WHERE CURRENT OF** *-nome del cursore*  
  
     Il modo più semplice per costruire il **impostare** clausola in un'istruzione di aggiornamento posizionato consiste nell'utilizzare marcatori di parametro per ogni colonna devono essere aggiornati e utilizzare **SQLBindParameter** per associare questi ai buffer di set di righe per il riga da aggiornare. In questo caso, il tipo di dati C del parametro sarà lo stesso come il tipo di dati C del buffer di set di righe.  
  
3.  Se verrà eseguito un'istruzione di aggiornamento posizionato, aggiorna i buffer di set di righe per la riga corrente. Dopo aver eseguito un'istruzione di aggiornamento posizionato, la libreria di cursori copia i valori di ogni colonna nella riga corrente nella relativa cache.  
  
    > [!CAUTION]  
    >  Se l'applicazione non viene aggiornato correttamente i buffer di set di righe prima di eseguire un'istruzione di aggiornamento posizionato, i dati nella cache non saranno corretto dopo l'esecuzione dell'istruzione.  
  
4.  Esegue l'aggiornamento posizionato o l'istruzione delete tramite un'istruzione diversa rispetto all'istruzione associato al cursore.  
  
    > [!CAUTION]  
    >  Il **dove** clausola costruito dalla libreria di cursori per identificare la riga corrente può avere esito negativo identificare le righe, identificare una riga diversa o più di una riga. Per ulteriori informazioni, vedere [la costruzione di istruzioni di ricerca](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 Tutti posizionato aggiornamento e le istruzioni delete richiedano un nome di cursore. Per specificare il nome del cursore, un'applicazione chiama **SQLSetCursorName** prima dell'apertura del cursore. Per utilizzare il nome del cursore generato dal driver, un'applicazione chiama **SQLGetCursorName** dopo l'apertura del cursore.  
  
 Dopo il cursore libreria esegue un aggiornamento posizionato o istruzione delete, la matrice di stato, i buffer di set di righe e cache gestita dalla libreria di cursori contengono i valori mostrati nella tabella seguente.  
  
|Istruzione utilizzata|Valore nella matrice di stato di riga|Valori in<br /><br /> buffer di set di righe|Valori in<br /><br /> buffer di cache|  
|--------------------|-------------------------------|----------------------------------|---------------------------------|  
|Aggiornamento posizionato|SQL_ROW_UPDATED|Nuovi valori [1]|Nuovi valori [1]|  
|Delete posizionata|SQL_ROW_DELETED|Valori precedenti|Valori precedenti|  
  
 [1] l'applicazione deve aggiornare i valori nei buffer di set di righe prima di eseguire l'istruzione di aggiornamento posizionato. Dopo l'esecuzione dell'istruzione di aggiornamento posizionato, la libreria di cursori copia i valori nei buffer di set di righe nella cache.
